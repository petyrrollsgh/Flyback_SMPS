# Flyback_SMPS
+12V, -12V, 5V, 3.3V DC power supply with 24V DC input with flyback topology


# Split-Rail, Switch-Mode, Power Supply
  For the Universal Sensor Interface (USI) project, I needed a power supply capable of powering op-amps with both +12V and -12V rails as well as +5V and might as well have +3.3V too.  I had previously designed (KiCad), had fabricated (from JPLPCB), ordered components (Mouser), hand-assembled and tested a very small board.  But the purpose of that board was mostly to figure out the entire workflow and practice soldering.  This was my first attempt to actually build something useful.  It worked, but there were a couple of minor errors that I was able to fix without ordering new boards.  However, the schematic shown below is corrected from the actual tested board.  I am confident the new schematic will work as intended.  Most of the errors were minor such as inverted diodes and incorrect values for the voltage adjustment.  The major critical addition was that of R22 a 10K resistor.  It turns out that without some current draw the fly back circuit will quickly overheat the protection circuit composed of  diodes D4 and D5.  

  The circuit was based largely on the LM2586 data sheet and followed the “Figure 32. Triple-Output Flyback Regulator” schematic.  The data sheet gives recommendations for coils to use and I chose the Q4338-BL coil.  The outputs were then sent to LT1963 and LT3015 LDO voltage regulators with the +5V output used to drive the regulated +3.3V output.

  Out of an abundance of caution I used a 4-layer board to ensure all power circuits had clear ground paths for current flow.  The extra cost of a 4-layer board is minor in comparison to the component cost and my own labor.  I was also careful to isolate the switch mode part of the system from the LDO parts of the circuit.  

  I spent a considerable amount of time studying how to ensure correct current flow paths to reduce noise.  There are many lectures and videos on the subject which emphasize that energy flow passes through the space between wires and/or circuit paths and not is the circular path that most schematics tend to emphasize.  But putting this concept into action became a difficult practical problem.  I just didn’t know if my routing was idiotic or not.  Eventually I decided that the best circuit design principle was to clearly determine where current traveled between components and ensure that all tracks out of a device were matched with a suitable ground plane through which the return current could pass and that no other subcircuits used or crossed that pathway.  My best analogy to the entire concept was that of an AC signal connected to a twisted pair of wires which then separated and terminated in a “T” to form an antenna.  The best circuit design was to keep the wires as tightly twisted as possible by providing a large and unique ground return path.  Inevitably at actual circuit devices these paths must separate forming an antenna.  I tried to keep these separations as minimal as possible.  

  All components were hand soldered and this was time consuming and difficult work.  For future circuits, I used the silk screen and a modified a toaster oven with a programmable power control to ramp up the temperature to appropriate levels.  The stainless-steel screen was less than 10 bucks, a minimal cost compared to my time, and produced superior solders.  This even made soldering 603 capacitors a breeze.  However, the screen tended to put down too much paste for the finer 0.5 mm spacing of VSSOP devices but was great for the larger spacing on SOIC devices.  
LM2586 4-V to 40-V, 3-A Step-Up Wide VIN Flyback Regulator datasheet (Rev. E)

  The KiCad files are on GitHub at https://github.com/petyrrollsgh/Flyback_SMPS.  Use these as a good starting point for your own design.  Double check everything. Many footprints will be missing.   If you don’t use KiCad then I suggest you download a copy and use that to translate the schematic to whatever you are using.  Better yet just redraw the schematic in you ECAD software and create your own PCB layout using my project as helpful suggestions.


![image](https://github.com/user-attachments/assets/aa0b4043-fd44-46f5-8e5b-7c09af51414c)

![image](https://github.com/user-attachments/assets/7022a2cc-61d6-4480-89e5-616dcea5f5fd)


 
 

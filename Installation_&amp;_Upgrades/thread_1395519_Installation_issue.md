---
title: "Installation issue"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by 1slackr on 2010-01-31
I have installed Ubuntu on 2 laptops with no problems. Both run cool and smooth. I have a Compaq Presario SR5110NX Desktop. 
On the Boot with the CD for installation, I get to click English, then a choice of install with no changes, or install, etc. menu. I click install with no changes to start. The screen starts like an install is happening, then goes dark. After a couple minutes the CD stops, and the hard drive indicator blinks like it's in idle. I wait another 10 min, no changes. Tried several times, no luck. Tried in safe graphics mode, screen blinks many times at the 2 minute install mark.
The Hardware:  Motherboard manufacturer's name: ECS MCP61PM-HM,
Processor = Athlon 64 3500, Graphics = NVIDIA GeForce 6150SE nForce 430,  1.5g ddr2 ram, Hard drive - 120 GB SATA 3G.
I had Vista on the machine, have switched to XP and updated the drivers for the hardware for xp. Works better now, but would rather have linux. .any ideas?

---

### Post by 1slackr on 2010-02-01
> **1slackr said:**
> I have installed Ubuntu on 2 laptops with no problems. Both run cool and smooth. I have a Compaq Presario SR5110NX Desktop. 
On the Boot with the CD for installation, I get to click English, then a choice of install with no changes, or install, etc. menu. I click install with no changes to start. The screen starts like an install is happening, then goes dark. After a couple minutes the CD stops, and the hard drive indicator blinks like it's in idle. I wait another 10 min, no changes. Tried several times, no luck. Tried in safe graphics mode, screen blinks many times at the 2 minute install mark.
The Hardware:  Motherboard manufacturer's name: ECS MCP61PM-HM,
Processor = Athlon 64 3500, Graphics = NVIDIA GeForce 6150SE nForce 430,  1.5g ddr2 ram, Hard drive - 120 GB SATA 3G.
I had Vista on the machine, have switched to XP and updated the drivers for the hardware for xp. Works better now, but would rather have linux. .any ideas?
I have now run wubi for the live install.  Everything seemed to install. .dual boot, hit ubuntu, then the installer finishes. Back to dual boot, hit ubuntu, and the icon comes up for about a minute, then nothing. Waited 10 minutes, still nothing. Can anyone help?

---

### Post by dukedempsey on 2010-02-01
I just installed It on my HP laptop from the live CD. I had to change the boot parameters. Go here for info 

[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)
 
Id did this 
 
"Some boot problems can be fixed by simply removing the quiet splash-- at the end of the boot options line. If that fails, you may try some of the commonly used options listed below:" 
 
And I also had to check the first option on the provided list.  "acpi=off"
 
However...after I succesfully installed to a USB stick and tried to boot that, I had to use the default parameters for it to boot.
 
Your system might be differnt. Trial and Error

---

### Post by 1slackr on 2010-02-01
Thanks, I tried that one, no luck. Appreciate the info, I'll keep the trial and error going. .

---


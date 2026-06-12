---
title: "Toshiba Satellite U925t"
date: 2015-12-19
forum: Installation &amp; Upgrades
---

### Post by Pierre_Renaud on 2015-12-19
I was given a Toshiba Satellite U925t. I installed Ubuntu, which seems to go pretty smoothly. However, it won't boot. All I get a the Toshiba splash screen. I looked all over the net and couldn't find anything helpful.    

I also tried to boot without success using Lubuntu from a USB key. 

Any help would be appreciated.

---

### Post by oldfred on 2015-12-19
What are the specs? CPU, RAM, video chip?

From live installer add Boot-Repair, and run the report.
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by ubfan1 on 2015-12-19
Also the firmware (BIOS) version on that machine should be made current if it is not already.

---

### Post by Pierre_Renaud on 2015-12-19
Here's the report from Boot Repair:

[http://paste.ubuntu.com/14100465/](http://paste.ubuntu.com/14100465/)

---

### Post by Pierre_Renaud on 2015-12-19
Bios: 1.20
EC Version: 1.00

---

### Post by oldfred on 2015-12-19
Newer Toshiba now is like HP.
They modify UEFI to only boot "Windows" by description which is not even allowed by UEFI spec.
Since only Ubuntu the simple work around is to add an UEFI boot entry that says "Windows" but really boots shim.

This assumes ESP - efi system partition is sda1, otherwise additional parameters required to tell it a different drive or partition.
 C: Use efibootmgr if only Ubuntu install, not dual boot, install to make Windows UEFI description boot grub or shim file
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

You may also want to add a fallback or default boot entry. That would be in a new folder /EFI/Boot/ and you copy shim into that folder and rename to bootx64.efi which UEFI uses as a default for devices. You may have to add it to UEFI or it may find it, or offer it. Details if desired in link in my signature or we can post those.

---

### Post by Pierre_Renaud on 2015-12-19
Hum, I copied/pasted the instruction to make sure I didn't make any mistake and it said command not found.

Here's a screen shot from Gparted: [https://goo.gl/photos/QwseNffpneEv4wQe6](https://goo.gl/photos/QwseNffpneEv4wQe6)

---

### Post by oldfred on 2015-12-19
Post this from UEFI boot of installer.
the efibootmgr command only works if booting in UEFI mode, which you had for Summary Report.
Or post this:
sudo efibootmgr -v

Then you need to change to boot "Windows" entry which then is really shim or grub2's Secure boot entry. That should work whether secure boot is on or not.

---

### Post by Pierre_Renaud on 2015-12-19
I'll have to find someone to guide me. This is way over my head. I keep rebooting and I keep getting [COLOR=#000000]command not found. Thank you all for trying to help. I'll try to find someone who can make sense of this post.[/COLOR]

---

### Post by oldfred on 2015-12-19
You should be booting the Ubuntu live install flash drive or DVD in UEFI boot mode. Otherwise it will not work.
And you need to open a terminal.

 Get a terminal by <ctrl_+alt+F1> & back to gui with ctrl alt f7
[https://help.ubuntu.com/community/UsingTheTerminal/](https://help.ubuntu.com/community/UsingTheTerminal/)
In Ubuntu you start a terminal window with ctrl + alt + t
or via the menu Program -- Accessories -- Terminal

---

### Post by ubfan1 on 2015-12-19
Looks like the BIOS version is up to 1.5.  Check at the Toshiba site and use your model:
[http://support.toshiba.com/support/driversResults?freeText=3575531](http://support.toshiba.com/support/driversResults?freeText=3575531)

---

### Post by Pierre_Renaud on 2015-12-20
Thanks for being so patient.

I reformatted the drive, re-installed Ubuntu, went though the following steps:

Converting Ubuntu into UEFI mode (with Boot Repair)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I tried sudo efibootmgr -v again, and this is what I get:
[https://goo.gl/photos/Bfxdxisxdh29NKaB8](https://goo.gl/photos/Bfxdxisxdh29NKaB8)

---

### Post by Pierre_Renaud on 2015-12-20
Gee, everything is completed... I don't even know which one I have. There are 6 Satellite U925t models. 

> **ubfan1 said:**
> Looks like the BIOS version is up to 1.5.  Check at the Toshiba site and use your model:
[http://support.toshiba.com/support/driversResults?freeText=3575531](http://support.toshiba.com/support/driversResults?freeText=3575531)

---

### Post by Pierre_Renaud on 2015-12-20
Last attempt...


Formatted in FAT32


Installation of Ubuntu 15.04 (Vivid Vervet) Desktop on UEFI Firmware Systems
[http://www.tecmint.com/ubuntu-15-04-installation-on-uefi-firmware/](http://www.tecmint.com/ubuntu-15-04-installation-on-uefi-firmware/)


Converting Ubuntu into UEFI mode with Boot Repair
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


Boot-Repair extra info
[http://paste.ubuntu.com/14114717/](http://paste.ubuntu.com/14114717/)

---

### Post by Pierre_Renaud on 2015-12-20
Hum, I just made a bootable USB key with rEFInd Boot Manager

[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)

Just booted for the first time.

---

### Post by Pierre_Renaud on 2015-12-20
Thanks again for all you help. Somehow, I could not make it work with the Terminal. I ended up doing it with Nautilus as root. Yay!! Problem Solved.

---


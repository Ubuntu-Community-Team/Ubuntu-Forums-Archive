---
title: "Do you lose your Grub menu in a dual boot Lubuntu 14.10 and Windows 8.1 ?"
date: 2015-03-28
forum: Installation &amp; Upgrades
---

### Post by googleorganico on 2015-03-28
First of all check out if you already ***disabled fast boot  and secure boot on Windows 8*** trying go to ***Control Pane***l and follow this instructions [http://www.instructables.com/id/Dual-Boot-Ubuntu-and-Windows-8-UEFI/step4/Deactivating-Fast-Startup-and-Secureboot]("http://www.instructables.com/id/Dual-Boot-Ubuntu-and-Windows-8-UEFI/step4/Deactivating-Fast-Startup-and-Secureboot/")

Then build a Live Usb persistent of your Lubuntu 14.10 and start it!Make sure you got the right version of UEFI Lubuntu version if it is your case!
Then when you running Lubuntu 14.10 on usb live and  [install Boot Repai]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu")r and follow this instructions! [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)   For me worked fine with first option in instructions!

After this you could go to Lubuntu console and short keys are ( Ctrl +  Alt + T ),  and do: [I][B]Sudo update-grub2 

[/B][/I]Then do: ***Sudo apt-get update***
Then:  [I][B]Sudo reboot

This might work so good for me then it worked fine for me![/B][/I]

---


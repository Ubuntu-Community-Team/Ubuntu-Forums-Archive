---
title: "Installing to laptop with RST enabled"
date: 2020-05-01
forum: Installation &amp; Upgrades
---

### Post by mpl21 on 2020-05-01
[SIZE=2][FONT=arial][COLOR=#333333]Today I wanted to install a dualboot system to my new Lenovo Ideapad C340. It came with Windows installed and I wanted to install Ubuntu next to it. During the installation process I got the message that RST was enabled on this laptop and that I had to follow [this]("https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347") tutorial.[/COLOR]
[COLOR=#333333]I followed it closely but despite making the changes in the windows register Windows had to be recovered.  So I'm in the command prompt, and commands lik this are not working: 
[/COLOR]> [FONT=system]bcdedit /deletevalue {default} safeboot
[/FONT][COLOR=#333333]So I need to dive into the bootpartition. The bootpartition had no assigned letter, so I first did that (don't know if this was a good idea). In that partition I can reach the /BOOT folder but the following command 
[/COLOR]> [FONT=system]ren BCD BCD.bak
[/FONT][COLOR=#333333]doesn't work.
[/COLOR]
What should I do? Is a dual boot impossible? Should I install Ubuntu alone, and will this work, now that RST is disabled in the bios? Or is it still possible to dual boot?
[/FONT][/SIZE][FONT=Ubuntu][COLOR=#333333][SIZE=2][FONT=arial]I also posted this problem in the dutch [ubuntuforum]("https://forum.ubuntu-nl.org/index.php?topic=107723.0"), but got no reaction. [/FONT][/SIZE]
[/COLOR][/FONT]

---

### Post by CelticWarrior on 2020-05-01
You need to install AHCI support in Windows (google that). Then change the mode from Intel RST to AHCI, install Ubuntu and then you have a dual-boot.

---

### Post by mpl21 on 2020-05-01
If I google that I only find the registry changes that are also mentioned on the (official Ubuntu) website I linked to above. I have made these changes in the Windows registry, still Windows is not booting properly after changing the bios setting to ahci.

---

### Post by CelticWarrior on 2020-05-01
Prepare a Windows installation USB to boot from while set to AHCI and use the repair feature. That should be enough.

---

### Post by oldfred on 2020-05-02
More instructions:

Windows AHCI instructions - some have found safeboot method better
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571)
[https://askubuntu.com/questions/1148120/ubuntu-18-0x-not-detecting-windows-ssd-during-installation](https://askubuntu.com/questions/1148120/ubuntu-18-0x-not-detecting-windows-ssd-during-installation) & 
[https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on#963100](https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on#963100)
[https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/](https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/)
AHCI enable - May have to unlock bitlocker if used
[https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243](https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243)

---


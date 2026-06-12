---
title: "Unable to install GRUB"
date: 2011-09-19
forum: Installation &amp; Upgrades
---

### Post by AlecTaylor on 2011-09-19
[IMG]http://i.stack.imgur.com/65dgI.png[/IMG]
  Unfortunately (as you can see) I cannot install grub. I have tried /dev/sda as well.
  Here is my partitioning schema:
  [IMG]http://i.stack.imgur.com/JupwB.png[/IMG]
  Troubleshooting + problems:
  
[LIST]
[*]Installed Windows 8 to logical partition (somehow got marked "active")
[*]Found Metro BCD to be lacking (takes forever to load, doesn't have other non-Windows OSs)
[*]Installed EasyBCD, couldn't detect the BCD. So I made my Win7 primary the active
[*]Something stuffed up in its BCD, it redirects to Win8 BCD, so I want to make GRUB default
[*]11.04 GRUB can't be activated for some reason
[/LIST]
  So I download 11.10 x64 Beta on my old laptop, push it to a USB, and attempt to install it on my other hard-drive.
  

Then I get the first mentioned error. I have also tried (before and after) running sudo grub-install manually on the respective drives, to no avail.
  

When I now attempt to boot to the hard-disk, I get PXE boot.


  Please suggest further troubleshooting steps (e.g. LILO?).


Thanks for all recommendations,


Alec Taylor

---

### Post by raja.genupula on 2011-09-19
you said you have 11.04 , are you able to boot into 11.04?

---

### Post by varunendra on 2011-09-19
Hi Alec,

Boot from the live USB you created, choose to "Try" ubuntu (not "Install"). Then in the live mode, open gparted and make sure the correct drive has the boot flag on it. Then reboot, go into BIOS and make sure the correct drive is set as first boot device in the boot order. If confused due to both drives being similar, just try toggling them in the boot order.

Skipping to PXE suggests that perhaps the BIOS is not even checking the hard drive for booting and one of the possible reasons may be absence of boot flag on the drive which has the priority in boot order.

For troubleshooting with grub, download > extract > run [boot info script ]("http://bootinfoscript.sourceforge.net/")and post back the contents of RESULTS.txt here (follow the steps on the linked page to see how to use it).

---


---
title: "CD Installation - HELP PLZ"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by davidallan on 2007-12-08
Hi,

Just to you know ive install Ubuntu on my laptop fine with the x64 cd.

So now i'm trying to install on my quad processor pc, live cd loads to menu. i select install/load says kernel alive then blank screen!, cd spins hdd lights flash but nothing else just a blank screen, :(  i've tried VGA install. Same.

Any suggestions??

thanks

---

### Post by Pumalite on 2007-12-08
I'm not sure we are ready for quad processors quite yet. Please correct me someone if I'm wrong.

---

### Post by davidallan on 2007-12-08
seems to be give a PCI : Failed to allocate mem resource error!

ive a Nvidia 9xxx 700+ram video card. i think its more a problem with that:confused:

gutted wanted to get rid of vista but guessing its gonna have to stay...buggar.

---

### Post by PmDematagoda on 2007-12-08
Linux handles Quad core Pumalite, I know a person who uses Ubuntu on his Quad core PC.

About the issue with the Live CD, why not try the Alternate CD?

---

### Post by davidallan on 2007-12-08
Sorry what alternate CD??


> **PmDematagoda said:**
> Linux handles Quad core Pumalite, I know a person who uses Ubuntu on his Quad core PC.

About the issue with the Live CD, why not try the Alternate CD?

---

### Post by Pumalite on 2007-12-08
From here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below sign 'Start Download'

---

### Post by davidallan on 2007-12-08
:oops: sorry yes i've just found it!

thanks

---

### Post by davidallan on 2007-12-08
weird how the x64 bit cd install give me a pci error and a blank screen. i've just installed the x86 fine with no problems. shame / any ideas why? oh and alternate cd installed but after reboot did same, i selected a option to debug and it looked like it was checking the boot scripts and file volumes then just ended at the command line. i typed startx and it come up and worked. however network card wasnt installed so it wasnt quite running as it should...ideas??

thanks

---

### Post by Pumalite on 2007-12-08
Finished the Alternate CD installation and at the blank screen:
Ctrl+Alt+F1 to get command line
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose 'vesa' as the driver
Then: startx
Or sudo /etc/init.d/gdm start

---

### Post by davidallan on 2007-12-08
ok thanks for reply > u think it will work???? :D

> **Pumalite said:**
> Finished the Alternate CD installation and at the blank screen:
Ctrl+Alt+F1 to get command line
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose 'vesa' as the driver
Then: startx
Or sudo /etc/init.d/gdm start

---

### Post by Pumalite on 2007-12-08
Try it.

---

### Post by davidallan on 2007-12-08
ok installing now.

one other thing; i have two 19" lcd screens, on the x86 version both were duplicating the image. (vista i had them to work as separate desktops) so i installed the restricted driver for the nvidia card. reboot. then one of the screens went blank. so into screens control panel and it only shows 1 screen...the 2nd is grayed out?...any idea why?

> **Pumalite said:**
> Try it.

---

### Post by Pumalite on 2007-12-08
Try with one monitor only and once you are IN the system, I'll tell you how to setup dual monitors.

---

### Post by davidallan on 2007-12-08
ok thanks > shouldnt be 2 long now 10mins max > so on the reboot after install blank screen will appear then...

Ctrl+Alt+F1 to get command line
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose 'vesa' as the driver
Then: startx
Or sudo /etc/init.d/gdm start

fingers crossed here!

---

### Post by davidallan on 2007-12-08
nope dead, monitor looking for signal as i type :(

gutted. so gu ess its back to x86 or Vista :(

---

### Post by Pumalite on 2007-12-08
Did you get the interface and all the steps?

---

### Post by davidallan on 2007-12-08
yeah i selected Vesa then most of the defaults or what i thought were best. works fine like i said before from the debug at command line typing startx. even after that reconfig. just when system restarts and goes to normal boot i get the pci error and blank screen.

thanks

---

### Post by Pumalite on 2007-12-08
Here is a guide and a collection of boot parameters to try:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317

---

### Post by davidallan on 2007-12-08
Thank you sir. :)

Ive just fixed my grub boot menu! thought id lost vista and my data which was on another harddrive! nightmare!

anyways sort that one > now back to ubuntu and the black screen!

---

### Post by Pumalite on 2007-12-08
Good luck!

---

### Post by davidallan on 2007-12-08
the only difference between normal and recovery mode is

normal - quiet splash

recovery - ro single

so all i need to do it work out what those switches do! --- splash must be the start up logo! lol

---

### Post by davidallan on 2007-12-08
well :D:D:D:D

it seems removing quiet and splash worked!! im in!! hehe

i guess it must of been the splash rather than the quiet boot.

anyways thank you for your time tonight its 1:30am here > dnt know where u are but its late here!

one last thing > enabling dual monitors??

---

### Post by Pumalite on 2007-12-08
Glad you got it working!
[http://ubuntuforums.org/showthread.php?t=606103](http://ubuntuforums.org/showthread.php?t=606103)

[http://www.phoronix.com/scan.php?page=article&item=387&num=1](http://www.phoronix.com/scan.php?page=article&item=387&num=1)
[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

### Post by davidallan on 2007-12-08
Cheers Puma :D

---


---
title: "new system hangs during bootup, HELP!"
date: 2012-02-11
forum: Installation &amp; Upgrades
---

### Post by gregtomko on 2012-02-11
Hi, I am trying to install ubuntu 11.10 (32 bit) on a new machine. It runs the OS off the live CD perfectly, and it installed the OS on my hard drive with no errors, but it just hangs while booting  after the initial restart.  It ends with the following on the screen....

Checking for running unattended-upgrades:
* Stopping Failsafe Boot Delay                           [ OK ]
* Stopping System V initialization compatibility         [ OK ]
* Starting  System V runlevel compatibility              [ OK ]
* Stopping automatic crash report generation             [fail]
* Starting eCryptfs                                      [ OK ]
* Starting restore sound card(s') mixer state(s)         [ OK ]
* Starting LightDM Display Manager                       [ OK ]
* Starting ACPI daemon                                   [ OK ]
* Starting anac(h)ronistic cron                          [ OK ]
* Stopping eCryptfs                                      [ OK ]
* Starting save kernel messages                          [ OK ]
* Starting CPU interrupts balancing daemon               [ OK ]
* Starting restore sound card(s') mixer state(s)         [fail]
* Starting deferred execution scheduler                  [ OK ]
* Starting regular background program processing daemon  [ OK ]
* Stopping save kernel messages                          [ OK ]
mountall: Disconnected from Plymouth
                                                         [ OK ]



It just sits like that afterwards until restarting, where it ends the same way again.  Is there a way to tell what the problem is?

The system:
  -ASRock N68C-S motherboard
  -Athlon II X3 455 3.3GHz
  -Raptor WD740ADFD 74GB 10000 RPM

Thanks in advance for any help!

---

### Post by MAFoElffen on 2012-02-11
> **gregtomko said:**
> Hi, I am trying to install ubuntu 11.10 (32 bit) on a new machine. It runs the OS off the live CD perfectly, and it installed the OS on my hard drive with no errors, but it just hangs while booting  after the initial restart.  It ends with the following on the screen....

Checking for running unattended-upgrades:
* Stopping Failsafe Boot Delay                           [ OK ]
* Stopping System V initialization compatibility         [ OK ]
* Starting  System V runlevel compatibility              [ OK ]
* Stopping automatic crash report generation             [fail]
* Starting eCryptfs                                      [ OK ]
* Starting restore sound card(s') mixer state(s)         [ OK ]
* Starting LightDM Display Manager                       [ OK ]
* Starting ACPI daemon                                   [ OK ]
* Starting anac(h)ronistic cron                          [ OK ]
* Stopping eCryptfs                                      [ OK ]
* Starting save kernel messages                          [ OK ]
* Starting CPU interrupts balancing daemon               [ OK ]
* Starting restore sound card(s') mixer state(s)         [fail]
* Starting deferred execution scheduler                  [ OK ]
* Starting regular background program processing daemon  [ OK ]
* Stopping save kernel messages                          [ OK ]
mountall: Disconnected from Plymouth
                                                         [ OK ]



It just sits like that afterwards until restarting, where it ends the same way again.  Is there a way to tell what the problem is?

The system:
  -ASRock N68C-S motherboard
  -Athlon II X3 455 3.3GHz
  -Raptor WD740ADFD 74GB 10000 RPM

Thanks in advance for any help!
You forgot to mention onboard NVidia graphics.  Use these directions to use "nomodeset" to boot into the desktop:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Temporarily Editing Grub Menu for Boot Options]("http://ubuntuforums.org/showpost.php?p=11491229&postcount=812")**[/SIZE][/COLOR][/SIZE][/COLOR]

If it boots into the desktop, go to System Settings, then Additional Drivers and install your driver.

If it doesn't let me know and I'll give your directions to install your driver from the command line.

---

### Post by gregtomko on 2012-02-11
> **MAFoElffen said:**
> You forgot to mention onboard NVidia graphics.  Use these directions to use "nomodeset" to boot into the desktop:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Temporarily Editing Grub Menu for Boot Options]("http://ubuntuforums.org/showpost.php?p=11491229&postcount=812")**[/SIZE][/COLOR][/SIZE][/COLOR]

If it boots into the desktop, go to System Settings, then Additional Drivers and install your driver.

If it doesn't let me know and I'll give your directions to install your driver from the command line.

Where can I access a "grub menu" ?  Do I have to boot into the live CD?

---

### Post by gregtomko on 2012-02-11
I would like to get 11.10 working, but I just installed 10.04 just to test the hardware, and it worked perfectly.

---

### Post by MAFoElffen on 2012-02-12
> **gregtomko said:**
> Where can I access a "grub menu" ?  Do I have to boot into the live CD?
Boot your PC. After the BIOS messages are through, hold down the shift key... If that doesn't show your Grub Menu, then reboot and press your shift key repeatedly... If that doesn't work:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][**Forcing Grub to Show Menu**]("http://ubuntuforums.org/showpost.php?p=11469860&postcount=800")
[/SIZE][/COLOR][/SIZE][/COLOR]
But if you have to force the menu to show and chroot your sys from the LiveCD, while in the chroot, you might as well install your drivers there using these instructions:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][**Installing NVidia Packaged Drivers**]("http://ubuntuforums.org/showpost.php?p=11467050&postcount=797")[/SIZE][/COLOR][/SIZE][/COLOR]

> **teryy said:**
> [COLOR=Red]If it boots into the desktop, go to System Settings, then Additional Drivers and install your driver. <snip> [/COLOR]
@teryy:
 - You read Post #2 right? Thank you for re-quoting me? LOL
> **MAFoElffen said:**
> You forgot to mention onboard NVidia  graphics.  Use these directions to use "nomodeset" to boot into the  desktop:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Temporarily Editing Grub Menu for Boot Options]("http://ubuntuforums.org/showpost.php?p=11491229&postcount=812")**[/SIZE][/COLOR][/SIZE][/COLOR]

[COLOR=Red]If it boots into the desktop, go to System Settings, then Additional Drivers and install your driver.[/COLOR]

If it doesn't, let me know and I'll give you directions to install your driver from the command line.

---


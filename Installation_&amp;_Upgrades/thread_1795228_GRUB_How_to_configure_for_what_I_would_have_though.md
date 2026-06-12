---
title: "GRUB: How to configure for what I would have thought were commonplace requirements?"
date: 2011-07-02
forum: Installation &amp; Upgrades
---

### Post by churlishbeaver on 2011-07-02
I Installed "ubuntu 11.04 Alpha 2" on my Intel Computerr.[1]

I had already installed Debian Linux (presumably version 6.0) all on the /dev/sda1 partition[2], so I set up the installer to install Ubuntu Linux on /dev/sda2.

In the roughly 2 hours installation time, during which time it must presumably have downloaded a lot from the non-Alpha-2 version from somewhere in ubuntu.com, it had installed 2.4G on /dev/sda2 , *but none of the needed changes seem to have been made to the boot sector*.

My computer would NOT boot to Ubuntu Linux.  It booted again straight to Debian Linux without even presenting me with  a bootloader menu.[3]
 
Can someone tell me how to rectify this, so that I can boot to either Debian Linux[4] on /dev/sda1 or to Ubuntu Linux on /dev/sda2 ?

I presumably need to change the bootloader, presumably GRUB, to rectify the problem, but even though I have been searching, reading and trying to install GRUB for well over a week now, I can't locate what I would find to be straightforward instructions that must exist somewhere that would shown me how to configure GRUB to allow booting from /dev/sda1 as well a /dev/sda2 .  An example of one of a number of pages I have read that has not given me the answers  in a form I have found helpful is [http://forums.debian.net/viewtopic.php?p=194877](http://forums.debian.net/viewtopic.php?p=194877) . Perhaps others may be able to see there the answers I need, but I cannot.

What I need instructions for is:

1. What file do I edit to say that I want GRUB to cause my computer to boot from either /dev/sda1 or /dev/sda2 .  (Is it /etc/default/grub or what?)

2. What do I need to put into the configuration file and ...

3. ... *what command* (grub-install, grub-mkconfig, grub-mkimage, ...? ) with *what command line parameters* do I need to run  to write the required information to the boot sector of /dev/sda(, /dev/sda1, dev/sda2 or whatever)?

**Can Linux be installed to boot up from a partition on a physical disk drive other than the first?**

Also, could anyone tell me if it is possible to boot up Linux (or another OS) from a parttion on other than on /dev/sda (or /dev/hda)?  It was not even my first preference to have to install those two Linux distributions on /dev/sda . 


Footnote(s)

1. I obtained the DVD from "Linux User and Developer" magazine ([http://www.linuxuser.co.uk/](http://www.linuxuser.co.uk/). I am unable to say at this moment what issue it was, but it would have been one in the last six months around issue 97.  The DVD also had on the label "PureOS 3.0" and "OpenSuse11.4"

2. /dev/sda3 was set up to be the swap partition for my installation of Debian Linux as well as for my installation of Ubuntu Linux.  No other partitions other than /dev/sda1 for Debian and /dev/sda2 for Ubuntu, were used

3. Even though I can't boot up Ubuntu Linux, I appreciate, at least, the fact that the installation of Ubuntu Linux has not in any way prevented my existing installation of Debian Linux from functioning. On more than one recent occasion, this has not been my experience when I have installed a second or subsequent distribution of Linux.

4. Debian Linux currently lacks Drupal ver 7.2.

---

### Post by churlishbeaver on 2011-07-02
People with expertise solving this problem, may also be able to solve the problem described in the  thread **[Cannot change default OS]("http://ubuntuforums.org/showthread.php?p=11004717#post11004717")! **

---

### Post by YesWeCan on 2011-07-02
> **churlishbeaver said:**
> Can someone tell me how to rectify this, so that I can boot to either Debian Linux[4] on /dev/sda1 or to Ubuntu Linux on /dev/sda2 ?
It depends what boot loader Debian uses. Is it Grub-legacy or Grub2?

> 1. What file do I edit to say that I want GRUB to cause my computer to boot from either /dev/sda1 or /dev/sda2 .  (Is it /etc/default/grub or what?)Let me assume Debian uses Grub-legacy. In Debian you need to edit /boot/grub/menu.lst to add an entry for Ubuntu. Something like:
```
title Ubuntu 11.04 alpha 2
root (hd0,1)
kernel  /boot/vmlinuz root=/dev/sda2 ro quiet splash
initrd  /boot/initrd.img
boot
```> **Can Linux be installed to boot up from a partition on a physical disk drive other than the first?**Yes, Grub can boot almost any OS on any partition on any disk. :)
Grub2 is more automated than Grub-legacy, at least in Ubuntu, so it is worth upgrading.

> Also, could anyone tell me if it is possible to boot up Linux (or another OS) from a parttion on other than on /dev/sda (or /dev/hda)?  It was not even my first preference to have to install those two Linux distributions on /dev/sda . Yes, linux isn't constrained like Windows. You can put your OS almost anywhere, including in an extended partition. You need to put Grub's boot code in the MBR of a disk, but it doesn't have to be the same disk as the OS that installed Grub. So you can have a USB stick, for example, with Grub installed to its MBR that you boot and it then boots another OS or shows you a menu of OSs to boot. Note that Grub relies on files in the /boot/grub partition of the OS you used to install grub to the MBR.

---

### Post by churlishbeaver on 2011-07-02
YesWeCan,

Sorry, I forgot to mention that Debian Linux with which I am trying to fix up the MBR grub uses grub2 rather than Grub-legacy. :(  So your suggested changes to /boot/grub/menu.lst won't help.

Can you tell me what I need to do to achieve the same with grub2?

Thanks for the informative answers to my other questions.  :) (With any luck that knowledge will enable me to install Linux onto M$ computers.  If I could learn how to do it with USB sticks, then I may be more easily able to overcome the paranoia of friends against Open Source operating systems.

---

### Post by dino99 on 2011-07-02
sudo update-grub
sudo apt-get install startupmanager

then run startupmanager to set your choice

---

### Post by churlishbeaver on 2011-07-02
Thanks, dino99.

That's solved all my serious outstanding problems. :KS 

I can now boot to either:
[INDENT]Debian Linux on /dev/sda1
[/INDENT]... or:
[INDENT]Ubuntu 11.04 Linux on /dev/sda2
[/INDENT][LEFT]I gather, from what YesWeCan told me, it should also be possible for startupmanager[1]  to also set up bootable parttions on /dev/sdb, dev/sdc, etc

One minor outstanding concern is that I still can't reboot Debian Linux to see the Grub start up menu.  :-? Unless I shut down Debian Linux (with 'shutdown -h now') it will reboot to Debian Linux without showing me the Grub menu.  Ubuntu Linux allows me to reboot (with 'shutdown -r now') to Debian Linux or to any other OS should I want to, but not Debian Linux.

Perhaps when Debian Linux is installed, the PC's BIOS is set to only allow rebooting to Debian Linux.  I can't think how else this would have occurred.

I gotta catch a wink in Oz now,  Thanks again for your great help, YesWeCan and dino99 :)

[B]
Footnote(s) [/B] 

1. What a great program is startupmanager :D , but I can see from the fact that it has an option to set up a boot up floppy that it must be somewhat dated (although if the world economy were to collapse -- and let's hope it does not -- I can see there may be need for us to get legacy computer hardware including PC's with floppy drives, out of scrap heaps and working again).
[/LEFT]

---


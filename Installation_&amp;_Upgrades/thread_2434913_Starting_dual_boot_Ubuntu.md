---
title: "Starting dual boot Ubuntu"
date: 2020-01-13
forum: Installation &amp; Upgrades
---

### Post by lwalper on 2020-01-13
Is there an easier way to start Ubuntu? I began with a Win10 install on a 1Tb drive. Shrank the partition to 500Gb giving 500Gb to Ubuntu. Installed 18.04 in the new unused space.

Now when I start up I have to press the Esc key which opens what I suppose is a BIOS window with two options - Windows or Ubuntu. When I select Ubuntu from that window another, what appears to be an Ubuntu window (it's purple) with the option to actually start Ubuntu in three different ways or Windows. Shouldn't that second purple screen be what load initially instead of needing to use the Esc key to trick the system into something it really doesn't want to do?

There are a ton of good posts here regarding boot issues which are beyond me. Seem like there used to be a boot file that could be edited to change boot order -- boot.ini or some such thing. I don't seem to be able to find that file. I try things suggested by others like

$ update grub

and get the following

Command 'update' not found, did you mean:

  command 'pupdate' from deb pbuilder-scripts
  command 'zupdate' from deb zutils
  command 'lupdate' from deb qtchooser
  command 'uupdate' from deb devscripts
  command 'xupdate' from deb libxml-xupdate-libxml-perl

Try: sudo apt install <deb name>

That doesn't seem to be giving me much useful information.

---

### Post by Impavidus on 2020-01-13
That menu with different ways to boot Ubuntu or Windows (known as the grub menu; it should mention grub at the top line) should indeed show without intervention. You have to configure your uefi to use the Ubuntu bootloader by default. Around the time you now use the escape key to get a menu (maybe a one time boot selection) you have to hit some key to get into the UEFI configuration. There are many small variations in UEFIs, so if you tell us more details about your hardware, somebody may know how.

BTW, the command to update grub is **sudo update-grub**, but that's not related to your problem.

---

### Post by crip720 on 2020-01-13
I have made the same mistake but the first command is  sudo update-grub,  need the little line between update and grub.  It almost sounds like windows is installed as UEFI and ubuntu installed as bios/legacy, but want someone else to comment on this.  The second screen sounds like the regular grub loading screen, which is usually the first one you see when powering up a computer dual booted.  Should also edit your post and tell us the make and model of computer.

---

### Post by lwalper on 2020-01-13
So,
UEFI Boot order: Internal CDRom
USB

OS Boot Manager:
Windows Boot Manager (Toshiba xxx)
ubuntu (Toshiba xxx)

Secure Boot: Enabled
CDROM Boot: Enabled
USB Boot: Enabled

OK. I changed the OS Boot Manager order to have ubuntu first and the grub screen does come up without the ESC key press.

Windows as UEFI? Probably. I seem to remember that when I installed Ubuntu from a USB stick that it wanted to do it from a UEFI source. Does that mean that Ubuntu is also installed as UEFI?

---

### Post by crip720 on 2020-01-13
Installing from an UEFI source would be the recommended way to install.  If you said/check yes, then ubuntu should be UEFI also.  Someone else will have to show you how to check.

---

### Post by CatKiller on 2020-01-13
> **crip720 said:**
> It almost sounds like windows is installed as UEFI and ubuntu installed as bios/legacy, but want someone else to comment on this.

It sounds that way to me:

> **lwalper said:**
> (it's purple) 

Grub using purple means that it's in BIOS mode; when it's in UEFI mode Grub's stuff has a black background. 

I have no idea how OP's Windows is installed. If it was an OEM install it would be UEFI, but if they did it themselves it could be either.

---

### Post by yancek on 2020-01-13
The UEFI boot order you posted in post 4 above shows windows as booting before ubuntu.  You should be able to move ubuntu up or windows down.  Check options in the BIOS, I don't use Toshiba so am not sure what keys to use to do that.

---

### Post by lwalper on 2020-01-13
I was reading in the UEFI help section here and came across this 
 [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"  

which returned

$  [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"  
EFI boot on HDD

-- and when I boot into Win10 BIOS mode says "UEFI" in the system info.

It looks like it's booting in EFI - Windows and Ubuntu. Then why the purple screen? Purple or black doesn't really make any difference to me - just curious?

---


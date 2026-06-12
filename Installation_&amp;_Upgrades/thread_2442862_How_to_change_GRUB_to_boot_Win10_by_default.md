---
title: "How to change GRUB to boot Win10 by default"
date: 2020-05-08
forum: Installation &amp; Upgrades
---

### Post by lwalper on 2020-05-08
I've installed Ubuntu 20.04 to SSD on a Win10 system. Everything works great, but I'd like to edit the GRUB to make Win10 be the default in the boot order. I changed the boot order in UEFI, to the Win10 boot loader, and that works fine, but bypasses the GRUB making it difficult to boot into Ubuntu. How do I edit GRUB to make Win10 the default?

---

### Post by jeremy31 on 2020-05-08
You will have to look at the grub menu at boot, the Ubuntu entry is considered 0, you might have
Ubuntu
Advanced Options
Windows
System Settings
With this the Windows is entry number 2, so you could edit /etc/default/grub and change ```
GRUB_DEFAULT=0
``` to ```
GRUB_DEFAULT=2
```
Save and exit then ```
sudo update-grub
```
Reboot

---

### Post by lwalper on 2020-05-08
I'm absolutely positive that would work; however, when I try to save the file after the alteration I'm told I don't have permission to save it. I'll need a little more info please. I'm told I'm not the owner so can't edit the file. I'm the installer, how do I become the owner? Or do I need to somehow open it in a terminal and do a sudo command of some sort?

---

### Post by oldfred on 2020-05-08
You have to use sudo to edit grub.

You can use number like jermey31 posted. Count starts at 0, and I once miscounted and had grub trying to boot a blank line.

You also can use description.

But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Boot Manager (on /dev/sda1)". Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates. You must use exact title, so only copy & paste from existing entry.

Best to backup old grub first:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
sudo cp -a /etc/default/grub /etc/default/grub.backup
find your windows entry in this and copy to grub default like this Windows entry:
cat /boot/grub/grub.cfg  | grep menuentry
or 
gedit /boot/grub/grub.cfg
and copy Windows entry into grub_default  here:
sudo nano /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new :
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Boot Manager (on /dev/sda1)"
Then do:
sudo update-grub

[https://help.ubuntu.com/community/Grub2/Setup#A.2BAC8-etc.2BAC8-default.2BAC8-grub](https://help.ubuntu.com/community/Grub2/Setup#A.2BAC8-etc.2BAC8-default.2BAC8-grub)

---

### Post by jeremy31 on 2020-05-08
To edit the file in ubuntu you can do ```
gedit admin:///etc/default/grub
```
I think it prompts for password twice

---

### Post by lwalper on 2020-05-08
OK, so, I open the terminal, navigate to /etc/default/ and enter

sudo edit grub

Enter password.

The file opens (or at least is readable) and I can delete characters there, but there does not appear to be any way to add or actually edit the data. Is there some other editor to use that will allow edits to the file? (or maybe a different command than 'edit' that I used)

---

### Post by jeremy31 on 2020-05-08
See above [https://ubuntuforums.org/showthread.php?t=2442862&p=13955201#post13955201](https://ubuntuforums.org/showthread.php?t=2442862&p=13955201#post13955201)

---

### Post by lwalper on 2020-05-08
So this is now what I have:

GRUB_DEFAULT=2
GRUB_DEFAULT="Windows Boot Manager (on /dev/sda3)"
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

Win10 boots normally, but the GRUB does not appear. I have to hold down the F12 key to enter UEFI boot where I can select the Ubuntu boot entry. THEN the GRUB displays and I can select either OS. How do I move the Win10 entry to the top of the list so the GRUB displays, or times out, and loads Win10 by default. The real problem is that I'm using a wireless keyboard which I can't use until the USB drivers are loaded for the keyboard; hence, no F12 key available, so am having to use a wired plugged-in USB keyboard in addition to the wireless one.

---

### Post by oldfred on 2020-05-08
Having two defaults may not help. Comment one or the other out with #.

If you remove quiet splash on linux line in grub, you see boot process which is then in log file. It usually stops a few lines past where real error is.

What brand/model & what video card? Some need boot parameters or settings.

---

### Post by lwalper on 2020-05-08
I was reading the Setup section of the Wiki (yea, who does that??) and found this:

[B]GRUB_DEFAULT=0 Sets the default menu entry by menu position. The first "menuentry" in grub.cfg is 0, the second is 1, etc.

Note: Grub 1.99 introduces a submenu menu structure. For a menu item in a submenu, the entry becomes a two-digit entry. The first entry is the position of the submenu title in the main menu. The second entry is the position within the submenu. If the submenu is the 3rd entry in the main entry, and the user wishes to boot the first entry in the submenu, it would be designated as "2>0". See the community documentation for a fuller explanation: Grub2/Submenus. 
[/B]

My GRUB lists:

UBUNTU
Ubuntu Advanced Options
Windows Boot Manager (on /dev/sda3)
UEFI Firmware Settings

Is this a menu/submenu? and if it is would this work? I'm just asking before I crash GRUB and can't boot into it. Would that load GRUB and then boot into Win10 if left unattended for 10 seconds?


GRUB_DEFAULT=0>2
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

or-- should I add a line like thus:

GRUB_DEFAULT=0
**SUDO GRUB-SET-DEFAULT 2**
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

and with that do I need to include the line

**GRUB_DEFAULT=saved** somewhere in the list?

which would (theoretically) load GRUB and then boot into Win10.

---

### Post by oldfred on 2020-05-08
All those questions are why I prefer to just use the description.

The sub-menu is under the advanced options.
You do not put sudo in grub.

More info:
[https://help.ubuntu.com/community/Grub2/Setup#Specific_Entries](https://help.ubuntu.com/community/Grub2/Setup#Specific_Entries)

---

### Post by lwalper on 2020-05-08
Well, it seems that I was trying to make it more difficult than it needed to be. Here's what I ended up with:

GRUB_DEFAULT=2
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

I had forgotten to change the UEFI boot order back to Ubuntu (which then loaded Win10 by default without seeing GRUB). So, changed the UEFI boot order back to Ubuntu and simply needed to change the GRUB_DEFAULT to '2' which then boots to Win10 when left undisturbed for 10 seconds. PRESTO!

Thanks everyone for your input and encouragement!!

---


---
title: "Gutsy Boot Problems"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by D-Rick86 on 2008-02-20
So I downloaded the .iso for the Live CD of Ubuntu. Got it on my laptop and it seemed like everything was going well.
I restarted the computer, GRUB loaded, but then I get a very long line of code that read over and over and over again:

/init: /init: 158: /bin/sleep: not found. (many lines of this)
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules 1s /dev
/init: /init: 158: modprobe: not found
/init: /init: 158: modprobe: not found
ALERT! /dev/disk/by-uuid/ffe039fc-40df-40c4-9641-b751a0030225 does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands. 

Then I get a command prompt type thing that reads:

(initramfs) _

I honestly have no idea what this means or how to remedy this. Anyone have any suggestions or things I can do to get me up and running with Ubuntu? I have checked the CD for defects and it turns out to be just fine. I'm brand new to Linux and could use some help figuring out what's going on. Thanks in advance for the replies.

~Derek

---

### Post by Pumalite on 2008-02-20
You might want to try this: (from an old thread on this problem):

At the LiveCD initial boot screen:
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

You will now boot into the LiveCD normally.

If you choose to install from the LiveCD, you must make the following modifications (or else your installed system will not be able to boot, just like the LiveCD):
Make note of the device id of the partitions that were used to install (such as /dev/hda1)
If you choose to install the '/boot' mount from a different partition make note of it as well (this would be done from the manual partition selection); jStarting up

then boots to the following:

/bin/sh: cant access tty; job control turned off.
(initramfs)

so, i try the following command as suggested:


/bin/sh: cant access tty; job control turned off.
(initramfs)modprobe piix
(initramfs)exit


This does the trick, Ubuntu starts up fine, and smoothly.

> Just to simplify a little, however, after the command (in the chroot env):
> sudo echo piix >> /etc/initramfs-tools/modules
> all I needed to do is issue the command
> sudo update-initramfs -u
> to update the initramfs (thus correcting the system) and then
> exit
>
(it might not work)

---

### Post by D-Rick86 on 2008-02-20
So just pop the LiveCD back in and try what you said?

---

### Post by Pumalite on 2008-02-20
Yup. No assurances though. It might or might not work. What do you have to loose?

---

### Post by D-Rick86 on 2008-02-20
Ok, I never got booted out to a command prompt, Ubuntu booted and I'm sitting at the desktop. 

When I pressed F6, I scrolled all the way over to the left and input the code you said, break=top

Did I put it in the wrong place?

---

### Post by Pumalite on 2008-02-20
Add the following option to the beginning of the options list:
break=top
o Press enter to start booting

---

### Post by D-Rick86 on 2008-02-20
Got it up and running!

Thanks!

---

### Post by Pumalite on 2008-02-20
You are welcome. Good luck. Here; to get you started:
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---

### Post by bill48er on 2008-02-24
Hi   ):P
Complete newbie - wanting to give Ubuntu a try but....
I'm having a similar Livecd boot up failure - when I saw this thread I though great just what I was looking for.
Following the instruction of placing break=top at the front of the boot options drops me to a (initramfs) prompt. Entering modprobe piix results in "FATAL: Module piix not found".
Then entering exit restarts the splash screen and the pc starts hunting for a floppy in dive A then drops to the (initramfs) prompt. The same thing happens when allowing the LiveCD to boot normally. Disabling the floppy in bios does not help.

Any further suggestions welcome as I'm hoping that I can avoid upgrading to windoze vista. :shock:

---

### Post by charmgene on 2008-03-21
> **D-Rick86 said:**
> So I downloaded the .iso for the Live CD of Ubuntu. Got it on my laptop and it seemed like everything was going well.
I restarted the computer, GRUB loaded, but then I get a very long line of code that read over and over and over again:

/init: /init: 158: /bin/sleep: not found. (many lines of this)
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules 1s /dev
/init: /init: 158: modprobe: not found
/init: /init: 158: modprobe: not found
ALERT! /dev/disk/by-uuid/ffe039fc-40df-40c4-9641-b751a0030225 does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands. 

Then I get a command prompt type thing that reads:

(initramfs) _

I honestly have no idea what this means or how to remedy this. Anyone have any suggestions or things I can do to get me up and running with Ubuntu? I have checked the CD for defects and it turns out to be just fine. I'm brand new to Linux and could use some help figuring out what's going on. Thanks in advance for the replies.

~Derek
i've got the same problems on my newly installed ubuntu hardy system, not on a livecd. everything was just fine last night, but this morning it just failed to boot.

---


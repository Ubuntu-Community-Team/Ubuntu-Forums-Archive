---
title: "Can't boot 6.06 after installing updates"
date: 2006-07-09
forum: Installation &amp; Upgrades
---

### Post by foxmajik on 2006-07-09
...

---

### Post by linuxfan128 on 2006-07-09
This might help.

```
 How to restore GRUB menu after Windows installation

    * Read #General Notes
    * Read #How to use Ubuntu Installation CD, to gain root user access 

    e.g. Assumed that /dev/hda is the location of /boot partition 

# grub-install /dev/hda

[edit]

```

```
 How to use Ubuntu Installation CD, to gain root user access

    * Read #General Notes
    * Boot-up computer into Ubuntu Installation CD
    * At "boot:" prompt, add "rescue" to the argument 

boot: rescue

    * Follow the instructions on screen 
```

---

### Post by foxmajik on 2006-07-10
[QUOTE=linuxfan128;1235162]This might help.

```
 How to restore GRUB menu after Windows installation

    * Read #General Notes
    * Read #How to use Ubuntu Installation CD, to gain root user access 

```
[/QOUTE]
I found the document referenced here by doing a google search, but I did exactly as instructed and I got an error.

*    e.g. Assumed that /dev/hda is the location of /boot partition *

# grub-install /dev/hda

ubuntu@ubuntu:~$ grub-install /dev/hda
mkdir: cannot create directory `/boot/grub': Permission denied
ubuntu@ubuntu:~$ sudo grub-install /dev/hda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$

```
 How to use Ubuntu Installation CD, to gain root user access

    * Read #General Notes
    * Boot-up computer into Ubuntu Installation CD
    * At "boot:" prompt, add "rescue" to the argument 

boot: rescue

    * Follow the instructions on screen 
```

"Could not find kernal image: rescue"

I'm using this image:
[http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-desktop-i386.iso](http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-desktop-i386.iso)

I don't understand how I am supposed to "add 'rescue' to the argument" when all I am presented with is a prompt that says "boot:".  No matter what I type I always get "Could not find kernal image: ... [whatevery I type]".

I guess what I'm asking here is, not so much how to fix the boot loader, but how to prevent the software updates from destroying it in the first place.

Is it possible that GRUB is being upgraded and the config file is being overwritten?

If this is so, why aren't more people having this problem?

---

### Post by foxmajik on 2006-07-10
Nevermind, I'm going back to Windows.

A week of trying to install an operating system and two pieces of hardware catching fire is enough for me.

In case you're curious, here's a summary of my experience:

. Downloaded CD image and burned
. Installed Ubuntu, used it and Windows a while, dual booting between them, this is nice
. Decided to upgrade to latest software updates, did so when prompted
. Rebooted, computer will no longer start up
. Spent an hour rebooting, checking cables, rebooting, checking BIOS settings
. Restored MBR using Windows 98 CD, finally can boot into Windows
. Went online and looked on forums for other users having the same problem, can't find any
. Installed Ubuntu again, maybe this was a fluke
. Immediately installed updates, PC immediately fails to boot
. Restored MBR again, Windows boots normally
. Went online to find out how to re-install GRUB
. Read lots of documentation, tried everything, can't get past the first step of any GRUB tutorial because the first step results in a different error every time when taking exactly the same steps -- odd, because GRUB installer works fine in Debian
. CD burner starts acting strange when booting into installer, at first it reads really slowly, then it starts making grinding noises
. Rebooted into Windows, drive works fine, burned a few CD's including a new copy of Ubuntu installer just in case the CD check missed something
. Tried to install Ubuntu again, installer hangs at "adding live CD user," drive starts smoking and catches fire
. Powered off and disconnected drive
. Replaced ruined CD burner with new CD burner, used with Windows for a couple of days, burned some CD's everything works beautifully
. Started up Ubuntu intaller again, installer gets to the point where it's "adding live CD user," new CD burner starts making grinding noise, I/O errors on screen, drive starts smoking and fails
. Powered off, threw away second ruined CD burner, went back to using Windows
. Burned some CD's with third CD burner, played a few CD's, rebooted many times, no problems

You know, I know it's hard to blame an operating system for not only causing your PC to fail to boot, but also to cause your CD burner to catch fire.  Twice.

Don't get me wrong, I didn't believe it either.  So I tried installing plain Debian Woody using the same drive model.  It installed with no problems and no smoke.

But I'd been using the same CD burner for two and a half years before I tried installing Ubuntu.  And since I stopped trying to install it, I haven't had any other hardware catch fire.  So draw your own conclusions.

I know it's called a CD "burner," but I don't expect it to literally catch fire.

---

### Post by darrenrxm on 2006-07-10
Yes, unfortunately, Ubuntu does not work properly for everyone. Sorry to see you go back to windows. I have had similar experiences to yours. Until I started to pay attention to what hardware Ubuntu supports. I had a tv tuner card that wasn't supported. So, what I did was sell it and buy one that was supported. I find this works better than complaining. Ubuntu does work wonderfully **IF** you have hardware that it supports.

Did you check if your hardware was supported by Ubuntu?

[http://doc.gwos.org/index.php/HCL](http://doc.gwos.org/index.php/HCL)

---


---
title: "My upgrade asploded"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by MadScotty on 2010-05-03
First off, my specs:
-------------------
Desktop
Intel Core 2 Duo
2GB RAM
Older ATI video card (I forget which one exactly)
Upgrade from 9.10 to 10.4

And here goes my issue:
-----------------------
I've been running Ubuntu on this computer off and on for a while, I believe I've had 8.10 on here before, as well as 9.10.  9.10 was running flawlessly before I upgraded, absolutely no problems, and the 9.10 install didn't require anything odd to install it, except that I had to run the liveCD from a USB instead of a disc.  After I finish upgrading, it dumps me into BusyBox with the following error messages:

```

- Boot args (cat /proc/cmdline)
    - Check rootdelay= (did the system wait long enough?)
    - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/(lots of numbers/letters) does not exist. Dropping to a shell!
```

After that, I tried a fresh install, rather than an upgrade.  The 10.4 liveCD runs fine, installed without error, but when I restart the computer, I get a blank screen, with just a cursor.  I hear or see nothing else.  The computer still seems responsive, in the sense that Ctrl-Alt-Del restarts the computer (I don't have to resort to the power button)

Like I said earlier, the computer ran 9.10 perfectly, and as of right now, I tried upgrading again (it seemed to get me the farthest) and I'm staring at BusyBox right now.

Please help, it would be much appreciated.

---

### Post by bobnutfield on 2010-05-03
> ALERT! /dev/disk/by-uuid/(lots of numbers/letters) does not exist. Dropping to a shell!

This is caused by Grub looking for the kernel on the wrong UUID.  The same thing occurred on a new install for me.  Now, I know that Lucid uses Grub2 by default, and I do not use Grub2 (I don't like it so I use legacy Grub.)  The UUID changes for some reason even when you install to the same partition (it did on my machine.)  If you start the liveCD and open a terminal and type:

> blkid /dev/sda1  assuming that is the partition you have Ubuntu installed to

This long number is UUID that you will append to the Grub root=UUID line in Grub.config.  But I am afraid I do not know where that is found in Grub2 (/etc/grub/grub.conf, I think).

I got the same error until I changed the UUID and it would then boot normally.

Hope that helps

---

### Post by MadScotty on 2010-05-03
Thanks for your help.  However, I keep looking, and I'm seeing no discrepancy between the uuid that it's looking for and the one I appear to have.  I found the grub.cfg file, and while I didn't find a line that said exactly grub root=(the uuid), but every instance of anything that looked remotely like a uuid was the same, no matter where I looked.

As for blkid, it did nothing in the terminal while using the liveCD, but in the busybox, it gives me two uuid's, one for my primary, and one for my swap (which is the correct number of partitions) and the number for the primary agreed with the uuid I've seen everywhere else.

I don't even see it flash "Loading GRUB" or anything of that nature, either....just an unusually long black screen (maybe around 10 seconds) then it dumps me into the shell.

---

### Post by uncleV on 2010-05-03
> **MadScotty said:**
> After that, I tried a fresh install, rather than an upgrade.  The 10.4 liveCD runs fine, installed without error, but when I restart the computer, I get a blank screen, with just a cursor.  I hear or see nothing else.  The computer still seems responsive, in the sense that [COLOR=Blue]Ctrl-Alt-Del[/COLOR] restarts the computer (I don't have to resort to the power button)

Like I said earlier, the computer ran 9.10 perfectly, and as of right now, I tried upgrading again (it seemed to get me the farthest) and I'm staring at BusyBox right now.

Please help, it would be much appreciated.

[COLOR=Black]If [/COLOR][COLOR=Black]Ctrl-Alt-Del restarts the computer are you sure you are running Linux-OS?[/COLOR]

---

### Post by MadScotty on 2010-05-04
Forgive me, but I can't exactly tell what you mean by that.

The issue isn't that I've got a messed up dual/multi-boot system.  It won't get as far as the OS.  There is no other operating system on the disk.....I used the entire disc for the install.  The only two partitions are the / and swap partitions.

Also, in almost every system ever, C-A-D will restart the system before control is passed to the OS.

But, if you were trying to be funny, disregard the previous statements.  Maybe I clicked the "Install MS-DOS" button on the LiveCD.

---

### Post by uncleV on 2010-05-04
Excuse me for being unclear!

I meant if you restart with Ctrl-Alt-Del you are not running Ubuntu because it doesn't respond to this key combination. It was my fault thinking you are complaining the new upgrade doesn't work. And it doesn't even pass you to the OS as I realised now and as you stated it already. I'm sorry.

---

### Post by uncleV on 2010-05-04
I picked up some answers on Launchpad for similar situations. Used "Missing modules" for serch.

[https://answers.launchpad.net/ubuntu/+source/bootchart/+question/58691](https://answers.launchpad.net/ubuntu/+source/bootchart/+question/58691)
[https://answers.launchpad.net/ubuntu/+question/108255](https://answers.launchpad.net/ubuntu/+question/108255)
[https://answers.launchpad.net/ubuntu/+source/grub/+question/79593](https://answers.launchpad.net/ubuntu/+source/grub/+question/79593)
[https://answers.launchpad.net/ubuntu/+question/59032](https://answers.launchpad.net/ubuntu/+question/59032)

Or you can directly ask there.

Btw are you sure you have enough hard-disk space?

---

### Post by tsaowang on 2010-05-04
Hello,

I have had the exact same problem from the day when Lucid Lynx was  released.
I have been looking everywhere on the net to find a solution and found  this :

[http://www.dedoimedo.com/computers/u...nitrd-bug.html]("http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html")

I haven't tested yet (at least today), after several installations of  Karmic<->Lucid, the only OS that is working for me is Xubuntu  10.04 (don't ask me why, because I should encounter the same issue)

Hope this can help

---


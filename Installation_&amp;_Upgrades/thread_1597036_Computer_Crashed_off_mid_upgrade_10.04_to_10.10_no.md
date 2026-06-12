---
title: "Computer Crashed off mid upgrade 10.04 to 10.10 now won't boot"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by spcmediaco on 2010-10-14
Hi, 

(PS 64bit)


After spending a few hours searching to see if I could find a resolution to my problem I decided just to post here and see if someone can help me.

I was upgrading from 10.04 to 10.10 and the computer completely froze and I restarted it thinking I would be able to restart the update where I left off (I'm new to ubuntu).  However when I restart I can't get anywhere, if I boot normally the ubuntu screen comes up and then it stops with the computer name in the middle of the screen and thats it (can't do anything i can't get into shell via ctrl-alt-f1 etc..) if i use the recovery from the grub menu it loads a bunch of things then stops i can't type anything but I can switch using ctrl-alt-f1 and ctrl-alt-f7 but I don't see anything except:

under ctrl-alt-f1 the last line reads: 

[2.711773] composite sync not supported

under ctrl-alt-f7: the last lines read
fsck from util-linux-ng 2.17.2
init: udevtrigger main process (421) terminated with status 1
init: udevtrigger post-stop process (424) terminated with status 1
init: udevmonitor main process (420) killed by TERM signal
/dev/sda3 has been mounted 22 times without being checked, check forced
modprobe: FATAL: Error inserting padlock_sha (/lib/modules/2.6.32-25-generic/kernal/drivers/crypto/padlock-sha.ko): No such device
/dev/sda3: 172296/2736128 files (0.4% non-contigious), 1573947/10938624 blocks


the older options don't work either..
the non recover last line goes like this:

ALERT! /dev/disk/by-uuid/0c86f3a9-7051-41de-8929-297daca7e174 does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for list of built-in commands.

thanks for the help..

thanks

s

---

### Post by spcmediaco on 2010-10-15
If I can somehow get to a command prompt I believe that there is a way to continue the update, no?

s

---

### Post by Hamishfox on 2010-10-15
This exact same thing happened to me. Does 10.10 work from a live CD? If so, you can use that as a temporary work-around, like I have been doing.

---

### Post by spcmediaco on 2010-10-15
Yeah it works from a Live CD and the live cd even has a 'recover' option however when I used that and got to a shell properly and tried the update again it seemed fine until it stopped after too many errors.  I think it may have to do with the fact that I chose to encrypt my 'drive' when I first installed ubuntu.. (however I have no idea.. as i am a newbie..)

s

---

### Post by dino99 on 2010-10-15
you'd better to make a clean install:

Howto install ubuntu, and what is required:

[http://ubuntuforums.org/showpost.php...63&postcount=4](http://ubuntuforums.org/showpost.php...63&postcount=4)

---

### Post by Hamishfox on 2010-10-15
It seems like it's something to do with nvidia drivers.

Someone's solved it in [this thread]("http://ubuntuforums.org/showthread.php?t=1595776"). I'm going to try it now. I'll reply in both threads if it works.

---

### Post by santana007 on 2010-10-15
Sounds pretty much the same as what happened to me. So I made this post:  [http://ubuntuforums.org/showthread.php?t=1584931](http://ubuntuforums.org/showthread.php?t=1584931)
Received a reply and got my system working again. Maybe it will help.

---


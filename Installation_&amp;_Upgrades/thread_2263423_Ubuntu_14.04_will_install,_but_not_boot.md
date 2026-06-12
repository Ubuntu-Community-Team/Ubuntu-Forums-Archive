---
title: "Ubuntu 14.04 will install, but not boot"
date: 2015-01-31
forum: Installation &amp; Upgrades
---

### Post by dcommini on 2015-01-31
Ok, 

I just got a new to me computer, no OS. It is an HP Pavillion dv6 1062xx. Put 14.04 on a thumbdrive, made sure it was bootable. Computer booted up just fine, went into BIOS no problems. Booted from the live thumbdrive with out any problems. Everything seemed to work great. Installed with out a problem. Turn off computer and turn it back on this is the message i see

> Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cdmline)
    - Check rootdelay= (did the system wait long enough?)
    - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT!/dev/disk/by-uuis/bdaca13-0daa-4d62-b43b-03ef8d4f234d does not exist. Dropping to a shell!

BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs)_


So question is what can I do to fix this problem? I tried two different thumbdrives, and two different versions or 14.04 (32 bit and 64 bit). Please help me, as my old computer is just not wanting to even type this message.

---

### Post by mörgæs on 2015-01-31
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by dcommini on 2015-02-01
> **mörgæs said:**
> [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thanks, but after running boot repair I still get the same message. The url I got from boot repair is [http://paste.ubuntu.com/9995787/](http://paste.ubuntu.com/9995787/) which I'm going to email to boot repair.

---

### Post by yancek on 2015-02-01
Have you removed the Sandisk and set the Toshiba to first boot priority in the BIOS?

---

### Post by dcommini on 2015-02-01
> **yancek said:**
> Have you removed the Sandisk and set the Toshiba to first boot priority in the BIOS?
It's an HP, and yes. Same results.

---

### Post by dcommini on 2015-02-09
So after a little while of trying to figure out what was going on I decided to contact the person I bought the computer from. It was then that I realized that he had sent me the wrong computer (based off of pictures). So I of course contacted him about the possible mix up and also why he thought the computer might be screwing up with the install. He did indeed send me the wrong computer, and had no idea why the computer wouldn't take the install. Then I shipped him the computer back and he shipped me the proper computer - which I promptly installed 14.04 on. It works wonderfully, and I am currently typing this message from the new computer.

I'm going to mark this thread as solved, but if any one might have any idea what was going on please leave a reply in case some one else experiences this problem.

---


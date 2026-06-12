---
title: "The disk drive for / is not ready yet or not present"
date: 2012-12-22
forum: Installation &amp; Upgrades
---

### Post by JoJ9 on 2012-12-22
Hi guys! I'm a newbie with this ubuntu stuff, so any help is much appreciated. 

I have an inspiron mini from dell using ubuntu. It was given to students at my school. I've had it for a few years now. I recently tried upgrading the computer using software update and as far as I can tell everything went fine. The computer rebooted and it said "The disk drive for / is not ready yet or not present " and underneath it says "continue to wait; or press S to skip mounting or M for manual recovery". I waited overnight and nothing happened. Clicking S doesn't seem to do anything and I have no idea what M wants me to do (I know the root password). Any advice?

I tried looking online for help, but I couldn't seem to follow what everyone was saying. I'm sorry if this is another repeat post, but thanks in advance!

---

### Post by Bashing-om on 2012-12-22
JoJ9; Hi ! Welcome to the forum.

Due to your difficulties, lets try a simpler approach,
1. Boot up your system from cold start, when the bios screen clears press and hold the shift key -> grub menu.
2. In this grub menu, choose the "recovery mode" to boot. 
3. Options menu -> choose fsck.
This will run the file system check and repair it if possible.

Post back with results.

[INDENT][INDENT][INDENT][INDENT]just try'n to help < == BDQ

[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by JoJ9 on 2012-12-22
Thanks for trying to help me! I tried pressing shift and it took me to a screen that says "GNU GRUB version 1.98-1ubuntu12". There are three "recovery modes" to chose from amongst others, and I tried all three. All of them take me to a black screen with white letters on it. The last thing it always says is "the disk drive...not present" all over again. 

I forgot to say that if need be, there is a tech desk I can go to, but it's currently closed for the holidays. Would them re-imaging the computer fix it? I've been told that that's the main solution for most problems.

---

### Post by Bashing-om on 2012-12-23
JoJ9; I have never heard of a "tech desk" for linux situations.
How bout beating around the bush a bit more before we go technical on you.
Try this one:
set in bios to boot 1st priority the cd drive;
insert install disk in drive, soon as bios screen clears, hold shift key -> language screen->escape to accept default->boot options screen;
In this boot options is "boot from hard disk" -> choose it and see if you can boot to the install system.
If you do, we do one thing
else, we have to do others.[INDENT]pokin', see what happens <== BDQ

[/INDENT]

---

### Post by darkod on 2012-12-23
Try to boot in live session so you can investigate little bit. You can use either cd or usb stick with ubuntu and select Try Ubuntu when booting from it.

Then open terminal and post the output of:
```
sudo parted -l
```

One thing you can also try from live mode is running boot-repair that can usually fix most common boot errors. You can use the program to try to automatically fix your problem, or you can use it to only create bootinfo and post the link here so we can look at the details. It would help.
The option to only create the bootinfo will not make any changes on your computer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by JoJ9 on 2012-12-23
Unfortunately I do not have an install disk or usb with ubuntu. My school gave these netbooks out years ago, with no installation discs. And by tech desk I mean that there is a goup at my current school in charge of handling computer issues, including ubuntu. Their main solution is to re-image the computer, so I'm not sure whether or not that would fix the problem?

---

### Post by darkod on 2012-12-23
Ubuntu is free to download and creating bootable usb with it is free. Just make sure it's the same version as you are running on the computer, it's better.

If you don't have any way to boot into live session at least, there is not much we can do.

---

### Post by Bashing-om on 2012-12-23
+1 on darkod's advise.
Be advised with an installCD of the current installed version there is no ubuntu situation that does not have some kind of a solution.

[INDENT][INDENT]just my 2 pounds worth <== BDQ

[/INDENT][/INDENT]

---

### Post by JoJ9 on 2012-12-23
Alright guys thanks for your advice! I've come to a conclusion that I'll just ask a friend to help with the computer since I'm afraid I'll permanently damage it. 

Happy holidays!

---

### Post by Bashing-om on 2012-12-23
JoJ9;
As you wish, We are here to assist.
As advised earlier, will require that you have an live medium to proceed.
In retrospect it is a simple matter to download the .iso and burn to a medium for booting up to check/repair your system.

[INDENT][INDENT]kind regards <== BDQ

[/INDENT][/INDENT]

---


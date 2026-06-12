---
title: "Dual Boot"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by BelgianCubbie on 2010-04-29
I'm want to install Ubuntu Studio 10.04 and Windows Vista on my computer. It's going to be fresh install for both OS. 
My question now is: which one should I install first? Ubunto or Vista? and please explain why.

---

### Post by The Thunder Chimp on 2010-04-29
> **BelgianCubbie said:**
> I'm want to install Ubuntu Studio 10.04 and Windows Vista on my computer. It's going to be fresh install for both OS. 
My question now is: which one should I install first? Ubunto or Vista? and please explain why.
 
Simply enough, Windows erases all on your disk before installing. If you had Ubuntu, it will erase, if you had Mac OS, it will delete it, if you had Windows XP, it will delete it, you get the point. You must install Windows first, then Ubuntu. It's easy to partition with an Ubuntu installer than to do it with Windows.
 
The Verdict is: Windows first, Ubutnu second.
 
Don't hesitate to ask me more questions if you need to.
 
Welcome to the Community by the way!):P

---

### Post by BelgianCubbie on 2010-04-29
I have 2 HD's in my laptop. So Windows on the 1st HD en Ubuntu on the 2nd?
and btw, I'm using Ubuntu for a while already, but on a different laptop. Now just going for the dualboot option so I only have to carry 1 laptop with me.

---

### Post by oldfred on 2010-04-29
With multiple drives I like to keep separate boot loaders in each MBR and the operating system on each drive with its boot loader. That way if a drive fails I can at least boot the other drive by switching boot order in BIOS.

Set BIOS to boot windows drive so it installs its boot loader to that drive.

Since Ubuntu/grub2 is so good at finding other systems I install it last to the second drive and set BIOS to boot that drive. To make sure grub2 installs to the correct drive use the advanced button on the last partition screen to make sure it is set for the second drive.

---

### Post by BelgianCubbie on 2010-05-02
Installed Vista on HD1, and Ubuntu on HD2. But then I discovered that my BIOS won't let me choose from which HD to boot. Installing Ubuntu for a 4th time now, each time with diff. grub settings. It never worked.
So here is the list that I get when in advanced settings for grub:

/dev/sda -->ATA WDC.... (320.1 GB)
/dev/sda1 --> Windows Vista (loader)
/dev/sda2 --> Windows Recovery Environment (loader)
/dev/sdb --> ATA Hitachi... (320.1 GB)
/dev/sdb1 --> Ubuntu 10.04 LTS (10.04)

So, now where do I have to put grub?

Edit: and btw, it's not for Ubuntu Studio anymore, but just for the plain version, cause in studio, I could not connect to my WiFi

---

### Post by BelgianCubbie on 2010-05-02
anyone?

---

### Post by oldfred on 2010-05-02
If you do not have SATA drives your BIOS does not control boot drive. Computers only boot from primary master.

Older IDE drives use cable select or tiny jumper pins on the drive for master/slave.
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)

You still should install grub to sdb. Do not install to any partitions. Then reset drives to boot sdb as primary master.

---

### Post by BelgianCubbie on 2010-05-02
In my BIOS there is no way I can select which drive to boot from, therefor I can not set sdb as primary master.

---

### Post by BelgianCubbie on 2010-05-02
I tried to put it in each of the drives and partitions and all failed.
The closest to any succes was to put it in sda, but then i got an error saying:

error: no such device: 918a9e14-a72c-4d16-ab22-71f95c71b491
grub rescue>

wtf is that all about?

---

### Post by malrost on 2010-05-02
I'm still using GRUB legacy not GRUB2, but I believe what you need is to use the drivemap command (formerly known as [map]("http://www.gnu.org/software/grub/manual/html_node/map.html")).

See [this thread]("http://kubuntuforums.net/forums/index.php?topic=3106368.15;wap2") for an example of someone using drivemap to boot windows from a non-first hard drive.

---

### Post by BelgianCubbie on 2010-05-02
Oh well, since I can't seem to find any help and I need my laptop at work running windows, I'm gonna give up on Ubuntu. Looked nice, seems to have it all, EXCEPT a way to make it bootable.

Therefor, Bye Bye Ubuntu

---

### Post by abra1 on 2010-05-02
[QUOTE=BelgianCubbie;9221332]Oh well, since I can't seem to find any help and I need my laptop at work running windows, I'm gonna give up on Ubuntu. Looked nice, seems to have it all, EXCEPT a way to make it bootable.

Therefor, _[FONT=Arial]Bye Bye Ubuntu[[/FONT]_/QUOTE]


Hi  BelgianCubbie, 

Before your final   "   Bye Bye "      have a look at this -  

[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")   

- there are lots of pictures and I believe they are self-explanatory. But you may have to start all over.

And let us know

---

### Post by BelgianCubbie on 2010-05-02
Again this didn't do anything for me... installing grub on the 2nd HD and then using another OS's grub to boot into it??? and like I said before, NO I CAN'T CHANGE MY BIOS TO BOOT FROM MY 2ND HD.

Unless someone comes up with a REAL solution, it's def. Bye Bye Ubuntu and for sure NO recommendations to anyone else.

---

### Post by abra1 on 2010-05-03
> **BelgianCubbie said:**
> Again this didn't do anything for me... installing grub on the 2nd HD and then using another OS's grub to boot into it??? and like I said before, NO I CAN'T CHANGE MY BIOS TO BOOT FROM MY 2ND HD.

Unless someone comes up with a REAL solution, it's def. Bye Bye Ubuntu and for sure NO recommendations to anyone else.


re: [http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")   

In the picture , Step 4 - "Prepare disk space "  is apparently scary  - because it appears that you are deleting Windows. 
But actually in the next step (see arrow down )  you  have a choice which disk to use for Ubuntu.
Please read the instructions on the right side of the screen (I suspect that you missed those -lol!

---

### Post by BelgianCubbie on 2010-05-03
I know how to install windows, I know how to install Ubuntu. They both run fine when installed on the 1st HD without the other OS installed. The problem is when installing Vista on HD0 and Ubuntu on HD1 that Grub just refuses to run and always comes up with this "no such device" error. I tried to install Grub in every possible place, but to no avail.
With Vista and Ubuntu installed, I have no problem running Vista after restoring their mbr.

So the problem is with installing that @#$% Grub.

---


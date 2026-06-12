---
title: "Installation problems Latitude C610 (CDROM)"
date: 2004-12-29
forum: Installation &amp; Upgrades
---

### Post by JHendrix on 2004-12-29
Here's the bag:

I'm trying to install Ubuntu on my Latitude c610.  However I'm having problems with the CDROM.

If I do the normal install, it'll go through the module loading and eventually it'll sit there a while and eventually "scan CDROM".  After that little progress bar goes away the system will just idle at the blue screen. 

So I try expert mode.  It goes through the setup steps till I get to "Detect and Mount CDROM".  It goes through the modules and eventually it'll go through the idle and scan CDROM steps described above.  Then it asks for HDPARM info.  It seems if I type anything in that box I'll get a big error message (screen turns red) and it goes back to the menu.

Then when I try "Load installer components from CD" it tells me it "failed to copy file from CDROM".

Obviously this is the main problem, but here's some food for thought:

I booted the system using a Knoppix CD I had lying around and that wouldn't boot up unless I gave it the nodma option since it would hang at "looking for CDROM at /dev/scd0"  However once I gave it the nodma option it would boot.

So any thoughts on how to fix this?

---

### Post by JHendrix on 2004-12-30
I'm trying it with the Live CD and I can not get the ide=nodma option to work.   Is there any way I can start the installer with DMA disabled?

---

### Post by Sioben on 2005-01-03
[QUOTE=JHendrix](...)
So I try expert mode.  It goes through the setup steps till I get to "Detect and Mount CDROM".  It goes through the modules and eventually it'll go through the idle and scan CDROM steps described above.  Then it asks for HDPARM info.  It seems if I type anything in that box I'll get a big error message (screen turns red) and it goes back to the menu.

Then when I try "Load installer components from CD" it tells me it "failed to copy file from CDROM".[/QUOTE]

Hello. I had exactly the same problem with my **Dell Latitude CPt S500GT**
I'm still trying to install Ubuntu, but I don't know what to do when I read the sentence "This CD is not an official Ubuntu CD-Rom" "corrupted..." something like this. I downloaded and burned two times orginal ISO files (+MD5 checksum: ok in both cases). So...? Probably a problem with the CD drive?

In expert mode, what's the best info to type for HDPARM?

---

### Post by critter42 on 2005-01-03
[QUOTE=JHendrix]I'm trying it with the Live CD and I can not get the ide=nodma option to work.   Is there any way I can start the installer with DMA disabled?[/QUOTE]

at the boot menu, press down to stop the countdown timer, then press back up again (so just plain Ubuntu is highlighted).  Now, if you press the left or right arrow key, you'll see the cursor move in the command line that's below the menu.  This is where you would type any options you want during startup.  ide=nodma doesn't work, but just nodma works.

As an aside, in order for it to boot on my Latitude D266XT I actually had to add both noscsi AND nodma

critter42

---

### Post by Sioben on 2005-01-06
I found an alternative solution here: 
[http://ubuntuforums.org/showthread.php?t=8350](http://ubuntuforums.org/showthread.php?t=8350)
(topic: "CD boots then installer can't find CD")

In fact, this is THE solution to load all installer components from CDROM. BUT after that, you keep the same problem with your CD-Rom drive...  (although it seems possible to mount cdrom at startup, but I'm still workin on it 'cause I'm a Linux newbie)...

-> Look at [https://bugzilla.ubuntu.com/show_bug.cgi?id=1440](https://bugzilla.ubuntu.com/show_bug.cgi?id=1440)
... especially at comment #42 and #43: they explain what's exactly the problem and how resolve it. 



===============
1. boot up as normal
2. Choose Language
3. Skip to tty2 by hitting alt-F2
4. do:
       insmod /lib/modules/2.6.xxxxx/kernel/drivers/cdrom/cdrom.ko
       insmod /lib/modules/2.6.xxxxx/kernel/drivers/ide/ide-core.ko
       insmod /lib/modules/2.6.xxxxx/kernel/drivers/ide/ide-generic.ko
       insmod /lib/modules/2.6.xxxxx/kernel/drivers/ide/ide-cd.ko
5. Return to tty1 by hitting alt-F1
6. Continue as usual loading other modules after the above are in place.

(-> where "2.6.xxxxx" is "2.6.8.1-3-386" for i386 PC)


"The above is from memory so I may have the order of module install wrong.  
I was more bluffing than doing something that I knew was strictly correct."

"This worked successfully to get the install finished.  However, now it 
appears that the installer has not configured /etc/modules (or some such) 
correctly and the same problem is exhibited by the installed system."

---

### Post by bennyp on 2005-01-13
I am installing Ubuntu sn an old IBM machine at school and this clever solution worked to get the the installer running! Thank you very much!

---

### Post by n00b on 2006-01-19
My appolgies for digging up such an old topic but I'm having the same problem and and want to try this. 

> ===============
1. boot up as normal
2. Choose Language
3. Skip to tty2 by hitting alt-F2
4. do:
insmod /lib/modules/2.6.xxxxx/kernel/drivers/cdrom/cdrom.ko
insmod /lib/modules/2.6.xxxxx/kernel/drivers/ide/ide-core.ko
insmod /lib/modules/2.6.xxxxx/kernel/drivers/ide/ide-generic.ko
insmod /lib/modules/2.6.xxxxx/kernel/drivers/ide/ide-cd.ko
5. Return to tty1 by hitting alt-F1
6. Continue as usual loading other modules after the above are in place.

(-> where "2.6.xxxxx" is "2.6.8.1-3-386" for i386 PC)

Now what do I have to substitute 2.6.xxxxxx with because I have ver. 5.10 for amd64 ?

Thanx

---

### Post by n00b on 2006-01-19
*bump*

Come on. This can't be such a hard question.

---

### Post by n00b on 2006-01-25
Just trying again.

---

### Post by Sioben on 2006-01-31
[QUOTE=n00b]Now what do I have to substitute 2.6.xxxxxx with because I have ver. 5.10 for amd64 ?[/QUOTE]

HI n00b.

First, to find your Linux kernel version, you have to type:
**uname -a** (or "uname -r" = only version number)

-> for Ubuntu 5.10 Breezy: it's normally Linux 2.6.12.6 , but I'm not sure how to write it for a 64-bit PC (AMD64)... so... try probably:
2.6.10-6-amd64-generic (or 2.6.12-6-amd64)
2.6.10-5-amd64-generic (or 2.6.12-5-amd64)
?... but type uname -r , it's easier ;-)

Good luck, cya,

---


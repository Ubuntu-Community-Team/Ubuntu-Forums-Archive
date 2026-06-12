---
title: "grub rescue prompt"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Quib on 2010-04-30
My first post to the forums is a desperate one. 

What I started with: Dual Boot Win 7 64 bit / Ubuntu 9.10 64 bit   I followed a tutorial to get the whole thing set up in the first place, so my skill level is very low when it comes to Ubuntu. The initial set up was a nightmare, but once it was finally up and running everything worked as it should. 

What I tried to do: I used the update manager in 9.10 to attempt to update to 10.04. After 6 hours of downloading and installing it asked me some questions about grub or updating grub and where to install grub... I really don't know. I read the suggestions and chose the the partition that I believe had the boot flag. I'm now not so sure.

What is happening now: GRUB loading. error: the symbol 'grub_puts_' not found  grub rescue>

I'm completely out of my depths here.

Why I am panic stricken: I'm two weeks from graduation and all of the materials and software that I need to complete papers/projects and such (many due within the next 5 days) are located on my win7 partition. 

What I need: In a perfect world, I'd love help restoring grub or my MBR or whatever needs to be done so that I can successfully dual boot into win7 and Ubuntu 10.04, but I don't need anything from the linux partitions. I absolutely must be able to boot into win 7 without losing any of my data or software. 

Please advise. Thanks in advance.

---

### Post by wilee-nilee on 2010-04-30
Do you have a install DVD for W7 or a recovery disc?

---

### Post by Quib on 2010-04-30
Yes, I have an install backup disc for win 7 pro, and I have a live disc for Karmic Koala. I'm replying on an old powerbook with no disc burning capabilities, so that's all I'm likely to have for now.

What next?

---

### Post by wilee-nilee on 2010-04-30
If at this point you would like to get W7 back and worry about the Ubuntu setup later this thread should help, post #4 has the instructions, post #5 has a link that shows the process. This will reload the W7 boot-loader.
[http://ubuntuforums.org/showthread.php?t=1466021](http://ubuntuforums.org/showthread.php?t=1466021)

You could also just boot the live Lucid cd see if it works, then go to gparted and delete the ext4 primary for Lucid then make a new ext4 and do a custom install in the partition gui in the installation of Lucid. It seems though that getting W7 back right away will be what works best for you.

---

### Post by Quib on 2010-04-30
I'll give that thread a look. thanks for the reply. You're right about the win 7 priority. If I can get back to that then I'll revisit the Ubuntu part of the equation after graduation.

---

### Post by wilee-nilee on 2010-04-30
> **Quib said:**
> I'll give that thread a look. thanks for the reply. You're right about the win 7 priority. If I can get back to that then I'll revisit the Ubuntu part of the equation after graduation.

I am a college student myself, finished midterms today. I would get a external HD to back that stuff on to, good luck with everything.

---

### Post by Quib on 2010-04-30
Ok, you are not going to believe this. 
I followed the instructions to repair the MBR. I didn't work, but there is a note on the page that says "*If this method fails to restore the MBR, you can try the *[**_*bootrec command*_**]("http://support.microsoft.com/kb/927392")*". *No big deal, reboot and try again.  Only now, when I get to the "press any key to boot from CD or DVD" screen, nothing happens. 

I can't fathom how attempting to repair the MBR would have any effect on this, but that is certainly how it appears. the only visible change is that now if I try and boot without a disc, there is only a flashing cursor. I suppose this is a windows issue now, but it is baffling. 

Idiot check: Is the disk in the disk drive? yes, Is the keyboard plugged in? Yes, the caps lock light is on, and I unplugged it/plugged it back in to be certain. Did it work just moments before? Yes, perfectly. **Will it boot from your 9.10 live disc? Yes, it will. WTF?**

I'm open to suggestions.

---

### Post by wilee-nilee on 2010-04-30
> **Quib said:**
> Ok, you are not going to believe this. 
I followed the instructions to repair the MBR. I didn't work, but there is a note on the page that says "*If this method fails to restore the MBR, you can try the *[**_*bootrec command*_**]("http://support.microsoft.com/kb/927392")*". *No big deal, reboot and try again.  Only now, when I get to the "press any key to boot from CD or DVD" screen, nothing happens. 

I can't fathom how attempting to repair the MBR would have any effect on this, but that is certainly how it appears. the only visible change is that now if I try and boot without a disc, there is only a flashing cursor. I suppose this is a windows issue now, but it is baffling. 

Idiot check: Is the disk in the disk drive? yes, Is the keyboard plugged in? Yes, the caps lock light is on, and I unplugged it/plugged it back in to be certain. Did it work just moments before? Yes, perfectly. **Will it boot from your 9.10 live disc? Yes, it will. WTF?**

I'm open to suggestions.

Did you run the auto repair or go to the command line to enter  BootRec.exe /fixmbr

Is the backup disc you have the backup you made when you bought the computer if this is correct? or is the disc a full install backup DVD.

---

### Post by Quib on 2010-04-30
Alright, it finally loaded the windows 7 disc so that I could try the bootsect.exe /fixmbr

This is what I've done: I ran the automatic startup repair and it did not detect a problem. I then I folowed the instruction that you pointed me towards. It claims "bootcode was successfully updated on all targeted volumes. Finally, as mentioned in those instructions, I also ran bootrec.exe /fix mbr.

nothing so far... I'm about to try again with bootrec.exe / fixboot

---

### Post by Quib on 2010-04-30
Woohoo! I did the bootrec.exe / fix mbr  and then immediately followed that with bootrec.exe / fixboot
That worked. I have no idea how this will help anyone else since I can't access a working version of Ubuntu at the moment, but at least I can get to semester projects. 

My experiences with Ubuntu installs have been very unpleasant but you have helped me immensely. I'll return when I have more time to tinker with Ubuntu. 
thanks. 
That 8am ethics class is going to suck even more today (it's 3am where I'm at).

---

### Post by wilee-nilee on 2010-04-30
> **Quib said:**
> Woohoo! I did the bootrec.exe / fix mbr  and then immediately followed that with bootrec.exe / fixboot
That worked. I have no idea how this will help anyone else since I can't access a working version of Ubuntu at the moment, but at least I can get to semester projects. 

My experiences with Ubuntu installs have been very unpleasant but you have helped me immensely. I'll return when I have more time to tinker with Ubuntu. 
thanks. 
That 8am ethics class is going to suck even more today (it's 3am where I'm at).

Whew I thought maybe that the backup was a full system backup. My upgrade version of W7 DVD is called a backup, I am as relieved as you are believe me. Do no harm is my first motto, it's the ethics you know. ;) The auto repair appears to not work when a bootloader other then a MS one is in the MBR.

---


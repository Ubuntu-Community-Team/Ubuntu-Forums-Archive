---
title: "How to do I preserve my separate '/home' partition when reinstalling Ubuntu 12.04"
date: 2012-06-27
forum: Installation &amp; Upgrades
---

### Post by Starfleet on 2012-06-27
Hi everyone, I have a pretty basic question I think, but I don't seem to be able to find a definitive answer by searching. This may mean I'm not asking the right question/s I guess. 

However, please can anyone confirm to me how to keep my current and separate '/home' partition intact when I reinstall Ubuntu 12.04LTS. I installed Ubuntu with a separate home partition to make some things easier and perhaps a bit more secure. I know I need to click the 'something else' button on the installation program and somehow tell it to leave the '/home' partition alone during reinstallation, but how? It is dual booted with Win7 with Grub2 on the 12.04 /boot partition so as not to get bootup glitches from big updates from either OS etc but I know the dual boot is not an issue of any kind for what I want to do. Clearly, I'll being backing up stuff before doing anything just in case of meltdown.

Great site by the way and much much better support in my opinion than the MS sites provide. ):P

---

### Post by Seb71 on 2012-06-27
Yes, choose "Something else" option durin install.

For /home, select that partition, choose the same file system as the existing one, mount as /home, without formatting that partition. If you also want to keep the settings, you should choose the same user name.

---

### Post by nipunshakya on 2012-06-27
You have already got it right upto selecting the 'something else' option... just be sure that you don't select to format the /home partition. Just point to your previous / partition, use the same user name as before and then select your previous /boot for the installation of the GRUB and everything should work as a charm....

Goodluck

---

### Post by dino99 on 2012-06-27
you need to choose the manual way for install, and when gparted will ask for partitioning, only format your root partition (/). 
Of course you need first to know exactly the actual partitions name for : /, /home, /swap (/dev/sdx, replace x by yours).
To do so, first run gparted only to take note of the partitions address

Then when installation will ask for partitioning:
 be sure to select the / partition (/dev/sd?) to format, set ext3 or ext4, make bootable & declared as /
select /home, without formatting, declared as /home
and finally select /swap declared as /swap (no formatting)

and "apply" changes to continue installation

later you will be asked about grub2, set it on /dev/sda (or else if your ubuntu's hdd is not sda)  ):P

---

### Post by Starfleet on 2012-06-27
Guys, thanks so much for the replies. I've been away from my computer working so sorry for the late come back. You all seem to be saying the same thing so that's great. Tomorrow I will be working on my machine and will follow the guidance you've given me. I'm sure it will go well...I'll mark this thread 'solved' when I've completed the work. 

bye for now...):P

---

### Post by nipunshakya on 2012-06-27
Goodluck buddy.. c ya on the other side.. :D

---

### Post by kalkems on 2012-06-28
Just a comment on this method.  On the computers I manage there are often more user accounts than one and at install one produces only one account.  After first startup you only see the account you created but all the others are preserved.  All you have to do is recreate the user accounts and they will be connected to the old home folders.

---

### Post by Starfleet on 2012-06-28
Kalkems, thanks for that info. It's doing the nitty gritty stuff, the actual turning of the nuts and bolts that is sometimes not explained quite enough for me. You guys have helped a bunch. Again thanks to all of you for your responses. I'll be working on my computer later today and will let you all know how it pans out. I'll be able to mark the thread solved at that point I'm sure. ):P

---

### Post by Starfleet on 2012-07-04
Hi Guys, I must thank you all again for your advice. I took it and the new dual boot system is working just brilliantly. The separate /home partition was preserved beautifully. 

I set up the system to dual boot with Win7 using what seems to be a really good and bullet proof way of preventing boot problems when big updates for Ubuntu or Windows come in. Something I'd experienced a time or two recently. The method uses EasyBCD in Windows to control the first part of the boot. I followed advice from the link below to try it with EasyBCD and Grub2 working together. It's working superbly and the big updates for both systems that came in once Ubuntu was reinstalled failed to upset anything, as it unfortunately did a day or two earlier.

[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/]("http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/")

The instructions in the link above are very easy to follow with pics and text and they work!:)

---

### Post by nipunshakya on 2012-07-04
Glad to see you on the other side... goodluck with your ubuntu experience...

Happy Linuxing... :)

---

### Post by Starfleet on 2012-07-04
Yep, it's all good! I've been using Linux Ubuntu for around 6 years now but because it's so trouble free, you never really have to do stuff to it. I've migrated it from computer to computer in that time and done some stuff with it. But I forget things easy and preserving my partition is really simple but just couldn't be sure. So you guys helped alot to get me going again. Incidentally, I don't normally run Windows of any sort on either of my machines, but had the chance to get a copy (fully legit) for next to nothing so thought I'd take a look. It installed easy, but straight away started to 'play up' and has been quite glitchy at times and of course, very slow compared to Linux. All stuff that reminded me of why I left Windows in the first place!

Again, thanks!;)

---

### Post by nipunshakya on 2012-07-04
> **Starfleet said:**
> Yep, it's all good!
All stuff that reminded me of why I left Windows in the first place!


Same here... :)

---


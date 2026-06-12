---
title: "How do you install Puppy Linux 5?! I don't get it! D:"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by TheNerdAL on 2010-05-19
I'm trying to install Puppy Linux 5 but there are a lot of windows that give me options and I don't get it, thanks.

---

### Post by jocko on 2010-05-20
Here's some pages you would have found with a very simple google search (keywords: install puppy linux):
[http://www.arsgeek.com/2006/12/05/installing-puppy-linux-to-your-hard-drive/](http://www.arsgeek.com/2006/12/05/installing-puppy-linux-to-your-hard-drive/)
[http://www.ehow.com/how_5063994_install-puppy-linux-hard-drive.html](http://www.ehow.com/how_5063994_install-puppy-linux-hard-drive.html)

---

### Post by TheNerdAL on 2010-05-20
> **jocko said:**
> Here's some pages you would have found with a very simple google search (keywords: install puppy linux):
[http://www.arsgeek.com/2006/12/05/installing-puppy-linux-to-your-hard-drive/](http://www.arsgeek.com/2006/12/05/installing-puppy-linux-to-your-hard-drive/)
[http://www.ehow.com/how_5063994_install-puppy-linux-hard-drive.html](http://www.ehow.com/how_5063994_install-puppy-linux-hard-drive.html)

I think Puppy Linux 5 is different than that.

---

### Post by wilee-nilee on 2010-05-20
Puppy can be kind of confusing, so hit the install, set up the partition ext3 at the most. When it gets to grub install choose install, in the 1st screen it would say sda1 if puppy is going into sda1 then in the next screen it asks in a partition and another but choose MBR do this process 2 times, at least this is what works for me twice running the grub install. On the reboot make sure the puppy files are saved in the sda1 or what ever partition you have installed in, be careful with all of this if you have more then 1 distro. You can open up gparted in puppy and any Linux distro while installing to confirm the partitions.

The MBR might not be safe is sort of like the grub install in Lucid that says if your not sure tick all. It is misinformation.

Now sometimes I have a puppy install that doesn't boot after a installation so I just reload grub2 since I have it dual booted with a distro with grub2 this seems to get it to boot correctly. Even though this is Lucid puppy it uses grub legacy as a boot loader so that file can be edited, but I have never edited grub files.

I have also had problems when I have had a MS bootloader and a grub bootloader in the MBR, so I just use a hirens disc to write the mbr to all 0's, this is done only when I have a empty hard drive since the program I use will write the whole HD to all 0's if left running.

---

### Post by TheNerdAL on 2010-05-20
> **wilee-nilee said:**
> Puppy can be kind of confusing, so hit the install, set up the partition ext3 at the most. When it gets to grub install choose install, in the 1st screen it would say sda1 if puppy is going into sda1 then in the next screen it asks in a partition and another but choose MBR do this process 2 times, at least this is what works for me twice running the grub install. On the reboot make sure the puppy files are saved in the sda1 or what ever partition you have installed in, be careful with all of this if you have more then 1 distro. You can open up gparted in puppy and any Linux distro while installing to confirm the partitions.

The MBR might not be safe is sort of like the grub install in Lucid that says if your not sure tick all. It is misinformation.

Now sometimes I have a puppy install that doesn't boot after a installation so I just reload grub2 since I have it dual booted with a distro with grub2 this seems to get it to boot correctly. Even though this is Lucid puppy it uses grub legacy as a boot loader so that file can be edited, but I have never edited grub files.

I have also had problems when I have had a MS bootloader and a grub bootloader in the MBR, so I just use a hirens disc to write the mbr to all 0's, this is done only when I have a empty hard drive since the program I use will write the whole HD to all 0's if left running.

How about if I want it on my whole hard drive?

---

### Post by Guitar John on 2010-05-20
> **TheNerdAL said:**
> How about if I want it on my whole hard drive?

This [HowTo]("http://puppylinux.org/wikka/InstallationFullHDD") is for Puppy 4.xx, but you may find what you need.

---

### Post by wilee-nilee on 2010-05-20
> **TheNerdAL said:**
> How about if I want it on my whole hard drive?

I think the instructions above me are good pretty much the same as mine. I have had hit and miss with puppy being correctly bootable after a install. I don't think your going to figure it out without just doing it.

I like grub2 so I just use puppy with another grub2 distro.

---

### Post by TheNerdAL on 2010-05-20
I get a darn kernel panic. :(

---

### Post by ultrasquid on 2010-05-21
Man, I have spent the last 2 hours banging my head on this one.  I eventually got it to work. Here is how.

1. Boot from disk and fire up gparted.  Delete all partitions.  If this is not a viable option I would say just make sure you have 1 empty ext3 partition you are going to install to.  Make sure that partition is flagged for boot by right clicking an selecting manage flags and checking boot.

2. Go to Setup> Puppy universal installer .   Select the Internal ide/sata hard drive option. Select the proper hard drive (if more than one) an hit ok.  Now click the little dog icon @ the top next to Install puppy on sda1 (might not be 1 if you have other partitions but I am just following what worked here.)  Select ok then when it asks where the files are tell it the cd. 

3. Now here is where I think I was having the issue I kept selecting "frugal" instead of full install.  I am a frugal guy :) But after going through this so many times I thought I would give full a shot.  When I did the fell disk install it actually started the grub install automatically (like in all the faq's I read on setup.) Rather than running manually after the install to hard disk.  Tell grub to install to the MBR on the hard drive.

After grub installed I shut down and  and did not save the pupsave file or the lupu500 file.  Saved nothing and shut it down.  On boot I got grub and it booted (no error 15 file not found)

I think the real issue lies with the frugal install.  [B][U]If you have an empty ext3 partition, I think you can do the full install and remedy your issues.
[/U][/B]
Keep in mind, I am doing this on a empty hard drive.  No other important stuff or other operating systems. I can't say I would advise this if you have important stuff on the drive.  In the future I hope to have puppy, kubuntu, windows xp, and windows 7 all living in harmony on this machine.  I will see how that plays out.  I hope this helps you fix your situation.

P.s. thanks to all the people actively working on puppy, it is a great distro!

---


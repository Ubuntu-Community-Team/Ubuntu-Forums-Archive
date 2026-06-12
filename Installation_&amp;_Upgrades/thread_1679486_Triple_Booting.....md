---
title: "Triple Booting...."
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by GeissT on 2011-02-01
Hey everyone,

I currently have Windows XP (urrggghhh) and Ubuntu 10.10 (:D) dual booting on grub fine. I want to add Backtrack. Now i have never triple booted before and I want to know how i can go about this.

Can the graphical installer for backtrack do this successfully? If not what are some other really easy solutions?

Please dont flame -.-.

GeissT

---

### Post by zvacet on 2011-02-01
I never tried Backtrack,but if your question was can you resize partitions with Backtrack installer answer is probably yes.If you can not do it with it try your Ubuntu live CD to shrink existing partition to make space for new system.

---

### Post by lewisskinner on 2011-02-01
> **zvacet said:**
> I never tried Backtrack,but if your question was can you resize partitions with Backtrack installer answer is probably yes.If you can not do it with it try your Ubuntu live CD to shrink existing partition to make space for new system.

I have previously triple- and even quad-booted before, Generally Virista (for gaming), Ubuntu (for day-to-day) and then a couple of small partitions (~5-10GB) upon which I install other OS's for testing/because I'm interested in how they differ (I've used ReactOS, FreeBSD, pure Debian, Slackware, DSL, Fedora, Open SuSe etc).

The installation will go fine, the main thing to do is to make sure you edit Grub so that XP, Ubuntu and  your Backtrack loaders are visible to it.  This can be done from a terminal, or via a grub editor (in the past, the list was located at /boot/grub/menu.lst, but if you have grub 2, and you will from Ubuntu 9.10, you'll need to look in /etc/grub.d).

Check out this page on [howtogeek](http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/) for more info.

Have triple penetration!

---

### Post by oldfred on 2011-02-01
Some have had issues getting grub2's osprober to find BT. I suggest you install the grub legacy from BT to the partition, definitely not to the MBR. Then if the osprober does not find it, you can chainload to it.

See this thread:
[SOLVED] Triple Boot Grub Help
[http://ubuntuforums.org/showthread.php?t=1676703](http://ubuntuforums.org/showthread.php?t=1676703)

---

### Post by GeissT on 2011-02-02
Thanks,

I am still a novice with Linux in general so I wont go messing with Grub manually.

But thanks. Would be better if BT would do all that for me :D

GeissT.

---

### Post by stkrzysiak on 2011-02-02
Not an answer to your question, but one option I would consider(if I were you) were a bootable BT4 usb or sd card.  Pop it in when you need it, and wala, persistent changes and all.  I picked up a 16GB card a week or so ago for $21.  

I know you said you were new to Linux, but there's no better crash course than trying to create a bootable ecnrypted usb drive, see here: [http://www.infosecramblings.com/backtrack/backtrack-4-bootable-usb-thumb-drive-with-full-disk-encryption/](http://www.infosecramblings.com/backtrack/backtrack-4-bootable-usb-thumb-drive-with-full-disk-encryption/)

Please note:  If you choose to follow that tutorial, follow the instructions completely.  In particular, when you get to that screen that says 'Ready to install' you have to click advanced and choose your removable media as the place where to boot the boot loader.  Trust me, this will ruin your night if you dont.  If you dont trust yourself, just disable the hard drive altogether for some extra protection :p

---

### Post by oldfred on 2011-02-03
If you want to get into multibooting you need to understand grub2. Originally there were compaints about not enough info on grub2, but now there is almost too much, so it can be difficult to find the exact small change you want to make. Many here can help with those kind of issues.

Reinstalling grub or grub2.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by lindsay7 on 2011-02-03
I have two computers with a triple boot, Ubuntu 10/4-windows 7-ubuntu 10/10 and the other is Ubuntu-windows 7-Jolli Cloud.

Grub2 set it all up without me doing anything special other then setting up the partitions before installing.

---

### Post by kansasnoob on 2011-02-03
I don't know how helpful this might be but I remembered meierfra helping me with a Backtrack boot problem quite some time ago:

[http://ubuntuforums.org/showthread.php?t=1411025](http://ubuntuforums.org/showthread.php?t=1411025)

That one included a separate /boot partition which I generally avoid like the plague! The only time I use separate /boot is on really OLD systems where multi-booting is not really an option.

---

### Post by kansasnoob on 2011-02-03
> **oldfred said:**
> **[COLOR="Red"]If you want to get into multibooting you need to understand grub2. [/COLOR]**Originally there were compaints about not enough info on grub2, but now there is almost too much, so it can be difficult to find the exact small change you want to make. Many here can help with those kind of issues.

Reinstalling grub or grub2.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

+1!

The change freaked me out a bit for a week or so but now it's just soooooooooo much easier than legacy grub that I wonder what took so long :guitar:

---

### Post by GeissT on 2011-02-04
Thanks everyone, i might make a bootable usb when i buy one.

Thanks all.

---


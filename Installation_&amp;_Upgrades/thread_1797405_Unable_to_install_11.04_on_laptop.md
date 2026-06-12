---
title: "Unable to install 11.04 on laptop"
date: 2011-07-05
forum: Installation &amp; Upgrades
---

### Post by bigbukcy on 2011-07-05
[FONT=Arial][SIZE=2]I am trying to install 11.04 on an older Averatec laptop.  (AMD Athlon XP-M 2200+, 512 MD DDR, 60 GB HD)  I tried Live CD and alternative.  They both freeze up during installation.  Live CD is definitely good as I can open Ubuntu as a trial on another computer.  Booting as a trial on the laptop also freezes up.
[/SIZE][/FONT][FONT=Arial][SIZE=2][SIZE=2]
Tried boot parameters "nomodeset" and "acpi=off" without success.  Reformated disk several times with dban which hasn't helped.  Even tried xbuntu in case there wasn't enough memory.  That froze up as well.

Any other suggestions?[/SIZE][/SIZE][/FONT]

---

### Post by mörgæs on 2011-07-05
Hi, welcome to the fora.

Xubuntu is not much lighter than Ubuntu. For this computer I would recommend Lubuntu.

---

### Post by bigbukcy on 2011-07-06
Lubuntu didn't work either.  They all freeze up midway through installation.  Anyone else know what I can do?

---

### Post by bigbukcy on 2011-07-06
Iso is good when checked with md5sum

I can boot a trial on my windows computer so the disk looks good.  But when I "check disk" on the laptop it freezes up.  All I see is a list of text and it stops at:
[6.547205] [<c178d0e0>] ? i386_start_kernel +0xe0/0xe8

Also I can't boot as a trial on the laptop.  If it was a problem with the hard drive on the laptop I wouldn't think I could reformat it with Dban without a problem.

---

### Post by foresthill on 2011-07-06
Couple of thoughts here.

Have you tried running Memtest from the initial menu on the install disc to rule out bad RAM?

Also. have you tried installing 10.10? I honestly don't see much improvement in 11.04 over 10.10. I have 11.04 installed on two different machines, but I don't use it because it's just WAYYY too buggy for me to use in its current state. Updates will probably straighten out most of the major problems, eventually. 

But until then, I would recommend sticking with 10.10. Or rather, that's what I'm doing, FWIW.

---

### Post by mörgæs on 2011-07-07
Yes, a memtest is a good idea. Also, there are more boot options to test:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

Other light distros are:
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)

---

### Post by bigbukcy on 2011-07-08
thanks for suggestions

Memtest was fine

Tried 10.10 and I could boot as a trial but again froze when trying to install

I have checked all the boot parameters when trying to install

I will try to find a copy of Lubuntu 10.10 but is it possible that none of these can be installed on my computer :(

---

### Post by wandalalakers on 2011-07-08
Video card?

---

### Post by foresthill on 2011-07-08
Yeah, the video card was my first thought too. Too bad it's a laptop and he can try a different card.

Aren't there some grub commands you can enter at the initial install screen for working around problematic video cards? 

I would look into that, since a video card would be the most likely culprit.

Another possibility might be to go into the bios and look at your SATA / IDE mode. Some bioses let you change that to "compatibility mode". An incompatible SATA / RAID / IDE controller would be my second guess.

---

### Post by malspa on 2011-07-08
11.04 from the CD was extremely slow installing to my notebook, but it didn't completely freeze up, and the installation eventually finished. An earlier installation from of Mepis 11 from the live DVD went quickly. Thinking maybe try to install 11.04 from a flash drive?

---

### Post by Blasphemist on 2011-07-08
Have you tried booting to and using a utility cd? System rescue cd, gparted, etc. I have to wonder about it being a video issue from what you describe. It sounds like it might be an issue with the hard drive but I don't know it's condition from what you've posted. You could boot to a GParted cd and get your partitions in order before an install and I'd think if your hdd is the issue it would show up.

---

### Post by bigbukcy on 2011-07-08
I'll try Gparted

Tried Lubuntu 10.10 as well with no luck.  I've tried booting from USB and same problem.  I've left it overnight and it stays frozen so I don't think it's just a slow installation.

I didn't see any compatability mode in bios.  Man, I'm so frustrated with this.  It's not making it easy to quit MS.

---

### Post by kennedyvelez on 2011-07-08
I also tried 11.04. It also a hangman... It takes forever to  load without installing after clicking "TRY Ubuntu" or "INSTALL Ubuntu." LTS is still good...

---

### Post by bigbukcy on 2011-07-09
I deleted the partitions that were created with the latest aborted installation using Gparted.  Tried installing again with no luck.  So I'm guessing if it's a video card issue there's not a lot I can do to get this to work?

---

### Post by mörgæs on 2011-07-09
Yes, it is likely to be a video card problem, and there are often lots of tricks one can do. As posted before, which card do you have?

There are also other distros worth trying:
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)

---

### Post by Blasphemist on 2011-07-09
This is a sticky thread on graphics issues. The OP is very good at helping with graphics issues. [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

The first 3 posts are where to start. See if that helps.

---

### Post by ronparent on 2011-07-09
None of my older AMD systems will boot current releases without a boot parameter. In my case that is 'nolapic'. I have to use that parameter to boot the live cd as well as modify the /etc/default/grub file after installation to include the needed parameter in the grub menu line to insure my system will run without freezing on me.

Finding a needed boot parameter is a tedious process initially requiring manually editing the live cd boot line until you find a parameter or combination of parameters that work. You can look at this reference for some suggested parameter to examine: [https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

Good luck and post how it works out for you.

---

### Post by bigbukcy on 2011-07-11
So tried Lubuntu 10.10 with all the F6 boot variables checked and it freezes

But I can boot from the Live CD as a trial with no parameters checked.  Even played a little minesweeper.  That doesn't seem to make sense if it is a video problem does it?

Tried "sudo service gdm start" and got the black screen but then I couldn't stop it.  It froze and I couldn't enter any further commands.

---


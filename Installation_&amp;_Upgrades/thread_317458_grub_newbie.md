---
title: "grub newbie"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by krelverehan on 2006-12-12
So I have tried to install ubuntu without a CD on my gentoo machine with no luck. Fortunately, I have a friend who had an unbuntu boot disk laying around. My computer boots using grub. How to I install ubuntu using grub (or any manner..), from the CD? I have no floppy drive...

](*,)

---

### Post by Klaidas on 2006-12-12
Um... is there a cdrom drive?

---

### Post by krelverehan on 2006-12-12
Sorry, I forgot to mention.

So, yes there is... But no burner.

---

### Post by bulldog on 2006-12-12
Do you have a install cd ie. Ubuntu live cd or the alternate cd?
Or do you just have GRUB on the cd.

---

### Post by krelverehan on 2006-12-12
Both, actually. :)

---

### Post by bulldog on 2006-12-12
Well boot from the live cd to see if your hardware is recognized properly.
If so, hit the install button on the desktop and install ubuntu.

Make sure you have enough space for Ubuntu,you should have about 10GB to make a decent test run.

---

### Post by krelverehan on 2006-12-12
Uh...

I am running gentoo, linux. Where would I find this install? Should I run it on wine?

---

### Post by krelverehan on 2006-12-12
I got the computer for free from a friend. It had gentoo on it already. I am familiar with linux and the command line, but gentoo is too much for me to handle.

---

### Post by bulldog on 2006-12-12
You have to reboot your computer.put the live cd in the player and set in BIOS to boot from cd-rom first.

Than the live cd will boot,with a little luck it should anyway.
You see a menu and choose the first option.
If all is okay,you will boot to the Ubuntu desktop,you can look around and see if your hardware works.

If you're satisfied with what you see,you can hit the install button,and install Ubuntu on your Gentoo partition.

Use the ext3 file format for your / and /home if you have this.
Swap is formatted as swap.

---

### Post by krelverehan on 2006-12-12
How do I set the bios to boot from a cd? I tried putting the CD in the drive and restarting the computer. The grub screen just displayed the OS I have currently running.

And another quick question: I choose the x86 rather than the x86-64 version. I am using and AMD Athlon XP +1800. I made the right choice, right?

---

### Post by bulldog on 2006-12-12
Yes,you don't need the 64bit version :D 

You have to go into your BIOS when you reboot [most cases the DEL key]
There you have to search for a thing like changing boot device,and change it from hd0 into cd-rom.

If you reboot,you can see,most often at the bottom of your screen,which key you have to use to get into your BIOS.

---

### Post by krelverehan on 2006-12-12
Thanks for you patience. I have to go to work now. I'll try it when I get back.

---

### Post by louieb on 2006-12-12
This may be what your lookin for. Shows how to get grub to boot a CD. This method works on 3 of my 4 PC's.   [http://gentoo-wiki.com/TIP_Chainloading_a_bootable_CD-ROM_from_GRUB](http://gentoo-wiki.com/TIP_Chainloading_a_bootable_CD-ROM_from_GRUB)

---

### Post by krelverehan on 2006-12-12
Interesting... So many options...

Now, I have a new question. Perhaps much easier than the last.

It turns out the boot disks that buddy gave me are for 5.04, and I would like, of course, the latest version (I believe it is 6.10). Is there an easy way to upgrade 5.04 to 6.10, or should I just go to the trouble and seek out 6.10, and install that instead?

Thanks.

---

### Post by jsteve54302 on 2006-12-12
> **krelverehan said:**
> Interesting... So many options...

Now, I have a new question. Perhaps much easier than the last.

It turns out the boot disks that buddy gave me are for 5.04, and I would like, of course, the latest version (I believe it is 6.10). Is there an easy way to upgrade 5.04 to 6.10, or should I just go to the trouble and seek out 6.10, and install that instead?

Thanks.

Try to get the 6.10 / Edgy CD...  I've seen no end of posts about things breaking after using the automatic upgrade or following the upgrade howtos.  Not a pretty situation, from what I've gathered...  I could be wrong, tho, as I quit using 5.04 when it couldn't find my kb, mouse, video card, sound card **and** several key mobo components, and only recently did a fresh Edgy install :), so I've never actually experienced the upgrade "issues"...
  BTW, I believe the beta of Feisty Fawn is available (I see many posts by users running it), but I strongly advise against using beta **anything** unless you're an experienced user willing to break (and fix) your system :)

---

### Post by krelverehan on 2006-12-13
Thanks for all the help guys.

I now have ubuntu up and running.

It is everything I dreamed of and more!

-Kiel

:KS

---


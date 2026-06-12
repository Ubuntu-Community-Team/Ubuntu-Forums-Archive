---
title: "cannot install 10.04 to dual boot with Win7"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by Favilla on 2010-08-10
Hi everyone!
I'm new to Linux and Ubuntu.;)
So I was trying to install Ubuntu on my VAIO VPCEA28EC. Since Win7 Ultimate is all ready installed, I decided to try dual booting form live CD coz someone told me that Wubi is a headache.
It all went fine until I got the Language option set, and chose "Install Ubuntu"...
Then it stayed forever with the progress bar on screen. 
At first I waited, but after about half an hour it's still there, and I don't think the CD driver was really working judging from the faint noise.:(
Then I rebooted and chose "Try Ubuntu without installing", but the same thing happened...
 
What can I do now?
 
BTW I tried Installing it within Windows, but got a "permission denied" warning when the progress bar went about half the way. Already tried "Run As Administrator"

---

### Post by mörgæs on 2010-08-10
If 'Try Ubuntu without installing' does not give a good result, I would not bother installing. You could try 9.10 or another Ubuntu:

[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by Favilla on 2010-08-10
Thanx for your advice! I will try that. I was suspcting a compatibility problem with my display card, which is an ATi RADEON 5650

---

### Post by Shahram A on 2010-08-10
I am new to Linux and Ubuntu as well. I have installed it with win 7 and am testing it out.
Just an advice, you need to first make enough space on your hard disk available to install Ubuntu.
1- free some space by moving your files
2- back up your files in case you make a mistake to able to bring them back
3- Go to disk management in win7 and either delete a partition at the end of your disk or make space by shrinking an already existing partition.
4- after this try installing Ubuntu by optical drive, installing by USB drives don't work well in my experience.
5- when installing you have to choose the empty space (first read the installation guides if this is your first attempt).

Ubuntu will install with EXT.. file system, from Ubuntu you'll be able to see and access your win7 partitions but from win7 you would not be able to access your ubuntu partition, unless you want to uninstall it and reformat the ubuntu partition in win 7 disk management.
However the two file systems don't match perfectly and you'll experience slow down of win 7, although every time you make a check disk maintenance in win 7 it will fix the problem...

Good luck

---

### Post by Favilla on 2010-08-10
I've already made a 100G empty space ready before I tried to install. And I did install it from LiveCD because the LiveUSB I made would warn me that it cannot find disk for many times before I could do anything.
Well, the problem now is that I just never reach the option part when trying to install it. It stays in the progress bar before that.

---

### Post by Favilla on 2010-08-11
I downloaded the ISO again and burnt it on a new disk. Then the installation completed!Maybe some files went wrong last time I downloaded it.Anyway it's working perfectly now.Thanks for your help! You guys are great!

---

### Post by mörgæs on 2010-08-11
You are welcome. Now you have a solution until april 2011, where support for 9.10 runs out.

---


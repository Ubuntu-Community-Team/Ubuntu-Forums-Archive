---
title: "Ubuntu on mac"
date: 2012-01-12
forum: Installation &amp; Upgrades
---

### Post by thewickedfreak on 2012-01-12
Helloes,

I'm trying to get ubuntu on my mac machine. 

Sinca OSX Lion changed bootcamp to only support windows, i tried using rEFIt as a bootloader and a GParted live cd to create an ext3 partition for ubuntu.

The only problem now is that when i try to boot the live cd, after some 5 minutes of progress I get prompted with the message "(initramfs) Unable to find a medium containing a live file system".

Any ideas ?

---

### Post by Lars Noodén on 2012-01-12
You can make an install DVD for Lion and use that to re-partition the hard drive to leave space for your Ubuntu installation.  How that is done can be found on the net and depends on whether you've already downloaded Lion or not.  Once you have space to install in, it's just a matter of booting the install disc.  Given a choice, I recommend the alternate install or the mac install.

One last things is that it is possible to use HFS for your /home partition but you can't do that until after you've finished the installation.  So to do that, make a partition for home but don't actually use it until you've booted the first time.  Then you can format it as HFS+.

---

### Post by thewickedfreak on 2012-01-12
Okai, so if I understand right, are you implying that the method I used to create the ext3 partition is wrong and is causing this initramfs error message ?

---

### Post by Lars Noodén on 2012-01-12
I'm not sure it's wrong but it's very different from the method I use when I create dual boot machines.  Things were much easier for some reason in earlier versions of OS X.  I had quite a bit of difficulty getting things running with Lion however.  But I did not keep many notes.  I was a bit miffed about not being able to get a Lion DVD and having to hop through some hoops to make one myself.  

If you have the materials available try the method I described and see if that gives better results.  If not we can figure out a third way to try.

---

### Post by thewickedfreak on 2012-01-12
Well, the method I am currently using seems to go to a dead end so the least I could do is try yours.

About the CD... my mac came with Lion already installed. So i'm probably going to have a hard time getting one but i'll try nevertheless.

Thanks for the hints!

---


---
title: "Create install disk from an existing system"
date: 2007-07-31
forum: Installation &amp; Upgrades
---

### Post by bdk6m2007 on 2007-07-31
I have a system setup (with Fiesty) that I want to create an install CD based on all of the packages I have installed on it.  Is there an easy way to do this?

I've found instructions on how to create install CDs assuming you have downloaded a standard install .iso and only want to make a few changes ([https://help.ubuntu.com/community/InstallCDCustomization)]("https://help.ubuntu.com/community/InstallCDCustomization%29......I%27ve") I've made many package changes using apt / dselect and just want to essentially copy the packages installed.  I suppose the instructions are the same but I was hoping for something easier given the amount of change.

---

### Post by jnorthr on 2007-07-31
So it sounds like you have a working ubuntu that you are happy with and want to ghost it to dvd just in case. You may be a pioneer here, so keep us advised. Thx,

---

### Post by bdk6m2007 on 2007-07-31
Not really.....I actually want to create an install disk based on the packages because it will be installed to different hardware.

---

### Post by az on 2007-07-31
You have several options:

1.  Use dpkg-repack and just spit all your installed debs into a directory, and them make a cd ([https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)).  You should remove all the ubuntu-base and Ubuntu-minmal dependencies first.  If you really want to get funky, you can put the actual installer on the disk, and make the disk bootable by installing isolinux, too.  

If you don't mind having an install cd, and then using your extra cd, this may work for you.

2.  run
sudo dpkg --get-selections > file

and then install the base system on the target machine, transfer the file over and run

sudo sudo dpkg --set-selections < file

and then

sudo apt-get dselect-upgrade

That will install all your extra packages from the repos.

3.  You can make a live cd out of your running system.  Use make-live or bootcd.  I am actually trying to work out how to make a custom derivative from scratch (not remastering an existing live cd).  Playing around with make-live is on my list of things to do.  Anyway, if you include Castper and Ubiquity on your live disk, you will include the live cd installer.  Now whether it will work on a custom disk is a good question.

The actual alternate install cd is built using package seeds (lists of packages that have dependencies.)  The autobuilders germinate these seeds (work out the list of dependencies and make a cd out of it) and tack on the ancillary stuff (memtest, installer scripts, manifest, md5sums...)  I don't know where you can get the autobuilder scripts.  Anyway, it would be hard to make use of unless you are running an official Ubuntu repository...

---

### Post by balleyne on 2007-07-31
Have you checked out partimage? I've got it on my "To Check Out" list, lol, so I'm not familiar with it yet, but I believe it's a program that will create an image of an entire partition.

In which case, you would make an image of your filesystem, and to restore you'd do a clean install, and then copy that image over the filesystem. If that makes sense.

Not sure if that's exactly what you're looking for, but it may be useful *shrugs*.

---

### Post by bdk6m2007 on 2007-07-31
> **az said:**
> 3.  You can make a live cd out of your running system.  Use make-live or bootcd.  I am actually trying to work out how to make a custom derivative from scratch (not remastering an existing live cd).  Playing around with make-live is on my list of things to do.  Anyway, if you include Castper and Ubiquity on your live disk, you will include the live cd installer.  Now whether it will work on a custom disk is a good question.


Thanks for the suggestion, sounds like this is exactly what I'm looking for.  I'll give it a shot and see if I can get one of these to work.

Either of the other two options sound like they would work as well, but I'm really trying to get to a single install CD solution.  Of course I could always fall back to starting with one of the standard install CDs and modify from there but it would be really nice not to have to do that.

Thanks!

---

### Post by JermaineG on 2007-08-08
i know that pclinuxos  uses mklivecd.deb to make an iso of your current install, and since it was made for debian, i don't know why it would not work for ubuntu? or maybe someone could make it work? I've looked into reconstructor and customize livecd, but the process is very involved, and reconstructor uses its own bootsplashes and desktop and other things i didn't like. but when i was playing around with pclos, i was able to install from the livecd, add and remove apps, update and upgrade everything, change theme, bootspash etc, then use mklivecd to make an iso of everything into my own remastered livecd. would it be possible to make it work for ubuntu also??

---


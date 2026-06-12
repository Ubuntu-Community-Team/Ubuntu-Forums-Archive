---
title: "Creating a OEM Installer?"
date: 2006-12-02
forum: Installation &amp; Upgrades
---

### Post by Coldbird on 2006-12-02
Hi - Coldbird here!
Well... after some work I set Ubuntu up to a Point that I dont wanna give away anymore... but like every Computer User... sometimes you get to the Point of formating and setting all stuff up from the beginning...

Well... Due to me only using Ubuntu on my very beloved Notebook... I thought a OEM Disc would be a good Idea... I mean... all HW is setup... All Stuff I need is properly installed aswell... GREAT!

But... how would I go about creating a OEM Disc for Ubuntu?

---

### Post by bapoumba on 2006-12-02
> **Coldbird said:**
> 
But... how would I go about creating a OEM Disc for Ubuntu?
Well, I am not sure that I really understand your question ... Please check out edgy [alternate install CDs]("http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download"). You can choose an OEM install.

---

### Post by Coldbird on 2006-12-02
I used the Alternate Disc to install Ubuntu, but how would I do a OEM Disc with everything the way it is right now... so... when I install again - ePSXe is properly setup... A 32bit Library Setup is installed... my Development Environment is setup, my Inet Connection aswell... and so on...

I wanna do a Disc especially for this Notebook... (Sort of...) That fits the Hardware perfectly...

---

### Post by BlaineM on 2007-05-02
is there an answer to your question?  I hope that there is.. because it takes me a long while to set up my machine the way that I want it to function as well, and my own installer would be nice...

anyone?

---

### Post by BlaineM on 2007-06-17
I guess there is nothing... pitty.

I guess you could ghost a spare hard drive with your install, and then just have it around.  then whenever you needed to put it back to that state.  then just re ghost over your usable drive.

maybe.

---

### Post by TheForkOfJustice on 2007-06-17
I know there are remastering tools out there but I don't know if it can examine all of the packages you have installed and create a new iso.  The iso would probably be too large for a CD anyway so it would have to be a DVD.

The first thing I would suggest is making a archive of all of the files in your /home folder and sending a copy to your gmail (or similar web email service) account.  In the case of a reinstall you can download the backed up config files and just overwrite everything in your new /home folder.

That's the best quick-and-dirty solution I can offer.

---

### Post by LMelior on 2007-06-20
I know this is just a revived old thread, but...

There was a relatively simple but somewhat lengthy (and poorly spelled) article on [www.cyberpunkcafe.com](www.cyberpunkcafe.com) on how to remaster (I believe) Ubuntu 6.06.  I found it again on Google but it's not loading at the moment.  It took me a few hours to go through and do it myself several months ago, but I never got it running because the article puts IceWM in place of GNOME and I didn't know what packages to keep when I was deleting some of them to keep the iso CD-sized.  If you really know what packages you want to keep and remove though, it shouldn't be too bad.  You can free up a pretty good-sized chunk taking out openoffice and a few others.

Basically it involves (roughly):
1. mounting the install cd 
2. saving all the contents (I want to say that the folders I created were isolinux, syslinux, filesystem) separately
3. uncompressing the squashfs filesystem
4. chrooting into your new system
5. using dpkg to remove and install stuff from packages that you've downloaded separately (i.e. you can't use apt-get to do it)
6. using squashfstools to recreate the compressed filesystem that the installer uses
7. building the iso

That's completely from memory, so I very likely missed and/or poorly explained some important steps.  There are other things you can do, like replacing the artwork and boot message, that the article talked about as well.  I can't even get Google's cache to bring it up, but maybe it'll come back at some point.


EDIT:  Oh yeah, it makes it MUCH easier to work from a fresh install, because you can just apt-get -d install all the packages you want and install the entire cache of .deb files from that one folder.  I didn't start from a fresh install, and it was not fun.

---

### Post by WiFi Ed on 2007-06-20
> **BlaineM said:**
> I guess there is nothing... pitty.

I guess you could ghost a spare hard drive with your install, and then just have it around.  then whenever you needed to put it back to that state.  then just re ghost over your usable drive.

maybe.

That's kinda sorta what I do. Since I still have a bootable Vista partition I use Acronis True Image to do this. After getting Ubuntu "just right" (definition of "just right" varies with time!) I booted Vista and created a complete backup of my Ubuntu install (backup copied to external USB hard drive).

Now, if needed, I can either boot to the Acronis bootable CD or Vista and restore Ubuntu. It works great.

I do the same with Vista too, having created a backup image of a fresh Vista install (already activated).

---


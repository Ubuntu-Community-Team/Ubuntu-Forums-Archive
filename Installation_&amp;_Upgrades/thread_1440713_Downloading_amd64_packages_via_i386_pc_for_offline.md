---
title: "Downloading amd64 packages via i386 pc for offline install"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by cameronem on 2010-03-27
Hi All,
 
I have a setup where I only have one machine that is able to access internet which is running ubuntu 9.10 i386.
 
However I need to update and install packages onto machines running the same version but on amd64.
 
Essentially below is what I "want" to do but not sure exactly how to go about it to get the amd64 packages etc.
 
1) Download the entire packages list
2) Copy this to the amd64 machine
3) Select what I need and only download what dependencies are missing
4) Copy some file back to the machine running i386
5) Download those packages
6) Copy packages across to amd64
7) Install them :)
 
I had a look at Keryx but can't see any option to force the architecture.
 
Does anybody have any ideas on the best (and preferably easy :P ) way of going about this?
 
Cheers

---

### Post by 2hot6ft2 on 2010-03-27
> **cameronem said:**
> 
I had a look at Keryx but can't see any option to force the architecture.
 
Does anybody have any ideas on the best (and preferably easy :P ) way of going about this?
 
Cheers
Well you would be creating the download script on the AMD64 and just using the 386 for downloading them, so it wouldn't matter what architecture the one downloading them is.

Like going to Synaptic on the one needing the packages and marking all the packages you want to install then clicking on File > Generate package download script
Then moving or saving the script to a usb flash drive which you can take to any linux box that is online and double clicking on it and selecting "Run" or "Run in Terminal if you want to be able to see when it finishes" it will download the packages to the same location as where the script is.

Then you take the usb to the machine that created the script and open Synaptic and click on File > Add downloaded packages
to install them.

The machine that creates the script is the architecture it will download them for. Not for the one you run the script on to download them.

I think keryz works the same way and updates your sources as well.

---

### Post by cameronem on 2010-03-27
Cool thanks.
 
However how will the offline one know what updates there are to generate the download script?
 
I gather I need to download some package repositories but not sure exactly what and where to place them?

---

### Post by mac9416 on 2010-03-28
> However how will the offline one know what updates there are to generate the download script?

It will not know what updates there are unless you use a tool like [Ubuntu Offline Updater]("http://code.google.com/p/ubuntu-offline-update-package-lists/downloads/list") to download and install the package lists.

But I think you'll find that to be more trouble than it's worth. I suggest using [Keryx]("http://keryxproject.org") instead. It acts much like Synaptic, except you can carry a snapshot ("project") of your offline computer to an online computer to get updates.

---


---
title: "Automating a custom Ubuntu install"
date: 2013-06-09
forum: Installation &amp; Upgrades
---

### Post by MartinMorrison on 2013-06-09
Hi,

I work in an organisation that installs donated computers in rural African schools. We decided to standardize software by using XUbuntu as the OS for computers, with a bunch of programs from the Edubuntu package. We then also add an offline Wikipedia (using Kiwix) and offline Khan academy videos on some subjects.

At the moment each computer is installed manually -> first the OS from a CD, then sync with Dropbox, copy an installation folder, run an install script, copy Kiwix/index etc.

Is there a way to set up a PC once, save its entire state to an iso, and clone it to new PCs? Please point me in the right direction. We don't want to use virtual machines or anything, the OS install should be made as easy as possible for the installers as they are not all technical people. 

Cheers

---

### Post by 2F4U on 2013-06-09
You might want to think about creating customized install media:

[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

---

### Post by Cheesehead on 2013-06-09
That's a complex setup.
You cannot get rid of the complexity...but you can move the complexity around.

For example, you currently have all the complexity handled by the human installers, and you don't like that.

You can improve your custom install script to add (and remove) dropbox and do all the sync work...but the the complexity is dependent upon who knows how to maintain the script. How many are they, and what happens when they leave?



Here is how I would structure it: I would reduce the number of install steps, and move the complexity into a preseed file.

1) Use a caching proxy to minimize your upstream network usage, and to replace the CD-based packages. Retain one old computer (or even just a VM) as a [caching proxy]("https://help.ubuntu.com/community/AptProxy"). It keeps a local copy of all the files, all the media, etc, and updates them as needed.

2) Use the package manager (instead of a custom script) to install/update/remove your custom content. Bundle all of your customizations, all of your custom content, all of your media into a set of .deb files. Create a new repository on the caching proxy machine for the custom-content .deb files.

3) Use a [preseed file]("https://help.ubuntu.com/12.04/installation-guide/i386/appendix-preseed.html") to specify the cache proxy, the local content .deb repository, the custom list of packages, and the other custom settings to the Ubuntu installer.

4) Create a new install CD/USB using the [mini-iso]("https://help.ubuntu.com/community/Installation/MinimalCD") and the preseed file. Put it in, turn it on, and it just installs everything the first time. No dropbox, no sync, no scripts.

---

### Post by gordintoronto on 2013-06-09
Cheesemill posted this solution: When you boot the installation media, hit SHIFT to get to the installation menu, then hit F4 and select 'OEM Install'. When Ubuntu has finished booting, install the system as usual, you will be prompted for a temporary username and password.

When installation has finished, boot the system and log on with the temporary username and password you created earlier, you can now make any other alterations to the system that you want, for example getting updates and installing extra software. (Corporate wallpaper!) When you're all done, just double-click on the 'Prepare for shipping to end user' icon on the desktop and then shut down the machine. You can take an image of the drive, and install that on as many computers as you want.

---

### Post by C.S.Cameron on 2013-06-09
There are several ways to do this.
Install and set up Ubuntu how you want it then use Remastersys to make an iso of the results, then use UNetbootin to install it to the computers.

[http://www.remastersys.com/](http://www.remastersys.com/)  The downloads are still working.

Or you can set things up how you want then make an image file, you can write the image to the computers using dd or an imagewriter gui,

Sudodus' instructions are worth looking at:

[http://ubuntuforums.org/showthread.php?t=1958073&highlight=sudodus](http://ubuntuforums.org/showthread.php?t=1958073&highlight=sudodus)

---


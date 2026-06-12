---
title: "Switching motherboard and processor"
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by worx101 on 2008-09-25
Will I need to reinstall ubuntu, or will it work fine?

And is their an option to reconfigure the hardware settings in the OS?

---

### Post by lisati on 2008-09-25
My guess is that it would depend on how similar the underlying hardware is: there is a good chance that you *might* have to reinstall, perhaps someone who has more experience than myself with this kind of thing might be able to offer more practical thoughts.

---

### Post by worx101 on 2008-09-26
bump

---

### Post by robert shearer on 2008-09-26
Well....backup,backup,backup.
So,you should backup all your personal data/home folder to some external media. 

Then you might want to make a reinstall live cd with your configured Hardy system and installed apps.

This can be done with Remastersys. see these links.

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

and read this from the Remastersys forum....

> You can use Remastersys to backup a fully updated system.

  The key is to make sure your /home/(your_username) does not contain a lot of large files, such as MP-3s, videos, pictures, etc.
  Move all such files to a separate data partition, and you will find that your system easily compresses to a file size of less than 4 gigabytes.  Mine generally is just a bit over 1 gig. 
  Before Remastering your system, be sure to unmount any other partitions, except for your / and /home, unmount any mounted network drives, and unplug any USB thumb-drives or hard drives, otherwise, Remastersys will include those in the backup, making the ISO file too large.  

Also look for the following folder:  /var/cache/apt/archives.  That folder is where Klikit, (and presumably Ubuntu and other Ubuntu-based distros}, store the DEB files for all the programs installed on your system.  The DEB files are binary installers, and once the program is installed, they are no longer needed, unless you need to reinstall the program for some reason.  You can copy the entire folder to your storage partition, or use AptonCD to make a backup disk, then you can safely delete the contents of the original folder ( do a "sudo apt-get clean") , which can free up a half a Gigabyte or more. 


You will then have a reinstall disc of your current system that can be used just like a standard Hardy install disc would , but having all your apps and setup configurations.( but not video card settings so do backup your xorg configuration. open with...

```
gksudo gedit /etc/X11/xorg.conf
```

and save this file(to external media))

 and copy across your home folder  if all turns to custard.

Having said that it is quite possibly that when you move the old hard drive into the new hardware it might just boot up ok.
If it doesn't then reinstall from the backup you will have created.


See also this thread...
[http://ubuntuforums.org/showthread.php?t=929914](http://ubuntuforums.org/showthread.php?t=929914)

---


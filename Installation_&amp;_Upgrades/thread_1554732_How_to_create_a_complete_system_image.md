---
title: "How to create a complete system image?"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by Muiske on 2010-08-17
Hello fellow Ubuntu users,


Please assist me with the following. I have two identical PC's - they are *exactly* the same, same MB, same processor, same RAM, same HD etc. etc. Not a single bit of difference. Now, on one of them which I shall henceforth name the 'work-PC' I have installed Ubuntu 10.04 which is working great. The other one, baptized 'media-PC' does not have any operating system whatsoever installed. To save me the hassle of going through the installation process again, I wish to create some sort of image from the work-PC which I then directly install on the media-PC. So, complete with all partitions (if that's possible), files, installed packages etc. A direct copy, if you will. 

The question is: how do I do this? I'd rather not be dependent on 3rd party software. I have a 1 TB external (USB) disk which I would like to use so I can spare writable CD's and DVD's. 

Any suggestions? Thanks.

- Muiske

---

### Post by lechien73 on 2010-08-17
You could try using Clonezilla ([http://www.clonezilla.org](http://www.clonezilla.org)), although you would probably have to re-install Grub on the new machine afterwards, since the UUIDs would be messed up.

If you wanted a cleaner install, then do a fresh installation of Ubuntu on the new machine, and clone the installed packages from work-PC to media-PC.

On work-PC:

```
sudo apt-get install dselect
sudo dpkg --get-selections > installed-packages

```
Copy the installed-packages file to media-PC, and type:

```
sudo apt-get install dselect
sudo dpkg --set-selections < installed-packages
sudo dselect
```

You could also copy your /home folder from work-PC to media-PC to retain any application settings.

---

### Post by Muiske on 2010-08-17
Thanks, lechien73. Your procedure is clear and to the point. I guess I can't get the whole thing done with 2 mouseclicks, but your option will still save me some work! :)

---

### Post by Irony on 2010-08-17
You can get it done with 2 or 3 mouse clicks using;

```
sudo cp -ax /. /newfolder/.
```

Basically boot up to your current installation and copy your installation to an external drive then boot up your new computer (with a live cd) then use the command to copy to your new computer drive from the external drive;

```
sudo cp -ax /. /newdrive/.
```

Then chroot to the new copied install and update grub.

---

### Post by Muiske on 2010-08-18
> **Irony said:**
> You can get it done with 2 or 3 mouse clicks using;

```
sudo cp -ax /. /newfolder/.
```

Basically boot up to your current installation and copy your installation to an external drive then boot up your new computer (with a live cd) then use the command to copy to your new computer drive from the external drive;

```
sudo cp -ax /. /newdrive/.
```

Then chroot to the new copied install and update grub.

Thank you, Irony. This indeed is a simple method, but does it require me creating new partitions on the media-PC or are they 'copied' with the files?

And what exactly does chroot do? I'm still learning basic commands and I'm only about a fourth into the book. :)

---


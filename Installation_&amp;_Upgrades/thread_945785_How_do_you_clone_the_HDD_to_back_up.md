---
title: "How do you clone the HDD to back up?"
date: 2008-10-12
forum: Installation &amp; Upgrades
---

### Post by quinnteq on 2008-10-12
How do you clone your HDD to back up your installation?

I am using a 4gb flash card in an IDE adaper, so space is very limited.  I want to clone my machine in case something terrible happens later.  I want to put the clone onto another hard drive via usb. 

Is there some way that i could possibly make this into an iso and burn it to cd to install later in case?  I would have to burn the cd on another computer (most likely one running windows) because the laptop i have linux installed on was made before cd burners were rarely heard of.

Thanks in advance!

---

### Post by gjoellee on 2008-10-12
read more about taking a backup of Ubuntu here: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

but  4g of space may be an issue, it may be enough if you have not installed any extra software since the new Ubuntu installation...

---

### Post by durand on 2008-10-12
I use sbackup for backups. It's in the repos.
```
sudo aptitude install sbackup
```
Then you need to configure it at System > Administration > Simple Backup Config.

There is a more crude way to clone your system using dd.

[http://docs.sun.com/app/docs/doc/805-7228/6j6q7uf21?a=view](http://docs.sun.com/app/docs/doc/805-7228/6j6q7uf21?a=view)

I don't know much about it but it will just copy each and every bit to a single file which you can move to your hard drive.

EDIT: gjoelle pointed out a really good method but sbackup does the exact same thing in a more user friendly manner.

---

### Post by uclalinux on 2008-10-12
If you want to clone a HDD. This means you want every bit copy the same. 
including the header files, tree files, everything. Then you should use the DD command, it is one of the original commands in bash. It will copy whatever you want. 

Some recommendations, make sure your backup hard drive is the same size as the original. If you dd your old hd to a back up hd the backup hd will think it is the same size as the old, because it copy all the formatting information. 

DD is also great an making CD isos' DVD isos'  or thumb drive iso's.

In your case i think it would be best to make an iso of your flash Card, If you just tell it a file location it will make a iso image of the device it was meant to copy. 

It would be something like this, just google to see how to use DD command, its one of the most powerful out there. 

DD if=/dev/sdXXX(device name) of=/home/user/where_ever_u_want.iso

---


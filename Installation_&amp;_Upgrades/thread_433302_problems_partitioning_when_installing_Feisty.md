---
title: "problems partitioning when installing Feisty"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by chris.olsen on 2007-05-04
My dell 6400 laptop currently has windows XP and Edgy Eft installed.  When installing with the alternate cd I am having problems setting the partition that I want to install to.

I select the Manual option, since I have to hold onto windows, from there I see something like the following

[FONT="Courier New"]
sda1  fat16    8MB        <-- some dell utilities
sda2  ntfs     40GB  B   <-- current location of the grub...or at least it is currently showing it to be the boot disk
sda5  ext3    40GB       <--where ubuntu is currently installed
sda6  swap   3GB
sda7  ext3    20GB       <-- seperate partition for various files
[/FONT]

This is the way that I would like to keep it, and re-install over sda5, but when I press "continue" it tells me that the boot disk is not set up.  When I change it to sda5 it then, of course, removes it from sda2 which is something that I don't want to do.

Does anyone know the steps that I should be taking for this?

Thanks

---

### Post by undecidable on 2007-05-04
It is hard to be sure I am getting the explanation right without having the install screen in front of me, but let me try.   Also I used the alternate install for Dapper and I assume it is similar for Feisty.  
The key is setting the mount points.  

What I think you want to do is:
.  set the mount point for sda5 to "/"
   This will also put /boot, which includes grub, on sda5.
.  set the mount point for sda7 to "/home"
   unless your documents are not in your /home dir,
   in which case I assume you know what you are doing.

If you wanted grub on sda2 you would set the mount point for sda2 to "/boot"
but I don't think this is what you want to do as:
a.  it is an ntfs partition, so I don't think it really has grub on it now.
     In fact sda2 looks like where you have W. installed. 
b.  you do not need a 40gb partition for /boot, just I think a few mb.  

Hope this is useful.

---

### Post by chris.olsen on 2007-05-04
thank for the help.

After fooling around with things for a while I had entered pretty much the same as you mentioned, so it is nice to see I am on the right track.

The issue now is that after setting up the partitions, like you mentioned, I get the following message as warning when trying to commit the changes:

"file system doesn t have expected sizes for windows to like it...."

I am allowed to ignore it, or correct it, but I haven't been able to figure out how to correct it, since everything I do results in the message.  Even after only changing sda5 to the boot "\" I get the message.

Is is safe to ignore this?

:( turns out whatever I have done up until now prevents ubuntu edgy from booting up, it just locks at the mid of the progress bar.

---

### Post by undecidable on 2007-05-04
I have received this msg as have others.   I have ignored it without impacting my installations, my partition integrity or my karma.  Safe to ignore it.  

I have never seen a post where anybody explains what causes it other than the usual 'Klingons messing with your head'.

---


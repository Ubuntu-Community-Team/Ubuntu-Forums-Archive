---
title: "Problem Adding Users"
date: 2005-02-22
forum: Installation &amp; Upgrades
---

### Post by wheatpuppet on 2005-02-22
I'm having this wierd problem with the installer:
When I add a new user, it brings me back to the dialog asking if I want to add a user. No matter how many times I add a user, it doesn't stick. When I bust out a console later on and add them manually by adduser, it gives me the following output:

root@gabrielite:/etc # adduser nhusher
Adding user nhusher...
Adding new group nhusher (1000).
Adding new user nhusher (1000) with group nhusher.
Creating home directory /home/nhusher.
chown 1000:1000 /home/nhusher: Operation not permitted
Cleaning up.
Removing directory '/home/nhusher'
Removing user 'nhusher'.
Removing group 'nhusher'.
groupdel: group nhusher does not exist

What the hell? I'm ***ROOT*** I should be able to do anything I want, and that's not even a particularly crazy thing to do.  ](*,)

---

### Post by bored2k on 2005-02-22
Did you try 
$sudo adduser nhusher ?

or launching 
#gksudo users-admin


?

---

### Post by wheatpuppet on 2005-02-22
[QUOTE=bored2k]Did you try 
$sudo adduser nhusher ?

or launching 
#gksudo users-admin


?[/QUOTE]
 I find it troubling that the installer itself breaks down. Shouldn't the installer be designed such that it will *always* be able to set up user accounts, and be very clear in confirming that defined user accounts are actually in place? A Linux machine with no accounts (and a disabled root) is no linux machine at all.

EDIT: Why would using SUDO change the result? I was under the impression that sudo executed commands in root's name. Since, in the above transaction, I was root, I don't see how using sudo would be helpful.

gksudo didn't work because I'm not running in an X environment. I tried enabling the root account in the terminal by defining a password. The password defined okay, but for some reason it didn't recognize it in the GUI login screen.

I'm thinking that Ubuntu's installer needs to be polished a lot, since I've been working on this for the better part of a weekend.

---

### Post by wheatpuppet on 2005-02-22
Apparently it's related to the fat32 partition I set up as /home as per [this thread](http://ubuntuforums.org/showthread.php?t=1864&page=1&pp=10).

---

### Post by codemac on 2005-03-20
No solutions?

---

### Post by wheatpuppet on 2005-03-21
The solution is not to put /home on a FAT32 partition. For some reason it has problems writing to said partition in the installation step.

I ended up having a /home mount point and a /shared mount point, I then did some linking wizardry to make it feel a bit like my /home was on the FAT32 partition. It's not a perfect solution, but the older I get, the less I think perfect solutions actually exist. :P

---


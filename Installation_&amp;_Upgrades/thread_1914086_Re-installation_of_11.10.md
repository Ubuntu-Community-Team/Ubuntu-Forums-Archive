---
title: "Re-installation of 11.10"
date: 2012-01-23
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2012-01-23
I have just done a reinstallation without a reformat. I used the other options in the installation program.  Loading lubuntu afresh shows that:

mdeia/mydocs has been changed to media/mydocs_ 
Most of my individually installed programs are no longer showing in the system tool,internet programs etc.


fstab is the correct version that I had set up before the re-install.

How can I get the system back to how it was before so that I can see my preferred programs. For example firefox is no longer showing as an option and most of the panel icons are no longer pointing at the original programs. 

I could reinstall the programs via rsync but i would prefer to try to understand what has happened before I make further changes.

---

### Post by heshoots67 on 2012-01-23
[https://help.ubuntu.com/11.10/installation-guide/]("https://help.ubuntu.com/11.10/installation-guide/")

Try this if it works.

---

### Post by Robbyx on 2012-01-23
Having already done the installation I  would appreciate your referring  me to the section that you feel I should study. I am hoping that somewhere in that document is the way to adjust the system references after the re-installation.

---

### Post by oldfred on 2012-01-24
If you did a reinstall with formating, you overwrite all the system & system settings. Do you have a separate /home?

I now always install to a new partition and keep data separate. Then I have a new install without any old history, but do have to reinstall all my applications.

My backup process Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh
is to allow me to restore my system from a clean install.

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by Robbyx on 2012-01-25
What I would have preferred to do was a repair, but with more than is offered by grub. I did not do a reformat but had to reinstall most of the programs that were not standard with the installation.

What choice should I have made from the installation disk to do a repair?

---

### Post by oldfred on 2012-01-25
All your user settings were in /home. Did you have a separate /home or a backup of /home including the hidden files & folders? If you restore your /home then you should have your settings back. 

If you just want repairs and cannot boot, you can chroot into system and update it. But that will not restore settings that have been overwritten or erased.

---


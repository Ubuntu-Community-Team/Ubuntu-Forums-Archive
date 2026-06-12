---
title: "Login to local install with LiveCD"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by thatsmyboy on 2008-06-03
Hardy Heron - Dell C521

Hey guys, I am a new Ubuntu (read Linux) user and due to some problems I decided to install Win XP SP2 on an NTFS recovery partition on my box. During the install I was notified that in order to boot windows I would need to inactivate the ext3 partition. I consented and subsequently lost the ability to boot Ubuntu directly. Using the LiveCD, I have been able to inspect the drive and verify that the information in Ubuntu is available and intact. My real problem is that there are a number of picture files that I need to copy to removable storage that based on permissions I cannot access.  I've devised a number of ways to attempt to solve this problem , but the lowest risk I can see right now is to login to my hard drive Ubuntu user account with the CD (if such a thing is possible). Just for information, i'm considering - 

logging in from a livecd

reinstalling GRUB
[http://ubuntuforums.org/showthread.php?t=816458]("http://ubuntuforums.org/showthread.php?t=816458")

finding out how to use gksu / gksudo

adding a user which has group privileges to the file

anything else you could think of. 

help is much appreciated

[IMG]http://i190.photobucket.com/albums/z63/fdklesd/Screenshot-unsortedpictures-FileBro.png[/IMG]

---

### Post by dstew on 2008-06-03
Try adding a new user onto the Live CD system with the same username as on the hard drive Ubuntu system. Give the new user administrative priveleges. Logon as the new user, and hopefully you will then be able to access your files.

---

### Post by thatsmyboy on 2008-06-09
Thanks dstew for your quick reply. Your suggestion worked ! for my limited aims, that was sufficient to solve my problem. I didn't try creating another user name with administrative privileges but i suppose that would work too. if anyone cares to take another stab at my original question, that would be welcome as it really seems like you should be able to log in to a user's account if you have the correct password. thanks again!

---

### Post by thatsmyboy on 2009-05-06
Looking back that this item I notice that the ```
su
``` command was really what I was looking for.
something like this : login unsing livecd
Open terminal.
su myboy
where myboy is the username of choice
type password for myboy
run nautilus (file manager) or chown to change permissions

also a little off topic, but i could have skipped the livecd altogether if I had downloaded, burned, and run [SuperGrubDisk]("http://www.supergrubdisk.org/")

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://en.wikipedia.org/wiki/Su_(Unix](http://en.wikipedia.org/wiki/Su_(Unix))

> su (short for substitute user or switch user) is a Unix command used to run the shell of another user without logging out. It is commonly used to change to root user permissions for administrative work without logging off and back on; it is also used to switch to other users in the same way. Desktop environments such as KDE and GNOME have programs that pop up a password query box before allowing a user to run commands that would typically require such access.

When invoked without a target user, the root user is assumed (identical to su root).

Usage

When run from a command line, as is typical, su asks for the target user's password, and, if accepted, grants the user access to that account and all of the files associated with it.

john@localhost:~$ su
Password: 
root@localhost:/home/john# exit
logout
john@localhost:~$

Additionally, one can switch to another user who is not the superuser; e.g. su jane.

john@localhost:~$ su jane
Password:
jane@localhost:/home/john$ exit
logout
john@localhost:~$

It should generally be used with a hyphen by administrators (su -, which is identical to sudo - root), which can be used to start a login shell. This way users can assume the user environment of the target user:

john@localhost:~$ su - jane
Password:
jane@localhost:~$


---


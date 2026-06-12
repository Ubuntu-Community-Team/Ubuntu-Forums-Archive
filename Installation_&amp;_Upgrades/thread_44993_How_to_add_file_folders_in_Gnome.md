---
title: "How to add file folders in Gnome"
date: 2005-06-28
forum: Installation &amp; Upgrades
---

### Post by SpaceWolf on 2005-06-28
I'm trying to manually mount my Zip drive since Ubuntu will not detect it and set it up for me.  I've found instructions for how to manually add the device, but I'm running into permission issues.  

The first step is to add a "zip0" dir in /media, but when I try to do that in Gnone, I get an error that I cannot create the folder.  If I pull up a terminal screen and go to /media and try sudo mkdir zip0, I get the following message "*username * is not in sudoers file".

Questions:
1.  Why would I get the "not in sudoers file" error when I've never done anything to the id's or file?

2. How do I modify or set up an ID that allows me to have admin access every time I log in?  This is a home PC and security is not really an issue.

3.  How do you get admin rights in the graphical interface so you don't have to go to a command line just to add a folder?

Note:  I'm new to Linux, but know my way around a PC.  I've worked with Novell and Windows for years and I'm just trying to figure out the Linux ID/security structure.  

Thanks for your help!

---

### Post by mingus on 2005-06-28
Linux security is very robust, but it can get complex.  Mostly it's just a matter of getting used to it.  

Ubuntu uses the "sudo" implementation to make it easier for the end-user, and to avoid any use of true root.  Likely I'll get dumped on for this, but . . . while I understand the rationale, personally I find it a bit of a pain.  None of my other distros (SuSE, Yoper, Gentoo, Xandros, Vector) do this.  And KDE makes this somewhat easier than Gnome, too.

This is how my sudoers file is set up (where the X's are my user name).  This gives me permission to do most anything except where I am modifying the OS itself, and that requires root:
XXXXXX  ALL=(ALL) ALL
With this your $sudo mkdir command should work.

Some procedures can be defined to not require root (like mounting & unmounting, or modifying shared files, done in the /etc/fstab setup), but others cannot (if a file  is owned by root, it cannot be modified by a user - this is the equiv of how Windows protects /system32 files - a good thing).

As far as adding that folder, depends on where.  If under a user owned directory, just go to Places/Home Folder.  If a system directory (think of /home as \MyDocuments and everything else as \Windows\) go to /Applications/System Tools/File Browser (Root), it will ask you for your password (it wants your user passwd, not root's).  It works like Windows Explorer.  (You will probably want to go to System/Preferences/File Manager to configure its behavior, in particular, under the Behavior tab click "Always open in browser windows" unless you want spatial windowing, the Apple method.)

Hope this helps.

---


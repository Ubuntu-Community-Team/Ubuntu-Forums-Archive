---
title: "install a program for all users"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by 77bridge on 2008-08-26
Hi,

When I install programs as a normal user, it seems that many of the applications, by default, store their binaries in my home directory.  For example: /home/john/google-earth/ . Does that mean that if I create a new user that they will not be able to access this application?

How can I install a program so that it is usable by other apps?

Also, I don't really like how this puts a bunch of application specific stuff in my home directory.  I need to install Eclipse, but I don't want everything to get stuffed in /home/john/eclipse/ , for example.

You're probably laughing at how elementary this question is.  :)

please enlighten me!  thx!

---

### Post by Scunge on 2008-08-26
When you installed these programs, did you run the installer as root, i.e. typed "sudo" in front of the command, or have to type in your admin password in some GUI installer? I am guessing that will do the trick.

The reason for installing programs not available to everyone in your home directory is because you as a user running without admin privileges, should not be able to do anything to affect other users or the system as a whole. So **your** directory is the **only** place to do that. /home/you contains everything to do with you...

Unlike Windows, for example, which has "My Documents" in one place whicb you can move to another drive if you like, but the rest of "Documents and Settings/You" (like your desktop, and application data, and your start menu) stays on C: no matter what. Then you have stuff in the registry, which is in the /Windows directory. And. And. And.

Using /home/you means "everything related to you", not just "Documents belonging to you". This has the nice advantage that you can copy /home/you to another machine and all "your" applications come with you. Try doing that in Windows!
[img]http://i268.photobucket.com/albums/jj22/Rob_0edab8/Spacer.gif[/img]

---


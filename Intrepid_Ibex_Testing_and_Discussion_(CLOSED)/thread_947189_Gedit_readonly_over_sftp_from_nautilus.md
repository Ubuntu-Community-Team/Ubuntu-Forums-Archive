---
title: "Gedit readonly over sftp from nautilus"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2008-10-14
If I open a php file on my remote server using nautilus "open with text editor", Gedit opens the file as read only.

Here is the weird part.

If I do the same process with Geany I can save the file just fine. If then open that same file with Gedit then I can save the file. This is not a permissions problem on my server , though!

I have checked gconf-editor settings for gedit and sftp/ssh is added to the save list , so that is not the problem.

I can replicate this bug on both 64 and 32 bit Intrepid betas.

It works fine on Hardy.

---

### Post by sonicb00m on 2008-10-15
Ok I have narrowed down the problem a bit.

GEdit2 seems to dislike it now when the owner of the file is not the user it is expecting and then goes into read only mode. It's not reading the permissions properly, it is like it is trying to anticipate the server behaviour, which is not OK at all.

When I save in Geany the owner then changes to the logged in user and Gedit will then open that file and save changes.

I have a cron script that runs every couple of minutes to put the correct owner back (since other people open the phps).

---

### Post by sonicb00m on 2008-10-15
Can anyone tell me the package version of Hardy Gedit2? I will compile it and see if it works.

---

### Post by pizzutz on 2008-10-16
I'm having the same problem, but I know others that are not.  There must be a setting there somewhere that I am missing, or got changed when I copied some of my . files over when I installed, that my buddy didn't do.  I'm getting the same read-only issues in graphical emacs and OO, but not in shell emacs when I am sshd into the server, so I assume it's something in Nautilus.  If I find it, I'll post it here.

---

### Post by sonicb00m on 2008-10-16
Please try adding your SSH user to a group and changing the ownership of the file you want to edit to the group.

I believe it is a problem with GEdit and the fact it expects the logged in user to be the owner of the remote file. As I said, Geany is not causing me a problem working in the same way.

---

### Post by MALEADt on 2008-10-16
I have the same problem. Gedit does not want to write a file if it's not the direct owner. Group permissions are ignored, and even logging in as root doesn't allow me to edit casual files owned  by another user.

[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/284540](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/284540)

---

### Post by sonicb00m on 2008-10-16
Yes that's exactly the problem, not even root will change it!

Thanks for making the bug report. I added mine to an existing one but I think it's been overlooked. Let's hope they can fix this asap. I have using geany over sftp, it's not very good at all. Very slow.

---

### Post by sonicb00m on 2008-10-17
I've install compiled and installed Gedit 2.22 for now and everything is working like normal.

[ftp://ftp.gnome.org/mirror/gnome.org/sources/gedit/2.22/](ftp://ftp.gnome.org/mirror/gnome.org/sources/gedit/2.22/)

---

### Post by sonicb00m on 2008-10-21
.

---


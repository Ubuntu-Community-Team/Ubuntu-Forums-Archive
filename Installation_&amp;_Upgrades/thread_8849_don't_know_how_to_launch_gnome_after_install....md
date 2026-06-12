---
title: "don't know how to launch gnome after install..."
date: 2004-12-21
forum: Installation &amp; Upgrades
---

### Post by Jason on 2004-12-21
Sorry for the newbie question.

I'm an experienced windows user and know old dos, but after ubuntu install i'm stuck in the Command Line Interface.

How do I get GNOME running?  Install seemed fine, but I can't get to the desktop.  I don't really know how the directory system for linux works and every time i type "help," half the commands listed scroll up and off the screen (don't know if there is a equivalent to the "/p" (pause) command in dos.

Can someone at least point me to a dummy-proof tutorial?

Thanks

 :confused:  <--'cause it was there

---

### Post by deshantm on 2004-12-21
A guide that I have found helpful is here: [http://www.myjavaserver.com/~mike001/ubuntu/](http://www.myjavaserver.com/~mike001/ubuntu/)

to get into gnome (assuming it is installed correctly)

login, type: sudo -s

if prompted for password type your password.

then type: /etc/init.d/gdm start

---

### Post by deshantm on 2004-12-21
more Ubuntu resources: 

FAQ: [http://www.ubuntulinux.org/support/documentation/faq/faqfolder_view](http://www.ubuntulinux.org/support/documentation/faq/faqfolder_view)
HOWTO: [http://www.ubuntulinux.org/support/documentation/howto/howtofolder_view](http://www.ubuntulinux.org/support/documentation/howto/howtofolder_view)
HOWTO: [http://wiki.ubuntulinux.org/HowTo](http://wiki.ubuntulinux.org/HowTo)
WIKI: [http://wiki.ubuntulinux.org/](http://wiki.ubuntulinux.org/)

---

### Post by Jason on 2004-12-21
Thanks for your reply!

After typing the "sudo -s" command, I was asked for my password, typed it in, and the prompt symbol changed from a "$" to a "#"

However, after typing "/etc/init.d/gdm start" it says:

bash: /etc/init.d/gdm: No such file or directory

any ideas?

(Thanks for the links, too)

---

### Post by Johan on 2004-12-21
[QUOTE=Jason]

However, after typing "/etc/init.d/gdm start" it says:

bash: /etc/init.d/gdm: No such file or directory
[/QUOTE]

Are you sure you have installed a complete Ubuntu system? There really should be a file named like that... :)
You can try to start gnome without the gdm by typing gnome-session.

---

### Post by jdong on 2004-12-21
**sudo apt-get install ubuntu-desktop**

---

### Post by Jason on 2004-12-21
I ended up reinstalling without doing the automatic updates during install and now it appears to work fine.  Thanks for the comments.

---


---
title: "Keyring to Unlock message"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by dodgingspam on 2008-02-25
Recently I reinstalled Ubuntu, installed ndiswrapper and my wireless card. I also added > ndiswrapper to /etc/modules file but now when I login I get the following prompt:
> **Enter password for default keyring to unlock**
The application 'nm-applet' (usr/bin/nm-applet) wants access to the default keyring, but it's locked.
[ Deny ] [ Accept ]


How do I get rid of this? I click Deny once and it brings a box to enter secure pass phrase for my wireless router, once I enter it it brings up this box again and I deny again and it all goes fine from that moment on.

---

### Post by dodgingspam on 2008-02-25
I looked in /usr/bin/ but can not even find nm-applet?...

---

### Post by erothoff on 2008-02-25
I am also looking for a way to disable this message, but I can tell you more about the message:

Enter password for default keyring to unlock
The application 'nm-applet' (usr/bin/nm-applet) wants access to the default keyring, but it's locked.
[ Deny ] [ Accept ]

This is asking for the password for your Keyring. The place that stores all of your passwords. 

The next message is for the password for your network. It is easy to misunderstand these messages. (I still do from time to time.)

Good luck...

---

### Post by utmark on 2008-02-26
Just delete the file default.keyring from your **~/.gnome2/keyrings/** directory

It worked like a charm for me. Keyring Manager uses a separate password for your account password. I just deleted the only .keyring file in that directory and the next time I was prompted for the password, I simply entered a new Keyring Manager Password.

Reference:
[http://ohioloco.ubuntuforums.org/showthread.php?t=130192]("http://ohioloco.ubuntuforums.org/showthread.php?t=130192")

-Mark

---

### Post by dodgingspam on 2008-02-28
I can't even locate /home/.gnome2/keyrings/ directory...

---

### Post by xaGe on 2008-06-15
Goto /home/yourusername in Nautilus... Then either press [CTRL]+[H] or look up on the Nautilus tool bar under [VIEW] and check the option to "Show hidden files" All will be revealed! :KS 

> **dodgingspam said:**
> I can't even locate /home/.gnome2/keyrings/ directory...

---


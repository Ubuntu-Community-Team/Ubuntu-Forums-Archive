---
title: "[SOLVED] Major problems with kde in Hardy"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by TrashmanL on 2008-05-31
Hello. I just recently purchased a LinuxCertified Laptop. It runs on an AMD Sempron 3200 Processor, which apparently is a 64 bit processor. It came with Ubuntu 8.04 x86_64  v1.0 "Hardy Heron" installed.

I have a desktop with 7.04 "Fiesty Fox" installed. On that desktop I succesffully have Ubuntu/Kubuntu and Xubuntu installed. I can't make up my mind, some days I feel like using Gnome, some days like KDE. (I'll probably uninstall xce, eventually)

Anyway, I wanted to do the same with this laptop, so I ran apt-get install kde-desktop. After searching the forums, I realize now this was a mistake, as I see all kinds of issues from people installing this. Oddly, it seems no one has the same issues, they're all different. That's why I created a new thread. Here's my problem:

kdm is now my login manager. kdm does not allow root login. That should be fine, just use sudo, right? WRONG. Whenever I use sudo, one of three things happen:

(1) If I am running KDE, it usually freezes up and I have to restart
(2) If it doesn't freeze up, it gives the error, "cannot authenticate"
(3) If I selected a GNOME session when I logged in, it asks me for my password, then NOTHING Happens, the program just never runs.

I get similar results if I run a su Terminal session.

Currently, the only way I can update/install anything on this computer is to restart, select recovery mode from GRUB, select a terminal session from the recovery menu, login to the terminal as root, then launch gdm from the root terminal. Here I can again login as root and update/install all I want.

I shouldn't HAVE to boot to a terminal to do this! I want gdm to be my default again, and I attempted to do so after doing the previous steps I described... but when I attempted a normal restart, kdm was still my login manager. That being said, sudo should work, too, but it doesn't. Any suggestions on how to remedy this? I may attempt to uninstall KDE, but I see from other forum posts other people were unsuccessful in uninstalling it. Should I try this, something else, or should I just wait and hope for an update that fixes issues with KDE in Hardy?

---

### Post by TrashmanL on 2008-05-31
An added note: The "cannot authenticate" error occurs not when I run sudo from the terminal, but when I access a program that requires admin rights which automatically initiates sudo. When I attempt to run the same program in Gnome, I get a more verbose error:

failed to run (program name) as user root
the underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

this one is a stab in the dark, but maybe there is some sort of sudo configuration issue I'm having? Is there a sudo.conf file somewhere? I'm not even going to attempt a solution like that without some advice, however.

---

### Post by TrashmanL on 2008-06-02
OK, well I don't know why, but KDE apparently rewrote /etc/sudoers I had to use visudo, but now everything is working.

---


---
title: "update manager can't find gutys upgrade available"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by spazsui on 2007-10-25
Help! My update manger hasn't been able to automatically find the Gutsy upgrade.  I found a thread that offered some suggestions using the terminal but none of them seem to work.  Below is the reaction for each command I typed.  Also, I do have a working internet connection otherwise I couldn't ask for help.  Take a look and tell me what you think is the trouble.

john@john-desktop:~$ sudo update-manager --dist-ugprade
Password:
john@john-desktop:~$ sudo update-manager -c 
warning: could not initiate dbus
john@john-desktop:~$ sudo update-manager --check-dist-upgrades
warning: could not initiate dbus
could not send the dbus Inhibit signal: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
john@john-desktop:~$ sudo update-manager --check-dist-upgrades


Any ideas or suggestions are greatly appreciated.  I would prefer to upgrade using update manager but if I have to do a clean install of Gutsy I am prepared to do that too.  Thanks!

---

### Post by toon on 2007-10-27
I have the exact same problem. Been searching for a while, higly annoying... :(

---

### Post by pizzy on 2007-10-27
Is the current system completley up to date?

---

### Post by toon on 2007-10-27
> **pizzy said:**
> Is the current system completley up to date?

Yes it is.

My problem was fixed by nuking sources.list and inserting 4 vanilla ubuntu lines. Since this was why on my computer, it should have been *explained* imho.

---

### Post by spazsui on 2007-10-29
How did you get your's fixed?  My system is completely up to date as well.  I have always applied the updates when they are available.

---

### Post by toon on 2007-10-29
> **spazsui said:**
> How did you get your's fixed?  My system is completely up to date as well.  I have always applied the updates when they are available.
As I said, I commented out everything in my sources.list file but the bare-minimum needed by Ubuntu. That made it recognize 7.10.

---

### Post by spazsui on 2007-10-29
I'm kind of a newb and get nervouse messing with the sourcelist.  What about using the gutsy alternate cd instead?  I've been poking the net and there appears to be alot of positive reviews using it as a option for upgrading an existing fiesty box.

---


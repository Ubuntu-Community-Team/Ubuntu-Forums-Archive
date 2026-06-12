---
title: "After upgrade to 8.04 .gvfs files are problematic"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by simonfishley on 2008-06-09
Hi all

We upgrade our server over the weekend and everything SEEMED fine until today when one user logged in and just got a blank desktop and nothing else except a mouse cursor. Rebooting did not help checked the permissions on his home dir and noticed the following:

-rwxr-x---  1 user user     89 2007-10-04 08:24 .gtkrc-1.2-gnome2
d?????????  ? ?     ?          ?                ? .gvfs
-rwxr-x---  1 user user  34145 2008-06-09 15:41 .ICEauthority

I have never come across something like this before and we cannot chmod the file at all. The terminal also spouts Nautilus errors when trying to logon and I understand the 2 are related.

I have tried deleting the user and re-adding him but that has not helped at all.

Any ideas or suggestions I may try?

Thanks in advance.
Simon

---


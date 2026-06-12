---
title: "[SOLVED] Upgrade Ubuntu and now have KDE"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by ehamman on 2008-05-21
Hi,

I have Ubuntu 7.04 installed and updated it online to 7.10.  Last night I decided to do the leap to do the online upgrade to 8.04.
I left the computer to do the auto downloads and installation of the packages in the Ubuntu update manager.
When I got back I found that a lack of electricity left it on battery power, which eventually ran out.  So I got no idea where the process may have stopped. 
So, when I boot up, I get the Grub loader that show Ubuntu 7.10 loaders and my Window XP.  I select Ubuntu, it seems to start , then shows on a black screen some processes (too fast to read) that has an error, then the loader orange screen starts.  That completes and goes black, then I get the login screen with "primary classroom graphic size", probably the standard 640x480. No problem with this as I know how to fix it. I log in, then voila I have KDE on my screen, no sign of Ubuntu.
I've tried running the Safe Mode and later reinstalling from the original disk, but this did not seem to work either, I still get Ubuntu loader, Ubuntu login page and then it goes to KDE.
I am unfamiliar with this environment, and have tried all "logical" links, but no luck.
How can I get Ubuntu desktop and confirm that the upgrade did in fact work?
Hope someone can help.

---

### Post by ehamman on 2008-05-21
:redface:
OK - I understand the Kubuntu part, but how do I get the Ubuntu?

---

### Post by damis648 on 2008-05-21
try
```
sudo aptitude update && sudo aptitude install ubuntu-desktop
```
in terminal and when it asks for login manager, choose GDM and then reboot when it is done.

---


---
title: "Can't log in, now screen unreadable"
date: 2005-07-26
forum: Installation &amp; Upgrades
---

### Post by Deicidus on 2005-07-26
During the user setup of the Ubuntu install, I had some problems entering passwords for both the root and user accounts. For the root account, no characters were visible as I typed. I thought that it was just not showing anything for security purposes, but it actually wasn't getting any characters. After backing up to the setup menu and trying again, it worked.

The user password was more of a problem. It repeatedly said that I hadn't entered a password, even though I had, so eventually I gave up, deciding to make the account later.

When the login screen came up, I found I couldn't log in to root from there, so with no user account to log in to, I looked up how to get into root. From there I attempted to create my secondary user account by typing "useradd <accountname>". It appeared to have been successful.

But *now*, when I start my computer, rather than the pretty, full-screen Ubuntu login screen, I get a little 640x480 (maybe 800x600) screen that is all garbled. I can't see anything. What happened? I can try to log in, but I see the red from the error message.

Hey wait! Just now while I was typing this, it the screen went black, going to a terminal or something, and then the pretty login screen showed up. Now, typing the username I just created won't let me log in. "Bad username or password". I tried a blank password and "passwd".

What's going on with all of this?

---

### Post by kondor on 2005-07-27
Same thing here. On first install, the default, no setup for a root password ever appeared. On second install, in expert mode, passwords were set up ok but no packages would install.

So, I installed Startcom Multimedia 4.0.4 distro - RAAM. It loaded without incident.

I checked the MD5 sums for Ubuntu and they were correct, so I don't know why the install went awry.

I may try it again later but don't have time to fiddle with it just now. :roll:

---


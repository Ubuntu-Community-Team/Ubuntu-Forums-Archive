---
title: "[SOLVED] Updating &amp;amp; Flash Player Problems"
date: 2007-04-08
forum: Installation &amp; Upgrades
---

### Post by jeremyj on 2007-04-08
I'm a new user to the Ubuntu world, & Linux world in general, so I apologize if these questions are pretty stupid.

As I was downloading updates for my Ubuntu OS 6.06 version, my laptop evidently got too hot and shut off on me twice.  Now whenever I try to finish downloading the updates I was previously working on, an error message pops up saying to "run dpkg -- configure -a" in the Terminal because I have a broken package.  I've gotten that far, and also taking advice from some other post here, I tried using the "sudo" command with dpkg -- configure -a.  I get to the "need an action option" info, and have looked at some of the commands there, but don't know what to do next.  What do I need to do to fix my Package Manager?

Also, I've downloaded the tar.gz file for Adobe Flash Player, but can't install it.  I use the Terminal to run it, go through the process of typing "y" for the installation to continue, but then it tells me it can't access /xxx/xxx/dpkg or something.  I'm the only user on my Ubuntu system, yet I'm not the root user?  How do I install Flash Player?  And how do I change my user status to the root user?  Please explain in simple terms because, after all, I'm new to this.  :)   Thanks in advance.

---

### Post by jeremyj on 2007-04-08
> **jeremyj said:**
> Also, I've downloaded the tar.gz file for Adobe Flash Player, but can't install it.  I use the Terminal to run it, go through the process of typing "y" for the installation to continue, but then it tells me it can't access /xxx/xxx/dpkg or something.  I'm the only user on my Ubuntu system, yet I'm not the root user?  How do I install Flash Player?  And how do I change my user status to the root user?  Please explain in simple terms because, after all, I'm new to this.  :)   Thanks in advance.

Sorry.  Nevermind about Flash Player.  I extracted the files onto the desktop, then ran the installer again, and it seems to have worked.  However, I still need help with my Package Manager problem.  Thanks again in advance.

---

### Post by Sef on 2007-04-08
> an error message pops up saying to "run dpkg -- configure -a" in the Terminal

Try this from the terminal:  sudo run dpkg -- configure -a

> Also, I've downloaded the tar.gz file for Adobe Flash Player, but can't install it

Read this from [Psychocat's]("http://www.psychocats.net/ubuntu/flash").  

> I'm a new user to the Ubuntu world, & Linux world in general, so I apologize if these questions are pretty stupid.


There are no stupid questions here; only ones that people are looking for answer to.

---

### Post by jeremyj on 2007-04-08
> **Sef said:**
> Try this from the terminal:  sudo run dpkg -- configure -a

Thanks, Sef!  It got me to a command line that I hadn't seen yet.  Previously, I didn't type "run" in the command line I tried.  But now it says "Password:" and when I try typing it in, the letters don't show up.  The "Enter" button works, though.  Is there a procedure for typing in my password that I'm not following?

Flash Player still seems to be working alright, too.  But how do I set my user status to the root user and keep it that way?  Is that even possible?

---

### Post by jeremyj on 2007-04-08
Nevermind.  I found the answer to my problems with my Package Manager and the updates I was trying to get in this forum article by ubuntu_demon: [http://ubuntuforums.org/showthread.php?t=186672]("http://ubuntuforums.org/showthread.php?t=186672").

To be more specific, I had to follow ubuntu_demon's instructions from Step 3 to Step 6.  As soon as I rebooted from the Terminal after following these instructions, a message by Update Manager popped up in the upper righthand corner of my desktop and told me updates were available.  Everything worked perfectly after that.

My system is up-to-date now, and I won't worry about setting my user status permanently to the root user anymore.  I get the impression that's just a security feature (like my password not showing up as I type it in the Terminal).  Thanks for the help!  And thanks for a great OS!

---


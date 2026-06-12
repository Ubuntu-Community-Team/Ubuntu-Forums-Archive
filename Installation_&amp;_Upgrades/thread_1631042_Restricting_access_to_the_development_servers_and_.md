---
title: "Restricting access to the development servers and protecting the data on them."
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by tmharish on 2010-11-26
**Problem Details:**

Every developer in our organization has access to a single development server and all development ( other than basic experimentation ) is done on this server. This is primarily because there are several interdependent systems and having copies of these systems on each developers machine slows that machine down to the extent of making it completely unusable.  All developers access this development server using ssh. Of course this implies that scp will also work as the sshd daemon is running making data vulnerable.

We are currently attempting to secure the code and data on this server from unauthorized copying and transfer. 


**Current approach to solving the problem:**

Currently I am attempting to set up virtual machines on each developer machine that can then be used to connect to the development server. I have created a shell that does nothing but allow for the typing of one command that simply transfers ( ssh login ) the user onto the development server.

I am using virtualBox and ubuntu mini to achieve this. 

**Problems:**

The first question is if this is a reasonable way to achieve what I am attempting to. Is there a better way?

The others is more in terms of the set-up:

I am attempting to resize the virtualBox console. I tried this by editing grub. Although I am able to resize the screen at start-up the entire screen goes back to ( what I believe is 800x600 ) after the Ubuntu splash screen. 

The virualBox seems to have completely messed up the keyboard detection – how can I rectify this?

The other is regarding the restricting of  shell access – I have currently done this by removing access to /bin/ for normal users. Is this secure enough or is there a better way?


I would really appropriate any help!

---

### Post by tmharish on 2010-11-26
I seem to have found the solutions.

I solved the resolution and console size problem by doing the following:

Update Grub to Grub2
Then follow instruction [here]("http://ubuntuforums.org/showthread.php?p=7942683") to change the console size.

Regarding the keyboard layout I solved that using information [HERE]("http://ubuntuforums.org/showthread.php?t=50501")

Regarding the security issue I managed to block of all commands by providing users with a jail-shell and changing the permissions on 'bin'. I also plugged in a key-logger just to be sure. 

Hope this helps someone!

---


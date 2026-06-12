---
title: "Password problem after upgrade."
date: 2016-05-03
forum: Installation &amp; Upgrades
---

### Post by civkoss on 2016-05-03
So I attempted to upgrade to 15.10 from 14.something. Now every time I try to boot I get stuck after the grub dual boot menu. It asks for a login. 

The lines I get is 

Ubuntu 15.10 Beatrice tty1 
Beatrice login: 
Password:

Regardless of what username or password I input, I just get told 'Login Incorrect'

I have tried to use recovery mode, but I still get asked to login. I was wondering if anyone here knew what login it is asking for, and a way to recover the password for it?

---

### Post by Impavidus on 2016-05-03
After a release upgrade gone wrong I usually suggest a clean install (of 16.04 in this case). It's difficult to say what's wrong with your system. Upgrades from 14.something to 15.10 aren't advisable and I think shouldn't be offered.

Use a live disk to make a backup of your files first.

---

### Post by ubfan1 on 2016-05-03
The login prompt is from virtual terminal 1 (vt1).  You probably have six of them, with the graphical interface on 7.  The response should be your original username and password from the old system -- an upgrade should not change those.  You can switch among the virtual terminals and the desktop using the key combinations ctrl-alt-F7 (function key 1-7).  Take a look at 7 to see if anything is running there.  If not login to 1, and try entering the command  startx   to try and start the desktop.  Probably you have a video problem, so  editing the grub boot command to add a kernel parameter like "nomodeset" might help.

---

### Post by Bucky Ball on 2016-05-03
Welcome. Just for future reference, LTS upgrades to LTS. 14.04 LTS could have gone to 16.04 LTS via a couple of terminal commands. After the point release in a few months you'll be able to do it through the GUI.

Updating 15.10 was not a good plan to start. Offering that upgrade was a bad idea on Canonical's part IMHO and this is not the first issue we've seen because of it screwing up. The other point is 15.10 is supported for another two and half months or so, 14.04 LTS is supported until April 2019 and 16.04 LTS until 2021. Guess you can see what I'm saying. You upgraded a release supported for the next three years to one that is supported for the next two and bit months, at which time you'll need to go through it all again. :|

LTS releases have five years support, everything else (interim releases) have nine months. Hope this info can help in the future.

PS: Unless you've done a clean install, the machine is waiting for the exact same username and password you were using with 15.10. You've upgraded the installed OS, not wiped it and started again, changing user details in the process. Everything should be the same as it was, just newer.

If the old username and pw aren't working, then gives us a better idea of what the problem might be.

---

### Post by civkoss on 2016-05-03
> **ubfan1 said:**
> The login prompt is from virtual terminal 1  (vt1).  You probably have six of them, with the graphical interface on  7.  The response should be your original username and password from the  old system -- an upgrade should not change those.  You can switch among  the virtual terminals and the desktop using the key combinations  ctrl-alt-F7 (function key 1-7).  Take a look at 7 to see if anything is  running there.  If not login to 1, and try entering the command  startx    to try and start the desktop.  Probably you have a video problem, so   editing the grub boot command to add a kernel parameter like "nomodeset"  might help.

Okay, so I figured out why my username did not work. I was dumb. I was capitalizing the first letter of the username >.<. 

But on the plus side I can login now. I still do not get into the graphical interface, just a command line. 

I  did what you said. When I used ctrl-alt-F7 there was nothing on the  screen it was just blank. When I switched to tty1 and ran startx I  reached my desktop but the interface seem borked. Instead of a cursor I  have an x and there's a lack of buttons and such. I'm not sure if that is  because something is wrong or because it is just a facsimile of the  actual desktop. F7 is still blank. I do seem to be able to access my  data though, which is good. I've backed up everything important, but  it's still nice to see it is still there. 

How do I edit the grub boot command?

> **Bucky Ball said:**
> Welcome. Just for future reference, LTS upgrades to LTS. 14.04 LTS could have gone to 16.04 LTS via a couple of terminal commands. After the point release in a few months you'll be able to do it through the GUI.

Updating 15.10 was not a good plan to start. 

Yeah I'm starting to see that. It was what the software updater recommended so I did it, but I should probably just have checked the latest version from the start.

Edit: I tried nomodeset, but it does not seem to have made any difference. I'll try and upgrade from the command line or an usb I guess.

---

### Post by ubfan1 on 2016-05-03
Instructions for grub editing appear at the bottom of the grub menu screen -- type e then edit, then ctrl X to boot.  Maybe the problem is caused by the old "dot" files (file names starting with a period) which are "hidden" from some directory listings.  .Xauthority and .ICEauthority are good ones to rename or just copy into  a directory you make to get them out of the way (or just copy all of them to the dir).   Were you running a proprietary video driver?  Restore the necessary repository (you should have turned it off before updating), apt-get update, and reinstall the video driver.

---

### Post by civkoss on 2016-05-04
> **ubfan1 said:**
> Instructions for grub editing appear at the bottom of the grub menu screen -- type e then edit, then ctrl X to boot.  Maybe the problem is caused by the old "dot" files (file names starting with a period) which are "hidden" from some directory listings.  .Xauthority and .ICEauthority are good ones to rename or just copy into  a directory you make to get them out of the way (or just copy all of them to the dir).   Were you running a proprietary video driver?  Restore the necessary repository (you should have turned it off before updating), apt-get update, and reinstall the video driver.

I resolved the issue by doing a clean install of ubuntu 16.04 ^_^ 

Still thank you for the help!

Not sure how to mark the thread as resolved.

---

### Post by Bucky Ball on 2016-05-04
Mark as solved by using Thread Tools at the top right of this page or check the second link in my signature. Thanks.

You are set for the next five years! Unless, of course, you decide to upgrade your 16.04 LTS to the next interim release when available, 16.10, or, and probably preferable if you're simply after a stable, day-to-day system, 18.04 LTS when that is available.

Good luck whatever you do. :)

---


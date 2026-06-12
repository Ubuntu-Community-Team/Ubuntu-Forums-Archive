---
title: "Help Im trying a Wubi Install on drive G;"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by deebee17701 on 2010-04-19
Virgin Newbie Here!
 
Trying to install Ubuntu 9.10 with Wubi, not locating it on C: , but on a 9 GB drive dedicated for this purpose called labeled G:
 
When I go to rebot I get a grub message.
 
But I don;t know what to do next?
 
Help /comments greatly appreciated .
 
Dee Bee

---

### Post by uRock on 2010-04-19
You have to install it in the C drive. It will not corrupt your Windows files. Though it boots separately, it runs just like any other program you have installed in Windows and stores everything in one large folder on the C drive.

---

### Post by bcbc on 2010-04-19
Check this out: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

You probably need to replace the wubildr file as described in the link.

---

### Post by deebee17701 on 2010-04-26
Thank you for the reply,
 
I have replaced wubildr file on C: and also on G;  when I boot the system goes directly to Windows XP  
 
Any ideas?
 
Dee Bee

---

### Post by bcbc on 2010-04-27
> **deebee17701 said:**
> Thank you for the reply,
 
I have replaced wubildr file on C: and also on G;  when I boot the system goes directly to Windows XP  
 
Any ideas?
 
Dee Bee

How far did you get on the install - did it ever complete? 

What you should have seen:
1) Run wubi install on windows (either from web or cd). This shows some progress and eventually says you need to reboot. You have to select Ubuntu from the menu when the computer restarts. If you don't (e.g. if you are not paying attention, and it times out and boots windows) you need to uninstall, and reinstall again.
2) When you restart and select Ubuntu, it will do the actual install. You'll see a 'slide show' and progress indicator and then at the end it reboots. After this ubuntu is installed and you'll see the grub menu following selection of 'Ubuntu'.
3) At this point I replaced my wubildr on C:\ and the install drive e:\ubuntu\winboot\  (my e: is a fat32 partition on an external drive)
4) Everything still works.

If you couldn't even get to the installation part (2 above) then you might need to replace wubildr after the initial windows 'install' prior to rebooting. 

Also, if you didn't complete  the installation part, you will need to 'uninstall first' (Control panel, Add/remove programs) and then reinstall.

If you did initially have ubuntu booting normally, then I'm not sure what's happened. Please  describe more details about the steps you took, the errors you are getting, and it will also help to post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/").

---


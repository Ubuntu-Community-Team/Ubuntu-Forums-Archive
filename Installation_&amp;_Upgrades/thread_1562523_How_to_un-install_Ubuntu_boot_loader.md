---
title: "How to un-install Ubuntu boot loader?"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by why_me? on 2010-08-27
I had to un-install Ubuntu as there were too many things that didn't work.  Bummer, I wanted to like it and use it.:(

Anyway it has left me with a screen at boot-up that I must choose between Windows and Ubuntu, that counts down automatically about 30 seconds and then finally boots into Windows as the default.  How can I get rid of this screen and go back to booting up into Windows normally?  Thanks for your help!

---

### Post by pastalavista on 2010-08-27
Boot up with a Windows install CD or from the recovery partition and run the commands

fixboot fixmbr

and it should boot directly to Windows after that

---

### Post by why_me? on 2010-08-28
Thanks for the info, but tried that, doesn't work...neither on my desktop which DOES have a CD drive, nor on my tiny 10.1" screen laptop which DOES NOT have a CD drive...anyone else have any ideas - especially for the computer without a CD drive?
:confused:

---

### Post by entropy1 on 2010-08-28
If you still have Ubuntu on your system [EDIT: just reread your post saying you uninstalled it], run System > Administration > Start-Up Manager.  If it's not there, install it with Synaptic.  The Start-Up Manager will allow you to select the default OS and also the timeout.  You can set the timeout as low as you like, say 2 sec in case you ever want to use Ubuntu again.  If you select the default OS as Windows, your system should boot directly into Windows with as short a wait as you like.

---

### Post by Sef on 2010-08-28
> If you still have Ubuntu on your system [EDIT: just reread your post saying you uninstalled it], run System > Administration > Start-Up Manager. If it's not there, install it with Synaptic. The Start-Up Manager will allow you to select the default OS and also the timeout. You can set the timeout as low as you like, say 2 sec in case you ever want to use Ubuntu again. If you select the default OS as Windows, your system should boot directly into Windows with as short a wait as you like.

If the op has a live cd, then that should work.

---

### Post by kansasnoob on 2010-08-28
It sounds to me like this may have been a Wubi install:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

If so you might benefit from reading the uninstall page for Wubi:

[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

I haven't used Wubi much so I can't help much beyond that.

---

### Post by oldfred on 2010-08-28
If you can still boot you must have installed wubi.

You need to edit the windows startup.

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?)
For Vista, you can use EasyBCD to edit the boot menu. Alternatively you  can modify the boot menu via Control Panel > System > Advanced  > Startup and Recovery and pressing "Edit"

I see kansasnoob beat me to it.

---

### Post by why_me? on 2010-08-28
Thanks, all!  Just editing the Windows startup file did the trick, now it works like I never even had Ubuntu, ha ha.  :P
Seriously I will probably try Ubuntu or another flavor again but now I am more oriented towards using the computer as a tool that works, and that I don't have to repair and fiddle with all the time - not that Windows is that great either, I still like the Amiga OS...

---


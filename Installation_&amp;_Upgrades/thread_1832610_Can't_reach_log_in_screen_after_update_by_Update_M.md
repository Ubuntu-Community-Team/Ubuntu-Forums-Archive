---
title: "Can't reach log in screen after update by Update Manager"
date: 2011-08-25
forum: Installation &amp; Upgrades
---

### Post by HaPpYb0i on 2011-08-25
Using 11.04. After an update by Update Manager, everything seems fine. but after I rebooted it fails to reach the log in screen. It shows Ubuntu is booting up, after that, it seems it has crash, though I managed to boot it up and go into my desktop in low graphics mode.

As I'm new to Ubuntu, I really do not know what to do. Any help will be appreciated. Thanks.

Here is a picture I've taken:
[http://imageshack.us/photo/my-images/204/img0037pn.jpg/](http://imageshack.us/photo/my-images/204/img0037pn.jpg/)

---

### Post by mörgæs on 2011-08-27
Hi, welcome to the fora.

Have you confirmed that 11.04 works in a live boot on this computer?

---

### Post by Mark Phelps on 2011-08-27
I encounter this far more often than should be the case ...

What I recommend is the following:
1) Boot, holding down the SHIFT key.  This will force the display of the GRUB menu
2) When the menu comes up, choose the top-most Recovery Mode option
3) That will eventually show a menu -- chose Repair Broken Packages
4) If that completes OK, choose the Normal Boot option.
5) If that doesn't work, it's liable to force you to login again.
6) If you are still in a text screen, enter"startx".

That should display your desktop again.

I though they had FINALLY fixed this problem ... but after several weeks, it happend to me again ... today.

---

### Post by Hakunka-Matata on 2011-08-27
[http://ubuntuforums.org/showthread.php?t=1743535&highlight=Graphical+problems&page=8]("http://ubuntuforums.org/showthread.php?t=1743535&highlight=Graphical+problems&page=8")
That's the thread the below information comes from:  it's a very long thread, sticky, excerpt from post #1 below:

Troubleshooting Flow Chart 
This is to break this down into steps:
Step 1. Do you have a Grub Menu?
- Yes: Go to step 2...
- No: Whiie booting, Press shift key (don't hold down) multiple times to see if the Grub menu will come up
- - If yes on Menu, go to step 2
- - If no, comment out /etc/default/grub/ GRUB_HIDDEN_TIMEOUT=00. and rerun grub-update (from a LiveCD)
- - - If yes on Grub Menu go to Step 2
- - - If No, reinstall grub and Start Step 1 from Beginning... Becuase it seems that Grub is not booting.

Step 2 "Does the Linux Kernel Boot?" At Grub Menu, go into edit mode and boot into a text console (see instructions below)
- Yes. Go to Step 3
- No. Messages will be verbose on what is loading, what are warnings and what are error messages. Shortcut keys will start to work as the kernel modules load. If if stops at an error, you will be able to use the shortcut navigation cuts to review the errors. Depending on the error, if it is a kernel error, you may be able to reinstall or renew the kernel image. If it is a device module, at least you have somewhere to go to reload that device module or driver.,,, Goal is to get a "booting kernel."

Step 3. From the Grub Menu, try to boot in Rescue mode/low graphics.
- If Yes, look for addtional drivers and install recommended driver.
- If No, goto Step 4 to verify that linux kernel will boot.

Step 4. Can you boot a graphical Xseesion from a text console session? From the command line type 
Code:
sudo service gdm start
- Yes No black screen/No problem... should boot straight from the grub menu.
- No. Reboot and start testing and changing gfx_modes and kernel boot graphical modes, still booting into the text console before you try to start an Xsession. Going this way, you will have more of a possible chance to be able to toogle between a graphical session or text terminal session (sometimes). ...and at a text console, at least you have the abilty to install files and make changes to config files. And if you can get back into a command prompt, you could then stop the gdm service that is locked.

You can stop the gdm service via
Code:
sudo service gdm stop

---

### Post by MAFoElffen on 2011-08-27
> **HaPpYb0i said:**
> Using 11.04. After an update by Update Manager, everything seems fine. but after I rebooted it fails to reach the log in screen. It shows Ubuntu is booting up, after that, it seems it has crash, though I managed to boot it up and go into my desktop in low graphics mode.

As I'm new to Ubuntu, I really do not know what to do. Any help will be appreciated. Thanks.

Here is a picture I've taken:
[http://imageshack.us/photo/my-images/204/img0037pn.jpg/](http://imageshack.us/photo/my-images/204/img0037pn.jpg/)
I recognized the error messages in your attached photo...

Follow the instructions from this post in my sticky:
[http://ubuntuforums.org/showpost.php?p=11078247&postcount=507](http://ubuntuforums.org/showpost.php?p=11078247&postcount=507)

It is the Lauchpad workaround for that problem. (With a few mods that made the fix universal)

Sidenote--> I really need to clean up and tie all those workarounds back to the first 3 posts of that sticky!  Still trying to decide whether to copy/paste them in -or- to make a contents page linking to all the graphics workarounds we worked out or found.(???)

---


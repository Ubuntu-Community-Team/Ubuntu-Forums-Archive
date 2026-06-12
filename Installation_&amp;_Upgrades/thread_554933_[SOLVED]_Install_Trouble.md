---
title: "[SOLVED] Install Trouble"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by Talthalra on 2007-09-19
I'm having trouble getting Ubuntu to install.  It gets to a point where there is a prompt, the cursor flashes, and my monitor turns off.  Could it be monitor or GPU issues?  

Acer 22"
Ati X1800XL

---

### Post by Pumalite on 2007-09-19
Either one or both. Post specs.

---

### Post by GavinZac on 2007-09-19
which cd are you installing from?

---

### Post by Talthalra on 2007-09-19
AMD Athlon 64 3500+ 2.4GHz
2GB RAM
ATI Radeon X1800XL

I downloaded the 7.04 from the site and made my own CD.

Need anything else?

Thanks for any help!

---

### Post by Pumalite on 2007-09-19
Try the Alternate CD first: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below green sign 'Start Download'

---

### Post by Talthalra on 2007-09-20
Ok, the alternate version got me further, but I can't seem to get equal Md5Sum values.  I'm new to this whole thing if you can't tell, haha.  Is there a fix for this issue?

Edit:

Well, I got it installed.  I still can't get any visual though.  I've done some research, but can't find anything.  If anyone knows of any fixes they would be much appreciated.
My specs are posted above.
Thanks

---

### Post by Talthalra on 2007-09-20
Nothing?

---

### Post by dabl on 2007-09-20
Probably this: [http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

:)

---

### Post by Pumalite on 2007-09-20
Do you end up with a command line or a blank screen?
Anyway; Ctrl+Alt+F1 to get command line. At the command line:
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx
Let me know how it goes.

---

### Post by Talthalra on 2007-09-20
Ok, I think the problem is that it's trying to use a pci slot while my card is in a pci-e slot.  I'm assuming I need to determine the slot number or name and place that in the field.  Is this correct?

---

### Post by Pumalite on 2007-09-20
Did you install with the Alternate CD as I suggested?. If yes, then the fix given by both dabl and I should work.

---

### Post by Talthalra on 2007-09-20
I went through everything you mentioned.
I can hear it start up, but my monitor shows no signal
and goes into standby.  Any other suggestions?

---

### Post by Pumalite on 2007-09-20
Well, it's your 22" display. I think you have to install something, but it escapes me at this moment. I'll investigate it. Stay in touch.

---

### Post by Pumalite on 2007-09-20
[http://ubuntuforums.org/showthread.php?t=274291](http://ubuntuforums.org/showthread.php?t=274291)

This thread might give you some ideas to try. I think it deals with configuring your xorg file in a special way. Make sure you backup first.

---

### Post by Pumalite on 2007-09-20
In the meantime you might want to try to boot your system with Super Grub: 
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Talthalra on 2007-09-20
This is what I get when I enter "startx" at the end:




xauth: creating new authority file /home/ryan86/.serverauth.5789

Fatal server error:
Server is already activer for display 0
  If this server is no longer running, remove /temp/.X0-lock

Xlib: Connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 Key
giving up
xinit: unable to connect to X server
xinit: No such process (errno 3): server error.




Thanks for all the help!

---

### Post by Pumalite on 2007-09-20
You might need to stop your xserver before reconfigurig; try this:
sudo /etc/init.d/gdm stop
If it tells you xwindow is stopped, then continue with the rest of the recipe.

---

### Post by Talthalra on 2007-09-21
I got it running!  Thanks for all the awesome advice!  The only thing I need to do now is get my resolution fixed, haha.

---


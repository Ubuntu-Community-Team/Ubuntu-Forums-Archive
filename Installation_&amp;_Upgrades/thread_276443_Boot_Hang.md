---
title: "Boot Hang"
date: 2006-10-12
forum: Installation &amp; Upgrades
---

### Post by sliPrix on 2006-10-12
I am extremely new to the Ubunutu and Linux community, so please forgive my lack of knowlege about whats going on.  I recently Installed a copy of Ubuntu 5.10 (from an official cd) to a blank 20Gb HDD.  The system installs what is necessacary, reboots, finishes installing the packages, it then goes to the screen with the Ubuntu logo where I believe it loads the kernel.  I hit Alt=F1 to see the statements.  As they are coming accross the screen I get an Error: "Temporary failure in name resolution" or something along those lines. It finishes loading a few more lines of text then brings me to a black screen with a non-moving cursor.  This is the point as to which I am stuck.  I have tried booting from the live cd using the following commands: gdth=disable:y, noapic nolapic, and aic7xxx=no_probe.  The PC is a Dell Optiplex GX150 and not hooked up to my network.  Any suggestions/solutions are greatly appreciated.

---

### Post by K.Mandla on 2006-10-13
> **sliPrix said:**
> I am extremely new to the Ubunutu and Linux community, so please forgive my lack of knowlege about whats going on.  I recently Installed a copy of Ubuntu 5.10 (from an official cd) to a blank 20Gb HDD.  The system installs what is necessacary, reboots, finishes installing the packages, it then goes to the screen with the Ubuntu logo where I believe it loads the kernel.  I hit Alt=F1 to see the statements.  As they are coming accross the screen I get an Error: "Temporary failure in name resolution" or something along those lines. It finishes loading a few more lines of text then brings me to a black screen with a non-moving cursor.  This is the point as to which I am stuck.  I have tried booting from the live cd using the following commands: gdth=disable:y, noapic nolapic, and aic7xxx=no_probe.  The PC is a Dell Optiplex GX150 and not hooked up to my network.  Any suggestions/solutions are greatly appreciated.
Hello and welcome. A couple of questions. ...

Any reason you're using the 5.10 disc? It's possible that the glitch you're experiencing was ironed out in later versions or updates.

Also, are you using the onboard video? I've installed 6.06.1 on a number of GX150's (I'm using one to type this -- running the Edgy beta with a GeForce4 440 AGP card), and I've run into a couple of problems with onboard video -- not like what you describe, but it could be related somehow. You never know.

I would suggest a couple of things: Try the 6.06.1 installation (alternate) ISO with the network plugged in. If that's still giving you problems, try a server installation and upgrade to ubuntu-desktop.

One last note ... I'm guessing you're at 1Ghz or lower, and you might want to use Xubuntu rather than straight Ubuntu. The system load under the default Gnome desktop in Ubuntu can be a little sluggish on sub-1Ghz machines, in my experience.

Cheers and good luck! :mrgreen:

---

### Post by sliPrix on 2006-10-13
The only reason I was using teh 5.10 disc was that I had it readily available, but I am going to try downloading the newer release. The graphics I am using is an ATI 92500 PCI.  The computer has a 1.2ghz processor, 512Mb RAM, and a 20Gb HDD (this is my old pc).  What I'm going to try to do, is use the newer release, try a different graphics card, and lastly use Xubuntu if this doesnt work.  Thanks for the help K.Mandla!  I'm still open for more suggestions from anyone, but I'll let you know how this goes.

---

### Post by K.Mandla on 2006-10-13
I don't know for certain that the graphics is to blame, but in my experience, a black screen with a cursor in the corner is generally some sort of video fault. See if you can tweak the hardware configuration enough to get past that point -- yank the video card, step down the memory, try the onboard stuff, update the BIOS, etc.

I don't think that video card should be particularly problematic, but there's always the possibility. Adding *pci=conf1* to your kernel boot line might also help, but to be honest, that's such an obscure trick that I couldn't even begin to explain when and why it works. If it does, it does; if it doesn't, nothing was lost.

Keep us posted. ;)

---

### Post by sliPrix on 2006-10-13
Hey, I finally got it working.  When I got home from school today I started the downoad of Ubuntu 6.06.1 and Xubuntu.  In the meantime I pulled my videocard out, booted and everything worked fine.  Now however, I want to end up using that card, so can anyone point me in a direction as to where to find/ how to install the drivers for the card (ATI Radeon 9250)

---

### Post by K.Mandla on 2006-10-14
> **sliPrix said:**
> Hey, I finally got it working.  When I got home from school today I started the downoad of Ubuntu 6.06.1 and Xubuntu.  In the meantime I pulled my videocard out, booted and everything worked fine.  Now however, I want to end up using that card, so can anyone point me in a direction as to where to find/ how to install the drivers for the card (ATI Radeon 9250)
If you install Xubuntu with that card attached, it should automatically pick the open-source drivers for ATI cards. You can check by opening the /etc/X11/xorg.conf file, and looking for a line about 2/3 of the way down that reads

```
Driver "ati"
```
Adding the card later is a little trickier but not impossible. Power down, insert the card, connect the cable, boot to BIOS, make sure it's using the inserted card and not the onboard, then reboot to Xubuntu.

That's when things will probably get a little ugly. You probably won't get a GUI, and you'll have to configure X to play nice with the ATI card.

I think the easiest way to get that working is to log in, then enter *sudo dpkg-reconfigure xserver-xorg*. You should get some menu options to configure your video card (it will seem like it takes forever; it'll ask about your keyboard and mouse too). 

If all goes well, X will set itself up to use the add-on card, and if you look in /etc/X11/xorg.conf again, you should see that Driver "ati" line. 

Start up the desktop with the *startx* command and see if it worked. (If it worked, you won't have to log in at the terminal screen again. It should go straight to the GUI login.)

If that still didn't work, we can try a different way. :)

---


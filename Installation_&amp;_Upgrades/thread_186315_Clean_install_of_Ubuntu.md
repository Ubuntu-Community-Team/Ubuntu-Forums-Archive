---
title: "Clean install of Ubuntu?"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by guice on 2006-06-01
Okay, so I followed the Kubuntu instructions and now my system is hosed. 
>     * In Adept go to Manage Repositories and change "breezy" to "dapper"
    * Click "Fetch Updates"
    * Click "Full Upgrade"
    * Click "Commit"
    * After all packages have installed reboot the computer

I look here and I see in the Ubuntu forums to kill ALL applications and use apt for the install.

Well, now my system is hosed and I'm just gonna do a fresh install (good thing I kept all my files on the USB drive). Is there a simple way to tell apt to do a full clean reinstall of everything or will I need to use the ISO/Netboot to do this?

I'm also contemplating on installing Ubuntu to play around with GNOME and since is seems that Ubuntu is about 3x better supported than Kubuntu....(sorry Kubuntu folks .. it's just the Ubuntu site and support forums feels 10x for organized. :( Not to mention the Ubuntu forums are 10x more trafficked.)

---

### Post by az on 2006-06-01
[QUOTE=guice]Okay, so I followed the Kubuntu instructions and now my system is hosed. 


I look here and I see in the Ubuntu forums to kill ALL applications and use apt for the install.

Well, now my system is hosed and I'm just gonna do a fresh install (good thing I kept all my files on the USB drive). I[/QUOTE]



What do you mean bu hosed?  Spend a few more minutes and you may be able to fix everything.

---

### Post by guice on 2006-06-01
[QUOTE=azz]What do you mean bu hosed?  Spend a few more minutes and you may be able to fix everything.[/QUOTE]
Well, for starters, through the install, Adept died. I thought it finished. So I went to restart and upon restart I get shot to command prompt login.

I log in and try to start kdm with no luck. Turns out kdm didn't even *install*! I had to install it myself. So, then when I tried to start kdm, screen would flick and just sit at the startup/shutdown Kubuntu screen. Hitting Cntl-Alt-Del a couple times rebooted the box (back to command line login).

So I checked and see my nvidia drivers are installed, but I was getting an nvidia error in Xorg log. So I did the dkg-reconfigure for xserver-xorg. That went through, but the graphics were messed up. Cursors were starting from one position off. I had extra 1 block shift aprox 3/4 down on the screen. Things were redrawing correctly scrolling up and down .. etc.

Anyway, I got through that selecting defaults for everything (adding my selection for 1280x1024). And tried to restart kdm. No luck (stall out again). So I rebooted and THIS time KDE started. However, it didn't start successfully.

It started unable find theme: Cannot open theme file /usr/share/apps/kdm/themes/kubuntu ('kdm' directory does not exist). And plops me into the default term window on the KDE "desktop". (You know the one, you have a background colour with a nice black box in the upper right hand corner with a prompt).

Not to mention through my editing, every attempt to /etc/init.d/kdm stop or start would popup the Kubuntu startup/shutdown screen and put my system in a stall out, once again.

Yeah, it's hosed. ^_^

I have NO clue what else Adept failed to install unfortunately.... apt-get -f install says nothing to install/upgrade. But the system is not acting properly. Something is still wrong.

---

### Post by az on 2006-06-01
[QUOTE=guice]
Yeah, it's hosed. ^_^

I have NO clue what else Adept failed to install unfortunately.... apt-get -f install says nothing to install/upgrade. But the system is not acting properly. Something is still wrong.[/QUOTE]

If apt-get -f install does not complain, can you see if kubuntu-desktop is installed and at the lastest version?  If adept failed to install anything, you would know about it.  Also, if you are using the nvidia binary drivers, make sure you have the latest (if they are the source of your woes, I cannot help you)

Also, can you run badblocks from a live cd?

sudo badblocks /dev/hda1


...yeah, that's all I got for you...

---

### Post by guice on 2006-06-01
[QUOTE=azz]If apt-get -f install does not complain, can you see if kubuntu-desktop is installed and at the lastest version?  If adept failed to install anything, you would know about it.  Also, if you are using the nvidia binary drivers, make sure you have the latest (if they are the source of your woes, I cannot help you)

Also, can you run badblocks from a live cd?

sudo badblocks /dev/hda1


...yeah, that's all I got for you...[/QUOTE]
Very interesting, It would seem kubuntu-desktop didn't even install correctly. Running an apt install on that prompt up a BUNCH of stuff. Running through that now. We'll see if that corrects anything. I expect this to take an hour or so (apt is saying ~1h).

---

### Post by az on 2006-06-01
Holy crap!  I thought you were screwed!

---

### Post by guice on 2006-06-01
Well, I said the system was hosed and it indeed was. The update didn't install kubuntu-desktop correctly. So, I was still right about it being hosed. ^_^

However, I still stand by the comments about Ubuntu seeming to have more/better support than Kubuntu. :D

---

### Post by az on 2006-06-01
So it everything okay?

Hosed implies permanent or unfixable dammage.  Borked is just borked.

---

### Post by guice on 2006-06-01
Well, that made a world of difference....I also had to install nvidia-glx as the distro upgrade didn't seem to take that into account (apparently it changed from nvidia-settings to nvidia-glx).

Good news, too, Kaffeine actually works now! Didn't in the previous version. I had to use MPlayer. ;)

Yes, it did work. Thanks much. Wonder what broke in the update to cause everything to go haywire...

---


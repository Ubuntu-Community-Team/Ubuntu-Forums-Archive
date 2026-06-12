---
title: "First update broke clean install of Ubuntu 7.10"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by jck99nz on 2008-01-04
Hi,
I've installed 7.10 from live CD, partitioned/reformatted disk etc. Everything looked good. I then installed recommended updates (147 of them). I did the recommended restart, and ended up with a blank sandy-coloured screen - no application icons at top, nothing along bottom. The mouse pointer is present and works, but I can't open a terminal. Ctrl-Alt-Del gave me the shutdown options. Restarting ended up with the same blank screen.
Hitting 'Esc' during grub loader, I went into recovery mode. Got terminal prompt - dmesg didn't show any obvious errors (seemed to pick up all hardware etc).
I've used the same disk a few times, on the same computer, and installed updates with no problems (I'm trying to build a mythtv system with no prior linux experience, so I've done a lot of new clean installs to fix messes I've made). This problem first appeared a few days ago. I upgraded my power supply in case it was causing display problems (I was underpowered for a new video card) but it hasn't fixed it. 
Does anyone know which of the 147 updates since 7.10 was released is likely to be the culprit, and how I can fix it?
Other details: Running Dell Optiplex GX260, 1GB RAM, ATI RadeonX1650 graphics card, 500GB HDD, Hauppauge PVR150 card.
Many Thanks,
Jeff

---

### Post by jck99nz on 2008-01-05
A bit more info - I've just done another clean install of Ubuntu. I accepted all the recommended updates then did the restart after they had all been installed. I got the graphical login screen, and after logging in I hear the Ubuntu music clip. At that point, a white bar appears at the top and bottom of the screen (where the menu and status bars should be) and flashes on and off 7 or 8 times, before disappearing and leaving the screen a blank sandy colour. 
Everything seems to work fine before I accept the recommended updates.
jeff

---

### Post by Craigus on 2008-01-05
Try rebooting in recovery mode to a root text terminal and do:

> dpkg-reconfigure -phigh xserver-xorg

reboot - does that help ?

---

### Post by jck99nz on 2008-01-05
Thanks Craigus. I get a message 'xserver-xorg not installed, no info available'. Rebooting results in same scenario as in last post (log in, flashing white bars, blank sand-coloured screen).
I looked at some logs in /var/log (daemon log etc) and only serious looking error was:

jklinux-desktop gdm[4911]: Glib-CRITICAL: g_key_file_get_string: assertion 'key_file != NULL' failed

Not sure what it means; saw some refs to it in a google search relating to problems a few months back, but no clear suggestions for how to fix it.

Jeff

PS typing above in so may be some minor typos - using a Windows machine in absence of functioning linux

---

### Post by bobfat on 2008-02-06
has anyone got an update, or ideas on this..

I'm a complete linux newb, but I've got the same situation.  Installed a clean Ubuntu 7.10 final.  Installed ok.

Lovely stuff, really enjoyed using it.

noticed there was 187! updates, it recommended i install.

Installed them all

now I get as far as the login screen, log in ok.. looks like the desktop is loading, mouse pointer appears, I can move the mouse around but the screen stays black.

no idea how to fix.

should I replace the xorg.conf file from the cdrom? (after I work out how to get root access :(

Any help appreciated, as I would rather learn than install a fresh again.  And not do ANY updates again.

Cheers
Bob

---

### Post by jck99nz on 2008-02-07
I got around it by doing a clean install again. I then accepted ONLY the security updates (went and unchecked all the others). I rebooted when prompted, then I accepted all the remaining updates. Everything worked fine after that. I never did get any other suggestions that worked.

Jeff

---

### Post by Partyboi2 on 2008-02-07
> **bobfat said:**
> 
should I replace the xorg.conf file from the cdrom? (after I work out how to get root access :(
Cheers
Bob
If you are able to get to a working terminal Ctrl+Alt+F2
and do what was suggested earlier in this thread
```
sudo dpkg-reconfigure xserver-xorg
```then choose your graphics card driver and finish answering all the questions, if unsure just choose the default ones that are displayed on screen.

---

### Post by themrcul on 2008-02-09
I can confirm this.
I have been spending the entire afternoon installing gutsy on two laptops for friends, and after full updates, they no longer boot. And I thought it was something I was doing, so I tried several times with different setups...
Just tried installing only security updates and rebooting, as bobfat advised, and it worked. I'll now attempt (with great trembling...) the recommended ones. What a waste of the last 5 hours... :mad:

---

### Post by ubersolid on 2008-02-11
I have the exact same problem. Installed Gutsy on 3 diffrent machines this weekend, two 32bit and one 64bit. My dekstop, the 32bit one is the problem. I will try the update method suggested here. I have reinstalled twice allready ...
Wonder what would cause something like this?

---


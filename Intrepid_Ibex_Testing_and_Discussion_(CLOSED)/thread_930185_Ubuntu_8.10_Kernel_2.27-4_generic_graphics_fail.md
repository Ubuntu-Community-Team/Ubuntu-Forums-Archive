---
title: "Ubuntu 8.10 Kernel 2.27-4 generic graphics fail"
date: 2008-09-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jcr2 on 2008-09-25
Don't know if this is the correct place for this, but I'll try here.

I just purchased this Sager NP9262 Notebook to replace my desktop.  Having three hard drives opens up the possibility of installing Ubuntu to give it a try.

I installed the x64 version of Ubuntu 8.04 and it seemed to work well other than the total inability to recognize the Intel PRO 5300 wireless card.  After some thorough forum searching, the general answer seemed to be that it was easiest to upgrade to Intrepid Alpha 5.

I did so, and it seemed to work okay until I rebooted.  The GNOME desktop graphical user interface no longer boots and I am left with a command line only.  This happens if I try to start kernel 2.24-19 as well.

What kind of information would be needed from me in order to resolve this?  The video card setup is dual nVidia 9800m cards.

Thanks.

---

### Post by WWSmith36 on 2008-09-25
Did you install any video drivers after installing intrepid

---

### Post by soxs on 2008-09-25
ATI video drivers don't support xorg 7.4 intrepid uses,(yet). I don't know about nvidia ones.
Remove them and you should be fine.
To make allow you logging in again, do:
press <strg><alt><f1> when your PC finished bbooting
log in
sudo nano /etc/X11/xorg.conf
replace ```
Driver "whatever"
``` in the Device section with ```
Driver "vesa"
```
save and reboot via ```
init 6
```

---

### Post by jcr2 on 2008-09-25
Thanks for the quick replies.

No, I just ran the update manager and updated.  GNOME failed to launch after the restart, so I never had the chance to install any video drivers.

---

### Post by soxs on 2008-09-25
can you log in when pressing <strg><alt><f1>

so you can try to reinstall it:
```
sudo apt-get install gdm ubuntu-desktop
```

and this still doesn't help, there is a brut force option, but this may brake some programs dependencies, so they get removed and not automatically instead
```
sudo apt-get remove --purge ubuntu-desktop gdm; sudo apt-get install ubuntu-desktop gdm
```

---

### Post by jcr2 on 2008-09-25
It lets me log in.  I'll give that a shot and let you know what happens.

Thanks again.

---

### Post by jcr2 on 2008-09-25
Well, replacing the driver with 'vesa' in the xorg.conf file didn't seem to do much (it did say 'nvidia'), and when I attempt the reinstall command it tells me that reinstall is not a valid command.  If I tell it to 'install' instead it informs me that I am already up to date.

There seem to be some pretty telling error messages popping up (something about vesa and v86d, making sure it is installed) but they go by a bit too fast.  Being a total n00b here, is there a text log file of the boot output?  I'm searching in /boot but not finding it.

If any further information is needed to get this working, I'll be glad to provide.

---

### Post by jcr2 on 2008-09-25
Attempting to start X11 using startx gives me the following:

```

Fatal Error:
no screens found.
giving up.

```

Not very helpful to me, but perhaps it is to someone else.

---

### Post by The Desert Fox on 2008-09-25
I have a similar problem: Here is what  I see in the sys log:
Glib Critical g_hash_table_lookup_extended assertion 'hash_Table != NULL' failed

ALso in gdm log i see:
Module ABI major version (0) does not match the screen version (1)
Failed to load module "dri"
VESA no valid monitor
Screens found but none have a usable config.

---

### Post by The Desert Fox on 2008-09-27
Try this, it worked for me. go to the teeerminal and start aptitude. Update your packet list and install all upgrades. See if that fixes it. If not then try removing obsolete packets.

---

### Post by soxs on 2008-09-28
> **jcr2 said:**
> Well, replacing the driver with 'vesa' in the xorg.conf file didn't seem to do much (it did say 'nvidia'), and when I attempt the reinstall command it tells me that reinstall is not a valid command.  If I tell it to 'install' instead it informs me that I am already up to date.

There seem to be some pretty telling error messages popping up (something about vesa and v86d, making sure it is installed) but they go by a bit too fast.  Being a total n00b here, is there a text log file of the boot output?  I'm searching in /boot but not finding it.

If any further information is needed to get this working, I'll be glad to provide.

I am sorry, I mixed it up with dpkg
so just use "install" instead of "reinstall"

Edited that post according

---

### Post by Sef on 2008-09-28
moved to Ibex forum.

---

### Post by zoomy942 on 2008-09-28
something that happened to me was this very thing when i used the JFS filesystem.  my workstation and tablet pc did the exact same thing 12 hours apart from one another.  I reinstalled to the ext3 filesystem and things have been fine so far...

so far anyway...

---

### Post by PGHammer on 2008-09-29
> **soxs said:**
> ATI video drivers don't support xorg 7.4 intrepid uses,(yet). I don't know about nvidia ones.
Remove them and you should be fine.
To make allow you logging in again, do:
press <strg><alt><f1> when your PC finished bbooting
log in
sudo nano /etc/X11/xorg.conf
replace ```
Driver "whatever"
``` in the Device section with ```
Driver "vesa"
```
save and reboot via ```
init 6
```

For all except R6xx and newer, there are *three* different options (all included with Intrepid A6):

1.  The "ati" driver (pre-Radeon chipsets)
2.  The "radeon" driver (Radeon through R5xx/RV5xx)
3.  The "radeonhd" driver (R5xx/RV5xx and eventually R6xx/R7xx).

X1K series can use either the "radeon" or "radeonhd" driver (radeonhd has faster 2D support, while the radeon driver has better 3D/DRI/Compiz support); I have the X1650PRO AGP in my Intrepid A6 setup; the configuration (default settings) uses the "radeon" driver.  (For the first time in all my Ubuntu usage, which goes back to Feisty Fawn, I'm not running any proprietary drivers whatever.)

---

### Post by keenish27 on 2008-09-29
> **PGHammer said:**
> For all except R6xx and newer, there are *three* different options (all included with Intrepid A6):

1.  The "ati" driver (pre-Radeon chipsets)
2.  The "radeon" driver (Radeon through R5xx/RV5xx)
3.  The "radeonhd" driver (R5xx/RV5xx and eventually R6xx/R7xx).

X1K series can use either the "radeon" or "radeonhd" driver (radeonhd has faster 2D support, while the radeon driver has better 3D/DRI/Compiz support); I have the X1650PRO AGP in my Intrepid A6 setup; the configuration (default settings) uses the "radeon" driver.  (For the first time in all my Ubuntu usage, which goes back to Feisty Fawn, I'm not running any proprietary drivers whatever.)

I have a Radeon HD2900.  Would that be "radeonhd" ?

---

### Post by soxs on 2008-09-29
> **keenish27 said:**
> I have a Radeon HD2900.  Would that be "radeonhd" ?

You've got a quite good card and radeonhd is still in developement, I really suggest you to sue fglrx to get the horses from your gpu to your tft/monitor

---

### Post by keenish27 on 2008-09-29
Well apparently there aren't any working fglrx drivers for intrepid yet.  I had to use "radeonhd" to see my desktop.  I'll just have to wait for workign fglrx drivers before I can do anything 3d.  Thanks for the help.

---

### Post by soxs on 2008-09-30
> **keenish27 said:**
> Well apparently there aren't any working fglrx drivers for intrepid yet.  I had to use "radeonhd" to see my desktop.  I'll just have to wait for workign fglrx drivers before I can do anything 3d.  Thanks for the help.

You can install 8.9 via the restricted mangers, but keep in mind: This will donwgrade X! I suggest you wait untiell endo of october and keep the hope 8.10 will support the new xorg release.

---

### Post by kronus on 2008-10-17
I've just run into the same problem.  

Upgrading from 8.04 to 8.10 beta, everything went fine, but I get dropped into a terminal at reboot.  Ctrl+Alt+F7 brings me to a blinking cursor in text mode.  I can log in, but trying to startx leads to the same error as the OP : no screens found, giving up.

I have an intel GM915 graphics chipset, xorg.conf had 'i810' listed as the driver, which is correct.  Changing this to 'vesa' did not help.

Any ideas?  The ubuntu liveCD I have is throwing buffer I/O errors :(

---


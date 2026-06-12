---
title: "Black screen boot-up after nVidia driver install"
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by newb_untu on 2010-11-08
Hello all, 
I realize that many have had the issue of getting a black screen when booting up.  I'm posting because I've tried a couple fixes that I read after doing a search and haven't had any luck yet.  

I have the 64-bit 10.04 installed on my netbook and my issue surfaced after installing the current nVidia accelerated graphics driver.  Following the install ubuntu now boots to a black screen and nothing more. 

'nomodeset' only allows me to boot ubuntu in low-graphics mode (which I'm in now) and this fix hasn't produced a solution either: [http://ubuntuforums.org/showpost.php?p=9965364&postcount=9](http://ubuntuforums.org/showpost.php?p=9965364&postcount=9) 

My netbook has nVidia ION2 graphics with an integrated as well as a discreet graphics card (Intel GMA3150 and NVIDIA GT218 )

Any ideas would be very much appreciated... or if I've overlooked a useful thread in my search, please let me know.  

Thank-you

---

### Post by dino99 on 2010-11-08
check that your video driver is activated: system admin additional driver

---

### Post by newb_untu on 2010-11-08
System->Administration->Hardware Drivers shows that 'This driver is activated and currently in use'

---

### Post by dino99 on 2010-11-08
so its time to look at errors logged into .xsession-errors (/home, ctrl+h to unhide it)

you can edit the boot line from grub menu and add either: nomodeset, noacpi, nolapic, noapic, irqpoll

often noacpi do the job

---

### Post by newb_untu on 2010-11-08
So I've tried noacpi nolapic noapic and irqpoll with no luck, although irqpoll allowed me to see the ubuntu splash screen before the screen went black.

Here are the errors from .xsession-errors

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-nlcAMv
GNOME_KEYRING_CONTROL=/tmp/keyring-nlcAMv
GNOME_KEYRING_CONTROL=/tmp/keyring-nlcAMv
SSH_AUTH_SOCK=/tmp/keyring-nlcAMv/ssh

(polkit-gnome-authentication-agent-1:1477): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1477): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gnome-power-manager:1478): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x22e52a0'
** (nm-applet:1482): DEBUG: old state indicates that this was not a disconnect 0
Initializing nautilus-gdu extension
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
/usr/bin/compiz (core) - Fatal: glXCreateContext failed
/usr/bin/compiz (core) - Error: Failed to manage screen: 0
/usr/bin/compiz (core) - Fatal: No manageable screens found on display :1.0

** (gnome-panel:1487): WARNING **: panel-applet-frame.c:1273: failed to load applet OAFIID:GNOME_FastUserSwitchApplet:
System exception: IDL:Bonobo/GeneralError:1.0 : Child process did not give an error message, unknown failure occurred
evolution-alarm-notify-Message: Setting timeout for 45142 1289278800 1289233658
evolution-alarm-notify-Message:  Tue Nov  9 00:00:00 2010

evolution-alarm-notify-Message:  Mon Nov  8 11:27:38 2010

** (update-notifier:1646): DEBUG: Skipping reboot required
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by Xoanan on 2010-11-08
The user name Beew found a workaround that worked for me; check his post in this thread

[http://ubuntuforums.org/showthread.php?t=1598591]("http://ubuntuforums.org/showthread.php?t=1598591")

Its post #7

---

### Post by newb_untu on 2010-11-08
Ok I apologize in advance for the clarification... but I'm very green with all of this.  

Regarding the workaround in the post you linked:

Step 1: remove all items in Synaptic beginning with nvidia?

Step 2: remove xserver-xorg... is that referring to xserver-xorg-core? There is no xserver-org (without some sort of suffix)... and I'm not certain what dependencies are.

Steps 4 and 6... not sure what/where the sources list is or how to refresh the repository (would help if I knew what it was)

---

### Post by dino99 on 2010-11-08
i think that compiz is to blame:

open synaptic (system admin synaptic) and search for "compiz": remove/purge (right click) all the related compiz packages installed. Then check that your problem is gone and reinstall compiz if you want it

note: dont remove nvidia or xserver-xorg-video-nvidia, or reinstall them immediatly

---

### Post by Xoanan on 2010-11-08
> **newb_untu said:**
> Ok I apologize in advance for the clarification... but I'm very green with all of this.  

Regarding the workaround in the post you linked:

Step 1: remove all items in Synaptic beginning with nvidia?

Step 2: remove xserver-xorg... is that referring to xserver-xorg-core? There is no xserver-org (without some sort of suffix)... and I'm not certain what dependencies are.

Steps 4 and 6... not sure what/where the sources list is or how to refresh the repository (would help if I knew what it was)

Hi There;

Regarding step 1: Yes, that's what I did;

Step 2 I think by removing xserver-xorg-core will remove most of the dependencies;  In synaptic, you can search for xserver-xorg and see what pops up;  anything you have installed will be checked.

Steps 4 and 6.

the file is located under etc/apt/sources.list.   You can use the terminal and navigate to it to make sure of its location(such as typing ```
cd /etc/apt
``` thereby changing the directories, then typing ```
ls
``` and finding the file name. 

You can edit the files by using nano, gedit, vi etc.
```
sudo nano /filename 
``` 


To move a directory, I believe its ```
 sudo mv /filename1 /filename2 
```

I recommend picking up a copy of the Ubuntu Toolbox as a nice desk reference for Bash(that's the lingo used in the terminal(command prompt)
Hope it helps

---

### Post by newb_untu on 2010-11-08
I removed everything related to compiz from Synaptic but the problem is still here...

---

### Post by newb_untu on 2010-11-08
Oh no...
 
I followed the workaround steps as best I could (I'm in 10.04 so my sources list had no reference to Maverick and so I left it unaltered) and now my computer won't boot into unbuntu even with using 'nomodeset'.  
 
Am I getting down to the point where a reinstallation of 10.04 is recommended to start fresh?  
 
I'm definitely going to pick up a copy of Ubuntu Linux Toolbox... any other suggested reading for a total novice?

---

### Post by Xoanan on 2010-11-08
> **newb_untu said:**
> Oh no...
 
I followed the workaround steps as best I could (I'm in 10.04 so my sources list had no reference to Maverick and so I left it unaltered) and now my computer won't boot into unbuntu even with using 'nomodeset'.  
 
Am I getting down to the point where a reinstallation of 10.04 is recommended to start fresh?  
 
I'm definitely going to pick up a copy of Ubuntu Linux Toolbox... any other suggested reading for a total novice?

I'm sorry;  I read the title, saw NVidia and immediately jumped to the conclusion that it was a Meerkat upgrade.  

What about recovery mode?  Does that appear as one of the options?

---

### Post by newb_untu on 2010-11-08
I have two recovery mode options (one for 2.6.32-25, one for 2.6.32-24... if I remembered the numbers correctly) and neither of them allow me to boot as well. I tried the recovery modes before having done the workaround and they didn't work then either.
 
I think I'm going to go ahead and try a fresh install.

---

### Post by newb_untu on 2010-11-09
Ok so I went ahead and reinstalled ubuntu clean and the first thing I did was install my ethernet driver to get my wired connection working.  The very next thing I did was to update the nVidia accelerated graphics driver and when I rebooted I got the black screen again.  I removed the driver and rebooted and I'm back to a normal boot.  The nVidia driver seems to be the issue.  Does this mean I won't be able to use the most up to date driver for my video card with ubuntu?

---

### Post by The Bird Man of Alcatraz on 2010-11-28
newb_untu,
 Are you using the Eee 1015pn, or 1215n?

The suggested solution here is in the BIOS.
[http://ubuntuforums.org/showthread.php?t=1616278&highlight=ion2](http://ubuntuforums.org/showthread.php?t=1616278&highlight=ion2)

If you have either one of those netbooks, it would be interesting to know if that option is available in your BIOS.  It's not totally convenient, but maybe it's a fix to a problem that many 1015pn and 1215n owners are having.

---


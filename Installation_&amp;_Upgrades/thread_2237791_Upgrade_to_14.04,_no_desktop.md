---
title: "Upgrade to 14.04, no desktop"
date: 2014-08-04
forum: Installation &amp; Upgrades
---

### Post by Xiguus on 2014-08-04
I have been running 12.04.5 with unity desktop, followed recommendation to install HWE enabler and lost my desktop, boots to black screen, recovery mode gives a terminal prompt.
Looked around and general advice is to install 14.04, which I did by 
```
sudo sed -i 's/precise/trusty/' /etc/apt/sources.list
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get upgrade
```
No dramas.
However, booting in standard mode gives me a message that the splash screen cannot be found, as a shared library is unavailable, and then proceeds to a terminal prompt, ie no desktop.
What can I do?
Thanks in anticipation...

---

### Post by Xiguus on 2014-08-04
Still trying to get this fixed, so I notice my MINT installation has a link /etc/X11/X -> /usr/binXorg which is missing from the 14.04. I make the link and boot, which gets me to the login screen (ie not the terminal prompt), which says the system is 12.04. 
Entering password returns a message 'login failure' and returns me to the login screen. Same with recovery-mode boot. 
I've removed the link and can now boot to a terminal (again) but, as I say, still trying to get it fixed...
Any help much appreciated.;)

---

### Post by Rob Sayer on 2014-08-05
```
sudo apt-get dist-upgrade
```

does not upgrade from one release to another.  It does updates where a program is replaced, not just updated.  This usually happens when a new kernel version is available.  This is why you're still running 12.04.

Do NOT extrapolate from a Mint system to a ubuntu one.  It's not the same DE and it doesn't use the same kernel as the ubuntu version it's based upon.

Here's a guide to apt-get:

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

But I wouldn't update that way myself.  I prefer to just get the iso live file and reinstall.  Fewer potential problems.

---

### Post by grahammechanical on 2014-08-05
This link shows how to upgrade from 12.04 to 14.04

[http://www.omgubuntu.co.uk/2014/04/upgrade-ubuntu-14-04-12-04](http://www.omgubuntu.co.uk/2014/04/upgrade-ubuntu-14-04-12-04)

Basically the command is

```
sudo update-manager -d
```

The command that you ran changed the sources list from precise to trusty. I used that command when 14.04 was released to move onto the 14.10 development branch. I do it every time a new development cycle begins but I do it during the first week of the development cycle when there are only minor differences between the code of the latest release and the development release that has just begun. I would not use your method of upgrading from 12.04 to 14.04.

Regards.

---

### Post by kansasnoob on 2014-08-05
> **grahammechanical said:**
> This link shows how to upgrade from 12.04 to 14.04

[http://www.omgubuntu.co.uk/2014/04/upgrade-ubuntu-14-04-12-04](http://www.omgubuntu.co.uk/2014/04/upgrade-ubuntu-14-04-12-04)

Basically the command is

```
sudo update-manager -d
```

The command that you ran changed the sources list from precise to trusty. I used that command when 14.04 was released to move onto the 14.10 development branch. I do it every time a new development cycle begins but I do it during the first week of the development cycle when there are only minor differences between the code of the latest release and the development release that has just begun. I would not use your method of upgrading from 12.04 to 14.04.

Regards.

But now that his sources are set to Trusty the "**[COLOR="#FF0000"]-d[/COLOR]**" will take him to Utopic!

Basically that was the wrong way to perform a release upgrade, no idea how someone would recover from that aside from a fresh install.

---

### Post by Xiguus on 2014-08-05
Thanks for the replies, it all helps.
Yes, I followed an instruction for MINT upgrade - oops.;)
I tried to fix the 12.04 HWE with
```
sudo update-manager -p 
```
from the terminal but got a failure message, no gui or somesuch. Obviously the wrong command.
I'll try
```
sudo update-manager -d
```
as you suggest; I've got no objections to Utopic if it will get my desktop back.
I have a backup sources.list for my 12.04, I can restore that if it will help, but I have an inkling it will be a waste of time (like, about 1½ hrs).
BTW, Grub sees a 3.13.0.32 kernel and my MINT install recognises 14.04.
Thanks again...

---

### Post by Xiguus on 2014-08-08
So I tried 
```

sudo update-manager -d

```
and got "GTK failed to initialise", which is no surprise because update-manager needs a gui.
Looking around I discover that 'do-release-upgrade' is the recommended command for the terminal, with the same switches as update-manager, ie[INDENT]-d       install development version ("unstable" release)
-p       install Ubuntu-proposed version (LTS?).
[/INDENT]
Accordingly
```

sudo do-release-upgrade -d -m desktop
No new version available
sudo do-release-upgrade -p -m desktop
No new version available 

```
I reinstate the precise source.list and try again, with the same result.
Maybe editing /var/lib/apt/lists as well will make it happen?
Alternatively, I may try booting with the 13.11.0.26 kernel still in the partition and seeing whether that forces the upgrade...
However, my understanding is that if the system will boot to a prompt it should boot to the desktop if all the components are available, so maybe it is a grub problem. I'll have a look around and see what I can find...
Cheerio for now...;)

---

### Post by Xiguus on 2014-08-11
I've been looking at what I have and am satisfied that 14.04 is the installed system. Attempts to repair this system by overwriting with another upgrade have failed and the errors introduced by the 12.04 HWE upgrade remain.
At the least this deleted my xorg.conf file and the link /etc/X11/X -> /usr/bin/Xorg. It may also have scrambled my grub.cfg, but that's not so obvious. As it stands I can boot to a prompt on tty1, which gives me access to the file system. 
Additionaly, I have reinstated xorg.conf by copying xorg.conf.failsafe and can, by making the link to Xorg, get to a login screen. Login via this screen fails with the message 'failed to load session "ubuntu"'. I can, however, Ctrl-Alt-F1 to a terminal, and other terminals are available on demand. 
The action plan is:[INDENT]verify that all necessary components are installed
repair configuration as required.[/INDENT]
Grub menu item is:
```

"Ubuntu, with Linux 3.13.0-32-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root __*lotsofnumbers*__
    linux /boot/vmlinuz-3.13.0-32-generic root=UUID=__*samelotsofnumbers*__ ro splash quiet $vt_handoff
    initrd /boot/initrd.img-3.13.0-32-generic

```
xorg.conf is:
```

Section          "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier      "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```

I also have:
```

lsmod  | grep -iE 'nvidia|fglrx|nouveau|radeon|i9'

```
returns nothing, although on my MINT installation it gives me
```

i915                           478689  7 
drm_kms_helper         46978    1 i915
drm                            241971  3 i915,drm_kms_helper
i2c_algo_bit                13423    1 i915
video                          19651    1 i915

```
I can see from the recent postings that there are quite a few other users who have had trouble with this particular upgrade so I will look through them and see if I can get some tips. Of course, If anyone can suggest a relevant shortcut, much appreciated ;);).
I'll also be taking a close look at my logs to see what they can tell me, but these can be very difficult to interpret. I'm still hopeful that I can get the upgrade to work and that I can get my previous workspace back again. I have backups for my user files and an package list so I can do a new installation if that is necessary, but I will still have to recompile my custom packages...

BR...
[INDENT]
[/INDENT]

---

### Post by Xiguus on 2014-08-13
The message
```

could not start boot splash: Can not access a needed shared library

```
refers to the boot splash, so it is very likely from plymouth. I have a plymouth log from before the HWE upgrade and this line is not present, so I have enabled plymouth logging for booting 14.04, by appending "plymouth:debug" to the linux line in the boot menu entry. Sure enough, the message is there, at line 83 ;).
Comparing the two logs I find that they are identical up to line 27. However, lines 24-26 read
```

[ply-utils.c]                               ply_open_module:Could not load module "/lib/plymouth/renderers/x11.so": /lib/plymouth/renderers/x11.so:[INDENT]cannot open shared object file: No such file or directory[/INDENT]
 __*blank_line*__
[./plugin.c]                                create_backend:creating renderer backend for device /dev/dri/card0
 
```
I check /lib/plymouth/renderers and find that X11.so is not present. Searching through dpkg tells me that x11.so belongs to the plymouth-x11 package, which is not installed. This error is obviously not critical because it didn't impede the boot for my 12.04 installation, but it might be good to install it anyway, just to keep things smooth. Maybe later...;).
For line 27 in 12.04 I have
```

[./plugin.c]                                   load_driver:Attempting to load driver 'i915'

```
which is good, while in 14.04 reads:
```

[./plugin.c]                                   load_driver:Attempting to load driver '(null)'

```
which is clearly the error I was looking for. It is followed by several more lines
```

[./plugin.c]                                   load_driver:drmOpen failed 
[ply-renderer.c]                             ply_renderer_open:could not open rendering device for plugin /lib/plymouth/renderers/drm.so 
[./plugin.c]                                create_backend:creating renderer backend for device /dev/fb0 
[./plugin.c]                                   open_device:could not open '/dev/fb0': No such file or directory 
[ply-renderer.c]                             ply_renderer_open:could not open rendering device for plugin /lib/plymouth/renderers/frame-buffer.so 
__*blank_line*__
[./plugin.c]                                   open_device:could not open '/dev/fb0': No such file or directory 
[ply-renderer.c]                             ply_renderer_open:could not open rendering device for plugin /lib/plymouth/renderers/vga16fb.so 
[ply-renderer.c]                             ply_renderer_open:could not find suitable rendering plugin 
[main.c]             add_default_displays_and_keyboard:could not open renderer /dev/fb 
[main.c]         add_display_and_keyboard_for_terminal:adding display and keyboard for /dev/tty7 

```
before the two logs align again.
What is interesting is that unlike x11.so the renderers referred to are all present.
OK, so dpkg tells me that i915 is a module in intel_drv.so, which is included in the xserver-xorg-video-intel-lts-trusty package, and which is is installed. My new job is to get this module loaded, and to resolve the problem with drmOpen...
As far as the splash-screen error message is concerned, I really can't say just yet which shared library it refers to, or whether it will need a separate fix. More later...
BR ;):p ...

---

### Post by Xiguus on 2014-08-15
Short story is that I've made some progress and have discovered that I need to manually install some (ie about 50) kernel modules left behind by the dist-upgrade. I've found some very useful tips here:  [INDENT][http://upstart.ubuntu.com/cookbook/upstart_cookbook.pdf](http://upstart.ubuntu.com/cookbook/upstart_cookbook.pdf)[/INDENT]
 which explains a lot about how the boot sequence is managed and the role of various components.
The nuts-and-bolts details are as follows:
I checked the boot.log and found the output corresponded to the screen messages following the splash screen failure message, ie post-plymouth. This began with 
```

fsck from util-linux 2.20.1 
VOLUME: clean, 395982/8323072 files, 3012827/33280647 blocks

```
and included numerous repetitions of "Starting bluetooth daemon", which is a nuisance as well as indicating a start failure. boot.log isn't rotated so I opened my MINT boot.log and compared them. The MINT log began with a number lines not included in the 14.04 log beginning with [ply-event-loop.c], which I assume originated in plymouth, and
```

Begin: Loading essential drivers ... done. 
Begin: Running /scripts/init-premount ... done. 
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done. 
Begin: Running /scripts/local-premount ... done. 
Begin: Running /scripts/local-bottom ... done. 
done. 
Begin: Running /scripts/init-bottom ... 

```
I'm thinking that this is promising, although I can't assume that just because these lines are in MINT but not 14.04 that this is related to the boot error, it may simply be that they are set to log different events. Anyway, init-premount &c reside in /etc/initramfs-tools/scripts and /usr/share/initramfs-tools/scripts, and the logged lines come from /usr/share/initramfs-tools/init. This is the shell script which executes the first stage of the boot sequence. Suffice to say that it is identical in both distributions.
The MINT boot.log has the fsck and VOLUME lines as for the 14.04 boot.log but diverges substantially in its subsequent load history. However, I have drm debugging enabled in MINT but not in the 14.04, and I want to know whether the initramfs sequence for the 14.04 boot can be viewed. I edit its grub menu entry to read
```

linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=*__lotsofnumbers__* ro   splash quiet $vt_handoff drm:debug 0xe

```
The new boot.log differs in a number of details from the unenhanced log but doesn't include the init script execution lines given in the MINT boot.log. Clearly, they do not originate with drm. 
I put this matter on hold while I gave some attention to the bluetooth problem. Having the load/start command issued repeatedly is not satisfactory because it is clearly failing. It may be interfering with other tasks and in any case there is no need for it to be available so early in the startup sequence. It was while looking for a solution to this issue that I was directed to the upstart tool. 
Upstart takes over from initramfs after the kernel modules have been loaded and implements the services they specify. In particular, upstart manages the directories and resources under /etc/init, including the init shell script. The caveat is that modules have to exist on the system in order to be managed, and /etc/init contains conf files, not modules.
Items in the boot.log are there courtesy of upstart and upstart provides the methods for enabling and disabling loadable modules. 
Two methods are suggested:[INDENT]change the name of the module's conf file to a suffix other than .conf
comment-out the "start on" line in the module's conf file.
[/INDENT]
as far as bluetooth is concerned, I will be using the second method.
The other half of current developments is rather more succinct. /lib/modules contains a directory for 3.11.0-26-generic, which is the HWE update, and 3.13.0-32-generic, which is the 14.04 upgrade. Each has subdirectories /kernel/drivers. For the 3.11 installation /drivers contains 74 items, including /gpu/drm/i915/i915.ko; for the 3.13 installation /drivers contains 21 items, not including /gpu... 
I have some work ahead of me. I can't anticipate imminent success, however, because the 3.11 installation won't boot-to-desktop either...
BR ;)...

---

### Post by Xiguus on 2014-08-19
I've now installed kernel 3.13.11 onto the distribution and can boot to a blank blue desktop screen, which is the same boot state as the 12.04 HWE kernel. 
In the sense that this is no longer an upgrade issue but a desktop (or possibly boot?) issue I'm of the view that the problem motivating this thread has been solved. I'd like to mark it as such, but I don't know how ;). 
I'll continue to work on this til I can get a working installation again, and am basically pretty happy that I don't (yet?) have to do a clean install and blitz my current software. 
One feature of the whole business that still puzzles me is that my system clock has been clutzed and these kernels boot with time set to 10 hours ahead. I know that some system operations need a properly-set clock, so this is something else I need to track down.
Anyway, I'm iving myself 6½/10 and hoping that the next stage will be a lot less stressful ;).
BR...

---

### Post by Xiguus on 2014-08-30
Just to wrap this whole thing up, I've abandoned the idea of making the new kernels work with the old setup and will be doing a new install to a full 14.04. Not so good, because I have to reinstall my custom software (eg imagemagick with fft, sage, texlive) but still cost-effective. I will mark the thread as "solved", although it is actually a meta-solution and not a corrective solution.
BR...;)

---


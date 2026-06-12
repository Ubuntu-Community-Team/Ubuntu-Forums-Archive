---
title: "Today's Kernel update broke xorg"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by pizzutz on 2007-09-03
Did anybody else have a problem with the recent kernel update?  It broke my X.  I tried twice to reboot after I updated, only to get the "xserver failed to start would you like to view the log" text based dialog box.  When I told grub to use the old kernel, I booted up fine.  This has happened before, but usually I can find a post on this forum with the reason.  I am not posting my specs or log messages at the moment cause It is late, I don't want to deal with this until tomorrow, and It's not a problem I can't deal with. I was just wondering if anyone else had the same problem.

I will say I am running an nvidia 5200 chipset with nvidia-glx-new driver installed from the multiverse repos.

I've got some googleing and patch note reading to do tomorrow to figure out my problem, I may just have a funky setup.  I'm not a newb looking for help, just simply wondering if anybody else had a problem.

---

### Post by PmDematagoda on 2007-09-03
I've had the same problem once, I fixed it by first trying to reconfigure xorg.conf, after that didn't work I used my backed up xorg.conf and it worked, why don't you first try reconfiguring xorg.conf through the recovery mode of the problem kernel?

---

### Post by pizzutz on 2007-09-03
I will try it, at the moment. I'm not even exiting into a usable terminal, though I'm sure I can switch to tty1 for one. I'm not getting an xorg.conf error though, I'm getting a failed module load. module "wfb" is not being found. I'm not sure what that is off the top of my head. Strange, though that this new kernel would not have support for a module that was there before.  Something else is wrong, I'm just not sure what yet.  Funny thing, though I was hanging out with  my only rl friend who also runs ubuntu linux tonight, and we talked about the kernel update which I hadn't installed at that point.  We were both saying we hate to install them till we have check the forums and/or wait a few days, but he installed it with no problems.  I need to check the patch notes and find out what that module is.

---

### Post by PmDematagoda on 2007-09-03
Am I right in assuming that the kernel update was 2.6.20-16?

---

### Post by pizzutz on 2007-09-03
yeah 2.6.20-15 boots fine. -16 is currently giving me a headache  I've got the source for 2.6.23-rc3 on my drive, I'm tempted to update the git for rc5 from linus' tree and recompile with my config file to see what that one does.

---

### Post by pizzutz on 2007-09-03
Ok, apparently it's just me.  That's what I needed to know.  I will fix it.

---

### Post by andylawrence on 2007-09-03
I think it's an ID10T problem

---

### Post by pizzutz on 2007-09-03
Thanks, Andy.  Very constructive :P

no, there is something screwed up with my modules.  I'll fix it manually when I get home from work tonight.

---

### Post by soma4me on 2007-09-07
Hi,

I finally fixed the problem by re-installing the restricted modules for 2.6.20-16.   Here is what I learned:

If nVidia driver is giving you trouble and you 'need' to get into GDM, you can simply change the driver definition in xorg.conf file from 'nvidia' to 'nv'.   Here is how:

(I'm using root terminal, if you are using regular terminal then you need to add 'sudo' in front of every command except 'cd')

```
cd /etc/X11/
cp xorg.conf xorg.conf.backup
vi xorg.conf
```

Then find the following section:

S```
ection "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7300 GT]"
    Driver         "nvidia"
    Busid          "PCI:1:0:0"
EndSection
```

and change it to:

```
Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7300 GT]"
    Driver         "[COLOR="Red"]nv[/COLOR]"
    Busid          "PCI:1:0:0"
EndSection
```

You now should be able to boot into the new kernel in normal mode.   NOTE: since you are now not using restricted module, your OpenGL application (such as the screen saver) will not work properly, and you refresh rate may be limited.

To permanently fix the driver issue, you need to first boot into the recovery mode from GRUB menu.    At command line, do the following:

```
apt-get update
apt-get install --reinstall linux-restricted-modules-2.6.20-16-generic
```

now you can boot into the new kernel normally :)

Hope this help.

---


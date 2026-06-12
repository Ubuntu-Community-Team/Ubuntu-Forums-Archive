---
title: "Found and fixed problem with xserver-xorg-core update and nvidia drivers on Feisty"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by oscarsfriend on 2008-01-18
Hi,

I just thought I'd post this here in case anyone else has had the same problem, and hasn't figured out how to fix it yet.  I installed the xorg update to day, and discovered that it broke my nvidia drivers (installed from nvidia's website).  Everything seemed OK until I ran MythTV and it restarted the X server and logged me out.  Running glxinfo/glxgears or anything else like that caused the same thing to happen.  The solution was to shut down the x server and reintall the drivers, after that everything worked fine and dandy (remember not to write over your working xorg.conf file).

The only thing to note was that during the reinstallation I got this error message, which I have never seen before:

```

ERROR: File '/usr/lib/xorg/modules/extensions/libglx.so' is not a symbolic link.

```

One of these days I'm going to install the drivers out of the restricted repos, so I don't have to go through all this everytime I update the kernel or xorg.  ;) EDIT: I tried that and [bad things happened](http://ubuntuforums.org/showthread.php?t=671160) (which took some effort to fix), so I won't be trying it again in a hurry!

---

### Post by oscarsfriend on 2008-01-18
Just a quick update for anyone else having this problem.  It seems the problem is that updating the xserver-xorg-core package overwrites a symbolic link to the nvidia drivers when you update with a file of its own.  All that is needed to fix this is to remove the appropriate file and reinstate the symlink, rather than reinstalling the drivers.  The file in question is /usr/lib/xorg/modules/extensions/libglx.so, which should link to your nvidia driver in the same directory, which should have a name of the form libglx.so.[somenumbers].  Mine is libglx.so.100.14.11.  Just symlink libglx.so to that file, and hopefully all should be working again.  (You may or may not have to reboot first.)  WARNING: make a backup of libglx.so before removing it, in case you need to copy it back again!

Also, see this thread where I figured it all out (a gutsy user had the same problem and my fix worked for them): [http://ubuntuforums.org/showthread.php?t=671261](http://ubuntuforums.org/showthread.php?t=671261)

NOTE: You may well have to do this again after updating to the fixed version of xserver-xorg-core, that is currently being placed in the repos.

---

### Post by Holge r on 2008-01-18
Just to let you know. The update caused also problems with Thinpad X60 with Intel 945G grafic Chipset. So it will be not only related to Nvidia cards.

---

### Post by oscarsfriend on 2008-01-18
When you get the time (I saw your post on launchpad ;) ) take a look and see if the same symlink problem is affecting you (I guess there may be a symlink to your intel drivers in the same place).  If all else fails try reinstalling your drivers.  Let us know what you find, it might help someone else.

---

### Post by Requiem on 2008-01-18
The xserver core update is throwing me a 403 Forbbiden error, care to look at it?

---

### Post by oscarsfriend on 2008-01-18
The update to xserver-xorg-core is now working (at least for feisty), and I have installed it.  I can confirm that it once again overwrites the symlink I mention above, and you will have to fix it by hand:

```

$ cd /usr/lib/xorg/modules/extensions/
$ sudo ln -s libglx.so.100.14.11 libglx.so

```

This did the trick for me.  You will have to replace libglx.so.100.14.11 with what ever file it is you need to link to in /usr/lib/xorg/modules/extensions/.  

Now, I believe there is a way to stop updates overwriting particular files.  Anyone know how you get this to work?  We should be able to stop the symlink being overwritten in future.  (It will no doubt happen again when the real update is put up -- the current update is really just a downgrade to the previous working version, as far as I know, but with the version number of the package increased rather than decreased.)

---

### Post by Requiem on 2008-01-18
thanks for the tip, still I yet have to get the update first. I get:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb)
  403 Forbidden

---

### Post by oscarsfriend on 2008-01-18
That file is the wrong one.  You want: [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.2_i386.deb)

You should be able to update through your package manager.

---

### Post by oscarsfriend on 2008-01-18
OK, people! I have tracked down the command which should stop an update overwriting that symlink to your graphics driver.  Anyone brave enough to try it before updating?

This should do the trick:
```

sudo dpkg-divert --add /usr/lib/xorg/modules/extensions/libglx.so

```

When you update the xorg package, the file should be renamed to /usr/lib/xorg/modules/extensions/libglx.so.distrib instead of overwriting the symlink.

I got it from this unrelated thread (way down near the bottom of the first post): [http://ubuntuforums.org/showthread.php?t=369596&highlight=firefox+widgets](http://ubuntuforums.org/showthread.php?t=369596&highlight=firefox+widgets)

EDIT: if this doesn't work, you should be able to undo the divert with:
```

sudo dpkg-divert --remove /usr/lib/xorg/modules/extensions/libglx.so

```
Then try removing and installing the update again.

EDIT: According to [someone on the bug report page on launchpad](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969/comments/65), the fixed version of the original update is due to be released "shortly", which should fix the problems that should have been fixed in the previous update, but which were unfixed in the update to the update, which wasn't really an update at all, but a downdate.  Confused?  You will be!  (That's my way of saying that I'll give it a try when I update later today/tomorrow.)

UPDATE: I couldn't seem to get this divert thing working.  It maybe because I tried something more complex than the above command, and messed it up.  Anyway, after the update I ended up having to delete the file and reinstating the link again.  I removed the divert as well.  If anyone else had any better luck with this, do let us know.

---

### Post by endo on 2008-01-18
> **oscarsfriend said:**
> The update to xserver-xorg-core is now working (at least for feisty), and I have installed it.  I can confirm that it once again overwrites the symlink I mention above, and you will have to fix it by hand:

```

$ cd /usr/lib/xorg/modules/extensions/
$ sudo ln -s libglx.so.100.14.11 libglx.so

```

This did the trick for me.  You will have to replace libglx.so.100.14.11 with what ever file it is you need to link to in /usr/lib/xorg/modules/extensions/.  

Now, I believe there is a way to stop updates overwriting particular files.  Anyone know how you get this to work?  We should be able to stop the symlink being overwritten in future.  (It will no doubt happen again when the real update is put up -- the current update is really just a downgrade to the previous working version, as far as I know, but with the version number of the package increased rather than decreased.)

Thanks a lot! This really solved the problem for me. :)
I would have tried to reinstall the driver,  but I would NEVER have guessed that the installation of xserver-xorg-core replaces the symlink with its own file! Quite tricky. ;)

---

### Post by HaguMe on 2008-01-19
Well, I have Feisty with an 7600gs nVidia card, and I had the same problem.

But, instead of fixing it with the method u posted in this thread, I did the following:

- Logging with xterm
- Open firefox and download the latest [nVidia driver](http://www.nvidia.com/object/linux_display_ia32_169.07.html)
-  apt-get dist-upgrade to automatically dl the latest update of the xserver-xorg-core
- CRTL+ALT+F1, and stop gdm and reinstall the driver.
- I know it appears "ERROR: File '/usr/lib/xorg/modules/extensions/libglx.so' is not a symbolic link." but I ommited it, and the nvidia installer seemed to fix it by itself.
- reboot X

And that was all...

Perhaps your solution is the best, but I didn't want to risk too much, I'd rather prefer that known method.

To all of you... I hope this works!

Sorry for my bad english,

Greetings.

---

### Post by jhetrick62 on 2008-01-20
I had the same issue after xserver-xorg-core update today and found this information on the nvidia forum helpful.  In my case, especially the red lines that I found I had to do.  It now works fine with the new xserver-xorg-core and the most recent NVIDIA driver 169.07.

<<
If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and[COLOR="Red"] xserver-xorg-dev packages are installed[/COLOR]
    * the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and [COLOR="Red"]/etc/init.d/nvidia-kernel do not exist[/COLOR]

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or [COLOR="Red"]/etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv nvidia_new"[/COLOR]

Additionally, delete the following file if it exists:

    /lib/linux-restricted-modules/.nvidia_new_installed
>>

Hope this helps
Jeff

---

### Post by olavjunior on 2008-01-21
> **jhetrick62 said:**
> I had the same issue after xserver-xorg-core update today and found this information on the nvidia forum helpful.  In my case, especially the red lines that I found I had to do.  It now works fine with the new xserver-xorg-core and the most recent NVIDIA driver 169.07.

<<
If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and[COLOR="Red"] xserver-xorg-dev packages are installed[/COLOR]
    * the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and [COLOR="Red"]/etc/init.d/nvidia-kernel do not exist[/COLOR]

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or [COLOR="Red"]/etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv nvidia_new"[/COLOR]

Additionally, delete the following file if it exists:

    /lib/linux-restricted-modules/.nvidia_new_installed
>>

Hope this helps
Jeff

Great! Worked perfect :) You saved my day!

---

### Post by emwine on 2008-01-21
First, thanks for this thread.  It took me a while to locate it, but in the end, it saved my system.

Second, this kind of stuff really makes me seriously consider disabling updates entirely.  I went through an hour of hell after this problem started, and blood pressure through the roof.

---

### Post by jhetrick62 on 2008-01-21
I have not had any issues with updates other than video driver type of updates.  Video is one of the most intricate parts of Linux as the drivers are not standardized.  My advice would be to notice when there is a video update in the package and run it separately, collecting your current information before hand so that you can quickly revert in the event of an issue.

Also, apply a video update about 1 week after you first see it as you can then search and read these things BEFORE you apply and know what you are up against.

Goodluck,
Jeff

---


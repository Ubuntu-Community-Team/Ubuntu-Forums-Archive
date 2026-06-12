---
title: "Help installing sudo sh NVIDIA-Linux-x86-256.53.run"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by hihihi100 on 2010-09-14
Hiya:

Im having problems to install the amentioned .run file. I always get:

```
ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at www.nvidia.com.

                                       OK  

```

and

```
 ERROR: Installation has failed.  Please see the file
         '/var/log/nvidia-installer.log' for details.  You may find            
         suggestions on fixing installation problems in the README available   
         on the Linux driver download page at www.nvidia.com.

                                       OK  

```

I have tried to turn off the x server via both /etc/init.d/gdm stop and ctrl-alt-backspace, but I always get the same result. In the first option, I get:

```
hihihi100@hihihi100-laptop:~/Downloads$ /etc/init.d/gdm stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service gdm stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop gdm
stop: Rejected send message, 1 matched rules; type="method_call", sender=":1.62" (uid=1000 pid=2722 comm="stop) interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

```

tips please

---

### Post by alarme on 2010-09-14
Try:

$ sudo /etc/init.d/gdm stop

or

$ sudo stop gdm

---

### Post by vortmax on 2010-09-14
Stupid question....you are using ubuntu/gnome right?  If you are using KDE (kubuntu), you need to do:

sudo stop kdm

Just a quick heads up though, if this is Lucid, that driver install package won't work...there is a bug with it.  You need to install it through the system panel in gnome or kde.

---

### Post by hihihi100 on 2010-09-15
Not a stupid question for a noob like me...

Anyway, I found [http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368) and followed its instructions, restarted x withour problems, and now I can activate the extra visual effects and the resolution is back to normal.

However, there is something I cannot understand:

System-Administration-Hardware drivers, please take a look at the uploaded screenshot. 

Activated but not in use? What drivers am I using then?

cheers

---

### Post by jimbo99 on 2010-09-15
The list of drivers you are pointing out are those provided by Canonical.  The driver you describe installing you downloaded directly from nVidia.  nVidia's installer knows nothing about those drivers provided by Canonical.

The drivers found in the location you are pointing out are usually a couple generations old.  They may also create problems if you install them and then try to install nVidia's drivers (maybe not the way it is today but in the past you could make it impossible to use nVidia's drivers if you had one or more of those drivers installed via Canonical's optional hardware drivers).

You ran into a dual issue.  1) after doing a kernel update you lost your ability to start X normally.  And 2) when trying to update those drivers you had X running.  Doing the sudo stop gdm or sudo stop kdm solved issue #2.  But as far as #1 goes the issue is with how kernel modules are loaded on a kernel by kernel basis in Linux.

Those drivers you listed are part of the solution to #1.  Having them installed gives you access to the 3d acceleration, etc., and the next time you update your kernel you shouldn't be required to reload the drivers.  The drawback is that those drivers are often older.  

BUT, in your case, because you downloaded the nVidia drivers and ran through the install, any time you update your kernel, you will need to re-invoke that installer to get the kernel module to load again.

It's a trade-off.  I use the drivers downloaded from nVidia's site.  (Personally, I like to ensure I have current drivers.) The drivers provided by Canonical are not that old and most of the newer drivers released by nVida probably don't add much functionality to my video cards (because their drivers are very mature).  I could live with the Canonical drivers and not feel as if I am missing anything.  And yes, it is a pain to have to stop your X session to install drivers at the command line.  Don't get me wrong, the command line is a convenience that I would never give up.

---

### Post by efflandt on 2010-09-15
The most recent nVidia version installed by hardware driver (at least in my 64-bit 10.04) is 195.36.24.  If you had used that instead it would automatically still work after any kernel updates.

Instead you installed and are using a newer v256.53 direct from nVidia which Ubuntu Hardware Drivers would not know about (hence "not in use"), and you might need to redo after any kernel updates.

Not sure what you gain from the newer driver, which may depend whether your video chip was fully supported be earlier drivers or not.  I have not done much gaming in Linux yet (anyone know any good games).  But for Battlefield Bad Company 2 in 64-bit Win7 I had to update nVidia driver from 186(?) to 258.96 for directx 11 to work properly for GT220 (although directx 9 had no problems and has higher frame rate).

---

### Post by Claus7 on 2010-09-15
Hello,

just one question: why these drivers (from Canonical) do not seem to be activated (on the fig given above)?

Is it because the proprietary drivers were installed, or for some other reason?

Regards!


EDIT: Think this is the answer I was looking for:
If the restricted driver remains unactivated after attempting to activate it in the Hardware Drivers dialog, you may not have the appropriate linux headers installed to compile the driver. Ensure that the linux-headers-XXX and linux-restricted-modules-XXX packages are installed, where XXX matches the version of the kernel you are using (linux-image-XXX). 

from [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
and
[http://ubuntuforums.org/showthread.php?p=2467633](http://ubuntuforums.org/showthread.php?p=2467633)

---

### Post by postenga on 2010-09-15
The Simple way :

1.sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

2.sudo apt-get update

3.sudo apt-get upgrade

* 260.19.04 version

---


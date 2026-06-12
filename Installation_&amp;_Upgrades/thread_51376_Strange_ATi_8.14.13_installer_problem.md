---
title: "Strange ATi 8.14.13 installer problem"
date: 2005-07-23
forum: Installation &amp; Upgrades
---

### Post by smiley2billion on 2005-07-23
Hello all, this is my first post to these forums that I use so much to help with getting everything running on Ubuntu.

I started using ubuntu about a month ago and now my friend wants it installed on his AMD64 system.  We tried a few things last night with the actual x86_64 version but decided it would be best to use the x86 version instead (because we couldn't get much running without a huge hassle).

I've installed Ubuntu 5.04 (x86) on here now and it seems to be running ok.  I've managed to get flash running in firefox (something I could not do on the AMD64 version) so I would suspect that this would be a lot easier to get things like wine up and running for him. 

When I got around to installing the new ATi drivers (8.14.13) with their new GUI installer something strange happend.  I went thru the process just I did on my machine (we both have Radeon 9800 Pros) and as I did last night with the AMD64 build where you download the file via wget and then run the sh script with sudo, except that on here it now does NOT load the gui, instead loads to a console based installer screen which seemed like it would work because it still contains all the same options as the GUI version, however it installs the driver (or it says it did) and exits with a final screen saying that it had errors and to check the log.  Here's the output from the log:

```
[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Error] Kernel Module : No kernel module build environment - please consult readme.
``` 

When I start the installer here's the text output before entering the NONgraphical installer:

```
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: Xorg 6.8.2
``` 

Not sure if the above will help anything, I'm just trying to be as detailed as possible.

Please also note that on this exact same system with the AMD64 build this exact same driver install with over smoothly and worked. (glxgears fps was around 3200, now its some where around 150)

Also, I could be considered a linux n00b :D  because I've only been using this for about a month.  I do learn fast, but just try to be detailed with an answer to this problem. TIA!!!

---

### Post by PeP on 2005-07-23
[QUOTE=smiley2billion]Hello all, this is my first post to these forums that I use so much to help with getting everything running on Ubuntu.

I started using ubuntu about a month ago and now my friend wants it installed on his AMD64 system.  We tried a few things last night with the actual x86_64 version but decided it would be best to use the x86 version instead (because we couldn't get much running without a huge hassle).

I've installed Ubuntu 5.04 (x86) on here now and it seems to be running ok.  I've managed to get flash running in firefox (something I could not do on the AMD64 version) so I would suspect that this would be a lot easier to get things like wine up and running for him. 

When I got around to installing the new ATi drivers (8.14.13) with their new GUI installer something strange happend.  I went thru the process just I did on my machine (we both have Radeon 9800 Pros) and as I did last night with the AMD64 build where you download the file via wget and then run the sh script with sudo, except that on here it now does NOT load the gui, instead loads to a console based installer screen which seemed like it would work because it still contains all the same options as the GUI version, however it installs the driver (or it says it did) and exits with a final screen saying that it had errors and to check the log.  Here's the output from the log:

```
[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Error] Kernel Module : No kernel module build environment - please consult readme.
``` 

When I start the installer here's the text output before entering the NONgraphical installer:

```
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: Xorg 6.8.2
``` 

Not sure if the above will help anything, I'm just trying to be as detailed as possible.

Please also note that on this exact same system with the AMD64 build this exact same driver install with over smoothly and worked. (glxgears fps was around 3200, now its some where around 150)

Also, I could be considered a linux n00b :D  because I've only been using this for about a month.  I do learn fast, but just try to be detailed with an answer to this problem. TIA!!![/QUOTE]
 > [Error] Kernel Module : No kernel module build environment - please consult readme.
what does Readme says,then ??

what is your kernel version?? (uname -r)

if you can't fix it you might want to use the ati drivers provided with ubuntu in the linux-restricted-modules package

---

### Post by KaiAllard on 2005-07-24
I have exactly the same problem... But I guess you are lucky because you only have a 9800. Just get via apt-get your Radeon driver (xorg) and get fglrxconfig ready ... that must be all you have to do... 

If anyone knows how to solve a driver problem with X800 please look at this thread I have posted... Thank you in advance

[http://www.ubuntuforums.org/showthread.php?p=269368#post269368](http://www.ubuntuforums.org/showthread.php?p=269368#post269368)

---


---
title: "video drivers not found"
date: 2014-03-16
forum: Installation &amp; Upgrades
---

### Post by salty2 on 2014-03-16
I have been following this post-install checklist.

[http://debianhelp.wordpress.com/2013/11/19/to-do-list-after-installing-ubuntu-13-10-aka-saucy-salamander-os-2/](http://debianhelp.wordpress.com/2013/11/19/to-do-list-after-installing-ubuntu-13-10-aka-saucy-salamander-os-2/)

Until I got the the section "[B]Video Drivers and Proprietary Drivers Check (Required):"

[/B]I found no additional drivers using the gui tool.  So I followed the remaining instructions which led me here:

emcee@hammer:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.3, 128 bits)
OpenGL version string:  2.1 Mesa 9.2.1

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

emcee@hammer:~$ lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Hawaii XT [Radeon R9 290X] [1002:67b0]
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:0b00]
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:aac8]
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:aac8]

I tried using some other guides (as below) to upgrade the drivers via command line, and in each case, rebooting left the system unable to use the video card - "low graphics mode"
[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

Help?

---

### Post by QIII on 2014-03-17
The R9 series (all the Rx series, in fact) are very new and a suitable driver is not found in the Saucy repo.

AMD's [14.2 Beta]("http://support.amd.com/en-us/kb-articles/Pages/latest-linux-beta-driver.aspx") ***may ***work, but I have seen many posts where people have still had problems.  I don't have one of these newer GPUs, so I have not been able to test them personally.  Also, bear in mind that it is a beta, not a final release.  I can't vouch for its behavior as a beta!

You will have to install that driver manually by doing one of the following, if you haven't yet tried them *with 14.2 Beta*. If you have tried them, then I can't help.

 In either case, make sure you are downloading the desired driver and take care to change the version names in the commands:

1. Create a .deb file as described in the wiki you referenced at "3. Installing upstream drivers directly from AMD's website".  I see one error, though.  Instead of using ```
sudo aticonfig --initial
```
 which had been deprecated, use
```
sudo amdconfig --initial
```
which is now preferred.  I'll try to correct that some day soon for whoever wrote that section of the wiki.  It's a relatively new change.

or 

2. Install directly from the .run as described in "3.2. Manually installing Catalyst 13.4, special case for Intel/AMD hybrid graphics"  (you can install it this way even if you don't have hybrid graphics and some things have changed in newer versions (lord, I need to update that section of the wiki!).).  Also note that for the second method I have specified that you MUST use ```
sudo amdconfig --uninstall
``` if you install this way and later want to uninstall.  Also, this method will NOT automatically update the driver through your package manager.

Of the two methods, the first is preferable.  As I say in the wiki, the second is really not recommended.

Again, though, if you tried these methods specifically with the beta driver it may simply be that the GPU is too new for AMD to have provided the Linux community with a working driver and I'll have to buy one to work out the kinks when one becomes available.  (Mrs. QIII sometimes gets grumpy with me when I suggest that I need to do this for the Ubuntu community, though!  She thinks I just want new toyz, which I do!)

---

### Post by salty2 on 2014-03-17
Thanks so much to you and Mrs. QIII!  

I had tried installing the beta driver as well as the stable released driver.  Both gave me the same result.  However, during beta installation I did use the aticonfig command instead of amdconfig.  I got an error and simply moved on to reboot hoping for the best.  Do you think it's worth to try again with amdconfig?  If I don't hear otherwise by 9p est, I'll give it a shot and post results here.

---


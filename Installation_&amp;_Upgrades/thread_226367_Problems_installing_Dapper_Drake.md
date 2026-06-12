---
title: "Problems installing Dapper Drake"
date: 2006-07-31
forum: Installation &amp; Upgrades
---

### Post by JJKebab on 2006-07-31
I am trying to install the latest version from CD. Have used the check CD feature and everything is fine.

After the splash screen and loading of a few modules the screen goes blank and the monitor tells me the input is out of range.

I have a GeForce 4400 AGP card (I think!) and am sure it has something to do with this. I have tried every combination of video mode from the initial menu (including VGA Safe mode). None of them work.

I would appreciate it if someone could tell me how to reconfigure the install so this does not happen and I can complete installation. I had this problem a long time ago with a SUSE install on the same machine, but the latest version of SUSE installs fine.

I really hope someone can help me because I'd rather be running Ubuntu the SUSE. I did search these forums for a solution but have not found anything.

---

### Post by adamkane on 2006-07-31
Your screen resolution is too high. Choose 1024x768 during install to be safe.

---

### Post by JJKebab on 2006-07-31
As I mentioned above, I have tried every single different resolution including VGA safe mode and it still happens.

---

### Post by adamkane on 2006-07-31
Here's a howto:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

This guy is the resident nvidia expert:
[http://www.ubuntuforums.org/member.php?u=19388](http://www.ubuntuforums.org/member.php?u=19388)

---

### Post by taurus on 2006-07-31
Or you can install Dapper with the alternate CD!  Don't worry about the desktop verison (LiveCD) then.

---

### Post by JJKebab on 2006-07-31
What's the difference between the Alternate CD and using the text install mode on the live CD?
I did use the text mode to install, but once rebooted to load the system for the first time, the screen goes blank after a few seconds (when loading the desktop I guess).

I only ask because it would be a real shame to download the ISO and then find I have exactly the same problem!

Thanks in advance.

---

### Post by taurus on 2006-07-31
Not much besides the desktop will boot up as LiveCD first and if you want to install it, you double click the install icon.  For alternate CD, you boot directly into the installer with text base so if you are having problem booting into LiveCD (with the desktop version), you should try the alternate CD.  They both come with the same stuff so no need to worry about if you are missing out something using the alternate CD.  And of course, you can always use apt-get/aptitude/synaptic to install whatever else you want...

---

### Post by JJKebab on 2006-07-31
OK. I get that.

But, if I am able to install using the text installer on the live CD and there is no difference between doing that and booting from the Alternate CD then using the Alternate CD would not help me.

After using the text installer, files are copied and then the system reboots to load the system. The screen then goes blank when the desktop is loaded.

I would assume, therefore, that the installer on the Alternate CD would be no different and so the same would happen.

Unfortunately the nVidia expert is not online so I am very stuck at the moment. I was hoping that there would be a simple solution to what is actually a very small problem.

---

### Post by az on 2006-07-31
> **JJKebab said:**
>  The screen then goes blank when the desktop is loaded.

I would assume, therefore, that the installer on the Alternate CD would be no different and so the same would happen.


Yes, but you can play around with it more.

boot into recovery mode, run
dpkg-reconfigure xserver-xorg
and try using the vesa driver.

Run 
init 2
to get into desktop mode.  Try again if it doesn't work.  Try different resolutions and so forth.

Once you can figure out what the problem is, you can file a proper bug report.  I had probelms with a certain combination of video card and LCD monitor.  It worked fine with another monitor or another video card.  It's just one of those things.

---

### Post by JJKebab on 2006-07-31
Kudos azz. I knew there would be a way to reconfig. Will try it, thanks.

---

### Post by yccheok on 2006-08-06
Hello, I am having similar problem as you when I try to install my Ubuntu with video card NVIDIA GeForce MX440 With AGP8x, monitor SAMSUNG SyncMaster 710v. 

At first, I thought that is my video card problem. I had tried a lot of alternative, editing xorg.config, getting the lastest nvidia driver..... all just won't work

I even try to refering the works by others

[http://www.ubuntuforums.org/archive/index.php/t-81818.html](http://www.ubuntuforums.org/archive/index.php/t-81818.html)
[http://www.ubuntuforums.org/showthread.php?t=190036&highlight=blank+screen](http://www.ubuntuforums.org/showthread.php?t=190036&highlight=blank+screen)
[http://www.ubuntuforums.org/showthread.php?t=191538&highlight=blank+screen](http://www.ubuntuforums.org/showthread.php?t=191538&highlight=blank+screen)
[http://www.uberdose.com/kbase/ubuntu-and-nvidia-geforce-6600/](http://www.uberdose.com/kbase/ubuntu-and-nvidia-geforce-6600/)
[http://www.nvidia.com/object/linux_display_ia32_1.0-8762.html](http://www.nvidia.com/object/linux_display_ia32_1.0-8762.html)

they won't work either for my case too.

[B]Soon, what I try to do is use an old CRT monitor. Then, the installation process just work like a charm. Before, I switch back to my 17" LCD monitor, I just ensure the default screen resolution is set to 1024x768 @ 60Hz
[/B]

Now, my ubuntu can run on my machine with no problem :)

---


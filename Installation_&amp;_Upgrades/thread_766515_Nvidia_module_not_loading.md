---
title: "Nvidia module not loading"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by Dabbill on 2008-04-25
I have been trying for several hours to get my nvidia driver to work. I have tried seing installer straight from nvidia.com, envyng, and just installing nvidia-glx-new from command line. Nothing will work. Every time I boot the computer it comes up with the low-graphics screen.

Here is pastbin of my log file.
[http://paste.ubuntu-nl.org/64353/](http://paste.ubuntu-nl.org/64353/)

---

### Post by howlingmadhowie on 2008-04-25
according to your logfile, you appear to still be using the vesa driver.

which nvidia card do you have? if you have an older card, you could try installing the older driver and then enabling it in the driver management section under system->administration.

also, download nvidia-settings so you can increase the resolution.

---

### Post by Archmage on 2008-04-25
This looks like the usual xorg-autoconfiguration that is new since Hardy. :(

Try to insert loading the driver nvidia manual into your xorg.conf.

---

### Post by Malfet on 2008-04-25
> **howlingmadhowie said:**
> according to your logfile, you appear to still be using the vesa driver.

I have exactly the same problem - nothing is working with NVidia in 8.04, while in 7.10 I had no problems with hardware at all. vesa driver is suggested by the system everytime it can't detect a graphic card properly.
Envy even recognize the graphic card, but still nothing is working.
Looks like I did a big mistake with the update. What the point to use new version of OS when is has much worse hardware support then a previous one? :(((

M.

---

### Post by Dabbill on 2008-04-25
I have a 8800GT. When I try to run nvidia-settings I get an error saying that I am not running the nvidia driver. My xorg.conf file is set to nvidia for the driver as well.

---

### Post by Malfet on 2008-04-25
> **Archmage said:**
> This looks like the usual xorg-autoconfiguration that is new since Hardy. :(
Try to insert loading the driver nvidia manual into your xorg.conf.

That I've try - just to copy settings from the xorg.conf of working Ubuntu 7.10.
No effect.

M.

---

### Post by Dabbill on 2008-04-25
I have tried that as well. Useing my xorg.conf from my 7.10 install. I did upgrade to 8.04 with the update manager. Should i download 8.04 and install fresh from CD? Just dont formate my /home partition?

---

### Post by Hugolp on 2008-04-25
Another one here. Nvidia 6150 is not being recogniced. I tried to install manually the driver from nvidia.com but no luck.

This seems to happen a lot (launchpad is full of it too), and not only with one model but with several Nvidia models. How this got to the final release?

Anyone has a solution?

Hugo

---

### Post by Dabbill on 2008-04-25
As Malfet said envyng is detecting my video card correctly, but for some reason the nvidia module wont load and it keeps defaulting back to vesa. Any one gotten any 8800GT's to work in hardy? If so did you do upgrade from 7.10, or did you do a fresh install?

---

### Post by RDV on 2008-04-25
Along with everyone else I am being kicked into vesa low graphics mode. I have a 8600 GTS, By looking through my "Xorg.0.log" (do not look at Xorg.log because that log reflects the loading of the failsafe drivers after nvidia driver load failed) I found that the ONLY error was that glrx module would not load with the following error "(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)". 
The installation of the drivers through EnvyNG completed successfully, I had been using Gutsy but with an upgraded kernel (2.6.24-14) so I doubt that this is a kernel issue. When I upgraded to the 2.6.24-14 kernel I just reinstalled the nvidia drivers with envy (not envyng) and I was back up with no problems.
I suspect as already mentioned that the issue is due to changes made in Hardy with xorg.conf my understanding is that some entries in the configuration file are ignored now versus in Gutsy. I am going to check out any related forum posts in regards to Hardy alpha/beta experiences with nvidia.

---

### Post by Pablo Pablovski on 2008-04-25
I had something similar after upgrading. On booting, the (kubuntu) splash screen appeared with the load progress bar as normal then, when the screen went black just before the mouse pointer normally appears, I saw a brief image of a low res version of the pointer followed by blackness. I could tell the system was booting, but the screen was blank.

I found that if I entered the GRUB menu and booted using the "ubuntu 804 kernel-2.6-24.16-generic" kernel (rather than the 2.6-24.16-386 one), the system booted properly and everything was as it should be.

Looks like a graphics driver problem to me - maybe it needs recompiled after the upgrade?

I've now edited GRUB's menu.lst to make the "generic" image the default and it boots properly everytime.

Hope this helps someone.

---

### Post by Malfet on 2008-04-25
> **Pablo Pablovski said:**
> 
I found that if I entered the GRUB menu and booted using the "ubuntu 804 kernel-2.6-24.16-generic" kernel (rather than the 2.6-24.16-386 one), the system booted properly and everything was as it should be.
Looks like a graphics driver problem to me - maybe it needs recompiled after the upgrade?

Don't think so. I have a generic kernel from the very beginning. Both now and before in 7.10 and never had -386 in the menu.lst

M.

---

### Post by Dabbill on 2008-04-25
I have recompiled it several times. Also fully removed any thing nvidia on my computer and installed it again.

---

### Post by Archmage on 2008-04-25
I've got a Geforce 3 TI 200. I also did try everything. Hardware Manager, EnvyNG, downloading the driver from NVIDIA, installing the legacy-package.

Nothing works. They best that I got was that I'm able to tell Hardy to use the "nv" driver instead the "vesa" driver. :(

---

### Post by johno84 on 2008-04-25
Same issue here. I used to have envy based drivers and looking on the envy site it suggests running "sudo envy --uninstall-all " before upgrading. I didn't do this so perhaps that could be the problem?

---

### Post by ddnev45 on 2008-04-25
Nvidia 8500GT

Did a clean install of 8.04, when trying to use the restricted drivers from Ubuntu, or after using EnvyNG, the monitor goes to sleep on the reboot.

---

### Post by Dabbill on 2008-04-25
ddnev45 just let the computer sit there for a few mins. With some geforce 8 cards the splash screen does not work and the monitor goes to sleep. If you get it a little time the login screen will come up.

---

### Post by RDV on 2008-04-25
SOLUTION! (At least from me). I picked most of these actions from some other posts. Here is what I did:
1) I un-installed any drivers I had installed with EnvyNG.
2) Re-installed the restricted drivers per a suggestion in another post. 
sudo apt-get install --reinstall linux-restricted-modules-$(uname -r) nvidia-glx

3) Installed the following modules as suggested by apt during the reinstall.
sudo apt-get install nvidia-kernel-source nvidia-settings

4) Rebooted
5) Enabled the Nvidia restricted drivers through "Settings>Administration>Hardware Drivers"
6) Rebooted
7) My usual resolution worked again! - Driver 169.12
8) Turned on Compiz-Fusion
9) Used Nvidia settings program I enabled both switches for "Sync VBlank"

Now Compiz-fusion, Awn and video play back are working again. 

Next challenge is to getting my sound working again.

---

### Post by david2b on 2008-04-25
I've got the same issue, with Nvidia 8600 GT. I think the problem is version missmatch between xorg and nvidia drivers... so wait and see until nvidia release a new driver for hardy

---

### Post by Dabbill on 2008-04-25
Thanks RDV I will give that a try once I get off work. They blocked port 22 :( No more SSH from work hehe.

---

### Post by Malfet on 2008-04-25
> **RDV said:**
>  Enabled the Nvidia restricted drivers through "Settings>Administration>Hardware Drivers"

I did it before and I follow your advice step by step now. No way. The problem is "Restricted drivers manager" just does not see graphic card. In Ubuntu 7.10 it was perfectly fine.

M.

---

### Post by chek2fire on 2008-04-25
I have the same problem in kubuntu 8.04 with my video card nvidia 8800gts. I have the same problem from hardy alpha but the problem exist until today. I have can install gpu driver only with envyng

---

### Post by Dabbill on 2008-04-25
Well I got my nvidia driver working correctly. Fount out for some reason gutsy kernel was loading still even tho grub pointed to hardy kernel. Had to remove hardy kernel and reload the hard backup kernel. Now every thing is working correctly. Now to just get Compiz working again heh.

Would have been better off to do a fresh install of hardy instead of doing upgrade. Which I still might do.

---

### Post by Antaresje on 2008-04-25
I had the same problem. Fresh install of 8.04, downloaded the drivers from the nvidia site, installed them, restarted gdm. Everything worked, compiz, dual screen, the works.

Until I rebooted and X dropped me into low resolution. I spent some time troubleshooting, and I found out that somehow the nvidia kernel module was being loaded, but without the i2c_core that it depends on. You can check this by doing 'lsmod | grep nvidia'

*Note: I did all this as root. Once I rebooted and my X wouldn't start properly, I went to tty1 (CTRL-ALT-F1) and stopped gdm with '/etc/init.d/gdm stop'. Once you're ready to start gdm again, use '/etc/init.d/gdm start'.*

Right after you install the nvidia drivers, you'll get output like this:

root@ubuntu:~# lsmod | grep nvidia
nvidia               8858052  34 
i2c_core               28544  2 nvidia,i2c_nforce2

If you give the same command after a reboot, you'll see that the i2c_core line is missing.

If you're in that situation, stop gdm, then give the command 'rmmod nvidia' and then the command 'modprobe nvidia'. Now you should have both lines again when you do an 'lsmod | grep nvidia'. Restart gdm, and you're good to go.

To make life easier on myself, I created a simple script in /etc/init.d that I called nvidia_workaround. The script looks like this:

#!/bin/bash
/sbin/rmmod nvidia
/sbin/modprobe nvidia

do a 'chmod u+x /etc/init.d/nvidia_workaround' to make it executable, and an 'ln -s /etc/init.d/nvidia_workaround /etc/rc2.d/S02nvidia_workaround' to get the the script to run automatically during boot.

Now, when you reboot, your nvidia driver will load properly.

I'm sure there's a nicer workaround to get the module to load properly, but it's late over here, and I'm off to sleep :)

---

### Post by easoukenka on 2008-04-25
I did an upgrade to hardy had the low resolution warning went to throw in my backup xorg file with a sudo command learned I couldn't sudo anything because of bad host name.  I troubleshot that for a bit got that working but still no luck with nvidia drivers.  I tryed envy uninstall and reinstall tried both nvidia-glx and nvidia-glx-new no luck with anything.  I will try the tips on here tomorrow but I have to goto bed unhappy tonight :)

---

### Post by tckrockz on 2008-04-26
> **Antaresje said:**
> I had the same problem. Fresh install of 8.04, downloaded the drivers from the nvidia site, installed them, restarted gdm. Everything worked, compiz, dual screen, the works.

Until I rebooted and X dropped me into low resolution. I spent some time troubleshooting, and I found out that somehow the nvidia kernel module was being loaded, but without the i2c_core that it depends on. You can check this by doing 'lsmod | grep nvidia'

*Note: I did all this as root. Once I rebooted and my X wouldn't start properly, I went to tty1 (CTRL-ALT-F1) and stopped gdm with '/etc/init.d/gdm stop'. Once you're ready to start gdm again, use '/etc/init.d/gdm start'.*

Right after you install the nvidia drivers, you'll get output like this:

root@ubuntu:~# lsmod | grep nvidia
nvidia               8858052  34 
i2c_core               28544  2 nvidia,i2c_nforce2

If you give the same command after a reboot, you'll see that the i2c_core line is missing.

If you're in that situation, stop gdm, then give the command 'rmmod nvidia' and then the command 'modprobe nvidia'. Now you should have both lines again when you do an 'lsmod | grep nvidia'. Restart gdm, and you're good to go.

To make life easier on myself, I created a simple script in /etc/init.d that I called nvidia_workaround. The script looks like this:

#!/bin/bash
/sbin/rmmod nvidia
/sbin/modprobe nvidia

do a 'chmod u+x /etc/init.d/nvidia_workaround' to make it executable, and an 'ls -s /etc/init.d/nvidia_workaround /etc/rc2.d/S02nvidia_workaround' to get the the script to run automatically during boot.

Now, when you reboot, your nvidia driver will load properly.

I'm sure there's a nicer workaround to get the module to load properly, but it's late over here, and I'm off to sleep :)

can u explain it? Pls

---

### Post by tckrockz on 2008-04-26
> **RDV said:**
> SOLUTION! (At least from me). I picked most of these actions from some other posts. Here is what I did:
1) I un-installed any drivers I had installed with EnvyNG.
2) Re-installed the restricted drivers per a suggestion in another post. 
sudo apt-get install --reinstall linux-restricted-modules-$(uname -r) nvidia-glx

[B]3) Installed the following modules as suggested by apt during the reinstall.
sudo apt-get install nvidia-kernel-source nvidia-settings[/B]

4) Rebooted
5) Enabled the Nvidia restricted drivers through "Settings>Administration>Hardware Drivers"
6) Rebooted
7) My usual resolution worked again! - Driver 169.12
8) Turned on Compiz-Fusion
9) Used Nvidia settings program I enabled both switches for "Sync VBlank"

Now Compiz-fusion, Awn and video play back are working again. 

Next challenge is to getting my sound working again.

step 3 is not working i get this 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting nvidia-new-kernel-source instead of nvidia-kernel-source
Package nvidia-settings is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-settings has no installation candidate

```

---

### Post by Malfet on 2008-04-26
I manage to solve it. I just removed all traces of drivers by Envy and then Synapric and try to reinstall again NVidia driver NVIDIA-Linux-x86-169.12-pkg1.run and then.. it worked!

1. ```
sudo chmod +x NVIDIA-Linux-x86-169.12.pkg1.run
```
2. CTRL+ALT+F1
3. Login
4. ```
sudo killall gdm
```
5. ```
sudo ./NVIDIA-Linux-x86-169.12.pkg1.run
```
6. Ignore warning about non-compartible compile module
7. Restart system and activate "standart" visual effects.

Compiz is working, just in 8.04 I don't have access to it throuth desctop setting, but only from the main menu. All eye candy do as well.
Only problem, Logitech web-cam started to work in Hardy after installation (it did not work in Gutsy) now stop working again... Dunno what is the problem between NVidia and webcam.

---

### Post by AntonL on 2008-04-26
I have had very similar problems, but finally found a solution.

It turned out that for some reason the menu.lst wasn't updated during the upgrade to Heron,

That meant that the old 7.04 kernel was loaded, I modified my menu.list file /boot/grub/menu.lst 

```
sudo gedit /boot/grub/menu.lst
```

```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=29d77fb9-9cd5-4ef7-be76-b9038f8746ff ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=29d77fb9-9cd5-4ef7-be76-b9038f8746ff ro single
initrd		/boot/initrd.img-2.6.24-16-generic

```

having done that I installed the nvidia-settings module

```
sudo apt-get install nvidia-settings
```

rebooted the machine

and ran System->Administration->NVIDIA X Server Settings

once that was done, every thing worked like a dream.

So it turned out that the real problem - for me - was that the grub menu wasn't updated during the upgrade process.

---

### Post by meimato on 2008-04-26
IMHO the problem is related to restricted-modules.
Like many others I have problems with my previuosly (in 7.10) working Nvidia card; when X fails to start and goes in failsafe mode, I can see in the log this error:


[INDENT]API mismatch: the NVIDIA kernel module has version 72.86.04,
[/INDENT]
[INDENT]but thie NVIDIA driver component has version 169.12[/INDENT]

---

### Post by AntonL on 2008-04-26
Sorry but I'm rather much a newbie, so I may not use the right terminology. In my case the symptom was that without the restricted NVIDIA drivers I was using some sort of safemode, with 800x600 resolution, and when I activated the restricted drivers, the X screen would blink back and forth several times between text mode and blank screen, until it finally stabelized with the most extreme display resolution, making it almost impossible to read the display.

Examining the Xorg.0.log I discovered that the VESA drivers were used and *not* the NVIDIA drivers, although it seemed as if the NVIDIA drivers were being loaded. Both lsmod and lspci reported the presence of NVIDIA card and modules.

What finally fixed the issue for me, was changing my GRUB menu.lst, ensuring that the correct version of the kernel was loaded. All I can say is that for me personally, it solved the problem.

---

### Post by meimato on 2008-04-26
My menu.lst was correctly updated during version upgrade: I'm booting using /boot/initrd.img-2.6.24-16-generic.
I'm afraid there might be a deepest problem, but it's really a shame: I can't understand how this bug has passed beta testing, it doesn't seem to be something too difficult to reproduce, judging on the number of systems affected...

---

### Post by AntonL on 2008-04-26
I agree that there seems to be several different issues giving rise to the same symptoms, i.e. NVIDIA restricted drivers not working properly. I suspect that in my case it was due to me having modified the original menu.lst in the 7.10 version.

I have a dual boot scenario, where I use GRUB to boot into XP, maybe that's why the dist upgrade failed to update my menu.lst

---

### Post by pooga on 2008-04-26
I had the same problem of the system loading up vesa drivers on a reboot with my 8600M GS card.  I am using a fresh install of Hardy.

I tried installing the nvidia drivers two ways, through System > Administration > Hardware Drivers, and through EnvyNG. Both gave the same results.

I managed to get it all working now (so far) but I'm not sure what exactly did the trick. I'll just list the steps I followed for anyone that wants to give it a go.

Following recommendations in other posts, I uninstalled the drivers I had through EnvyNG, and then reinstalled nvidia-kernel and linux-restricted-modules-2.6.24-16-generic in Synaptic. I then rebooted.

I reinstalled the nvidia drivers through System > Administration > Hardware Drivers, but I **did not** reboot at this point. I then installed nvidia-settings through Synaptic.

I went to tty1 (<Ctrl> <Alt> F1) and stopped gdm using "/etc/init.d/gdm stop". I then restarted it again using "/etc/init.d/gdm start". This brought me back the login screen.

The next thing I did was to run the nvidia settings manager to have a look (I didn't actually change anything). 

I then ran "lsmod | grep nvidia" which found the modules:
nvidia
i2c_core
agpgart

I then tried out compiz which worked.

Finally I rebooted the system which to my pleasant surprise actually booted correctly with the nvidia drivers loaded properly.  After running "lsmod | grep nvidia" again I got the same output as before I booted.

Hope this actually helps someone.  Good luck with it.

---

### Post by Jorick on 2008-04-26
> **Antaresje said:**
> I had the same problem. Fresh install of 8.04, downloaded the drivers from the nvidia site, installed them, restarted gdm. Everything worked, compiz, dual screen, the works.

Until I rebooted and X dropped me into low resolution. I spent some time troubleshooting, and I found out that somehow the nvidia kernel module was being loaded, but without the i2c_core that it depends on. You can check this by doing 'lsmod | grep nvidia'

*Note: I did all this as root. Once I rebooted and my X wouldn't start properly, I went to tty1 (CTRL-ALT-F1) and stopped gdm with '/etc/init.d/gdm stop'. Once you're ready to start gdm again, use '/etc/init.d/gdm start'.*

Right after you install the nvidia drivers, you'll get output like this:

root@ubuntu:~# lsmod | grep nvidia
nvidia               8858052  34 
i2c_core               28544  2 nvidia,i2c_nforce2

If you give the same command after a reboot, you'll see that the i2c_core line is missing.

If you're in that situation, stop gdm, then give the command 'rmmod nvidia' and then the command 'modprobe nvidia'. Now you should have both lines again when you do an 'lsmod | grep nvidia'. Restart gdm, and you're good to go.

To make life easier on myself, I created a simple script in /etc/init.d that I called nvidia_workaround. The script looks like this:

#!/bin/bash
/sbin/rmmod nvidia
/sbin/modprobe nvidia

do a 'chmod u+x /etc/init.d/nvidia_workaround' to make it executable, and an 'ls -s /etc/init.d/nvidia_workaround /etc/rc2.d/S02nvidia_workaround' to get the the script to run automatically during boot.

Now, when you reboot, your nvidia driver will load properly.

I'm sure there's a nicer workaround to get the module to load properly, but it's late over here, and I'm off to sleep :)

You should use 'l**n** -s /etc/init.d/nvidia_workaround /etc/rc2.d/S02nvidia_workaround' 
instead of 
'ls -s /etc/init.d/nvidia_workaround /etc/rc2.d/S02nvidia_workaround'

Then it works great ( running 173.08 )! :)

---

### Post by Antaresje on 2008-04-26
> **Jorick said:**
> You should use 'l**n** -s /etc/init.d/nvidia_workaround /etc/rc2.d/S02nvidia_workaround' 
instead of 
'ls -s /etc/init.d/nvidia_workaround /etc/rc2.d/S02nvidia_workaround'

Then it works great ( running 173.08 )! :)

Oops, that's a rather important difference. Thanks for noticing :)

---

### Post by Hugolp on 2008-04-26
Its solved now for me. After trying different things with no luck, I reinstalled Hardy for the fourth time, and still did not work. A couple of hour laters I came back to this computer and tryed to dis-enable and enable again the Nvidia propietary driver in Drivers. And then it installed nvidia-glx-new and it worked. Have no idea why it worked this time and not the previous, but I have rebooted several times and everything seems fine now. Maybe the Ubuntu repositories where so loaded before that the download did not work?

Hugo

---

### Post by SnakeHips on 2008-04-26
you could try this...

[http://ubuntuforums.org/showpost.php?p=4792026&postcount=11](http://ubuntuforums.org/showpost.php?p=4792026&postcount=11)

---

### Post by sparky64 on 2008-04-26
Have just tried again with a new install.
First thing after install did an upgrade.
Then installed envyng with all dependencies (using synaptic)
Manually chose which nvidia driver to use and installed ok.
Reboot.
Everything now works ok BUT if you go to system settings it still says using standard drivers. If you change to propriety it stuffs the setting and reboots to 800x600.
Also my wireless worked this time first time? tried everything before.
Even compiz is working fine.:)

---

### Post by easoukenka on 2008-04-26
Ok I am having the same problem did an upgrade and nvidia quit working.  I tried a few of the tips on here with no luck.  I installed drivers through envy uninstalled reinstalled a bunch of times, tried both nvidia-glx and the nvidia-glx in synaptic.  Tried removing all those xserver etc from synaptic and doing a fresh install nothing.

Now I do not even get the nvidia drivers to load at all in the restricted manager it doesn't say anything now.  I installed with envy still nothing.  I tried to edit my grub file because I don't think I am having the correct kernel load in my grub file but I get some weird command prompt when I try to boot to it.  After many hours of tinkering with stuff I am now downloading the CD and am going to do a fresh install.  I notice more tips coming up but I am sick of it at this point.  I love ubuntu just wish I would have waited for all this to sort itself out.  Hopefully this fixes my problem I will post back my status.  Wish me luck :guitar:

---

### Post by pmorton on 2008-04-26
> **easoukenka said:**
> I installed drivers through envy uninstalled reinstalled a bunch of times, tried both nvidia-glx and the nvidia-glx in synaptic.  Tried removing all those xserver etc from synaptic and doing a fresh install nothing.

My 5th load of Hardy, unlike the other 4, has been a pain. (Two of those were perfect - the ones without NVidia graphics cards that is, and 2 were slightly problematic - certainly enough to sicken any tentative windows convert for life). The setup on this machine is a 20" Apple Cinema WSXGA+ and, for my sins, a NVidia Geforce 7300 controller. This configuration has  always been a nuisance, but it's surpassed itself this time. 

Having read everyone else's horror stories, I eventually dumped my update for a fresh Hardy Alternate CD install (/home is on a separate partition). X started but was still an unreadable mess. This is where I started  asking myself about the readiness of Hardy for the unsuspecting public.  Forget NVidia's binary and its attendant grief - how come the open driver doesn't just work? It's a crap ad for Ubuntu, and doesn't help the image of GNU/Linux.

Anyhow, I installed Alberto Milone's envyng  ("sudo apt-get envyng-gtk -t" the '-t' giving the text version)and chose a manual install. This time I chose the old 96.43.05 driver instead of the new 169.12 version. Finally, I've got a viewable 1680x1050 screen. Albeit running the NVidia binary driver, when all I want is the 2-D open job (having got fed up of X breaking with every kernel upgrade).

There's another thing that's been raised here and in launchpad. You used to be able to fix up the open driver nicely with 'dpkg-reconfigure xserver-xorg' which allowed you to build a new xorg.config file. Now some bright spark has taken its video section, a la redmond, out of the user's hands, and there's nothing you can do. Tssssch....

---

### Post by NEUR0M4NCER on 2008-04-26
I spent two weeks bashing away at Hardy Beta trying to get the Nvidia driver working for my 8500GT. Here's some threads that document my (and many other people's) progress - or lack thereof:


[INDENT][Is there an alternative to Ctrl + Alt + F1?](http://ubuntuforums.org/showthread.php?t=756709)

[Hardy Alpha 5 Nvidia 8600M GT white screen of death](http://ubuntuforums.org/showthread.php?t=712479)

[Missing nvidia entry in Hardware Drivers](http://ubuntuforums.org/showthread.php?t=760508)

[odd issues on xorg](http://ubuntuforums.org/showthread.php?t=761286)

[nvidia graphics driver not loading after upgrade to 8.04](http://ubuntuforums.org/showthread.php?t=757590)

[Last night update broke my video (nvidia)](http://ubuntuforums.org/showthread.php?t=763503)[/INDENT]


This next one is asking the best question yet:

[INDENT][Whats the replacement for - sudo dpkg-reconfigure xserver-xorg](http://ubuntuforums.org/showthread.php?t=750305)[/INDENT]


... and, of course, my bug report:

[INDENT][Bug #217694 in xserver-xorg-video-nv (Ubuntu)](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/217694)[/INDENT]
Doesn't look like it's in the right section, but admin moved it there, so...


I haven't even managed to figure out whether it's a problem with the new xorg, the Nvidia restricted driver, the upgrade process itself, or something entirely 'other'.

There are many other bug reports of a similar nature. I was really hoping this would be cleared up by release (I went back to Gutsy in a fit of childish spite three days ago;)), but it looks like it hasn't. This seems to be a major deal-breaker for the new release. I know that "People in the Know" *know* to wait until 8.04.**1**, but for those guys new to Ubuntu with Gutsy, a botched upgrade is all that's needed to give a poor impression of the OS and usher them along to another place.

Even if one of you uber-smarties out there figures out a real work-around for this, let's face it - who really wants to go hacking around in the terminal to get a basic feature working? Not I, I tells ya (although the letters on my keyboard are that much fainter after all the things I tried).

I've loved Ubuntu since first install a year ago, but until I read something official telling me Nvidia hardware will definitely *work*, i'll be sticking with Gutsy 7.10, LTS or not.



Even though it's absolutely killing me not clicking that 'Upgrade' button, out of sheer (morbid) curiosity.

Regards

---

### Post by broderboy on 2008-04-26
I was able to fix this by doing:

# Completely remove nvidia-glx-new

# Remove nvidia-kernel-common (this also removes linux-restricted-modules), (I am not sure if step 2 is required)

# install build-essentials

# Download the Nvidia beta driver that came out on April 10. You can get it here

# hit ctrl + alt + f1 to break out of gnome

# "sudo /etc/init.d/gdm stop" to shutdown the X server

# sudo sh NVIDIA-Linux-x86-173.08-pkg1.run to install the driver. If it asks you to update you're xorg.conf file, let it.

# Reboot. ("sudo reboot") You should now be able to enable Desktop effects.

Details here: [http://blog.gpowered.net/2008/04/fixing-nvidia-8600-gt-on-hardy-heron.html]("http://blog.gpowered.net/2008/04/fixing-nvidia-8600-gt-on-hardy-heron.html")

---

### Post by jblackhall on 2008-04-26
If you are experiencing this problem would you please run "uname -a" (without quotes) in Terminal and see what version of the kernel you're running?  If it is version 2.6.22-14 (or lower) you are still running the Gutsy kernel.  If it is version 2.6.24-16 (or higher) you are running the Hardy kernel.  I had this problem also when I upgraded and when asked about my menu.lst, I told them to keep the one I've been using (not use the manufacturer's version).  It appears that this is keeping my menu.lst from listing the new kernel version, so I automatically boot into the old one.  By simply uninstalling the old linux kernel image (2.6.22-14) via Synaptic (as long as 2.6.24-16 is installed) you should be ok, and then when asked about your menu.lst file (again) tell it you want to use the manufacturer's version.  This should preserve any non-Ubuntu partitions currently listed in menu.lst (such as a Windows partition).

[http://ubuntuforums.org/showthread.php?p=4802647](http://ubuntuforums.org/showthread.php?p=4802647)
[http://ubuntuforums.org/showthread.php?p=4803739](http://ubuntuforums.org/showthread.php?p=4803739)

---

### Post by starchild7778 on 2008-04-26
I had the same problem when upgrading an Edubuntu 7.10 installation to Hardy.  I was able to get a viewable screen when changing the video driver to "vesa", but kept running into these forementioned issues when using "nvidia".  I have a Geforce 6800 video card.

I did a clean installation of Ubuntu 8.04 and all is well now, including the nvidia drivers installed through Ubuntu.

---

### Post by cardio on 2008-04-26
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Option          "AddARGBGLXVisuals"     "True"
        Defaultdepth    24
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "de"
        Option          "XkbVariant"    "deadgraveacute"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Extensions"
        Option          "Composite"     "Enable"
EndSection

```
Seriously, this is one horrible update. How could no one have noticed this during beta testing? None of the usual fixes work. My monitor won't be recognized, my graphics card won't be recognized. Envy, installation by hand, repositories, reinstallation... Everything's completely useless, I can't even reconfigure the X server! It will just go back to a useless, bare-bones xorg.conf. My whole system is broken because all the worthless eye candy that KDE lugs around slows everything down to a crawl. The horrible resolution makes my eyes hurt, to boot.

Thanks a lot, Ubuntu. No way I'm going to be able to learn for my Java finals this monday, thanks to my bright idea of just quickly running distupgrade this morning. The devs can go screw themselves, this is worse than unpatched WinXP :mad:

---

### Post by Gwarkill on 2008-04-26
i have a large feeling that this has to do with a kernel issue. 

Found my fix here:

[http://www.lucioalbenga.com/2008/04/25/hardy-heron-nvidia-drivers/](http://www.lucioalbenga.com/2008/04/25/hardy-heron-nvidia-drivers/)

anyone know about the sound?

---

### Post by Fibonacci on 2008-04-26
I've tried every single suggestion on this thread short of doing a fresh install. And still no dice - I'm stuck with vesa.

---

### Post by fusionisthefuture on 2008-04-27
the restricted driver manager now works fine for me (it did not on april 24th) it said the driver was enabled but not in use.  today after reading hugos post i tried it again and it downloaded nvidia-glx-new and installed and works fine. 
im using an HP dv2200cto laptop with an nvida 6150 go vid card.  
-fitf

---

### Post by Fibonacci on 2008-04-27
Just did a fresh install and the nVidia driver is finally working. I couldn't get it to work by any other means.

---

### Post by diebels on 2008-04-27
> **Dabbill said:**
> Thanks RDV I will give that a try once I get off work. They blocked port 22 :( No more SSH from work hehe.

Try ajaxterm.

---

### Post by oooh on 2008-04-27
In my case:
MAde it work with Envy in gutsy gibon 7.10

Upgraded to Hardy heron 8.04, and stopped to work. Uninstalled drivers with Envy. Restarted and it definitelly work. However, configuration was lost, and system restarted in 800x600 always. 
Installed nvidia-settings package. Executed it as a root, so: sudo nvidia-settings. Save settings in Server configuration tab to an X file (/etc/X11/xorg.conf).
Restart and nvidia settings will be remembered, never reset to default anymore.

---

### Post by Dabbill on 2008-04-27
I finally did get every thing to run right on my system. Got tired of the upgrade. So just downloaded the 8.04 install CD and installed that way. Backed up my docs to windows HD. Then did a complete fresh install of 8.04. It detected my card and auto installed the restricted drivers.

---

### Post by a6jarvi on 2008-08-09
> **Antaresje said:**
> 
To make life easier on myself, I created a simple script in /etc/init.d that I called nvidia_workaround. The script looks like this:

#!/bin/bash
/sbin/rmmod nvidia
/sbin/modprobe nvidia

do a 'chmod u+x /etc/init.d/nvidia_workaround' to make it executable, and an 'ln -s /etc/init.d/nvidia_workaround /etc/rc2.d/S02nvidia_workaround' to get the the script to run automatically during boot.


Thank you so much for this! Finally, after two weeks of total frustration, I'm able to use my comp again! :)

I noticed that when I installed the drivers, I could start kdm, but after reboot no more, which meant that the kernel modules weren't loading up automatically. This fixes it, and while it may be a little dirty, it's OK because now I know why all I got was VESA with max resolution of 800x600 (or total freeze with black screen...). Nothing's worse than having no idea what to do! :)

---


---
title: "Kernel update today"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by lsutiger on 2008-06-04
There was a kernel update today. Any problems for anyone?

---

### Post by Pumalite on 2008-06-04
None.

---

### Post by steveneddy on 2008-06-04
I noticed that Ekiga wouldn't start without crashing and a quick reinstall from Synaptic resolved the issue.

I think it runs a little better, actually.

Hardy 64 bit.

System76 laptop Serval Performance Type 1

---

### Post by lsutiger on 2008-06-04
Thanx for the detailed response steveneddy! 

Could the rest of you do the same and post the details of your computer?

---

### Post by Pumalite on 2008-06-04
Core 2 Duo, 'Prescott', 32 and 64 bit Two Intel motherboards; 2 Ausus. 2 Apple's Core 2 Duo

---

### Post by elj4176 on 2008-06-04
HP dv9074 notebook- AMD64X2
64 bit hardy.

Didn't reboot fully until after several hard resets. My tasklist in the panel doesn't seem to be working. I use pidgin and it is simply gone when I close the buddy list (yes I checked with ps ax | grep pidgin) - kopete is still running but not in the tasklist panel either. I also had to re-add the weather applet to the panel.

My wireless seems to be flaky again. The initial upgrade to hardy seemed to have corrected this. The wireless works only 1 in maybe 5 or 6 reboots. 
:confused:

edit: I had to add my notification area to teh panel again and I removed and reinstalled pidgin and it seems to be working now. I'm afraid to reboot though.

---

### Post by ohiomoto on 2008-06-04
Hosed many today:  

[http://ubuntuforums.org/showthread.php?t=818241](http://ubuntuforums.org/showthread.php?t=818241)

---

### Post by empty_tank on 2008-06-05
no problem in kernel update but no noticeable difference in performance

==
Vostro 1400n core2duo 1.66; 4 GB RAM; 120 GB Sata HDD; Hardy Heron

---

### Post by VMC on 2008-06-05
No problem on my end: Dell Optiplex GX670, 2gig ram, integrated video, IDE hard drives. I keep seeing troubles being reported.

---

### Post by jmontelius on 2008-06-05
Three machines upgraded and no problem. Reinstalled openafs on top of the new kernel without any problems.

AMD Phenom 9500 / Asus M3A32-MVP
AMD 64 X2 3800+ / Asus M2NPV-MX
Intel Celeron / MSI Mega 651

---

### Post by nsramkishen on 2008-06-05
After I installed kernel -18 and restarted the machine, I got the blue screen with initrmfs error. For me, only the default -16 kernel works. Mine is an Intel Core2Duo system with Vista pre-installed. I heard somewhere that this error had been corrected in -18. I simply comment out the -18 related entries in the grub menu and use the (good) old -16 kernel. Keeping fingers crossed :(

Do I need to provide more info about my machine?

---

### Post by gavinjb on 2008-06-05
Only problem I had is that there is not a VirtualBox-Modules available yet for this version so I cant run VBox until this is available.

---

### Post by ShodanjoDM on 2008-06-05
No problem here in my PC. Although I haven't upgraded my laptop (Toshiba Satellite M200) since I will have to recompile the omnibook kernel module for the bluetooth.

Not a big deal, but I still don't feel like doing it for now.

---

### Post by br0ken on 2008-06-05
no problems thus far.

intel core 2 duo e6300
2GB DDR2 PC2400 RAM
320GB SATA II HD
Hardy Heron

---

### Post by epee on 2008-06-05
My update was uneventful.

AMD 64-bit
2GB DDR RAM
1 x 160GB IDE HD
2 x 320GB SATA in hardware RAID1 configuration for /home
Hardy Heron

---

### Post by wheelz247 on 2008-06-05
well for starters im still fairly new with ubuntu, but i feel ive downloaded all the drivers and everything needed it and it comes up fine but when actually executing it this comes up

VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

sayings i dont have drivers dont understand that. help would be greatly appreciated.

---

### Post by gulmer on 2008-06-05
See my post with title "  Adept Updater appears to be stuck"
gulmer

---

### Post by Mr. Scott on 2008-06-05
The new updated kernel, .18, failed to install properly, causing a boot failure. I booted the previous .17 kernel then reinstalled the .18 from Synaptic, which solved the problem. Now running fine on the new kernel.

HP Pavillion a700n
Athlon XP 2.1 Ghz Processor
768 MB RAM
Dual boot with XP Home and Ubuntu 8.04

---

### Post by nsramkishen on 2008-06-06
> **Mr. Scott said:**
> The new updated kernel, .18, failed to install properly, causing a boot failure. I booted the previous .17 kernel then reinstalled the .18 from Synaptic, which solved the problem. Now running fine on the new kernel.

HP Pavillion a700n
Athlon XP 2.1 Ghz Processor
768 MB RAM
Dual boot with XP Home and Ubuntu 8.04

Do you mean to say that installing the kernel update using Synaptic would solve the problem? Let me try this.

---

### Post by figgles on 2008-06-06
Update via update-manager went smoothly; virtualbox is dead in the water. I need the kernel module for 18; which isn't in the repo yet. Argh!

Dell 1520: * Processor: Intel Core 2 Duo T7300 (2.0 GHz/4MB L2 Cache) * Hard Drive: 80 GB SATA @ 5400RPM * Screen: 15.4" WSXGA Widescreen (1680 x 1050) * Graphics: NVIDIA GeForce 8600M GT 256MB  * RAM: 2.0GB DDR2 SDRAM @667 MHz (2 x 1GB)  * Optical Drive: 8x CD/DVD burner (DVD+/-RW) w/Double Layer Support * Battery: 9-cell lithium ion * Wireless: Intel 4965AGN * Ports/Slots: 1 IEEE 1394 (FireWire); 4 Universal Serial Bus (USB 2.0); 8-in-1 Memory Card Reader; VGA Out; S-Video; RJ-45 Ethernet LAN; RJ-11 Modem; ExpressCard 54mm; stereo in, headphone/speaker out and dual digital mics

---

### Post by sports fan Matt on 2008-06-06
2-6-24.19 is an update..i'll post back as soon as its downloaded..HP Pavillion Itel Cellron priocessor Pentium 3 384 RAM

---

### Post by sports fan Matt on 2008-06-06
no problems :)

---

### Post by NJC on 2008-06-06
I ran all of the upgrades, but it's booting to -16, and not -18?? 
As I write this I recall after all updates were downloaded and install began, I had the option to "keep the same" and I selected. Maybe that was part of the problem.
 
How to get -18 though when no updates are available?

---

### Post by ohiomoto on 2008-06-06
> **NJC said:**
> I ran all of the upgrades, but it's booting to -16, and not -18?? 
As I write this I recall after all updates were downloaded and install began, I had the option to "keep the same" and I selected. Maybe that was part of the problem.
 
How to get -18 though when no updates are available?

You can use Synaptic Manager.  Be careful with -18...a lot of us had problems with it.  I kept having strange issues with headers in -18.

Here is what worked for me:

1. Clean out the package cache and history in Synaptic by going to "Synaptic->Settings->Preferences->Files".  Hopefully this will make sure you avoid any issues.  

2.  Go down the list and mark the following packages for installation:```
linux-image-2.6.22-18-generic
linux-headers-2.6.22-18-generic
linux-restricted-modules-2.6.22-18-generic
linux-ubuntu-modules-2.6.22-18-generic
```

If you encounter any problems go back and try removing the installed packages.

Here is a link to my post describing the -18 issues I encountered and the help that I received: [http://ubuntuforums.org/showthread.php?t=818241](http://ubuntuforums.org/showthread.php?t=818241)

---

### Post by lsutiger on 2008-06-06
Unfortunately, I can not even try to update on my desktop - it is my work computer. IOW - I NEED it to work. Good thing is that I do not live too far from the office and will be able to try it out during the weekend.
With all the help here, I am sure I will be able to either get through this flawlessly or with just a little work.

Thanx again for all of the posts!

---

### Post by mabovo on 2008-06-06
> **lsutiger said:**
> There was a kernel update today. Any problems for anyone?

Wireless none on MacBook2,1

mabovo@macbook:~$ cd madwifi-trunk-r3699-20080605/
mabovo@macbook:~/madwifi-trunk-r3699-20080605$ make
cd: 1: can't cd to /lib/modules/2.6.24-19-rt/build
Makefile.inc:66: *** /lib/modules/2.6.24-19-rt/build is missing, please set KERNELPATH.  Stop.
mabovo@macbook:~/madwifi-trunk-r3699-20080605$

Also, lost keyboard configuration for portuguese language.

---

### Post by chmosbrook on 2008-06-06
In 18 I lost my wireless.
 In 19 I got the wireless working but could not connect to a signal. I also lost my sound.
Currently I am using 17 which has no problems.

---

### Post by Bubba64 on 2008-06-06
> **NJC said:**
> I ran all of the upgrades, but it's booting to -16, and not -18?? 
As I write this I recall after all updates were downloaded and install began, I had the option to "keep the same" and I selected. Maybe that was part of the problem.
 
How to get -18 though when no updates are available?

If you don't have startup manager in system preferences install it from synaptic it allows you to pick the booting kernel and other adjustments. Startup Manager can be installed from the terminal as well. I upgraded to Kernel 19 today I suspect it was from proposed I didn't look, only had to do 2 restarts to get it running correctly.

---

### Post by Bubba64 on 2008-06-06
> **chmosbrook said:**
> In 18 I lost my wireless.
 In 19 I got the wireless working but could not connect to a signal. I also lost my sound.
Currently I am using 17 which has no problems.

Have you tried the roaming option in the wired and wireless section of Network Manager that usually works for me to get every thing recognized to switch back to manual.

---

### Post by ohiomoto on 2008-06-06
> **chmosbrook said:**
> In 18 I lost my wireless.
 In 19 I got the wireless working but could not connect to a signal. I also lost my sound.
Currently I am using 17 which has no problems.

Try the steps I described in post #24. My 18 kernel works perfectly now and I think it's  a little faster.  Maybe even just do step #1 and see what happens in your newer kernels.

---

### Post by Em-Buntu on 2008-06-07
Anyone have a link to the changelog file for kernels 17->18->19?

I updated from 17->18 but have no idea of the changes.

Quad 865 Opteron
ASUS K8N-DL
ATI Radeon x1800
2 GB ECC DRAM

---

### Post by spandanj on 2008-06-07
I can't change my background from the appearance window. so i have to actually go the picture file, open it and set it from there.

---

### Post by madscientist on 2008-06-07
2.6.24-18 went fine.

However, 2.6.24-19 screwed up my nvidia card.  I get errors saying the kernel module cannot be loaded and X starts the configuration tool.  Looking around I see that after the install (I DID upgrade linux-restricted-drivers etc.) there's no /lib/modules/2.6.24-18-generic/volatile/nvidia.ko on my system.  That file apparently somehow gets created during the install; it's not shipped that way in any package.

Here's what I have:

```
linux-headers-2.6.24-19                    2.6.24-19.33
linux-headers-2.6.24-19-generic            2.6.24-19.33
linux-image-2.6.24-19-generic              2.6.24-19.33
linux-libc-dev                             2.6.24-19.33
linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19
linux-restricted-modules-common            2.6.24.13-19
linux-ubuntu-modules-2.6.24-19-generic     2.6.24-19.27
```

I had to leave work in order to make it to soccer practice so I couldn't mess with it more.  Is there something I need to do (dpkg-reconfigure or something) to get the nvidia.ko files to show up?

---

### Post by m2.g5ru6y7s on 2008-06-07
> **madscientist said:**
> 2.6.24-18 went fine.

However, 2.6.24-19 screwed up my nvidia card.  I get errors saying the kernel module cannot be loaded and X starts the configuration tool.  Looking around I see that after the install (I DID upgrade linux-restricted-drivers etc.) there's no /lib/modules/2.6.24-18-generic/volatile/nvidia.ko on my system.  That file apparently somehow gets created during the install; it's not shipped that way in any package.

Here's what I have:

```
linux-headers-2.6.24-19                    2.6.24-19.33
linux-headers-2.6.24-19-generic            2.6.24-19.33
linux-image-2.6.24-19-generic              2.6.24-19.33
linux-libc-dev                             2.6.24-19.33
linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19
linux-restricted-modules-common            2.6.24.13-19
linux-ubuntu-modules-2.6.24-19-generic     2.6.24-19.27
```

I had to leave work in order to make it to soccer practice so I couldn't mess with it more.  Is there something I need to do (dpkg-reconfigure or something) to get the nvidia.ko files to show up?

Please select the correct restricted-modules package for your kernel and everything will be work fine after a reboot. (see link)
[http://img176.imageshack.us/img176/6929/schermafdruksynapticpakhc9.png](http://img176.imageshack.us/img176/6929/schermafdruksynapticpakhc9.png)

---

### Post by madscientist on 2008-06-07
Sorry, my bad; I messed up my cut/paste and left off the last few characters.  I actually already have the same package you mention installed.  Here's another copy, this time fully qualified:

```
linux-headers-2.6.24-19                    2.6.24-19.33
linux-headers-2.6.24-19-generic            2.6.24-19.33
linux-image-2.6.24-19-generic              2.6.24-19.33
linux-libc-dev                             2.6.24-19.33
linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.42
linux-restricted-modules-common            2.6.24.13-19.42
linux-ubuntu-modules-2.6.24-19-generic     2.6.24-19.27
```

---

### Post by madscientist on 2008-06-07
OK, I tried this:```
sudo dpkg-reconfigure linux-restricted-modules-2.6.24-19-generic
```and now I can see the nvidia.ko files again:```
/lib/modules$ find -name nvidia.ko
./2.6.24-19-generic/volatile/nvidia.ko
```

However, after I rebooted that .ko was gone again!!  I've tried this 3 times and the behavior is exactly the same each time.  What could be removing those .ko files on reboot?!?!

If I bring down the failsafe X server, then run the dpkg-reconfigure, then run /etc/init.d/gdm restart to bring back up X, all is fine and dandy... until I reboot!  Then I have to do it all over again.  That's pretty annoying....

---

### Post by lsutiger on 2008-06-07
OK I installed my cloned drive (I use it for updates - have 8.04 on it and 7.10 on the live drive) and updated to .18

It fixed a problem I had with the panel being jacked up. I also can not change backgrounds. Virtualbox does not work (tells you to /etc/init.d/vboxdrv setup, but that gives an error). I absolutely need Virtualbox for work..all of the computers use PCAnywhere for remote access.

Firefox seems very sluggish, like...have you ever opened a web page and scrolled in IE without the video driver being installed in Windows?..like that. In fact any graphics seem sluggish a bit. I have the restricted drivers installed for my ATI 1150. 

Stunningly, my wireless did not break with the kernel update. Thats a new good thing...I always had to reinstall the wireless driver with a kernel update. I tried to get the .19 update with the update manager, but it said my computer was up to date.

For now I will stick with 7.10 on this machine and kernel .16 on the desktop (at work).

---

### Post by NJC on 2008-06-07
> **ohiomoto said:**
> 
2.  Go down the list and mark the following packages for installation:```
linux-image-2.6.22-18-generic
linux-headers-2.6.22-18-generic
linux-restricted-modules-2.6.22-18-generic
linux-ubuntu-modules-2.6.22-18-generic
```

Thanks for the help. I had a look at 2.6.24-16 and as well as the above 4 packages, there's a 5th one:```
linux-image-2.6.24-18-386

```Maybe it's because I picked the "keep the local version currently installed" for menu.lst after the upgrade. :confused: Therefore it didn't add menu.lst entries for 2.6.24.18?? But why would the installer default to that option?

I manually edited menu.lst to include an entry for 2.6.24-17 and it booted fine ... so I'll reinstall -18 and do the same manual config to the file.

---

### Post by m2.g5ru6y7s on 2008-06-08
> **lsutiger said:**
>  Virtualbox does not work (tells you to /etc/init.d/vboxdrv setup, but that gives an error). I absolutely need Virtualbox for work..all of the computers use PCAnywhere for remote access.


VirtualBox can be fixed by downloading and installing it again from the site. 
First you have you remove the old one (please do not remove it completely because then your existing configuration is also lost)

---

### Post by mtantawy on 2008-06-08
Please see this link
[http://ubuntuforums.org/showthread.php?t=818241]("http://ubuntuforums.org/showthread.php?t=818241")

alot of us have problems...
myself, i cant boot now coz my laptop doesn't proceed after entering my username and password

but before that, the rhytmbox didnt play any music and i just have to FORCE QUIT
beside many side effects from the kernel -18
till kernel -17 everything was working great

You said the update is okay, then why some systems were broken or malfunction after this specific update???
any suggestions for a beginner, or info i should know about kernels and so??

Thanks in advance
Mahmoud Tantawy

---

### Post by mtantawy on 2008-06-08
> **mtantawy said:**
> Please see this link
[http://ubuntuforums.org/showthread.php?t=818241]("http://ubuntuforums.org/showthread.php?t=818241")

alot of us have problems...
myself, i cant boot now coz my laptop doesn't proceed after entering my username and password

but before that, the rhytmbox didnt play any music and i just have to FORCE QUIT
beside many side effects from the kernel -18
till kernel -17 everything was working great

You said the update is okay, then why some systems were broken or malfunction after this specific update???
any suggestions for a beginner, or info i should know about kernels and so??

Thanks in advance
Mahmoud Tantawy
hey, anybody here!!!!
i dont think that this post was done for only members who had no problems to post a reply saying ::""no no problems at all the update is cute""

---

### Post by bkline on 2008-06-08
My main workstation was made unusable by 2.6.24-18-generic, though I had no problems with my other three Ubuntu machines after the upgrade.  Originally I was able to keep going by falling back to 2.6.24-17-generic, but after a little more experimentation in a vain attempt to understand the cause of the failure I have no kernel which doesn't freeze up the machine solid after a few seconds.  Waiting for -19 to hit the main repos.

---

### Post by lsutiger on 2008-06-08
> **m2.g5ru6y7s said:**
> VirtualBox can be fixed by downloading and installing it again from the site. 
First you have you remove the old one (please do not remove it completely because then your existing configuration is also lost)

I tried that after I posted. Though I did not remove the previous installation of VB. During the install I watched terminal output. I noticed and did an 'upgrade'. Anyhow, when I started VB, it lost the XP install ("not accessible") and the W2k3 install wouldn't recognize any keystrokes ( couldn't login).

---

### Post by Pumalite on 2008-06-08
> **bkline said:**
> My main workstation was made unusable by 2.6.24-18-generic, though I had no problems with my other three Ubuntu machines after the upgrade.  Originally I was able to keep going by falling back to 2.6.24-17-generic, but after a little more experimentation in a vain attempt to understand the cause of the failure I have no kernel which doesn't freeze up the machine solid after a few seconds.  Waiting for -19 to hit the main repos.

pumalite@pumalite-desktop:~$ uname -a
Linux pumalite-desktop 2.6.24-19-generic #1 SMP Wed Jun 4 15:10:52 UTC 2008 x86_64 GNU/Linux
pumalite@pumalite-desktop:~$

---

### Post by NJC on 2008-06-09
The only difference I've noticed with -18 is Suspend is now borked. Blinking cursor when I try to awake.

---

### Post by dogbert176 on 2008-06-09
I see that with every kernel update, my root size increase.
It started at 2.5 GB with 2.6.24.16; 6.x after an update to 2.6.24.17, and now over 11 GB with the 2.6.24.18-update.

Can I get rid of the old versions?

---

### Post by lsutiger on 2008-06-13
Anybody fixed any of their problems listed here? Any new problems??
Just trying to keep this thread alive for the content it may provide in helping other fix these problems.

---

### Post by mtantawy on 2008-06-14
so, anybody gave kernel -19 a try yet??

also, is it officially out??

what about the suspend/hibernate problems "ofcourse i mean with those who had problems in the older kernels like -17 & -18"???

iam installing a new clean ubuntu hardy coz kernel -18 broke my system completely last time and i'll install -19 after hearing from you...

so am waitin for suggestions and advices..

Thanks in advance,
Mahmoud Tantawy

---

### Post by figgles on 2008-06-15
-19 is working with minor tweaks. I've had one direct change (sound defaults changed -- fixed by updating the volume preference) one possibly (but not clearly) related issue (OpenOffice updates breaking) and one app-specific issue (virtualBox kernel module). The OpenOffice issue I fixed by removing all OO binaries and libraries through synaptic and reinstalling via the OpenOffice Suite selection. Here's the (good to know) fix for virtualbox: [http://mcb.lessthanthree.se/?p=26](http://mcb.lessthanthree.se/?p=26) 

Would running a fsck at bootup prior to performing a kernel update smooth the whole process?

---

### Post by figgles on 2008-06-15
You mention rhythmbox not working -- do you have any sound working at all? What happens when you go to System > Preferences > Sound and click on the Test button for Sound Events? The Kernel Update changes my sound preferences but I changed my default device in the volumen preference panel, by right-clicking the volume tray, and choosing preferences.

---

### Post by sports fan Matt on 2008-06-15
19 completely borked sound to the point that I couldnt even open volume control on an intel cellron  hp 7920.  It had said "no gstreamer plugins or devices found" so I had to drop back to the 18 kernel..just an fyi...

---

### Post by NJC on 2008-06-16
> **mtantawy said:**
> 
what about the suspend/hibernate problems "of course i mean with those who had problems in the older kernels like -17 & -18"
Identical problem with my machine: -17 and -18 kernels bork Suspend by it works with -16.

---

### Post by Cuppa-Chino on 2008-06-16
> **chmosbrook said:**
> In 18 I lost my wireless.
 In 19 I got the wireless working but could not connect to a signal. I also lost my sound.
Currently I am using 17 which has no problems.

I lost sound and wireless in anything above -17 (ie -18 and -19). 

Have audigy2 and rt61 based card, both worked absolutely out of the box before...

---

### Post by lsutiger on 2008-06-17
I noticed that we had another update from ubuntu for 2.6.24.19.21. I am still at 17, what about you guys and gals?

It seems that this release was not vetted correctly.

---

### Post by Karl S. on 2008-06-17
> **dogbert176 said:**
> I see that with every kernel update, my root size increase.
It started at 2.5 GB with 2.6.24.16; 6.x after an update to 2.6.24.17, and now over 11 GB with the 2.6.24.18-update.

Can I get rid of the old versions?

I don't see why not.

---

### Post by cyoo on 2008-06-18
Kernel -16 was the only kernel with hibernation sort of working. Kernels -17 and -18 failed to wake up after hibernation. However, kernel -19 wakes up with no sound after hibernation (the same problem with -16.) If I reboot -19 (and -16), sound will work but I cannot get the microphone work.

Toshiba Satellite A205-S5825
Updated to 2G RAM

---

### Post by ChrisMcCann on 2008-06-18
Yes, it is causing problems.  I am seeing the CPU go to 100% while
playing java games on the network.  The system is almost unstable.

System:

SONY VAIO  -  Pentium 3 laptop with 256 MB of RAM, 15 GB harddrive.

Swap file in use, running around 100 MB in use.

How do I uninstall
this kernel for the previous version?

---

### Post by rbrick49 on 2008-06-18
no problems here 
msi main board amd 6000+ processor 4gb ram nvidia 8500 video card
regards Ron

---

### Post by rehin on 2008-06-18
I have sound problem on my Toshiba laptop after the update to 19. In fact at my first Hardy installation I had been able to hear sound only with a headphone. Then I had corrected that problem. But now sound has gone completely after updating to 19. What do I miss if I use kernel 18 or 16?

---

### Post by jimbo99 on 2008-06-18
All sorts of issues on multiple machines.  Very unhappy.  They need to better scrutinize these updates for side affects. It should never be their philosophy to leave people high and dry knowing their updates will do this.  This is an OS for the human beings not for the geeky zealots.

---

### Post by jimbo99 on 2008-06-18
> **rehin said:**
> I have sound problem on my Toshiba laptop after the update to 19. In fact at my first Hardy installation I had been able to hear sound only with a headphone. Then I had corrected that problem. But now sound has gone completely after updating to 19. What do I miss if I use kernel 18 or 16?

Please tell us, for posterity, exactly what you did to fix the issue with only hearing sound through the head phones on your toshiba.  Or link your original thread and your solution on that thread.

Please.

---

### Post by rehin on 2008-06-18
> **jimbo99 said:**
> Please tell us, for posterity, exactly what you did to fix the issue with only hearing sound through the head phones on your toshiba.  Or link your original thread and your solution on that thread.

Please.

link to fix the issue with only hearing sound through the head phones: [http://ubuntuforums.org/showthread.php?t=314383&highlight=alsa+fujitsu+headphone](http://ubuntuforums.org/showthread.php?t=314383&highlight=alsa+fujitsu+headphone)

---


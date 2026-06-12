---
title: "update 2.6.27-2-generic broke wireless/nvidia"
date: 2008-08-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by gmclachl on 2008-08-30
Hi,
   I just done an update this morning,including a kernel update (2.6.27-2-generic) after a reboot I no longer have wireless and my nvidia card is not working, both of these were fine with the previous 2.6.27 kernel. 

Anyone encounter the same issues?

George

---

### Post by thaumielx72 on 2008-08-30
I don't use wireless and my nvidia card seems to be ok, but...

I wanted to give Intrepid a whirl and have a couple partitions I haven't used in a while.  I tried it out on my notebook and the install went fine but when I rebooted I could not get more than half the web pages to load.  Particularly anything with Ubuntu in the title.

I gave up on the notebook and fell back to hardy which, of course, works fine.  I figured I'd try again with my desktop and got the same result.  Only a few websites will even try to open.  I also could not get Synaptic to download Any more files.

I rebooted and fell back to 26-5 and now everything appears to be fine.  Just thought you might wanna know.

---

### Post by Slug71 on 2008-08-30
It might be possible that newer drivers came in with it and now you have a confliction.

---

### Post by ubulette on 2008-08-30
yesterday, i decided to reboot to try the new 2.6.27 kernel, and the new nvidia 177.70 driver. Just after reboot, gdm was fine, but X went to safe mode afterwards (vesa 800x600). I spent 5 minutes trying to see what was wrong, found nothing, tried to reconfigure X, nada. Everything looked fine. I remember last time such thing occurred, a 2nd reboot helped... i really hate reboots so i delay them as long as possible, i did it anyway and it helped this time too. No clue why. My usual conf was back on without me doing anything.

EDIT: it was not my usual conf. something changed nvidia into nv, i could have swear i checked that too.
It's all fine now.

---

### Post by gmclachl on 2008-08-30
Well wireless seems to have started working after a few reboots, I can't seem to get it to use the ath9k drivers though.

Nvidia is still a no go. Not sure what the issue is, but I know there are a few posts about issues with nvidia when intrepid moved to 2.6.27 so I will look at those

---

### Post by awam66 on 2008-08-30
A little off topic but my update to 2.6.27 has been held back in update manager.
Any ideas why.

AMD 64 processor.

---

### Post by Slug71 on 2008-08-30
Do you have 2.6.27-1 installed? The 2.6.27-2 updates might only install if you have that and not be available for 2.6.26 users yet? Not sure though.

---

### Post by Slug71 on 2008-08-30
> **gmclachl said:**
> Well wireless seems to have started working after a few reboots, I can't seem to get it to use the ath9k drivers though.

Nvidia is still a no go. Not sure what the issue is, but I know there are a few posts about issues with nvidia when intrepid moved to 2.6.27 so I will look at those


Did you get the nvidia updates that came through yesterday?

---

### Post by awam66 on 2008-08-30
> **Slug71 said:**
> Do you have 2.6.27-1 installed? The 2.6.27-2 updates might only install if you have that and not be available for 2.6.26 users yet? Not sure though.

No I did a fresh install from alpha 4 the other day and after all the updates the new kernel was held back together with cups. I can't print either!

---

### Post by plun on 2008-08-30
> **awam66 said:**
> No I did a fresh install from alpha 4 the other day and after all the updates the new kernel was held back together with cups. I can't print either!

Can you please post the output from this terminal command

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Just answer No if you are unsure about what happens.

Intrepid can break....

---

### Post by Gina on 2008-08-30
> **Slug71 said:**
> Do you have 2.6.27-1 installed? The 2.6.27-2 updates might only install if you have that and not be available for 2.6.26 users yet? Not sure though.27-1 wouldn't work on my P4 system so I returned to 26-5 and updated fron that - no trouble, using it now.

My AMD64 has nVidia graphics and it took two boots to get the driver installed (177) after updating to kernel 27-2.

---

### Post by plun on 2008-08-30
> **Gina said:**
> 27-1 wouldn't work on my P4 system so I returned to 26-5 and updated fron that - no trouble, using it now.



Can you see any errors..  ?

The fsck, /home "mismatch" bug is rather confusing, just to wait
 a minute and then reboot.

---

### Post by wuguai on 2008-08-30
Found the fix to the nvidia drivers:

1. Goto Synaptic Package Manager -> install linux-headers-2.6.27-2-generic or the version of the kernel that you&#341;e running.

2. Hardware Drivers -> Select the Nvidia driver version that works (there are 3 versions)

3. If above fails goto Synaptic Package Manager -> install linux-restricted-modules

---

### Post by Gina on 2008-08-30
> **plun said:**
> Can you see any errors..  ?

The fsck, /home "mismatch" bug is rather confusing, just to wait
 a minute and then reboot.It hung at Bluetooth, both starting and stopping.  Even recovery mode wouldn't work.  But whatever the trouble was, it was fixed for 27-2.

---

### Post by awam66 on 2008-08-30
Here is 

sudo apt-get update
[sudo] password for alistair: 
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_GB
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release [65.9kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release
Get: 3 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages [1225kB]
Get: 4 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages [7914B]
Get: 5 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources [476kB]
Get: 6 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources [2542B]
Get: 7 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages [4537kB]
Get: 8 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources [1966kB]            
Get: 9 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages [199kB]          
Get: 10 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Sources [92.6kB]         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Sources             
Fetched 8572kB in 14s (595kB/s)                                                
Reading package lists... Done

and 

 sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  cups cupsys-driver-gutenprint ghostscript hal libgs8 libmagick10 libsmbios-bin
  linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic ubuntu-desktop ubuntu-minimal
The following packages will be upgraded:
  xserver-xorg-input-synaptics
1 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
Need to get 66.0kB of archives.
After this operation, 12.3kB of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by gmclachl on 2008-08-30
> **Slug71 said:**
> Did you get the nvidia updates that came through yesterday?

Yeah I did. It's working now. It was weird. I tried to re-install the nvidia drivers and it still failed. So I tried the restricted drivers manager and it crashed when I tried to install 177. 

So I selected 173 and it installed ok. Then selected 177 this time it didn't crash and install the 177 drivers. 

When I rebooted I had nvidia drivers were working.

George

---

### Post by douham on 2008-08-30
> **gmclachl said:**
> Yeah I did. It's working now. It was weird. I tried to re-install the nvidia drivers and it still failed. So I tried the restricted drivers manager and it crashed when I tried to install 177. 

So I selected 173 and it installed ok. Then selected 177 this time it didn't crash and install the 177 drivers. 

When I rebooted I had nvidia drivers were working.

George

This has just been my experience exactly. Also while doing the dist-upgrade (thanx Plun, I have been staying away from them for the last few days) my wired connection dropped out a few times before the updates were even being applied.
Nothing from Calc's PPA has came in and OpenOffice 2.4 completely removed.

Doug

---

### Post by caryb on 2008-08-30
I can't use 27.2 as X is totally unusable (remember CGA graphics) & 27.1 now boots to low graphics mode as well, I tried to install the Nvidia beta driver 177.70 but it borks & says it cant install on a Xen kernel (don't have any Xen kernel loaded uname -a Linux stinkpad 2.6.27-1-generic #1 SMP Sat Aug 23 23:19:01 UTC 2008 x86_64 GNU/Linux) So I went to the Nvidia manager in the system tab on the taskbar (KDE4) & it said no Nvidia driver loaded & suggested I run "nvidia-xconfig" at the terminal. I now boot to low graphics mode & when I select continue it will load the Nvidia driver after approx 20 seconds.

This is strange behavior! If I boot to 27.2 it will totally overwrite the xorg.conf & I'm back to where I started.

Any thoughts on this one:confused:

Cary

---

### Post by RIchard James13 on 2008-08-30
Everytime I get a Kernal update I need to manually reinstall the Nvidia drivers using something like this:
```
sudo dpkg -i /var/cache/apt/archives/nvidia-177-kernel-source_177.70-0ubuntu1_i386.deb
```
This is in Kubuntu Intrepid, should not the system automatically do this? If so how can I fix it so it does.

---

### Post by douham on 2008-08-30
> **RIchard James13 said:**
> Everytime I get a Kernal update I need to manually reinstall the Nvidia drivers using something like this:
```
sudo dpkg -i /var/cache/apt/archives/nvidia-177-kernel-source_177.70-0ubuntu1_i386.deb
```
This is in Kubuntu Intrepid, should not the system automatically do this? If so how can I fix it so it does.

Alberto's blog has something about about the current state in intrepid with kernel updates.. [http://albertomilone.com/wordpress/?p=212](http://albertomilone.com/wordpress/?p=212)  
At the moment my experience with the 27-2 kernel and the 177 driver on my Core2 machine and 8400GS graphics card is as mentioned earlier. I'm having all sorts of driver hassles on my P3 1GHz, with TNT2 card (71.7 drivers)

Doug

---


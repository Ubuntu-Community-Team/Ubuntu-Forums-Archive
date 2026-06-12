---
title: "upgrade dependency conflict"
date: 2014-07-15
forum: Installation &amp; Upgrades
---

### Post by frogeyedan on 2014-07-15
trying to use a system that hasnt been used too much [recently] i am having issues with teh update. this is the message i get from the software update program:[INDENT]Your current Hardware Enablement Stack (HWE) is going out of support
on 08/07/2014.  After this date security updates for critical parts (kernel
and graphics stack) of your system will no longer be available.

For more information, please see:
[http://wiki.ubuntu.com/1204_HWE_EOL](http://wiki.ubuntu.com/1204_HWE_EOL)


and when i try:

Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

The following packages have unmet dependencies:

libgl1-mesa-glx-lts-trusty: Depends: libglapi-mesa-lts-trusty (= 10.1.3-0ubuntu0.1~precise1) but 10.1.3-0ubuntu0.1~precise1 is to be installed
                            Depends: libx11-6 (>= 2:1.4.99.1) but 2:1.4.99.1-0ubuntu2.2 is to be installed
                            Depends: libxdamage1 (>= 1:1.1) but 1:1.1.3-2build1 is to be installed
xserver-xorg-lts-trusty: Depends: xserver-xorg-core-lts-trusty (>= 2:1.11) but 2:1.15.1-0ubuntu2~precise1 is to be installed
[/INDENT]
This is an old system that has been updated several times and has multiple destops and window managers, which i like, but it seems to be out of hand.
do i need to delete certain of the above packages?  
(this system has a lot of stuff on it or i would just over install)
thanks 
frogeyedan

---

### Post by Ben_Landvatter on 2014-07-16
I have the exact same error in update manager.

Again in my case it's a re-purposed older pc.

I never really USE Ubuntu, I have this beside my current PC and I tinker.  Would really appreciate a bit of advice with this problem.

[ATTACH=CONFIG]254755[/ATTACH]

---

### Post by terrykiwi83 on 2014-07-16
I think the command you are looking for is:

> 
sudo apt-get -f install


Try that in terminal and report back on the results

---

### Post by Ben_Landvatter on 2014-07-16
I just ran that and this is what I got.

ben@BensLappy:~$ sudo apt-get -f install
[sudo] password for ben: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gwibber-service-identica odbcinst1debian2 odbcinst unixodbc libgif4
  libgif4:i386 liborc-0.4-0:i386 libgstreamer-plugins-base0.10-0:i386
  libgstreamer0.10-0:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I'm not quite sure what I'm meant to do with that.  Thanks for the input!

---

### Post by terrykiwi83 on 2014-07-16
try running

> 
sudo apt-get autoremove
sudo apt-get update && sudo apt-get upgrade


Let us know the outcome.

---

### Post by Ben_Landvatter on 2014-07-16
That ran its course just fine with no errors, but the error persists when trying to update, even after a restart.

Thanks again for the help.

---

### Post by terrykiwi83 on 2014-07-16
In terminal type this, and post the output back.

> 
sudo apt-get install libwxgtk2.8-0 libwxbase2.8-0 wx-common libglu1-mesa libgl1-mesa-glx zlib1g bzip2 gpsd gpsd-clients xcalib libportaudio2


---

### Post by Ben_Landvatter on 2014-07-16
ben@BensLappy:~$ sudo apt-get install libwxgtk2.8-0 libwxbase2.8-0 wx-common libglu1-mesa libgl1-mesa-glx zlib1g bzip2 gpsd gpsd-clients xcalib libportaudio2
[sudo] password for ben: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bzip2 is already the newest version.
libportaudio2 is already the newest version.
libportaudio2 set to manually installed.
zlib1g is already the newest version.
libwxbase2.8-0 is already the newest version.
libwxbase2.8-0 set to manually installed.
libwxgtk2.8-0 is already the newest version.
libwxgtk2.8-0 set to manually installed.
libglu1-mesa is already the newest version.
libglu1-mesa set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libgl1-mesa-glx : Depends: libglapi-mesa (= 8.0.4-0ubuntu0.7)
                   Recommends: libgl1-mesa-dri (>= 7.2)
E: Unable to correct problems, you have held broken packages.

---

### Post by terrykiwi83 on 2014-07-16
Does this work

> 
sudo apt-get install libgl1-mesa-dri


---

### Post by bapoumba on 2014-07-16
Are your repositories stock or are you using any additional third parties or ppa ?
Have you installed hwe-support-status tool as recommended ?

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by Ben_Landvatter on 2014-07-16
Thanks much for the continued replies, it's bed time for me, will check back in on the thread tomorrow.

---

### Post by kansasnoob on 2014-07-16
I don't think you should be seeing that yet unless you have proposed updates enabled which is not a good idea unless you really, really know what you're doing.

But I'm preparing for a mind blowing three week interval of iso/upgrade testing beginning next week:

July 21st thru 24th: 14.04.1 testing (need to squash a few pesky bugs)

July 28th thru 31st: 14.10 Alpha 2 testing

August 4th thru 7th: 12.04.5 testing (ships with the Trusty hardware enablement stack)

I'll know more after August 7th :)

---

### Post by Ben_Landvatter on 2014-07-18
Thanks for the input everybody.  I decided to change the partition layout on this machine and make it an all-linux box, so I did a fresh start. After a fresh re-install and a big update, this problem is completely gone.  Perhaps these tips will help the original poster of this thread can get some help from your input.  

Thanks much!

Ben

---


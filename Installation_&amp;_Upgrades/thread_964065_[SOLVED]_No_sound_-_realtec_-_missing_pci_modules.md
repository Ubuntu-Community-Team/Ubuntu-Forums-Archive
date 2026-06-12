---
title: "[SOLVED] No sound - realtec - missing pci modules?"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by kagy on 2008-10-30
I lost my sound after a clean install of 8.10; i've a Realtec ALC880 onboard sound. All was working fine in Hardy.
I've check out /lib/modules/2.6.27-7-generic/kernel/sound and there's no snd*.ko. there's not even a pci folder.
Is this the cause of it? 
If so how do I fix it? Getting this far has nearly overheated my noob brain.


```
$ uname -a
Linux xcube 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64 GNU/Linux
```
```
$ sudo lshw -c multimedia
*-multimedia UNCLAIMED description: Audio device  
product: IXP SB4x0 High Definition Audio Controller  
vendor: ATI Technologies Inc 
physical id: 14.2                                         
bus info: pci@0000:00:14.2 
version: 01 
width: 64 bits
clock: 33MHz 
capabilities: bus_master cap_list
configuration: latency=64  
```

---

### Post by martrn on 2008-10-30
I do not know the cause of your sound problems.  The amount of times I have needed to rebuild sound drivers (or sound kernel modules) [same thing] means this should just be a matter of rebuilding the sound modules.  Check the other items on this list first.

[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

If you wish to rebuild your sound  drivers (sound kernel modules) just skip to the section that says:

**Using alsa-source**

and :
- Open up a shell: 
- Type ```
sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source
```
 
-Type  ```
sudo dpkg-reconfigure alsa-source
``` 

Now have a big blue dialog box [MODULE-ASSISTANT] and some (left and right keys to choose 'Yes' and 'No', Enter key proceed). and carry on with the instructions located at **Using alsa-source** from

[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

Its not that hard the only difficulty would be matching your sound card up to the alsa matrix [http://www.alsa-project.org/main/index.php/Matrix:Main]("http://www.alsa-project.org/main/index.php/Matrix:Main")

---

### Post by kagy on 2008-10-30
I found why the module are missing, I tried to run the realtek Linux drivers from their website. I've just checked the install script (not that I know much about it) and the first thing the do is remove a load of directories!

From looking at the install log I think that the previous kernel version is hard coded somewhere.. I'm just going to look now...

---

### Post by kagy on 2008-10-31
So realtek script didn't work, neither did purging and reinstalling alsa with apt-get!

Okay, trying to compile from source (virgin territory for me!), I couldn't compile/configure Alsa-drivers-1.0.17 (couldn't find snd-*.*o) so I tried the 1.0.15 that I had on the system from a realtek install. It complied okay but the make returned errors, here's the tail of it.

```
make -C /usr/src/linux-headers-2.6.27-7-generic SUBDIRS=/usr/src/alsa/alsa-driver-1.0.15  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/usr/src/alsa/alsa-driver-1.0.15/acore/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.15/acore] Error 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.15] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [compile] Error 2
```

how do I fix it to use EXTRA_CFLAGS, if that's the problem.

---

### Post by kagy on 2008-10-31
Finally got it working thanks to [http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)

---


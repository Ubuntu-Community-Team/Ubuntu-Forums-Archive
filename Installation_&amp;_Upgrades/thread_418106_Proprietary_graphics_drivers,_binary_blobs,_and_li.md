---
title: "Proprietary graphics drivers, binary blobs, and linux."
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by sdide on 2007-04-22
This posting is a combination of frustaration, tiredness and in generel despair.

I upgraded to Feisty and 3D acceleration did not work, 
ok - so no big deal, the upgrade made me go from 2.6.17 to 2.6.20 and kernel upgrades in generel spawns this problem . So I didn't expect them to work anyways. 
However I was getting pretty well trained at getting them to work again under Edgy. After the upgrade I had to go through various "trial and error" scenarios, reading about other peoples problems and what not. 
Finally after what was something like 4 hours of tampering about, I finally get the fglrx drivers working.
Lets resume a few of the problems i met:

1: feisty installs Xorg 7.20 ... the 8.35 binary blob from ATI can't work with that in install mode, so you need to tell the blob, that its 7.10. 

2: The 8.35 binary blob, worked neither on direct install, nor by building the Ubunty/feisty or Ubuntu/7.04 deb packages and follow the install procedure on the wiki.([http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide))

3. A colleague of mine running Fedora core 6, have exactly the same problems, of course with different solutions. For him, the solution was to go back to the 8.32 driver, which worked for him. After failing here too, both trying the direct install and building deb packages I went on to the - 

4: I then actually began to pacth the source-code and doing make, and make-install to build the fglrx  module  manually, didn't work.

5: 8.36 driver. after trying building the deb packages, and it didn't work, I tried unloading and loading the module, and found out it still loaded the 8.32 built one, so I deleted everything in /lib/modules except the current kernel version 2.6.20.*

5: Finally ran the 8.36 binary with the Xorg 7.10 argument - and it installed succesfully.

But - excuse the language - DAMN ... I know everyone has different hardware and different software history on their machines ... but it simply has to be possible for someone who knows about this these things to wirte a failsafe script, that can install these cursed drivers successfully, given the kernelversion ...

Frustated Ubuntu upgrader.

---

### Post by pepsi_max2k on 2007-04-22
> **sdide said:**
> But - excuse the language - DAMN ...Frustated Ubuntu upgrader.

welcome to linux :lolflag: 

tips for less linux based frustration:

1. Always use a package manager to install anything (especially drivers) wherever possible. It'll make sure it uses the ones that work, so you won't get any problems compiling code and less problems configuring programs.

2. Never upgrade a whole OS. Too much new stuff conflicting with too much old stuff. Clean install's are always preferred.

3. Use Nvidia graphics card. Ok, so they haven't released a single XP driver (for anything less that 8xxx series) in nearly 6 months, and only a couple of linux ones in the same time frame, but the linux world still swears by them. I didn't have to do anything to install my drivers. Not even install them. Just tried to turn desktop effects on, and accept it when it says it wants to load the drivers for me before hand. Compared to what I had to do with ATI in Suse, that's one hell of an improvement.

---


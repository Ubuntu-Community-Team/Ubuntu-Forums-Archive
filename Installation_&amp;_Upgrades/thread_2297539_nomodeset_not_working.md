---
title: "nomodeset not working"
date: 2015-10-04
forum: Installation &amp; Upgrades
---

### Post by matt18 on 2015-10-04
So i ma trying to install lubunutu 14.04 or ubuntu 14.04 to my other desktop. It has a 1900xtx ati gpu, amd 5400+ and 4gb ram. Here is the issue, both live cd's go black right after the splash screen with the dots. I tried setting the install to nomodeset and still no go. I noticed even after the no modeset option, the cli showed a failed to get acpi.. i think that is what it said. What shall i do next?

I am installing onto a 40GB 7200 IDE drive. Bios detects the drive just fine and mem test passes fine.

thanks

---

### Post by matt18 on 2015-10-04
I have tried this and it still goes to a black screen


[LIST=1]
[*]Put your installation media into the computer
[*]Switch on the computer
[*]Press the spacebar as soon as the picture of the keyboard and human display at the bottom of the screen
[*]Choose your language
[*]Select &#8220;Try Ubuntu without any changes&#8221;
[*]Press F6
[*]Select &#8220;nomodeset&#8221;
[*]Press Escape (Esc)
[*]Type i915.modeset=0 xforcevesa
[/LIST]

still no go. Driving me crazy. i just want to install ubuntu and not my winxp. why does linux have to be this complicated haha

---

### Post by matt18 on 2015-10-04
Ok so now i tried to type the follwing in. I noticed that when i hiot f6, selected nomodeset. nothing was being added to boot options. so i actually replaced quite splash with:

nomodeset xforcevesa

no it tries to boot to the installer or the live cd desktop but now it hangs at stopping failsafe boot delay. 

been 15 minutes and still stuck.. hmmm. this really sucks. 

i tried to install on a older system and the funny thing is, it actually loaded the installer:)

haha. 

thanks guys

---

### Post by matt18 on 2015-10-04
ok after more troubleshooting and testing differnt boot options. it seems to hang on the following:

65.958357 drm:radeon_init *ERRO* No UMS support in radeon module!

apparently according to launchpad, there is a bug about this and some kernel versions... now i have no idea what to do. actually, im gonna see if 12.04 will work..

thanks for readin all of this. i hope i am helping others as well

---

### Post by matt18 on 2015-10-04
12.04 does not work either. Goes to black screen as usual. I try the nomodeset option and now it gives me a cpu 0 exceptiin 4 error.  It looks as if ubuntu is not going to instalk on my 8 year old pc

---

### Post by matt18 on 2015-10-05
I know this is a kernle panic, but whats odd is 14.04 will throw a diff error and its not a hardware error. Only on 12.04 does it throw the cpu error. It was running windows just fine until the mbr got screwed up so i just decided to instal ubuntu but that aint workin haha.

---

### Post by matt18 on 2015-10-05
I am at a complete loss. My mobo doesnot have on board gpu so i cant test it out that way. I have no idea what to do now... is there any other info or things i can try??

thanks

---


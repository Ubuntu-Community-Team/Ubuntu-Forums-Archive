---
title: "I'm a little concerned."
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by chrispche on 2010-04-23
I tried to test the beta2. I got no video in the GDM or even Splash. So now I go and download the RC, the same thing. No video on splash or GDM.

My video card is on a Samsung R20 laptop and is ATI Technologies Inc Radeon Xpress 1250.

Where do I report this?

I hope the final version works!

---

### Post by Queue29 on 2010-04-23
> **chrispche said:**
> I tried to test the beta2. I got no video in the GDM or even Splash. So now I go and download the RC, the same thing. No video on splash or GDM.

My video card is on a Samsung R20 laptop and is ATI Technologies Inc Radeon Xpress 1250.

Where do I report this?

I hope the final version works!

The RC pretty much is the final version.

Report it here: [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)
Of course, they've made it difficult to report bugs without using the bug reporting tool nowadays.

---

### Post by alligoodw on 2010-04-23
I have a HP Pavilion laptop with a Nvidia card inside and I can't even install this thing.  When I insert the CD and reboot, the screen is illigible . . . I can't install it.  Seeing that video is such a fundamental element to computing, you would think Ubuntu would have conquered this problem a long time ago; difficulties with hardware and their drivers should be a thing of the past.

---

### Post by waspbr on 2010-04-23
what video card do you have? I have been running on a pavilion tx1320us with a GF 6150Go without any problems...

have you tried the alternate install perhaps?

---

### Post by BrokeMahPC on 2010-04-23
I'm a little concerned too - this release is my first time testing and I wondered if things were always as bad as this? Video drivers is one area that should "just work".
Get info about your hardware and driver:
```
lspci | grep VGA
``````
sudo lshw -C video
```The 2nd command also lists the driver you are using under configuration.

RE your problems:
Have you tried starting in safe graphics mode? If not, press any key at the  initial boot screen, then press F6 and select nomodeset,  then continue to boot.

Also see this thread about applying the above permanently - look at post #18
[http://ubuntuforums.org/showthread.php?t=1451977&highlight=nomodeset&page=2](http://ubuntuforums.org/showthread.php?t=1451977&highlight=nomodeset&page=2)

The problem appears to be with kms (kernel mode setting) which affects some cards.
Some have success with radeon.modeset=0 or pci=nomsi as grub boot parameters.                      
If you do manage to install and boot give the ATI fglrx driver a try look at system->Administration->HardwareDrivers to enable it.
After enabling the driver also run:
```
sudo aticonfig --initial -f
```NOW REBOOT!

more info: have a look at these:
[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)
[http://ubuntuforums.org/showthread.php?p=7996934](http://ubuntuforums.org/showthread.php?p=7996934)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by chrispche on 2010-04-23
I have reported a bug in launchpad to do with my card. Let's hope something get's done.

---

### Post by alligoodw on 2010-04-23
> **waspbr said:**
> what video card do you have? I have been running on a pavilion tx1320us with a GF 6150Go without any problems...

have you tried the alternate install perhaps?

Define alternate install.

---

### Post by pdspatrick on 2010-04-23
> **alligoodw said:**
> Define alternate install.

It's the alternate install disk. Uses text based install instead of GNOME.

[http://releases.ubuntu.com/releases/10.04/ubuntu-10.04-rc-alternate-i386.iso](http://releases.ubuntu.com/releases/10.04/ubuntu-10.04-rc-alternate-i386.iso)

---

### Post by chrispche on 2010-04-23
OK This has been completely resolved by updating GRUB2 and adding "nomodeset", god knows what that does, but it works. Someone on IRC told me to do it. Now I'm running 10.04.

---

### Post by QLee on 2010-04-23
[QUOTE=chrispche]OK This has been completely resolved by updating GRUB2 and adding "nomodeset", god knows what that does, but it works. Someone on IRC told me to do it. Now I'm running 10.04.[/QUOTE]

If you use the "search" function of the forum (and only search this sub forum) with the keyword "nomodeset" you will get some hits of threads to look at that include nomodeset. You would be able to follow some of the progress with the modules at this stage of approaching release and get an idea of what has been happening. Perhaps you might also understand that unreleased software is a "rolling target". Or, you may only want to video card designation as keyword and just read about peoples experience with your exact card.

That person on IRC was likely just trying to get you "up", may not have had time to explain and you might not have asked for an explanation.

---

### Post by Longinus00 on 2010-04-23
> **BrokeMahPC said:**
> 
If you are using an HD card you should be using radeonHD or fglrx.
[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

Wrong, you shouldn't need to use radeonHD. radeon has more features than HD so there's no real point unless there's some specific feature you want. [http://www.x.org/wiki/radeon](http://www.x.org/wiki/radeon)

---

### Post by BrokeMahPC on 2010-04-23
As I understood a recent explanation - radeonHD has power management features that radeon does not have? This was supposed to solve some of the crash issues due to KMS and you could edit your xorg to use the radeonHD driver.
This may not be true, if I'm wrong, I'm wrong, it happens :) - please let me know and I will edit the above post.
(radeonHD has the HDMI support for anyone using a flat screen TV)

---

### Post by chrispche on 2010-04-23
> **QLee said:**
> If you use the "search" function of the forum (and only search this sub forum) with the keyword "nomodeset" you will get some hits of threads to look at that include nomodeset. You would be able to follow some of the progress with the modules at this stage of approaching release and get an idea of what has been happening. Perhaps you might also understand that unreleased software is a "rolling target". Or, you may only want to video card designation as keyword and just read about peoples experience with your exact card.

That person on IRC was likely just trying to get you "up", may not have had time to explain and you might not have asked for an explanation.

So are you saying all that flaffing about, won't be an issue in the final release?

---

### Post by QLee on 2010-04-23
[QUOTE=chrispche]So are you saying all that flaffing about, won't be an issue in the final release?[/QUOTE]

That is the "hope", ...and as far as I can tell, the purpose of testing.  It appears to be a big enough problem, and widespread enough, that I do feel confident that if will be worked on until a solution is found. It's been my experience that as video interfaces have evolved, there have continued to be problems implementing the changes in GNU/Linux, although, it seems better these days. I can't say if your issue will be fixed at release, but for now the workaround seems to give you a usable system, eh?

---

### Post by Longinus00 on 2010-04-23
> **BrokeMahPC said:**
> As I understood a recent explanation - radeonHD has power management features that radeon does not have? This was supposed to solve some of the crash issues due to KMS and you could edit your xorg to use the radeonHD driver.
This may not be true, if I'm wrong, I'm wrong, it happens :) - please let me know and I will edit the above post.
(radeonHD has the HDMI support for anyone using a flat screen TV)

[LIST=1]
[*]I'm almost certain radeonHD has the same or less power management features than radeon (radeon had power management before radeonHD did). According to the x.org wiki you have to explicitly enable radeonHD's power management and it might cause the fan to run full speed. [http://www.x.org/wiki/radeonhd](http://www.x.org/wiki/radeonhd)
[*]radeon also has HDMI support. The only difference was that radeonHD has HDMI audio support but the newest radeon drivers also have this feature. [http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)
[/LIST]

---

### Post by BrokeMahPC on 2010-04-23
ok I'll scrub that - hope there is some detailed video documentation updates/how to's - some people are having awfully complicated video woes.

---

### Post by Longinus00 on 2010-04-23
> **BrokeMahPC said:**
> ok I'll scrub that - hope there is some detailed video documentation updates/how to's - some people are having awfully complicated video woes.

That isn't to say there aren't any bugs in the current version of radeon that might make people want to run radeonHD instead. It's just that feature wise radeon and radeonhd are pretty comparable. In the long run it seems like radeonHD might eventually get dropped/merged into radeon (maybe around when everything is done with gallium?).

---

### Post by priegog on 2010-04-23
@chrispche and alligoodw and possibly others in this thread.
There is a crazy bug right now with some nvidia and ati cards that prevents the live CD from even booting (not only that, but if you install the system it won't boot either. For some of us not even with boot parameters like nomodeset or xforcevesa).
Check it out in [this thread]("http://ubuntuforums.org/showthread.php?p=9034838") and/or [the associated bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539878") and see if yours' is the same problem and please subscribe to it... we really need people making noise and saying this is a real problem affecting a number of people, because even tho the bug has been marked as "high importance" noone is taking care of it.
And I predict it will affect A LOT of people when it suddenly gets released but not enough people complained in the development phase.

---

### Post by chrispche on 2010-04-24
> **QLee said:**
> That is the "hope", ...and as far as I can tell, the purpose of testing.  It appears to be a big enough problem, and widespread enough, that I do feel confident that if will be worked on until a solution is found. It's been my experience that as video interfaces have evolved, there have continued to be problems implementing the changes in GNU/Linux, although, it seems better these days. I can't say if your issue will be fixed at release, but for now the workaround seems to give you a usable system, eh?

Indeed.

---

### Post by waspbr on 2010-04-24
actually, If i remeber correctly I did have some issues with the liveCD when trying to install it in my HP, what happened was that somewhere along the boot process the screen would just go blank. I tried doing ctrl + alt + F2 followed by ctrl + Alt + F7 but that would just get me to the GDM screen, which I didn't know how to bypass.

So I used the alternate CD to install it, it went well. then after installing I had a similar issue and used the  ctrl + alt + F2 followed by ctrl + Alt + F7 approach, which would get me to the GDM successfully. 

but that was some time ago and the problem just corrected itself, so I didn't bother reporting it.

---


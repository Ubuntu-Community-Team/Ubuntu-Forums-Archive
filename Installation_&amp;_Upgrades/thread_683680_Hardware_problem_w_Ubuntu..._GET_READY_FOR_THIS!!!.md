---
title: "Hardware problem w/ Ubuntu... GET READY FOR THIS!!!"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by SkittleLinux18 on 2008-01-31
All you experts out there who are dying for an actual challenge, here it is!! (I promise to keep this as concise as I can to cut down on excess verbiage and unnecessary reading.)

I have a laptop that I am dual booting with (XP and Linux). Initially, I had PCLOS on there, but three weeks ago decided to put Ubuntu on. I had some initial trouble installing the GRUB, but that got worked out only to present the real reason for this post.

Before I continue, I think it is important to mention that another post of mine deals with this stuff: [http://www.linuxforums.org/forum/ubu...d-install.html](http://www.linuxforums.org/forum/ubu...d-install.html)

(You will have to read through the initial posts of the thread as it had started due to something else and evolved into the problem it is now; at which time it was suggested I start a new thread.)

Ok, so here we go. When I finally got past the GRUB issues, and got Ubuntu installed for the first time, I went to do the initial first-boot. (Ubuntu installed on partitions: hda2, hda4, and hda5). I couldn't get to the graphical splash screen. Instead, once I got past GRUB, the screen would just black out. So I would ALT-F1 into the verbose mode. The message I was getting was this:

10.755109] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
Loading, please wait...
kinit: name_to_dev_t (/dev/disk/by-uuid/6e84da2f-9406-4f87-8a4c-530821e5d0f8 ) = hda5 (3,5)
kinit: trying to resume from /dev/disk/by-uuid/6e84da2f-9406-4f87-8a4c-530821e5d0f8
kinit: No resume image, doing normal boot...
[ 194.136576] Buffer I/O error on device hda2, logical block 109
[ 194.136576] Buffer I/O error on device hda2, logical block 110
[ 194.136576] Buffer I/O error on device hda2, logical block 111
[ 194.136576] Buffer I/O error on device hda2, logical block 112
[ 194.136576] Buffer I/O error on device hda2, logical block 113
[ 194.136576] Buffer I/O error on device hda2, logical block 114
[ 194.136576] Buffer I/O error on device hda2, logical block 115
[ 194.136576] Buffer I/O error on device hda2, logical block 116
[ 194.136576] Buffer I/O error on device hda2, logical block 117
[ 194.136576] Buffer I/O error on device hda2, logical block 118

Also, somewhere embedded in this message (I forget exactly where, but definitely before the I/O error repeats), I get a message about "unexpected inconsistencies with the filesystem." So it tried to run fsck. But it failed every time, and that's when it went into the "normal boot," causing the I/O error messages to begin repeating.

This part of message would repeat until it finally stopped. After 60 hours of trying to fix the problem, I gave up and decided to reinstall PCLOS. After getting it installed, another user on this forum had convinced to stick it out with Ubuntu. I conceded and went to install Ubuntu with the Alternate Install cd. I figured if he was going to help me, I had better get as far as I could on my own. Well, to our absolute astonishment, Ubuntu installed and booted just fine!! We figured it was hardware failure and just decided to be happy that it was working.

Well, two nights ago, I was working in Ubuntu. I had upgraded and installed some new packages through Synaptic. One of them being DKMS. Once I was done with Synaptic, Ubuntu just froze up. I held the power button down until the computer restarted. Except this time, all I got was a blank screen and nothing worked. By nothing, I mean every key combination I could think of, the power button, ect. It was just locked in a blank screen. So I unplugged the power cord and pulled out the battery. Put it all back in and tried booting again.

It was able to boot, but it gave me an error message before the computer could even get to the POST. It said that CMOS was wrong and asked me to boot into it or reset default settings. I chose the latter. Then I was brought to the GRUB screen and I selected Ubuntu. I got to the graphical splash screen for like 5 seconds and then the screen blanked. I did ALT-F1 to see the problem. It was identical to what I was getting the week before, except a little different. The message that would repeat had something to do with superblocks and other failures.

I don't remember the exact message, and I will get to that in a second. At this point of the story, I started trying the LiveCD for Ubuntu, LinuxMint, Sabayon, and openSUSE. None of them worked!! I got the same funky message I was getting the second time. So I said, "forget it," and installed PCLOS. That install worked fine, once again.

Since then, it was suggested that I start a new thread to address these problems. I had already installed PCLOS, so I just loaded up the LiveCD for Ubuntu to get the exact error message I was getting the second time (I'm getting to why I forgot it now). However, the LiveCD booted just fine for both Ubuntu and LinuxMint. So I couldn't see the error message and I don't remember it.

The last note I will add is that every time Ubuntu worked was after a PCLOS install. That is so weird!! It's almost as if whatever the problem was/is got fixed by virtue of the PCLOS install; at least until Ubuntu would decide to break again.

Anyway, let the suggestions flow!!

And feel free to revert back to the other thread I gave the link for above. It will have other details. Like I said, you will have to skim through the first 7 or 8 posts until you get to point where these issues pick up. Secondly, I don't know how good it will be since everything is working and I am not in the mood for wiping my PCLOS install just to get Ubuntu to break again ONLY for the sake of running diagnostics. Having said that, let's see what all of you have to say and maybe something worth it will come up.

---

### Post by chewearn on 2008-02-01
The link you put up there don't fully work; get truncated or something.

---

### Post by SkittleLinux18 on 2008-02-01
Yeah, you're right it doesn't. Well, we did figure out on another forum that it is definitely hardware problems, but nothing is wrong with my hardware. It's a matter of compatibility. Ubuntu just doesn't like my current configuration on my laptop. So I am going to leave PCLOS on it and install Ubuntu on my desktop.

If you still want to check out that link, try this:

[http://www.linuxforums.org/forum/ubuntu-help/113051-grub-failed-install.html](http://www.linuxforums.org/forum/ubuntu-help/113051-grub-failed-install.html)

---

### Post by SkittleLinux18 on 2008-02-02
In case anybody comes across this, know that this issue has been solved. I used the Alternate Install CD and everything worked like a charm!

---


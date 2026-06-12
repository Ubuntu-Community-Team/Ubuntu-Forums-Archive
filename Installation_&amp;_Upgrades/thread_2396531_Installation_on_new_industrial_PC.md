---
title: "Installation on new industrial PC"
date: 2018-07-17
forum: Installation &amp; Upgrades
---

### Post by rewolff on 2018-07-17
Hi, 
About 20 years ago I installed Suse Linux on an industrial PC. That PC needs rejuvenation so a new PC has been acquired.. Since then I've come to my senses and decided that I want to use Ubuntu from now on. 

The PC boots the Ubuntu 18.04 USB stick, and when I hit "install" it shows the ubuntu logo (human <-> computer) or when using server install images, just a cursor in the top-left corner. I have now let the "blinking cursor" sit for over half an hour without any change, and then forced a reboot. This time I ticked some of the "more options" items, that I thought might help with compatibility in some cases. Again nothing but the blinking cursor. 

The CPU is an Intel CORE 2. 

I have managed to get a 32-bit install up-and-running by installing an i386 image onto a harddisk and swapping the harddisk. The other PC has similar problems starting the AMD64 install. 

I started out using usb-bootdisk-creator-gtk to create a bootable USB stick, but I have since switched to writing the ISO directly to the USB stick. 
I have the following images that I have tried the past few days:> 8388f7232b400bdc80279668847f90da  mini_amd64.iso
c7b21dea4d2ea037c3d97d5dac19af99  mini_i386.iso
129292a182136a35e1f89c586dbac2e2  ubuntu-18.04-desktop-amd64.iso
1413c9797dbfa1e57fabfb5c91cfb96f  ubuntu-18.04-server-amd64.iso

Looking at: [https://www.ubuntu.com/download/alternative-downloads](https://www.ubuntu.com/download/alternative-downloads) it seems as if the 32-bit version is being deprecated, and as this system is likely to get a long life again, starting out with a deprecated install is not recommended..... 

The "perform memtest" option shows "loading ...<somthing> OK" and then hangs. 

What am I doing wrong?

---

### Post by SeijiSensei on 2018-07-17
Modern machines use UEFI for booting.  If yours does too, you should try creating a bootable USB drive on a Windows machine using [Rufus]("https://rufus.akeo.ie/").  Also most any modern machine supports a 64-bit architecture.  I haven't installed an i386 version on physical hardware for years.

---

### Post by rewolff on 2018-07-17
I don't have windows machines. 
This machine (they didn't ask me what machine to get), seems to have a BIOS from 2013,  don't think it is using UEFI. 

My new laptop DOES use UEFI. Indeed it even uses "secure boot". It successfully boots the usb-creator-gtk  created USB stick with the 64-bit desktop version. That one was installed one or two weeks before this issue from the same downloaded iso image.

---

### Post by oldfred on 2018-07-17
Exactly which cpu?
Is it core2 duo as that is 64 bit. My 2006 laptop was Intel Core2 T5500 and I have 64 bit Ubuntu on it. I retired it a couple of years ago, but installed 16.04 64 bit desktop just to see if it worked. It had 12.04 and seemed a bit faster with 16.04.

What video card are you using. The nVidia cards need nomodeset boot parameter. Press any key with the initial screen and f8 to add boot parameter(s).  

There are now two server install versions. The newer graphical version still has some limits.
[https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes#Ubuntu_Server](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes#Ubuntu_Server)

---

### Post by rewolff on 2018-07-17
I tried something that amounted to the "nomodeset"  that you mention through the "F6" menu. 

I have the impression that the intention was to show the kernel commandline at the bottom of that screen, but it looks as if it drops off of the screen at both ends. I did not see the "nomodeset" argument appear there, so I'll try the F8 tomorrow. 

Twenty years ago the core software ran just fine on a pentium 133. So even if we have a 5 year old CPU/bios, it's going to be plenty fast. The baseboard is LGA775 IIRC. Does that tell you anything? I'm not with the machine right now, so I can't check the BIOS boot messages for you. It defintively has two cores. 

I googled LGA775 and core 2 duo and found a "discontinued" processor on the Intel site. The goal of this whole exercise is to move to "spare parts can be obtained off-the-shelf"...

---

### Post by oldfred on 2018-07-17
My older BIOS desktop used the LGA775 with core2.
Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
That originally was from 2006. The nVidia card blew its capacators and I replaced motherboard, power supply & video card in 2009. By 2011 I was thinking of a new system, but bought a low cost 64GB SSD for booting and that made system fast enough, that it was another 3 years before I got a new system.

New parts, if available, are likely to be more expensive. But used parts may be available, but quality may vary.

I think even the system I built 2 years ago is now has obsolete parts. And RAM tripled in price.

---

### Post by rewolff on 2018-07-18
OK. Checked the CPU. It is an E7400: [https://ark.intel.com/products/36500/Intel-Core2-Duo-Processor-E7400-3M-Cache-2_80-GHz-1066-MHz-FSB](https://ark.intel.com/products/36500/Intel-Core2-Duo-Processor-E7400-3M-Cache-2_80-GHz-1066-MHz-FSB)
Intel says it has 64-bit instructions. 

I tried a few more images. 16.04 server, 14.04 server and the 18.04 mini iso for 386. All of them behave very similar: nothing happens until the screen clears and I get a single blinking cursor in the top left corner. On the mini iso I figured out how to edit the commandline. I removed the "quiet" and the "---" and now I get "loading linux .." and "loading initrd ..." and then about 47 seconds later, the blank screen.

---

### Post by oldfred on 2018-07-18
What video card/chip?
If in nVidia, you need the nomodeset boot paramater. I normally suggest replacing quiet splash as then you also see boot process and if other errors.

---

### Post by rewolff on 2018-07-18
I have now booted the HDD that was installed on another machine. But it would certainly be nice to be able to boot the machine itself using an USB stick. For recovery should anything go wrong. 
> 00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
The CPu is reported as: 
> model name      : Intel(R) Core(TM)2 Duo CPU     E7400  @ 2.80GHz

Someone mentioned "F8". When I boot the memory stick, it asks something about language first and then gives me a few options. "install Ubuntu" is the first. And below there is a list of function keys. F1 is help. F6 allows me to set a few flags. F8 seems to do nothing.  I have been able to tick stuff like "expert mode" and "nomodeset" but I don't see the "currently active commandline" change in response to the flags I set. When I have set the tickmarks, how do I return to the menu to activate those settings? I use "esc" and when I hit F6 again, the previously set ticks remain, so I am thinging I did not abort the whole "setting boot flags" thing. Or should I save-and-apply with a different key?

On the MINI.iso I was able to edit the commandline. When I remove "quiet" and "---" I get "loading Linux.gz" and "loading initrd.gz" and then after > 45 seconds the blank screen.

---

### Post by oldfred on 2018-07-18
If Intel video you should not need nomodeset.
My core2 system just worked, but I have not tried newest Ubuntu since old desktop is now missing parts and has not booted since 14.04.

Some parameters to experiment with.
        i915.i915_enable_rc6=1 
            Intel Video
[http://askubuntu.com/questions/496944/after-using-boot-repair-i-cannot-change-screen-resolution/497712#497712](http://askubuntu.com/questions/496944/after-using-boot-repair-i-cannot-change-screen-resolution/497712#497712)
Force Intel Video mode as boot parameter in grub menu - Must change to your screen size, not 1280x1024
video=1280x1024-24@60 
    
       Installer BIOS screens shown and other boot parameters
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by rewolff on 2018-07-18
I burned a DVD. 

It stops doing stuff on the screen a few times but just as I was deciding: "its hung, lets hit the reset", it continues. 

Using the DVD it took only 15-20 seconds to go to the "screen with just the cursor", while I timed it at 47 seconds before when running from the USB stick. That screen now went away after a while, but running from the USB stick  I left it over half an hour, so I'm pretty sure it crashed somehow in that case. 

What I value about Linux is that when things go wrong, it usually helps you figure out what goes wrong.  When "Windows 10" tells you: "Timeout waiting for a DHCP response", the experts apparently know "this means you need to type ipconfig/renew" or something like that. 

The nice-and-clean boot procedures that don't show any clutter are nice when things go right, but highly annoying when it fails without any hint as to what went wrong. 

The install finished, I rebooted and... it's now been sitting at Ubuntu ..... for 5 minutes. The dots stopped moving 5 minutes ago. Sigh. 

Do you think it is say fsck-ing my (freshly installed) disk and that I need to give it another hour or so, or do you think it is crashed? Update: screen went black. Neither mouse or keyboard brings back the screen.

I now booted into "recovery mode" to install ssh, I then typed "apt upgrade" because it was telling me it needed to upgrade some 200 packages. Fetching was quick, (close to the speed of my internet connection: )
> Fetched 66.9 MB in 1s (45.7 MB/s)                   
Then it started doing stuff. After 10 minutes it is showing a progress bar at 5%. System load according to "top": 0.00. 

Hmm. OK. recovery mode and install ssh is good, recovery mode and apt-get upgrade is not.

Update: after finishing the upgrade, I did an "apt remove xwayland". That seems to have fixed the "hangs with 'Ubunutu ...,,'  on the screen" problem. I now get a login prompt.

I was "told" [https://blog.ubuntu.com/2018/01/26/bionic-beaver-18-04-lts-to-use-xorg-by-default](https://blog.ubuntu.com/2018/01/26/bionic-beaver-18-04-lts-to-use-xorg-by-default) that bionic would not use wayland....

---


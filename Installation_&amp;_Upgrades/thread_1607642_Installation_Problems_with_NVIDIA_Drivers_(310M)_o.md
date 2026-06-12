---
title: "Installation Problems with NVIDIA Drivers (310M) on a Dell Vostro 3300"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by Casper315 on 2010-10-28
Hello,
I have a Dell Vostro 3300, i5 460 processor with a NVIDIA 310M Graphics Card. I'm doing a KUBUNTU 10.10 (Maverick) install with the following results.[INDENT]      The Live CD boots just fine to, "TEST," or "Install." Installation goes fine. However, the graphics card being used is the Intel i915. 
[/INDENT][INDENT]      I have tried installing the NVIDIA drivers directly from the, "Additional Drivers," tool and after the reboot I get through the boot screen to the console. I try to manually startx and I get the errors, "no device found," "no screens found."
[/INDENT][INDENT]      The second install I tried purging and blacklisting the nouveau drivers and entering safe mode. Then using apt-get install nvidia-current. After that, nvidia-xconfig. Same results.
[/INDENT][INDENT]      The third attempt I re-installed and this time downloaded the drivers from the Nvidia site (version 256.53). Blacklisted nouveau, remove all nvidia, updated initramfs, etc. The install went fine however I still end up at a console after boot with the same messages as above. No device found, no screens found.
[/INDENT][INDENT]      I've tried searching through the forum and web and have tried things like adding the modset option along with many other hacks, tips and fixes. still, no go.
[/INDENT][INDENT]      I can live with the Intel graphics for now although I lose 512MB of memory. Unfortunately there is no way to disable or change this set-up in the BIOS. I've seen quite a few bug reports at Launchpad:
[/INDENT][INDENT][INDENT]           1. Is this something I should just wait til a fix comes? **Will** a fix come? 
[/INDENT][/INDENT][INDENT][INDENT]           2. Is there, or will there be an official Updated Ubuntu Guide for Maverick         to install NVIDIA drivers with this tecnology?
[/INDENT][/INDENT][INDENT][INDENT]           3. Lastly, is there anything else I should try??
[/INDENT][/INDENT]Any opinions or comments (constructive) would be greatly appreciated!!! 
Thank You All Very Much!

---

### Post by efflandt on 2010-10-28
Does lspci show nvidia video?  Because someone else was endlessly trying to install nvidia drivers when all indications were that they had Intel video.

Not sure if the default nvidia version 260.19.06 supports the 300M series (since there have been many threads about that), but 260.19.12 is supposed to. [http://www.google.com/search?client=ubuntu&channel=fs&q=nvidia+260.19.12&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=nvidia+260.19.12&ie=utf-8&oe=utf-8)

Not sure how to undo what you have done (short of reinstalling).  But if you can get Ubuntu to boot with default drivers, nvidia 2.60.19 is in the x-swat ppa repositories [http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

But an easier way to install nvidia without knowing exact package name (assuming you are connected to internet) is:
[FONT=monospace]
[/FONT]**sudo add-apt-repository ppa:ubuntu-x-swat/x-updates**

**sudo apt-get update**

Then go to System > Administration > Additional Drivers and see if it comes up with nvidia (if not, you may not have nvidia).  Activate that and reboot after it is finished.  That should install both nvidia-current which should include both the 260.12.19 nvidia-graphics-drivers and nvidia-settings.

PS: Then you might want to use Synaptic to update nvidia-current-modaliases, because the above did not seem to do that automatically (or maybe Update Manager would do that next updates)

---

### Post by Casper315 on 2010-10-29
Hello efflandt.[INDENT]Thanks so much for taking time to write a response I appreciate it!! I can't do a lspci command on the Vostro right now because it is down. I have to do a re-install and wanted to do some more research first. I did do the lspci command and I know I have the 310m Graphics Card. As a matter of fact, when I tried the first install, I installed the Broadcom Drivers and it also said that I had to enable the drivers for the NVIDIA Card (for 2D or 3D effects) as well. When I tried this I got what I stated earlier, boot screen to console, tried, "startx," command and get the message, no device found and no screens found. 
[/INDENT][INDENT]I didn't say this above, but on one of my attempts I updated the repositories first using x-swat/x-updates. I came up with the same problem.
[/INDENT][INDENT]I can print your post and give it a re-try. I have nothing to loose at this point. It's funny because even when I did my first boot BEFORE I installed any NVIDIA Divers I saw the message: Nouveau found ---- but can't enable because it can't get device config (something to that effect). So even the Nouveau drivers don't set-up properly.
[/INDENT][INDENT]Oh, well, it's always something :)
[/INDENT]Again, thanks for the response and help!!!

---

### Post by leonpf on 2010-11-05
[COLOR=#000000]Good  morning everybody, I'm having the same problem above, I bought a Dell Vostro  3500 notebook with a core i5 64bit with Geforce 310M and I cant  install it. [/COLOR]I searched on forums, lists, in many places, several tutorials but nothing helped.
I tried using the versions:
NVIDIA-Linux-x86-260.19.12
NVIDIA-Linux-x86-195.36.24
And  some others, but none worked, I tried to activate using System>  Administration> Additional Drivers, but when I restart it does not  enter in graphic mode. The error is "no screens found."
I do not know what else to do, I bought the notebook on Monday and already Friday. I love Ubuntu and I would not replace it, but without the video card working properly I have no other alternative.
If someone can help ...

I am with Ubuntu 10.10 64bit

Thanks guys

---

### Post by yorik on 2010-11-24
Same problem here, trying to investigate ( [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/643895](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/643895) ) but not much luck until now...

---

### Post by leonpf on 2010-11-25
Good morning, after trying many times and unable to function correctly my video card I quit Ubuntu.
I'm using another distro that automatically recognized my card and I'm very happy in this new community. I  had the pleasure of using Ubuntu since version 7.04 and always  following the updates and hoping for news, I saw the Ubuntu grow, and  saw that things will change in that I disapprove. Thanks for everything.

;)

---

### Post by aalex85 on 2010-11-26
> **leonpf said:**
> Good morning, after trying many times and unable to function correctly my video card I quit Ubuntu.
I'm using another distro that automatically recognized my card and I'm very happy in this new community. I  had the pleasure of using Ubuntu since version 7.04 and always  following the updates and hoping for news, I saw the Ubuntu grow, and  saw that things will change in that I disapprove. Thanks for everything.

;)
Could you please tell us which distro?
Thanks.

---

### Post by leonpf on 2010-11-26
[COLOR=#000000]Yeah  sure, I'm using Mint 10, based on Debian and Ubuntu, But It Recognized  my card automatically activated When The driver and functioned Normally.
[/COLOR]The staff is very receptive and I'm using the system well.
Again thanks to all the Ubuntu community is all the knowledge i had while I was here.

Greetings

---

### Post by azuluaga on 2010-11-28
Hi leonpf.

I've just installed Linux Mint 10 (Julia) on my Dell Vostro 3400 but still have the same problems with the NVidia video card.
After the restricted drivers installation the graphical environment doesn't start and only works by removing the /etc/X11/xorg.conf file, so it starts using the integrated intel video card.

Did you do any other configuration or a different installation type?

Regards.

---

### Post by leonpf on 2010-11-29
Hi, I have no idea, I just active the diver ad works nice.

Best Regards

---

### Post by aalex85 on 2010-11-29
Tried to install **Mint on my Vostro 3300 and as I expected nothing changed**: after activation of nvidia driver X error "screen not found". The only positive aspect of Mint is that I end up on a terminal and not on blank screen, still have to remove nvidia-common and erase xorg.conf to have again X working.

---


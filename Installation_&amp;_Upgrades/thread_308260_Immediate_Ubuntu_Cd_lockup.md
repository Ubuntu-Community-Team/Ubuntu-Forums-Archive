---
title: "Immediate Ubuntu Cd lockup"
date: 2006-11-27
forum: Installation &amp; Upgrades
---

### Post by cdawg on 2006-11-27
Hi All.

I just got a new laptop, a Compal HEL80. I have been having problems installing Ubuntu or booting the livecd for that matter.

I burned a livecd of Ubuntu 6.10. I boot to the cd and the screen comes up with the options like Memory Test and Install Ubuntu (maybe not exact phrase). when i press enter and select the top option to Install Ubuntu, it says "loading Linux kernel" and just locks immediately. The cd spins and it just sits there. Never making any progress. 

I have tried every option in the list, even memtest locks up.

I have tried adding options to the kernel like "noapic", "nolapic", and "apci=off". No change. 

I have burned more cds than I can count and have tested them with other machines. They work, just not on my laptop.

I have installed the latest firmware for my laptop. No change.

Heres the weird thing. I have tried SuSe, Fedora, Ubuntu, Kubuntu, DSL, and Gentoo. 

Of these, Ubuntu and DSL fail to boot. All the others boot fine. Kubuntu even works which leads me to believe there is a major difference between the default kernel in Kubuntu and Ubuntu. 

I am a gnome guy and I have been running Gnome on top of KDE for a while, however its just not the same [-(  and I'm desperately wishing for Ubuntu.

My conclusions: My Disk drive is fine seeing as how other distros load fine. There is some kind of specific kernel option that my machine doesn't agree with.

Ive been trying to solve this for a while and am at a loss.](*,)  Any hints would be greatly appreciated.

---

### Post by dcstar on 2006-11-27
> **cdawg said:**
> Hi All.
.......
Ive been trying to solve this for a while and am at a loss.](*,)  Any hints would be greatly appreciated.

Have you tried a 6.06 CD?

---

### Post by cdawg on 2006-11-28
I have tried 6.06 LiveCd, the 6.06 alternate cd, Xubuntu 6.06 and 6.10 Livecd. 

Kubuntu 6.06 Seems to work however. What would the difference be?

---

### Post by kvonb on 2006-11-28
I may be wrong, but as a workaround you can install kubuntu, then in a terminal type:

sudo apt-get install ubuntu-desktop

I believe that will install the gnome stuff (although it may take a while to download!), then logout and select gnome from sessions (bottom left menu), save it as default if it works.

Regards, Kev :)

---

### Post by cdawg on 2006-11-28
Thanks Kvonb

I am currently running Ubuntu with gnome at the moment. It does work I agree, however there are inconsistencies with the standard Ubuntu. The kernel version seems to be different and will not update on it's own. Also installing beryl on top of this kind of setup does not work well. I have found several strange problems which I can only assume are from the mixing of ubuntu-desktop package and Kubuntu install. 

Alot of the software just runs and gives strange behavior. Enough to make me use windows until I get Ubuntu Installed. 

This is my motivation to get Ubuntu installed. 

Does anyone know maybe if kubuntu and ubuntu use different kernels for the livecd what would cause this? If so is there a way to make my own cd? Are there any kernel options I can try that I havent already?

Thanks for your suggestions!

---

### Post by cdawg on 2006-11-29
Ok, I worked around this problem by using the Ubuntu live DVD. No idea what the difference is, however I'm happy, i got my Ubuntu. Thanks everyone for your help.

---

### Post by kwilliam on 2007-03-07
How well does Kubuntu run on a Compal HEL80?  Does it hibernate, webcam work, microphone, volume control, touchpad, bluetooth, etc work?  (Is there anything that doesn't work?)  I've been searching ubuntuforums for info on the Compal HEL80 and the posts haven't been very encouraging so far.  (I'm considering buying one from powernotebooks.com)

---


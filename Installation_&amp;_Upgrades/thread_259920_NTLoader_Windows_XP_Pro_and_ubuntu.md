---
title: "NTLoader Windows XP Pro and ubuntu"
date: 2006-09-18
forum: Installation &amp; Upgrades
---

### Post by onewisp on 2006-09-18
Hi,

I have research countless hours reading regarding boot.ini and lilo regarding this subject. I am trying to install ubuntu 6.06 into the 3rd partition (the first partition being used by Win XP and second by linux swap).

Now the problem is when I tried booting it from NTLoader it says HAL.dll not found. This is probably because I have not set up Lilo in my ubuntu partition. So how can I install lilo inside the 3rd partition? I have used BootPart program to create the linux.bin file. All I need is to get lilo to be install inside the 3rd partition. Please help linux experts! I am a linux newb. :) Thanks for all those who responds.

---

### Post by bigken on 2006-09-18
why dont you use grub instead and let ubuntu do it for you this creates a boot menu and you select which os you want to boot ;)

---

### Post by onewisp on 2006-09-18
It's because I am more familiar with Windows XP. Is there an easy way to install lilo on my current linux partition? How can I access it if there is no lilo install there?

---

### Post by onewisp on 2006-09-18
> **bigken said:**
> why dont you use grub instead and let ubuntu do it for you this creates a boot menu and you select which os you want to boot ;)

I can't even find where to select Grub installation. When live cd finished booting and entered into ubuntu, i clicked install on the desktop and choose the partition where i want to install it to. I click next, next next and finish. I still do not have grub or lilo option to install. Am i missing something?

---

### Post by louistan3 on 2006-09-18
i believe that when you install ubuntu.. it installs grub with it.. so i thnk its automatic.. maybe u ddnt install it right? just a thought.. :D

---

### Post by onewisp on 2006-09-18
> **louistan3 said:**
> i believe that when you install ubuntu.. it installs grub with it.. so i thnk its automatic.. maybe u ddnt install it right? just a thought.. :D

After the live cd goes into the ubuntu desktop, I clicked install. Is there anything else am I suppose to do? I still don't know what I need to do to install ubuntu. I have installed it 3 times and it still goes into Windows XP partition. There is no option to install lilo nor grub.

---

### Post by bigken on 2006-09-19
I dont think that it is installing properly if I were you I download the 
[**Alternate install CD**]("http://se.releases.ubuntu.com/6.06/")

this gives you total control of the install procedure ;)

---

### Post by onewisp on 2006-09-19
I did download the alternate version and tried to install it from there. It finished installing it yesterday but it seems that ubuntu keep freezing after finish loading the desktop. I have AMD64 3500+, Radeon 9600, and 2GB memory. I am not sure how to fix it. I also screw my MBR with lilo. There was amd-generic package that it cannot be found during installation which ended up with a corrupted lilo on my first try. I tried installing everything over from there using grub but it still keep booting lilo.

Now I am in the process of reinstalling win XP since installing a corrupt lilo, it won't boot any more.

---

### Post by bulldog on 2006-09-19
What's the thing with LILO?

Where did you get it from?

Ubuntu install GRUB not LILO,so I wonder.............

---

### Post by onewisp on 2006-09-19
I installed lilo after I burned my alternative cd. At this time, i have already installed uBuntu using the live cd. Anyway, before finishing up the installation, it says "linux-amd-generic" package not found or something, and the installation cannot be completed.

From there, I tried to delete the whole partition and reinstall ubuntu with GRUB. For some reason after the installation ended the same way (saying "linux-amd-generic" package, installation failed).

When the bios tried to load the MBR, it loaded lilo but freeze in between. 

I formated and reinstall again with lilo (so that I can boot with NTLoader), but this time, after lilo has loaded, the screen freeze, **_similar to loading the live cd without the safe graphic mode_**.

On the third try, I gave up and decided to go with GRUB. I formated once more and install Ubuntu. Everything is good. After it restarted, GRUB loaded and says

loading Grub x.xx version
ERROR 22 or something

I tried sys Rescue cd and play around with it. But no luck, so I decided to fixmbr from Windows XP cd since I cannot load Windows any more. And after the bios loads up, it says 1234F: I am not sure what this means.

Anyone has any problem like this before? I check the compatibility, and ubuntu is compatible with Radeon 9600, but how come my screen still **freeze** after loading ubuntu live cd?

---


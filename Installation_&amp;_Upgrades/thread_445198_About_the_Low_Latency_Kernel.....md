---
title: "About the Low Latency Kernel...."
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by Izobalax on 2007-05-15
I'm running Ubuntu Feisty as normal, but after reading about Ubunto Studio, and deciding ***not*** to distro-hop anymore, I'm thinking about installing the Low Latency kernel to aid me in my music production. 

From what I've heard, installing the kernel will create another option in my GRUB menu, so that I can choose normal Ubuntu Feisty, or with the low latency kernel. Is this the case?

Basically, what are the pro's and con's of doing this, because I ***really*** don't want to be screwing my system around. :grin:

/izo

---

### Post by andydread on 2007-05-21
I have no clue. what the cons are. i wish someone would educate us. 
 I installed it on my core1 laptop and it seems to make my laptop fly. 
it is a helluva lot more responsive over the i386 kernel that was installed.  it shows up 
in grub when u boot up.  You can edit /boot/grub/menu.list and change the default from 0 to 2 after installing it if you want to boot to it without selecting on each boot.  

Andy

---

### Post by MetalMusicAddict on 2007-05-21
> **andydread said:**
> I have no clue. what the cons are. i wish someone would educate us. 
 I installed it on my core1 laptop and it seems to make my laptop fly. 
it is a helluva lot more responsive over the i386 kernel that was installed.  it shows up 
in grub when u boot up.  You can edit /boot/grub/menu.list and change the default from 0 to 2 after installing it if you want to boot to it without selecting on each boot.  

Andy

Andy for you I would try out the -generic kernel and use that full time. The -lowlatency will drain your battery faster.

Basically the kernel is for audio work. If your not doing that I wouldnt use it.

---

### Post by tgalati4 on 2007-05-21
I have used Dynebolic which has a low-latency kernel.  You can download it and run it as a Live CD so it won't touch your system.  It has a complete set of audio tools.  It's worth checking out.

Low-latency guarantees 95% of the CPU cycles will go to your primary application.  If you are running Audacity for mixing or recording music, then 95% of the CPU cycles will go to Audacity.  This is helpful if you are recording a 2-hour concert directly to disk and you don't want any interrupts in recording.

The downside is that the mouse is sluggish and any other application that doesn't hook into the real-time kernel will only only get 5% of the CPU, so low-latency is not good for general desktop use.  That is why you need to boot into it separate from a regular kernel.

It works well.  If you run 'top' you can clearly see that 95% of the CPU goes to your primary application.  Everything else gets postponed until the primary appliation is finished doing what it needs to do.

If you are doing anything "Live" such as recording, streaming to the web, or just want better video or audio editing performance then low-latency can help out.  Don't expect a responsive machine otherwise for desktop use.  Sometimes it is easier to dedicate a machine for music production (as I have) so that you can run the real-time kernel all the time on that machine.  Then use another machine for everything else.

Ubuntu Studio will run on modern hardware, Dynebolic is slimmed down to run on older hardware.  I have used it successfully to stream and record audio with an M-Audio Delta sound card on a PII, 300 MHz machine.  Ubuntu Studio will run well on a PIII or better and lots of RAM.

Good luck.

---

### Post by oxalá on 2007-06-14
> **tgalati4 said:**
> I have used Dynebolic which has a low-latency kernel.  You can download it and run it as a Live CD so it won't touch your system.  It has a complete set of audio tools.  It's worth checking out.

Low-latency guarantees 95% of the CPU cycles will go to your primary application.  If you are running Audacity for mixing or recording music, then 95% of the CPU cycles will go to Audacity.  This is helpful if you are recording a 2-hour concert directly to disk and you don't want any interrupts in recording.

The downside is that the mouse is sluggish and any other application that doesn't hook into the real-time kernel will only only get 5% of the CPU, so low-latency is not good for general desktop use.  That is why you need to boot into it separate from a regular kernel.

It works well.  If you run 'top' you can clearly see that 95% of the CPU goes to your primary application.  Everything else gets postponed until the primary appliation is finished doing what it needs to do.

If you are doing anything "Live" such as recording, streaming to the web, or just want better video or audio editing performance then low-latency can help out.  Don't expect a responsive machine otherwise for desktop use.  Sometimes it is easier to dedicate a machine for music production (as I have) so that you can run the real-time kernel all the time on that machine.  Then use another machine for everything else.

Ubuntu Studio will run on modern hardware, Dynebolic is slimmed down to run on older hardware.  I have used it successfully to stream and record audio with an M-Audio Delta sound card on a PII, 300 MHz machine.  Ubuntu Studio will run well on a PIII or better and lots of RAM.

Good luck.

wow.  thanks.
i love Ubuntu and had high hopes for Ubuntu Studio, but I keep running into problems merely trying to record audio (the whole point of this particular exercise).  You've kind of sold me on Dynebolic, so i'll be giving that a try.

---

### Post by Sweet Mercury on 2007-06-18
> **tgalati4 said:**
> I have used Dynebolic which has a low-latency kernel.  You can download it and run it as a Live CD so it won't touch your system.  It has a complete set of audio tools.  It's worth checking out.

Low-latency guarantees 95% of the CPU cycles will go to your primary application.  If you are running Audacity for mixing or recording music, then 95% of the CPU cycles will go to Audacity.  This is helpful if you are recording a 2-hour concert directly to disk and you don't want any interrupts in recording.

The downside is that the mouse is sluggish and any other application that doesn't hook into the real-time kernel will only only get 5% of the CPU, so low-latency is not good for general desktop use.  That is why you need to boot into it separate from a regular kernel.

It works well.  If you run 'top' you can clearly see that 95% of the CPU goes to your primary application.  Everything else gets postponed until the primary appliation is finished doing what it needs to do.

If you are doing anything "Live" such as recording, streaming to the web, or just want better video or audio editing performance then low-latency can help out.  Don't expect a responsive machine otherwise for desktop use.  Sometimes it is easier to dedicate a machine for music production (as I have) so that you can run the real-time kernel all the time on that machine.  Then use another machine for everything else.

Ubuntu Studio will run on modern hardware, Dynebolic is slimmed down to run on older hardware.  I have used it successfully to stream and record audio with an M-Audio Delta sound card on a PII, 300 MHz machine.  Ubuntu Studio will run well on a PIII or better and lots of RAM.

Good luck.

That's good information. I had wondered about the same thing.

Can Ubuntu Studio be installed alongside a generic kernel, (dual boot)? I like the look of US, and woudl like to test out some of the programs, but would also need to use a few other things that the LL Kernel might fudge up.

---

### Post by calvinthomas on 2007-06-19
US installs both the standard kernel and the low-latency one as standard, just choose the one you want at boot-up!

Calv

---

### Post by Keisad on 2007-06-21
Uhh...

Forewarning, I had a lot of system lockups with the low latency kernel. This may only be the case for me, but it doesn't matter anyways since you can choose not to use it if you don;t want to.

---

### Post by tgalati4 on 2007-06-21
Are you sure they were system lockups?  Many times, the lack of response is just an indication that  some other application is getting the CPU cycles.  The same thing happens in Windows.

If you are impatient, then you just control-alt-del in Windows.  In Linux, you can look at your processes and kill the ones that are hogging your cycles.

Next time your Ubuntu Studio machine freezes, let it run for a while.  If the clock gets updated, then you know that the machine is still running.  You are just experiencing slow desktop response.

You should be running only one major application with low-latency.  Either audio, video, or graphics.  Running multiple apps will get you in trouble.  Unfortunately with Linux, it's easy to have a 100 processes running at the same time.

---

### Post by vbmds on 2007-08-27
I note my wifes laptop is running FFawn LL kernel - she's just installed Freespire 2

---


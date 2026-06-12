---
title: "Who's tested Ubuntu Studio 9.04 alpha or beta?"
date: 2009-03-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by homerj742 on 2009-03-26
Anyone tested this yet? I'm curious to know what people think? Stable? bugs?

---

### Post by Stochastic on 2009-03-27
Moved to Jaunty Jackalope Testing and Discussion.

---

### Post by homerj742 on 2009-03-27
Sorry about that, thank you.

Anyone?

---

### Post by Stochastic on 2009-03-27
I've been testing it throughout the cycle, things are steadily improving.  Many really nice changes are in store (newer programs, etc...) but the rt kernel has yet to stabilize to where I would like to see it.  Is there any particular issue you're curious about?

---

### Post by homerj742 on 2009-03-27
I'm mostly curious about the RT kernel, and I hear that 9.04 has some speed improvements. 

If the RT kernel isn't up to par, would you recommend I go with 8.04 instead? or are there RT Kernel issues with that as well?

---

### Post by markbuntu on 2009-03-27
The rt kernel has just appeared recently so some improvement is hopefully expected by release. Much of the rt effort is currently focused on the 2.6.29 kernel which will most likely be in Koala. The generic kernel is quite fast though, a lot faster than 8.04 or 8.10. I have not really loaded it up yet with my usual jack/ardour/rosegarden/hydrogen/jackrack/patchage/qsynth to see what happens but will soon and will post back here FYI.

The rt kernel is very useful and stable in 8.04. The only issue I have with it is that the newer fglrx drivers from ati are missing the rt patch and so do not work with it. But this is a very minor problem.

That said, if ubuntu would change the scheduling parameters and preempt setting in the kernel, the need for rt would not exist but from what I have read these are necessary for the nvidia drivers and a few other items that hog the cpu and do not like to be preempted but then why do they work with the rt patches? and with the current kernel scheduling glitch free pulse cannot work.
It is a conundrum.
I really hope they get all this worked out by Koala.

---

### Post by Stochastic on 2009-03-27
> **homerj742 said:**
> I'm mostly curious about the RT kernel, and I hear that 9.04 has some speed improvements. 

If the RT kernel isn't up to par, would you recommend I go with 8.04 instead? or are there RT Kernel issues with that as well?

If you're just switching to UbuntuStudio right now, go with 8.04, if you're an experienced user give Jaunty a try on an extra partition, continue to update it, report bugs, and help the cause.

RT is actively being worked on for the Jaunty release, which also means there's still bugs.  I have found that the generic kernel in Jaunty is pretty good for basic audio stuff.

---

### Post by amendt on 2009-03-27
Someone brought me non bootable Gateway Laptop this morning so I download 9.04 beta and installed it. It crashed doing the partitioning but when through when I installed it from CD.   I just looked at Bitorrent (3 hours since I started the file downloading) and it has been downloaded over 100 times with over 500 seeders and 250 lechers.  Ubuntu is getting quite popular. 
After installing it and doing an update (130 megs at 40 kB/s) I haven't found any other issues.  GREAT WORK GUYS

---

### Post by Stochastic on 2009-03-28
> **amendt said:**
> Someone brought me non bootable Gateway Laptop this morning so I download 9.04 beta and installed it. It crashed doing the partitioning but when through when I installed it from CD.   I just looked at Bitorrent (3 hours since I started the file downloading) and it has been downloaded over 100 times with over 500 seeders and 250 lechers.  Ubuntu is getting quite popular. 
After installing it and doing an update (130 megs at 40 kB/s) I haven't found any other issues.  GREAT WORK GUYS

This thread is discussing UbuntuStudio 9.04 and as far as I'm aware there's no bittorrent download option for UbuntuStudio right now.

---

### Post by ELWisty on 2009-03-28
I installed 9.04 on my Acer Aspire 5040 laptop and so far have been more than happy. For instance the wireless, which I only could get to work by manually reloading the driver for the atheros wlan card every time, works faultlessly now. 

One issue I have noticed: some random web pages on firefox 3.0.7, which in 8.10 showed ok, no longer do so. I can't see any text on the pages, the only way to see it is copying and pasting to a text editor. The browser is as it came with Jaunty, excepting that I installed the flashplugin and Java.

---

### Post by SvenGB on 2009-03-28
i have a dell XPS 1530 and so far i am happy with 9.04 my mouse works it is not cooking my hand or lap when using it like a laptop should be used. fast easy install, as for the technical side of things i am not sure what to say only had it in since 2 am this morning and passed out. will let you know about other things i find as i go through.

---

### Post by Stochastic on 2009-03-29
One area that we'd really like to hear user reports on is the RT kernel.  Are you getting any XRUNS?  any lockups?  2.6.28-3 just recently came into Jaunty and we need feedback.

---

### Post by homerj742 on 2009-03-29
Installed 8.04.1

Looks real nice!

However, when I start up Jack, I can get my guitar working just fine (MAUdio Delta 44), however can't get sound from Hydrogen, or any of my music players (audacious, amarok).

---

### Post by eric71 on 2009-03-30
I have added some of the Ubuntustudio packages to a regular Jaunty alpha6 (now up to beta) installation. Mainly the realtime kernel, jackd, qjackctl and qsynth. I use these with wineasio to run Reaper and Band In A Box, so my uses are a bit different than standard Ubuntustudio. At first, I had what I would consider a lot of xruns, and problems with jackd disconnecting from wineasio if I did almost anything. Someone suggested I raise the "timeout" setting in Qjackctl and this hekped a lot. I think it was Saturday morning (in Finland) when I marked all updates in Synaptic and the rt-kernel and jackd both got upgraded. Not sure what changed, but something definitely improved regarding rt jack performance. Since then things have been better - less xruns. When I get them, it is from loading large vsts. I'll give it a go with Ardourvst 2.8 within the next few days too.

Should note that I also uninstalled pulseaudio immediately. I'm not sure if this is included in a normal Ubuntustudio install.

---

### Post by markbuntu on 2009-03-30
Well, the rt kernel will not boot on my system. Just locks up hard shortly after starting up. No kernel panic. Hopefully this update will fix that and i will have something to report about rt.

But anyway, I was using jaunty a few days ago with the generic kernel and was able to record a radio stream playing in Amarok2 with Ardour while in gnome. (A little stress test for all the new libs.) I figure the chain went something like this Internet-Amarok-KDE4libs-phonon-xine-phonon-pulseaudio-jack-ardour-jackrack(a little echo/delay)-ardour-jack-alsa-hardware. 

I got the pulse-jack module from the debian repos and thought I would take the whole shebang out for a spin. I had to set the latency fairly high, 23ms to eliminate xruns and not touch anything when recording but it worked!

If I can get the rt kernel up and running I am sure I can get the latency down around 6msec or less without any xruns. Even with this kernel I did not get xruns greater than ~12msec and I think a lot of that was due to pulseaudio adjusting itself periodically due to kernel scheduling/alsa buffer issues which is a well known issue at the pulse mailing list and the reason glitch free had to be abandoned for Jaunty.

So, it looks like everything is coming along nicely for this release.

---

### Post by Stochastic on 2009-03-31
> **eric71 said:**
> Should note that I also uninstalled pulseaudio immediately. I'm not sure if this is included in a normal Ubuntustudio install.

Pulseaudio is part of a normal UbuntuStudio install - but since it's normally suspended as soon as jack starts up, it should not make any difference to your audio tests, xruns, etc...


I too have found these latest updates of the RT kernel to be extremely nice and stable (I've yet to turn compiz back on after the first rt-compiz complications I had weeks back - I guess that's the next test).

Markbuntu, if you still have an unbootable system after you do all the latest upgrades please report this issue to the ubuntustudio-dev team.  (I'll point them toward this thread next time I talk with them)

---

### Post by markbuntu on 2009-03-31
Well, after the latest update the problem persists. I will try a few boot options and maybe change a few bios settings before giving a report. If I can get it to boot by doing that i think it may be more helpful than the scarce information I can give now since i can find nothing in any of the logs that this kernel ever even tried to boot and my screen fills with long hex numbers that I would need to copy by hand or take a photo of when the machine locks up solid very early in the boot process.

---

### Post by Coplen on 2009-03-31
I can't get the rt kernel or the i386 kernel to boot on my machine. Heh. That's my only gripe.

---

### Post by jhenager on 2009-04-02
Just downoaded/installed the 64 bit version. I love it from the opening progress bar up to here.
Super job. Will upgrade as soon as the RTM is released.

---

### Post by ecullerton on 2009-04-09
Hi all,

I tested ubuntu studio jaunty last night and had a VERY good experience.

My hardware setup:

Intel DP35DP motherboard
4G of memory
Nvidia 8800 video card
2 Focusrite Saffire pro 10 firewire audio interfaces

I have been using 8.04 with "OK" results for this set up using ffado and ardour. I always had some stabilty issues with the firewire driver when running both saffire pro's at 96kHz.  I would see xruns and broken pipes on the firewire.

I loaded up jaunty, and to my pleasant surprise I found a real time kernel!  Finally!  Added nvidia driver and found that I did not need to reboot?  I'm not sure if this is true, because I rebooted anyway. (old habit)

So far so good. Turned on all the options in the studio control panel.  Rebooted to be safe.

I next checked the package list to see that ffado is already installed!  Hallelujah! No more compiling code! I saw that the ffado mixer was not installed, so I installed it. 

I fired up my saffire pro's and started up qjackctl.  I checked the realtime option and set other options to 256, 3, and 96kHz.  I think the latency was around 4 ms.  Fired it up and got any error about real time priority.

I checked to see if there was an audio group in the users and groups menu, and there was not.  So I added the audio group, and added my user to that group, logged out and logged back in.

Started up qjackctl and started it up.  Got another error about raw1394 permissions.  Fixed that with a chmod command.

Started up qjackctl again, and BAM! It worked.  I had 2 focusrite pro 10's up and running at 96kHz with ZERO xruns! Wow!

Next I started up Ardour.  Version 2.7.1.  It's not 2.8, but I'm not complaining.  Added 20 tracks and started recording.  Works great.  No xruns.  Recorded for about ten minutes to my satisfaction.  This is great!

My last test was the ffado mixer.  This is where I ran into a some trouble.  I spent about twenty minutes trying to get it to work, but didn't have any luck.  I'll give it another try later and post some more details.

This whole process took about 2 hours.  AWESOME!  This same process took about 5-6 hours on Hardy Heron.  I had to compile ffado, jack, and Ardour, which was a real pain.

I look forward to the final release.  Great work to all the guys developing!

---

### Post by zenithdave on 2009-04-09
After ecullerton's glowing write up i can't resist :guitar:

downloading..................ohh that's big !, report tomorrow :D

---

### Post by ecullerton on 2009-04-10
Hello to everyone again!

After more testing, I have some not so good results. :(

I reported yesterday some good news, but further testing wasn't as good.

I noted that the raw1394 permissions had to be changed, and I can't figure out how to make the permissions stick after reboot?  I thought this was taken care of using the ubuntu studio controls, but it does not seem to be the case.  

That was the least of my problems.

I found that I can only start the ffado mixer using sudo in the command line.  Another permissions issue?  When it started, things became VERY unstable.  Qjackctl crashed within a few seconds.  When I say crashed, it just disappeared. Poof!  This continued to happen even when I did not open the mixer.  The led on the front panel of the focusrite stays on, but I don't see jackd running in the process list anymore.  I had to reboot after the crash to get things started again.     

The next thing I did was to compile ffado and jack from source.  I may have made things worse by doing this, but I'm not sure. I still saw the same crash.

Now I'm having trouble getting both focusrite's to run at the same time, at least not stable.  I'm still testing at 96kHz, 3, 256.  I tried other buffer settings, but had worse results.  The leds on the focusrite would not light up, and I get a bunch of broken pipe errors from qjackctl.

I should mention my results from using 8.04.  I always had some stabilty problems when running 2 focusrites at 96kHz.  Things were pretty good at lower sampling frequencies.  The really sad news is that I have no problems running 2 focusrites on Windows at 96kHz (Vista Ultimate, same hardware)

I'm starting to get the feeling that the firewire implementation in Linux/ and or ffado is not up to par.  I should be able to get 3 of these firewire devices to run simultainuously. (according to focusrite)

I've read bits and pieces about a new improved firewire stack in development, but ffado 2.x does not use the new implementation.  I looked at the timeline at the ffado developement page, and ffado 3.0 will be using the new firewire stack, but no work has been done. :(  I may have to just wait before I can run a setup like I have.

I'm going to wait a few more days for the final release, and test it again.  I'm sure all the permissions stuff will get settled, and maybe there are some tricks (like IRQ priorities) that I can tinker with to get this setup to work.

That's it for now, I'll report any new results later.

---

### Post by zenithdave on 2009-04-10
My install broke at the end so i never got to try it :S

---

### Post by roaldz on 2009-04-18
I've got a laptop with VIA Firewire hardware. Got a Presonus Firepod audio interface. If I try to run it with rt kernel, its a matter of seconds before it will lockup the WHOLE system. I've had xrun-free low-latency (1.6ms) recording on this laptop, so its not a hardware problem. The ffado driver will hold longer, but will hang eventually. Freebob is a mess in stability. I've always used freebob without problems on 8.04 amd64. On 8.04 32bit it will hang too. amd64 is more stable for me :S

Roald

---

### Post by steefjeqv on 2009-04-18
Hi,

I've installed Ubuntu Studio 9.04 RC-64 bit on my PC. The install went fine.

The system boots but hangs at login (gdm is completely garbled).
If I change my xorg.conf driver to vesa, the login screen is fine.
When I try to change the resolution (using vesa), the screen gets garbled again.

Hardware : Asrock Dual Sata-AMD opteron 146 (sckt 939)-2x512 mb-ATI X600 pci-e.

Greetings,
Steven

---

### Post by barisurum on 2009-04-19
Hi

I Installed ubuntu studio RC 9.04 today. I had no problems during install.

When I booted to the new system it seemed just fine. But after a while I experienced serious instability issues. System hard freezed randomly approximately 2-3 minutes after the boot. Updates or installation of any package was impossible. So I downloaded the generic kernel (2.6.28.11.42) packages using my 8.04 live cd and was lucky to install them within the 2-3 minute time that was granted to me :D So I use the generic kernel with my 9.04 testing partition now. But I was able to test some of the things with the rt kernel prior to that. Here are the results: 

[COLOR="Red"]*** RT kernel results ***[/COLOR]

Graphics:

The new open source ati driver worked well with my X1650XT. I tested with glxgears and had about 4500 fps which is half of the fglrx but not bad. Compositing was working too. So I had no problems with graphics. I think the system hangs don't have anything to do with the graphics drivers because my rt system was hanging even in the console screen!

Audio:

Pulseaudio didn't work from the beginning with rt kernel. Doesn't work with the generic kernel I installed tonight either. I will try further with generic kernel and let you know about the results. For now audio is non-existent. If anyone has a fix for this please let me know.

Kernel:

I was lucky to upgrade the rt kernel once before switching to generic one. It was the 2.6.28.3-rt to 2.6.28.3.12-rt update. But it didn't solve the hard freezes. For now ubuntu studio 9.04 has a nightmare rt kernel which is completely unusable. I hope the situation improves in the future. I will keep upgrading and booting to my rt kernel and let you know the results.

My specs are:

AMD K8 dual core 2.8 ghz
4gb of 800 mhz ram
Ati X1650XT with 256 mb ddr3

---

### Post by venomgyz on 2009-04-19
I just tried Ubuntu Studio 9.04 rc, and it would stop responding to my mouse and keyboard after about 10 seconds (with the rt kernel). The interesting thing is that it was just the mouse and the keyboard that were not responding. The clock was still updating, also when I pressed the power button, the shutdown menu came up. Looks like some interrupts aren't working the way they are supposed to ;)

Didn't have a chance to update to the newer rt kernel, it is kind of impossible.

specs: intel e8400 @ 3ghz
4gb of 800mhz ram
nvidia 8800gt

---

### Post by barisurum on 2009-04-20
I have been using the generic kernel for a while now. Pulseaudio sucks and is completely unusable for me. But jack works fluently with 5ms latency on my usb-audio card. I made the necessary changes to /etc/security/limits.conf/ and created an audio group with me as member and it works! I will further test it for longer periods and report here, for now jack is the only source of audio in my system.

---


---
title: "Herdy fault, very very very very very very slow system?"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by Skokie on 2008-04-25
I have installed Kubuntu 8.04 on a number of machines (mostly not important ones hehe) but alas the Office PC has a severe problem.

It seems that something is causing the workstation to go very very very slowly.  Any new click takes one minute to resolve with 100% CPU on both cores.

Loading eclipse takes up of 20minutes (didnt wait it out sorry).

This was a problem with the install live CD also (but from other posts felt it was a CD only problem).  I upgraded from 7.10 in 7.10 desktop as it was the only way to get round the install.

This system is 

HP Compac DC7700
Core Duo 2.4Ghz
2GB ram
Intel G965 chipset
G3000 integrated graphics.
(Its an off the shelf HP).

Im guessing it is something low level with the chipset (since other "slow" reports seem to be intel Gxxx based also).

It doesnt seem to be Gfx related since it works the same as 7.10 (on bad days its bad, on good it flies).

I have tried many noapm acpi type kernel things on the install CD and nothing fixed it. Tried turning a few BIOS options (power management and VM related) but no avail.  Also these office off the shelf things have very limited options there anyway.

The next step is to gather some knowledge see if it is just me :)

Thanks
/G

---

### Post by Patsoe on 2008-04-25
Hello again :)

I had the same type of problem on an older release and with very different hardware, so probably this won't help you, but it won't harm either: it was a timer bug for the ATi Xpress200 chipset, and the solution was to use "noapic nolapic" boot parameters.

---

### Post by tormod on 2008-04-25
> **Skokie said:**
> It seems that something is causing the workstation to go very very very slowly.  Any new click takes one minute to resolve with 100% CPU on both cores.
Try using the "vesa" graphics driver, to see if it's the "intel" driver that is causing problems (edit /etc/X11/xorg.conf). Make sure you also disable Compiz (desktop effects) and such.

---

### Post by Skokie on 2008-04-25
Hei,  Firstly the system seems to crawl from the moment the kernel starts (its spuradic in that some parts of boot just drag on and on, others seem to go ok) so I dont think its X specific this time. 

I had not tried nolapic before so I am currently waiting for the system to boot. 400 seconds so far and it finally got up to cleaning the filesystems (still miles from x hehe).

I think it has to be a kernel bug with this hardware.

:(

---

### Post by Skokie on 2008-04-25
I was just finding other "slow" related threads and remembered the old AMD x2 cool'n'quiet thing.  Perhaps there is a clocksource issue with this latest kernel.

if I do a cat of /sys/devices/system/clocksource/.../current_clocksource  I get "tsc".

Alas I have no idea if this is good or bad, or in deed how to change it to see if it is related.

sniff

---

### Post by Ayuthia on 2008-04-25
Are there any error messages when you run dmesg from the Konsole?

---

### Post by Skokie on 2008-04-25
Honestly, it looks normal, I grepped it for errors and such.  The timestamp goes to 40 seconds then on acpi has a little jump (its disabled in the boot line), the rest from about 150 seconds takes approx 1312 seconds.

it feels like the old P90s when you turned the internal cache off hehe

Dmesg attached...

I will go quiet for a while due to family demands and I wanted to thank you for your ideas so far!

/G

---

### Post by Archmage on 2008-04-25
Is top showing any strange process?

---

### Post by Ayuthia on 2008-04-25
I would go ahead and take out the noapic nolapic parameters.  You should not need them with the Intel hardware.

As Archmage said, it would be helpful to see what process is taking up your CPU cycles.

---

### Post by Skokie on 2008-04-25
Hei,

I guess im a little useless at explaining.  This isnt a normal rouge process kinda thing.  Anything or everything will use 100% when you run it...  it stays 100% for about 2 minutes until all resources are up for that software (an example would be it should take 2 seconds to for software to reach this state), then it idles 5% CPU.  Doing a menu or something new, back to 100% for another 40 or so seconds.

This is not program specific, but what is interesting is that if you run say ksysguard, it uses about 60% CPU permanently because it is redrawing all the time. But remember its not a drawing thing...  in runlevel 1 the system is slow... boot is slow...

So as I say, its like the CPU is running slow, rather than something burning all the cycles.

Im just not sure how to pin it down...  I agree with the apic and such, but its interesting cos all the intel hardware have open sourced drivers (i thought).  It should be the most stable system on the planet hehe

So im naturally not in the office for the weekend, but on monday I will try and get some more diagnosis and I would be delighted for all the help!

Maybe the few days between now and then will collect some more examples (people) with the problem, help us get to the bottom of it.

Thanks, have a lovely weekend.
/G

---

### Post by tormod on 2008-04-25
This sounds like a serious kernel regression that you should report in launchpad as soon as possible, if it's not done already. This way it will get the attention of the Ubuntu kernel maintainers. File it on "linux" and attach lspci and dmidecode output.

---

### Post by Skokie on 2008-04-26
OK I will do this on monday when I am next to the machine again.

Something else I was thinking, to help pin it down...  what if someone could post a similar dmesg output so we could try and see where this machine suddenly gets slower?

Im wondering if there is a part of the kernel bring up that makes it go very slow...  If we could compare the distribution of time (as the CPUs will vary) I may be able to see where the slowness begins. This could point people with the know directly to the area?

/G

---

### Post by hanlect on 2008-04-26
I have a problem that may be related. With the new kernel (2.6.24-16-generic) my fan goes all the time because the cpu runs hot.

Looking at htop output I noticed several spikes in cpu usage. It looks like a serious kernel flaw, since with the previous kernel (2.6.22-16) I don't have these problems.

By the way, how can I install linux-image-2.6.22-16 and the restricted modules in hardy? It seems to be out of the repository. Maybe a kernel rollback can solve your issue, too.

---

### Post by tormod on 2008-04-26
> **hanlect said:**
> By the way, how can I install linux-image-2.6.22-16 and the restricted modules in hardy? It seems to be out of the repository.
This is not something I can recommend, but you can download the .deb packages from launchpad and install them directly with "sudo dpkg-i".

---

### Post by moonshinerat on 2008-04-27
I left a thread on here yesterday with very similar problems. Intel 945GN chipset and Intel E4400 Core2. Usually my menus just lock up but when they work it takes my menus 40 seconds to fade in and then about a minute to respond to a click.

The vesa driver has made no difference to me but my boot time is substantially quicker than ten minutes. I've reinstalled from the livecd and the alternate CD twice now. Hardy is completely unuseable on my system. Iwonder if this is a kernel problem because I'm now having the same problem with Fedora 9 as well.

---

### Post by Skokie on 2008-04-28
Hei,

OK SUCCESS!!!

I did a bit of reading yesterday and found some DC7700 unrelated stuff.  But there where similarities so I read on.

It seems the DC7700 bios is next to useless.  One guy was saying he had problems with "slowness" in an older version of linux and that all the kernel parameters didnt help.

I followed the advice under the "successfull heading" here :-

[http://slonopotamus.livejournal.com/99744.html](http://slonopotamus.livejournal.com/99744.html)

2 steps.

1) Upgrade the BIOS (put it on a USB and use the F10 bios setup flash utility). Something cool about this machine, year surprised me too since I imagined having to create crappy windows boot discs just to flash a bios lol.

2) Set the disk system to "RAID" mode.  This allows linux to use DMA (dont ask, I have no idea why).

Now its not slow, all seems well and even the desktop gfx is zippy.  Also note that I do not have any special params on the kernel.  Didnt seem to need them.

Oh the BIOS i upgraded to was v1.14 from the HP BIOS downloads page.

Thank you to everyone who helped, I hope my success can be repeated for others.
/G

---

### Post by tormod on 2008-04-28
Please file a bug report anyway. Especially since this worked fine before, there's no reason this shouldn't work out-of-the-box without having to resort to BIOS updates and false settings.

---

### Post by Skokie on 2008-04-28
Bug raised as

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/223647](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/223647)

Its unfortunate that I can no longer reproduce the bug (since the BIOS upgrade has resolved it) but hopefully it will be of some use.

Thanks again for all the effort.
/G

---


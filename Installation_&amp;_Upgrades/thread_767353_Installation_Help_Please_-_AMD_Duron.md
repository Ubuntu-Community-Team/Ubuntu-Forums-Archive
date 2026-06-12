---
title: "Installation Help Please - AMD Duron"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by moldy on 2008-04-25
Hi all

Firstly, I have searched the forums and not been able to find anything that has resolved my problems, so i apologise if the answer is already here somewhere.

I am trying to resurrect an old AMD Duron 1000mhz (512mb RAM) to use as a backend mythtv box - and would like to do this with Ubuntu. However, i am having no luck installing either gutsy or heron onto the machine. both versions are giving me the same problem.

When i install from livecd, the GUI arrives properly and i am able to use all of the functions. but when i go to install, it says "loading kernal" (no problem), and then starts to load with the ubuntu logo and the moving progress bar.

After some time the bar stops still, and the computer hangs (more often than not with the caps lock and scroll lock keys flashing). i have tried waiting for a fair while, but it seems to be truely frozen.

This happens with both hardy and gutsy, and both when i use the ide=nodma option and not. so i am out of ideas about how to get ubuntu up and running. the machine works fine with windoze - but i'd rather use ubuntu if able.

i'm fairly noob to ubuntu - so any help would be greatly appreciated.

regards, moldy.

---

### Post by raul_ on 2008-04-25
I would try the Alternate CD.

In the ubuntu download page, select Alternate Install CD

It's a text based installation, but it's pretty straightforward, so give it a shot.

Good luck

---

### Post by Pumalite on 2008-04-25
Clean the lens in your burner, do md5sum, burn at 4x or less, check CD integrity before install.

---

### Post by moldy on 2008-04-25
thanks for the quick reply guys. 2 small questions though:

1. raul_: if i download the alternative cd, will the installation process be straightforward, or will i need to go hunting for command line prompts (i really am a noob).

2. pumalite: thanks, i have checked the cd integrities and burned at my slowest possible (twice). I will clean the lens too. but can you please tell me what md5sum is? sorry if that's an idiot question!

cheers, moldy

---

### Post by raul_ on 2008-04-25
> **moldy said:**
> thanks for the quick reply guys. 2 small questions though:

1. raul_: if i download the alternative cd, will the installation process be straightforward, or will i need to go hunting for command line prompts (i really am a noob).

2. pumalite: thanks, i have checked the cd integrities and burned at my slowest possible (twice). I will clean the lens too. but can you please tell me what md5sum is? sorry if that's an idiot question!

cheers, moldy

It was straightforward, as far as I remembered. If you have any troubles, just post here, and we'll help.

You can check the md5sum when you burn the cd. There should be an option like "verify md5sum". It's a way of verifying the integrity of the data

---

### Post by moldy on 2008-04-25
> **raul_ said:**
> It was straightforward, as far as I remembered. If you have any troubles, just post here, and we'll help.

You can check the md5sum when you burn the cd. There should be an option like "verify md5sum". It's a way of verifying the integrity of the data

thanks mate, will download now and post my results here. cheers, moldy.

---

### Post by Pumalite on 2008-04-25
[http://en.wikipedia.org/wiki/Md5sum](http://en.wikipedia.org/wiki/Md5sum)
[http://etree.org/md5com.html](http://etree.org/md5com.html)

---

### Post by moldy on 2008-04-26
> **raul_ said:**
> If you have any troubles, just post here, and we'll help.

Raul_: i have downloaded the alternative cd and have tried installing by that method. it seems to work well until i get to partitioning the hdd. once i select to use "guided entire disk" (or similar), the system freezes at 33% and says the following:

"creating ext3 file system for / in parition #1 of SCSI2 (0.0.0) (sda)..."

i have seen in other forum posts that i might use "acpi-off" and "irqpoll" - which i have both tried (and together), and still the same result.

if you have any ideas as to why the partitioning might freeze always at 33% then i could really use some more advice.

regards, moldy.

p.s. i have tried waiting for some time, and it doesn't progress past 33%.

---

### Post by raul_ on 2008-04-26
At least you know where the installation is freezing, it's a start. I'm afraid i'm clueless about the motives though. :(

---

### Post by Pumalite on 2008-04-26
Try: all-generic-ide

---

### Post by moldy on 2008-04-26
> **Pumalite said:**
> Try: all-generic-ide

Thanks Pumalite, but unfortunately no luck. The system still froze when the partitioning (as described above) got to 33%.

Do you have any ideas why this might be freezing - or any topics i should be researching? i am really only guided by you guys, as i have no idea why it's failing.

thanks for the help so far, moldy.

---

### Post by Pumalite on 2008-04-26
Sorry, I made a typo. It's all_generic_ide.
More boot parameters to try:
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
Try the most common ones first. One by one or in different xcombinations:
noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off vga=0x317 vga=791 vga=775

---

### Post by jchance on 2008-04-26
For what its worth, I had the EXACT same problem, same blinking lights on the keyboard, but it was hardware related- my AMD Opteron processor was overheating.  If I remember right the duron/opteron chips had the same chipset, so its possible your situation is the same.

I was going nuts trying 3 or 4 different CDs from two different burners- every single one locked up on install.

I checked the temp on the chip in the BIOS and it was WAY out of safe range, and when it locked up everything just stopped and the keyboard lights started their blinks, which I guess in BIOS-eese is "your crap is on fire".

I cleaned out the heat sinks, put new thermal compound on the chips, and everything was good to go- perhaps your old processor needs a little cleaning too?

---

### Post by moldy on 2008-04-26
Thanks guys, I will give both suggestions a try - and let you know how i go.

---

### Post by moldy on 2008-05-16
well i gave some combinations of boot parameters a try without luck (coculd well be that i'm not experienced enough to know what i'm doing).

I will give the components a clean tonight and see how i go.

jchance - your theory has increased credibility recently - as i have just purchased a new HDD for this machine (which i will just use as a backup drive if things dont work out) - and the same thing happens. Gets to 33% and frozen with the flashing lights.

if anyone else should read this, and thinks they know the answer, then please post a reply - i will post the result of my cleaning hopefully later tonight.

cheers, moldy.

---

### Post by moldy on 2008-05-16
SOLVED.

It was some dodgy RAM. Even though it had previously worked fine under windows, ubuntu installer wasn't impressed. I took out the offeding RAM and everything worked fine with only 256mb.

Thanks to all for their assistance. It is much appreciated by Noobs like me.

---


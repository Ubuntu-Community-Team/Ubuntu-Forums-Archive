---
title: "Installing Ubuntu 14.04.2 LTS Issues"
date: 2015-04-01
forum: Installation &amp; Upgrades
---

### Post by johnny32 on 2015-04-01
Hello,

I am new to the forum and [sort of] new to Ubuntu - loving it so far.

I am trying to instal Ubuntu 14.04.2 LTS from a USB however I am having issues.

Hardware;


[LIST]
[*]Dell Optiplex
[*]160GB WD HD
[*]6GB RAM
[*]Intel core 2 duo
[*]64 bit
[/LIST]


I had Ubuntu 12.0.4 installed until recently with no issues until I decided to format und update to 14.04.

I am following the official install documentation however still no success. Firstly I thought it was my 80gb hdd, so I got replacement 160gb one - same issue.

I am able to boot from the usb and go through the installer steps (I create the bootable usb following the official docs using *Universal USB Installer* and *Unetbootin*).

I am able to choosing my country, language and when I enter my name I get the error message and crash error.


[HTML]...

'...the following file did not match its source on the copy cd/dvd...

target/lib/modules/3.16.0-30-generic/kernel/drivers/mtd/chips/cfi_cmdset_0001.ko

...[/HTML]


I have researched this and apparentley it's related to a dodgy iso file, however I have downloaded both versions (64/32) from the official Ubuntu site, and other mirrors. Same error.

Other times when I re-try the install I won't receive the error at all, the screen will simply go black. No info at all, meaning I have to restart the process and try again.

Things I have tried so far;


[LIST]
[*]two hdds (80gb WD and 160gb WD)
[*]two usb's (2gb and 8gb)
[*]formatted boths hdds multiple times
[*]ubuntu 14.04.2 (64bit)
[*]ubuntu 14.04.2 (32bit)
[*]verified md5 hash was correct
[*]tried installing 12.04 again
[/LIST]

From what I can see I am following all the steps, and I meet the hardware/software requirements. I would appreciate any advice or direction here as I am lost!

---

### Post by sudodus on 2015-04-01
Welcome to the Ubuntu Forums :-)

Please specify the graphics chip/card and wifi chip/card.

- There may be driver issues with the hardware, maybe it will be solved with some boot option and proprietary drivers.

- Maybe you should revert back to Ubuntu 12.04 LTS, which will be supported until April 2017, so for two more years.

---

### Post by johnny32 on 2015-04-01
Hi sudodus thanks for the reply!

I was able to choose 'Try Ubuntu without installing' to get your suggested details.

Memory 5.9GB
Processor Inter Core 2 CPU 6600 @ 2.40GHz x 2
Graphics Inter 965Q x86/MMX/SSE2
OS Type 32 bit
Disk 3.2GB

Does this help any?

Also I have already tried to format my hdd an re-install UBuntu 12.04 LTS and the exact same thing is hapenning. It always seems to be at the 'Who are you?' stage of installation, whenever I enter my name or try to click next.

---

### Post by sudodus on 2015-04-01
12.04 LTS used to work but not now. If you had very low RAM, it would have explained your problem, but 6 GB RAM is a lot. Maybe one of the RAM sticks is bad. Please test the RAM with ***memtest*** (from the early menu of the installer.

How did you install 12.04 LTS (from an iso file, or did you upgrade the system from an earlier version)?

---

### Post by johnny32 on 2015-04-01
Well it was running 12.04 LTS fine until I decided to upgrade to 14.04 which at the time didn't seem to work. So as the PC is simply for testing/experimenting I formatted the hdd, and added 2 x extra 2GB of RAM (taking it from 2BG to 6GB). This is the only hardware change I have made, and I presumed it would have helped things rather than hindered them? Good idea though maybe I should remove this additional RAM and try again?

Like I say this PC is simply for me to familiarise myself with Ubuntu and the installatio etc so I can format/re-format as many times as necessray, I'm not concerned with loss of data.

I am installing each (12.04 and 14.04) from an iso downloaded from the official Ubuntu website. Installing via a bootable usb as described in the official docs. This process worked initially a few months back, however since the re-format and additional RAM it seems to be causing issues.

---

### Post by grahammechanical on 2015-04-01
> [COLOR=#000000]It always seems to be at the 'Who are you?' stage of installation, whenever I enter my name or try to click next.[/COLOR]

That could be coincidence. While we are entering those details the installer is working away in the background. I have the same CPU and only 1GB RAM and I have no problem installing even the newest versions of Ubuntu (15.04) and I have done so many times. I do have a different video adapter. A Nvidia GT220.

A .ko file is a Loadable Kernel Module.

[http://en.wikipedia.org/wiki/Loadable_kernel_module](http://en.wikipedia.org/wiki/Loadable_kernel_module)

My installed Ubuntu has 11 .ko files in that ..... /mtd/chips folder. In fact it has a set of .ko files for every Linux kernel that is on my system. It seems that in copying the file from the install medium to the hard disk and then comparing the copy with the original that differences are being found.

None of this is much help. Sorry.

---

### Post by johnny32 on 2015-04-01
Thanks grahammechanical and sudodus, I have removed the two extra sticks of RAM and it has installed successfully!

Why would this have happened? Faulty RAM? Too much RAM? RAM in incorrect slots? Should I keep it with 2gb RAM or would performace be noticeably better with the extra 4gb?

Thanks again

---

### Post by oldfred on 2015-04-01
Usually too much RAM is just not recognized. Did BIOS show the full 6GB?

There are a lot of rules on RAM. Some require matched pairs (same color slot if different often the case), some require certain slots filled first.
You must have same speed on RAM and often just better to have same brand, model & speed to know they all work.
You can more fully test each 2GB by itself to see if it works. And sometimes just removing & cleaning contacts helps.

---

### Post by sudodus on 2015-04-01
Test the RAM with ***memtest*** (from the boot menu), test each RAM stick for hours. One single error is too much.

---


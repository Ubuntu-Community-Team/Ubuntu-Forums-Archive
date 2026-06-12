---
title: "Dual booting with Windows 8 on a Sony Vaio"
date: 2013-06-11
forum: Installation &amp; Upgrades
---

### Post by tbid18 on 2013-06-11
Hey all,

I'm getting a new laptop, and right now I'm interested in the [Sony Vaio Pro 13 Touch]("http://store.sony.com/webapp/wcs/stores/servlet/SYCTOProcess?catalogId=10551&storeId=10151&langId=-1&LBomId=8198552921666580655&categoryId=8198552921644859012") that recently came out. Is getting this to dual-boot with some distro (probably linux mint) going to be a problem? I haven't had issues in the past, but I know secure boot and uefi has caused problems for some people, so I want to make sure this is doable before pulling the trigger. The laptop has the new haswell chip and an SSD, if that matters.

Any advice is welcome.

Thanks

---

### Post by oldfred on 2013-06-11
It looks like it is an UltraBook. That adds complications separate from UEFI due to dual video and Intel SRT which uses RAID.
Dual video preliminary support has just been released by nVidia, but most with older systems have installed bumblebee.
Intel SRT uses the SSD as cache to make Windows seem faster. It uses RAID which the Desktop installer used to not work at all as RAID support was only in server or alternative installer versions. But now installer seems to see RAID, but grub still does not install correctly as it does not know if RAID or not. Most turn off Intel SRT. Some then prefer Ubuntu and install / (root) to SSD and /home (or data partitions) to hard drive and never turn SRT back on. Others use Windows more and do a standard dual boot and turn SRT back on after the install of Ubuntu. 

See link in my signature for more info. But your system is so new as you will be the one testing it. 

This site usually installs the pre-release versions of kernel & video to see the future.
[http://www.phoronix.com/scan.php?page=news_item&px=MTM4NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTM4NzE)

Often with Linux it takes a release or two before drivers really catch up with new hardware.

---

### Post by tbid18 on 2013-06-11
It is an ultrabook, and thank you for that information as I was not aware that it added an inherent complication. I saved those links, hopefully things either work well or the necessary solutions will be somewhere there. Much appreciated.

---

### Post by metRo_ on 2013-06-27
> **tbid18 said:**
> It is an ultrabook, and thank you for that information as I was not aware that it added an inherent complication. I saved those links, hopefully things either work well or the necessary solutions will be somewhere there. Much appreciated.

Do you have news about it? Did you try? :)

---

### Post by Krayn on 2013-06-28
Hey hey,

i recieved my pro 13 without touch yesterday...

when trying to install ubuntu 13.04 i cant get past the grub from the liveCD when i have uefi enabled...whatever option i choose in grub i get a black screen... without uefi it will boot..though as it seems there isnt a driver for the wifi card yet

since i wanted to keep uefi enabled i tryed the ubuntu 13.10 development branch... 13.10 boots just fine with uefi enabled...though in order to boot the 13.10 i installed i had to run boot-repair...and since wifi doesnt work i am using a old wifi usb stick i had...hoping that there will be support for the card soon (FYI the wifi card is called "Intel Wireless-N 7260")

edit: ah and... after running the "boot-repair" i am able to dualboot ;)

---

### Post by Dillon on 2013-07-01
Thank you for the update! This is the only post I've found related to Linux on the new Vaio Pro. I am seriously considering purchasing this ultrabook before returning to college this fall, but have found absolutely zero information about Linux compatibility. 

I have bookmarked this thread and would like to ask you, if you aren't too busy, to keep, at the very least me, updated. Is there anything that doesn't work very well or at all ( besides the wifi)? Touchpad, graphics, etc... 

Thanks again!

---

### Post by Krayn on 2013-07-02
> **Dillon said:**
> Thank you for the update! This is the only post I've found related to Linux on the new Vaio Pro. I am seriously considering purchasing this ultrabook before returning to college this fall, but have found absolutely zero information about Linux compatibility. 

I have bookmarked this thread and would like to ask you, if you aren't too busy, to keep, at the very least me, updated. 

Hey hey,

well then here is an update.

after Reading some about the wifi i found something about a [patch]("http://www.spinics.net/lists/linux-wireless/msg108912.html") in iwlwifi regarding that card. After another bit of reading on how to get that driver into my kernel i stumbled across a [blog]("https://spicious.com/sony-vaio-pro-11-with-ubuntu.html#disqus_thread") where someone managed to compile a kernel with working wifi for the pro 11. That did the Trick for me aswell.

After a recent update of 13.10 (before i switched to the kernel with wifi) some stuff broke though...right now i have no time, bluetooth or battery indicator in my menu bar. For the bluetooth indicator im getting a crash report. The other two are just gone. Though since i have the extra sheet battery i don't desperately need the battery indicator (would be nice to get back though).

So generally right now everything i need works just fine.

Im getting about 5 hours of use per battery with the current configuration. That is with the screen at about 50%, which is still bright enough. Though im hoping for better values here once 13.10 gets into a more stable development stage.

>  Is there anything that doesn't work very well or at all ( besides the wifi)? Touchpad, graphics, etc... 

Well wifi works now ;)

The touchpad works. But right now it sometimes recognizes a right click with two fingers, and sometimes it doesn't. The two finger scrolling works without problems though.

The graphics are recognized as "Intel Haswell Mobile" im not sure if they are correctly used. But they seem to work. Though i only tested some really minor games with steam on it. I am planning to test some more demanding linux games once i find some time.

the only other thing i noticed that doesn't work is nfc. if i type "sudo rfkill list all" it will list the nfc, so it might just not correctly been setup. But that doesn't bother me so far ;)

---

### Post by darksaboteur on 2013-07-02
I picked my i5 Vaio Pro 13 up on saturday and have installed Fedora 19 Linux on it.
Overall works pretty well, I get a solid 5-6 hours from the battery.
I wrote a post detailing the issues I encountered if anyone is interested[http://www.nicksplace.com.au/2013/07/01/sony-vaio-pro-13-vs-fedora-19/]("http://www.nicksplace.com.au/2013/07/01/sony-vaio-pro-13-vs-fedora-19/")

Let me know if anyone wants any more info or help getting Linux running on this beautiful piece of hardware

---

### Post by Dillon on 2013-07-02
Good to know, guys! I'm glad Linux is working well even at this early stage and can only get better. Pretty sure I'll be picking one of these up in the coming weeks.

---

### Post by ooddiittyy on 2013-07-03
> [COLOR=#000000]Let me know if anyone wants any more info or help getting Linux running on this beautiful piece of hardware[/COLOR]

Hey, so this may be too much work for you but: I'm completely new to Linux, just got a Vaio Pro 13 and installed Linux Mint to try it out (real install, wiped Windows); no WiFi, and everything seems a bit choppy generally. I was wondering if you have any particular advice for Linux Mint, if the method you used would work or...?

I very much appreciate any help you might be able to lend. I assume once these laptops become more prevalent support will increase, but if I can get something bootstrapped short-term that'd be fantastic.

---

### Post by darksaboteur on 2013-07-04
Hi ooddiittyy,
Have a look at [https://spicious.com/sony-vaio-pro-11-with-ubuntu.html](https://spicious.com/sony-vaio-pro-11-with-ubuntu.html)
As Mint is a derivative of Ubuntu and the Vaio Pro 11 shares the same WiFi as the 13 his instructions should be applicable to you.
The choppiness probably comes from the CPU not having the right frequency governor out of the box and hence is stuck at 800Mhz. The link above has a solution for that too.

Good Luck,
Nick

---

### Post by ooddiittyy on 2013-07-04
Thanks Nick; I had come across that page earlier today, but it's a bit over my head at the moment. I can dig into it more if need be, but I suppose I was hoping for a holy grail first. I assume eventually the hardware will be supported, but I haven't been part of the Linux community long enough to know what the latency is for that sort of thing. Thanks again for the response.

---

### Post by Dre_des on 2014-02-17
I wrote a post detailing the issues I encountered if anyone is interested[http://www.nicksplace.com.au/2013/07/01/sony-vaio-pro-13-vs-fedora-19/](http://www.nicksplace.com.au/2013/07/01/sony-vaio-pro-13-vs-fedora-19/)

Let me know if anyone wants any more info or help getting Linux running on this beautiful piece of hardware[/QUOTE]


Hi,
I was searching for Linux installations on Sony Viao Win8... wanted to find out how you fared with your fedora installation, but I cannot seem to open your link... anyway wanted to gauge if Fedora had more hiccups than Ubuntu..
regards

---


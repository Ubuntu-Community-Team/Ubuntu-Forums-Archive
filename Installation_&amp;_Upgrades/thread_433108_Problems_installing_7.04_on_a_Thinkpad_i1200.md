---
title: "Problems installing 7.04 on a Thinkpad i1200"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by vegardjo on 2007-05-04
Hi all, 

after failing to upgrade from 6.06 to 6.10 on my Thinkpad i1200 I wanted to try a fresh install of 7.04. 

When booting the CD the install stalls immediately, but when booting with the pci=conf2 option I get through the first progress bar, get to choose language and keyboard settings, but then it stalls again during "Detecting hardware to find CD-ROM drives" - at "Starting PC card services" (91% in).  I have tried with the noapic and nolapic options as well, and in combination with pci=conf2, but with the same result. 

Some additional info: under startup (with boot option pci=conf2) it says "[some numbers] Fatal: No config space access function found". Using the alternative install CD. 

And some more additional info: I had 6.06 successfully installed on this computer, but after upgrading to 6.10 it stalls during start up. If I try to boot with pci=conf2 I almost get to start it, but it failes to load X - I have tried the solution in this thread: [http://ubuntuforums.org/showthread.php?t=187177](http://ubuntuforums.org/showthread.php?t=187177) but also with no luck. 

Anyways, I would be happy if I could get a clean install of 7.04, as there are no importaint data on the computer. Anyone knows any tricks I can do to get this done? Oh, and I'm a complete n00b on Linux too, so please make it as detailed as possible :) All help appreciated!

---

### Post by vegardjo on 2007-05-12
For reference: 

After a lot of googling, cursing, trying and failing I am back with a clean install of 6.06. I was not able to do a update from 6.06 to 6.10 on the Thinkpad i1200, Nor a fresh install of 6.10, nor a fresh install of Ubuntu 7.04 or Xubuntu 7.04. 

I tried to boot with noapic, nolapic, apci=off, irqpoll, pci=conf2 and other options that I was recommended. All installs were tried from alternate CDs. 

To be able to install 6.06 successfully, I had to boot with the irqpoll option, or else it wouldn't find my cd-rom (it ignored the fact that it was already installing from that very cd-rom...). When booting with the irqpoll option everything went smooth. 

In short, installing Ubuntu / Xubuntu 6.10 / 7.04 on a IBM Thinkpad i1200 is not something any Linux beginner should try to do :) On a positive side, Ubuntu 6.06 runs like a charm!

I'd be interested if anyone has different experiences with this computer!

---

### Post by eightysix on 2007-05-14
Why use pci=conf2? I installed Xubuntu 7.04 without any special parameters and it worked just fine. 

Although, my battery life isn't showing up correctly. Did you get that to work?

---

### Post by vegardjo on 2007-05-15
Really, on the Thinkpad i1200? Strange, but good news (for you) :) 

When I tried to install without any additional boot options, the install stalled immediately. The only way I could get *any* progress on 6.10 and 7.04 was with the pci=conf2 option, but still no cigar. For 6.06 I needed to use the irqpoll option to get it installed. 

However, after reinstalling 6.06 it runs *a lot* better than my previous install of it. My previous install used 10+ minutes to start, and failed on "loading hardware drivers" during start up. On the new install everything runs perfectly, and start up time is around 2 minutes. Both were clean installs from the very same CD, so it doesn't make much sense. Maybe the disk wasn't properly formatted the first time or similar...?

Haven't really experimented with battery life, as it has been plugged in as long as I've used it after this latest install. The indicator worked fine on my previous install, but battery life seemed to be drastically reduced compared to what win XP used. From around 1.5 hours on a fully charged battery to around 45 minutes.

---

### Post by eightysix on 2007-05-15
> **vegardjo said:**
> 
Haven't really experimented with battery life, as it has been plugged in as long as I've used it after this latest install. The indicator worked fine on my previous install, but battery life seemed to be drastically reduced compared to what win XP used. From around 1.5 hours on a fully charged battery to around 45 minutes.

Let me know if you ever get the battery indicator working correctly. Mine still shows 00:-1 for the time for some damn reason. I think it was working in Dapper when I still had it installed, but I know for sure it worked before.

Also, what do the irqpoll and pci=conf2 switches do? :confused:

---

### Post by vegardjo on 2007-05-15
I can check it later today, but remember I am still on Dapper, as Feisty wouldn't install here.. 

What the boot options do? I have not the slightest idea, but changing these options is what you typically are recommended to try if you have any problems. And sometimes it works :)

---

### Post by byrdmeln on 2007-06-30
I also have an ibm thinkpad i1200 upgraded to 196 megs memory.

Funny, I also failed the 6.06 to 6.10 upgrade, but i had no problems with the 7.04 install itself (though i was using Xubuntu instead of ubuntu).  I didn't pick any boot options, just took all the suggested default parameters.  

Compared to 6.06, though, this version is VERY slow, and I'm also having the battery time in the negative error.   The problems were too annoying (there are a lot of other little bugs and hiccups it seems with 7.04, at least on my computer) so i took xubuntu off and am currently trying some other distros before I go back to 6.06 (unless i find something i like better of course!).  I currently have pupplylinux on.  It's fast -very fast- and getting my wireless to work was much, much easier then it was on Ubuntu (they almost seem to go out of their way to make it tough in Ubuntu?), but it uses Seamonkey and I hate seamonkey, it's ruining my whole experience.

---

### Post by lproven on 2008-04-29
Interested to read that someone else other than me has had problems with their i1200 series. I have an 1161-93g; if you Google for "thinkpad 1161-93g linux" you'll mostly find me looking for help in various forums and mailing lists!

I've just been trying 8.04 on my machine, as a Wubi installation, just out of curiosity, and to my surprise, it works rather better than before, but now the screen doesn't work.

I found the best kernel switch to use was "acpi=force". This overrides the kernel's detection of "safe" ACPI BIOSes and makes it use whatever is there. This gave me more joy than turning ACPI off manually, which the kernel does automatically anyway when it finds my 1999 BIOS.

Sound works and inserting a Cardbus USB2 adaptor worked. Hibernation seemed to hang the machine. 

However, my screen defaults to 800x600 and the xorg.conf file contains no mentions at all of screens or modes; I think I've just got some safe VESA fallback mode or something.

I fear these are pretty much Windows-only notebooks. :¬(

It may interest you to know, though, that on mine, PC-BSD 1.5 installed flawlessly and ran well. However, PC-BSD is a bit primitive compared to Linux. No power management, no wireless networking, no automounting of disk drives, nothing like that.

But if you use your Thinkpad on the mains on a wired network - my Xircom RealPort2 Ethernet card was detected and used automatically - then PC-BSD is an option.

I have, with regret, put Windows 2000 back on mine. With this, it works perfectly, and I get keyboard volume control, a working modem, power management, suspend/resume, DVD playback and so on. The only thing W2K doesn't do that XP supports is multiple monitors. XP is faster to boot and suspend/resume but 2K is noticeably faster in use. 

Mind you, although the 1161 /officially/ maxes out at 192MB, I have put a 256MB SO-DIMM in mine for 320MB RAM. That helps 2K/XP a *lot*.

HTH. HAND.

---


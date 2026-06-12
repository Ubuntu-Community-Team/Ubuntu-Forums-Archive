---
title: "system freezes/hangs, possibly Nvidia-related"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by Fipi on 2008-11-24
Hi, I'm having some trouble after installing Intrepid. I'm a linux newbie (first time having installed linux), so sorry in advance about any dumb things I say or do, noobness, etc. :D
First off, when I tried to install Ubuntu with the live CD, the setup would always freeze at different points throughout the installation, even in safe graphics mode. So I tried the alternate (text only) CD, and that worked. I got it all set up okay and everything seems to be working, except that occasionally the system freezes completely (ctrl-alt-F2 doesn't work). This usually happens when there is considerable activity, like opening a program, installing new stuff, scanning for music in Rhythmbox, etc. After many hours of intense googling and messing around, I haven't been able to solve the problem. Here are some things I've tried:

-turning off visual effects ... no change, still freezes
-checking "top" for high CPU % ... no problem here
-monitoring CPU temperature ... no problem
-running memtest overnight ... no problems
-changing boot options (including acpi=off, nolapic, noapic) ... boot errors resulted
-enabling the proprietary Nvidia driver (ver. 177) ... this actually makes the freezing more frequent, I think (maybe my mistake though)
-disabling VSync in the proprietary driver ... didn't help
-turning off powernow and then enabling the proprietary driver ... I don't think this helped, since after doing this I ran "glxgears" and the system froze after about 20 seconds (but the gears did not stop spinning, strangely). Also I'm kind of hesitant to leave powernow off for very long, I don't know if there's any danger to the CPU...

So I'm suspicious of my Nvidia card. It doesn't seem like it can be anything else. But I don't have any hard evidence, so I guess it could be anything. Help would be MUCH appreciated. I really want to get this working, because Ubuntu seems pretty cool. :)

My system specs:
Intel Core 2 Duo 2.4ghz
Abit AB9 motherboard
2gb RAM (all recognized by Ubuntu)
Nvidia 7900 GS video card
40gb IDE HD (Ubuntu is installed on this)
I also have a SATA hard drive with Windows XP on it (set up for dual boot with GRUB), if that helps any.

---

### Post by inobe on 2008-11-24
i have a few questions !

any memory and cpu timings other than stock including gpu ?

what is your current bios version ?

what temp is your video card reporting in ubuntu looking at nvidia settings ?

what channels are your memory sticks plugged into ?

--------------------------------------------------------------

side not: i think you are having this problem because of either a bad ide cable' or a bios issue between controllers !

backing up your data' then in your bios choose optimal defaults, save and exit may solve this.

---

### Post by Fipi on 2008-11-24
> **inobe said:**
> any memory and cpu timings other than stock including gpu ?
Nope, everything is running at stock timing.

> **inobe said:**
> what temp is your video card reporting in ubuntu looking at nvidia settings ?
While I could see the temperature it ran from 57 to about 60 degrees C. (The video card temperature is only available when the proprietary Nvidia driver is enabled.)

> **inobe said:**
> what channels are your memory sticks plugged into ?
They're both in channel A, 1 gb in each slot (they're the exact same model).

> **inobe said:**
> what is your current bios version ?
In my FlashMenu utility it says i965-W627EHG-6A79LA1AC-15. I'm pretty sure it's not the newest version.

EDIT: OK, so I have version 15 from 2006, and the the newest version is 22, so I'll update it to that.

> **inobe said:**
> in your bios choose optimal defaults, save and exit may solve this.
I did this, and Ubuntu still froze a few times. I'll try updating the bios, and see if that helps.

Oh, and by the way, I had Windows XP installed on this IDE hard drive for a long time and it never had any problems, and there were never any problems with my memory or video card in XP.

Thanks!

---

### Post by Fipi on 2008-11-24
Okay, this might take a while... FlashMenu (which is supposed to be able to update the abit BIOS automatically) says my motherboard isn't supported..... So I've been trying to make a bootable CD with the bios update files on it, because I don't have a floppy drive on my computer, but so far I haven't been successful. I tried following the instructions of several sites, including [Bart's]("http://www.nu2.nu/bootcd/#clean") and [another site]("http://www.bay-wolf.com/bootcd-bios.htm"), and a few others I can't find anymore, but the CDs all gave various errors when booting. ](*,)
I think I'll only work on this some more tomorrow. I have to do homework now. :(

---

### Post by Fipi on 2008-11-24
Would a floppy disk be any easier to work with to update the bios? From what I've read I get the idea that it would be easier, but I'm kind of noob about this stuff so I don't know. Maybe I'll just buy a floppy drive (if it's easier that way), because trying to make bootable CDs is a pain in the neck. If not then I'll just buy a few CD-RWs so that I don't waste any more CDs...

---

### Post by Fipi on 2008-11-25
Whew... I finally updated the bios. After many failed attempts at making a bootable CD, I made my USB flash drive bootable and flashed the bios from there. When I booted into Ubuntu I tried enabling the proprietary Nvidia driver, and it worked! (Before I was only able to do this with powernow turned off.) So I rebooted and, just to make sure, I ran a bunch of programs at the same time and did things that could have caused freezing before, and there was no freezing. w0000000000000000000t!!!!!! :guitar:
So I'm pretty sure everything is okay now, but time will tell. Thanks a bunch, inobe!!! :D:D:D

---

### Post by inobe on 2008-11-26
hey your welcome, glad to see you stuck it out' even threw difficult situations :)

---


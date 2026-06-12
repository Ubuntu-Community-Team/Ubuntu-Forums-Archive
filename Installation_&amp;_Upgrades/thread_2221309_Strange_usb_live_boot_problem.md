---
title: "Strange usb live boot problem"
date: 2014-05-01
forum: Installation &amp; Upgrades
---

### Post by rob20 on 2014-05-01
Hi all.

I have a strange problem I hope you can help me with.
I have created a live usb stick using Unetbootin which I have heard does a good job. The image I wrote from was a lubuntu 14.04 iso file.
I booted the stick on my machine to make sure it was working, reset the keyboard yo uk etc. No problems.

I then took the stick to a freinds, who is currently using Win xp and wished to carry on using her laptop but would like to change to another OS.
The machine is a Fujitsu Siemens Amilo L7320GW.
I have a "screen shot" of the problem.
Sorry for the quality, it was taken with a mobile phone.

[IMG]http://s23.postimg.org/wpraio17v/jen_boot_failiure.jpg[/IMG]
For some reason you can see the lubuntu bar at the botton of the screen, but also the xp shutdown screen behind it. I have no idea what is happening here. I can't see how this could happen, Either XP boots, or lubuntu, not both.
I removed the dhh and this odd behaviour stopped, but if I wish to install, I cannot do that. I also have some graphics driver issues, but I think that could be for next time. Once I figure out what is happening here.

Apparently the machine uses a VIA/S3G UniChrome Pro IGP chipset. I have no idea if Lubuntu would handle this.

If anyone has any idea what is happening here I would love to know.

Thanks.

Rob
Trying to convert the masses to Linux, one user at a time :)

---

### Post by C.S.Cameron on 2014-05-01
Wow! looks like you have found a way to do a true dual boot.

Does this still work if you do a full shut down before booting Lubuntu.

---

### Post by rob20 on 2014-05-01
This was from a cold boot. I had to change the bios settings to get it to boot from stick, so this is a boot from a powered off state. The only way I could stop this happening was to physically remove the internal hard drive of the machine. I tried several times and this is all I could get with the hard drive installed. With the hard drive removed it did boot into lubuntu, but I had graphics driver issues. That's another problem though.
I just don't know how it is possible to achieve this. As far as I am aware, you can only boot from one device at a time.... I have been in to computers for years, and have never come across this before. I'm at a lose to explain it

As I posted, the stick worked fine with my machine (Blazingly quick on an i5 with 8Gb even from stick. wow) but seems to have some really odd issues with the Amilo. As I posted in the title. Strange......

---

### Post by jetblackstar on 2014-06-07
Just tried 14.04 on an old fugitsu Siemens Amilo L7320GW.
Same issue visually, though without the windows gfx lag. Red freaked out graphics which partially work and boots the Ubuntu interface. But its in unusable.
I am relatively sure the issue is a gfx driver or setting issue with 14.04. 
I've tried the various basic boot options (press any key when little man ubuntu symbol comes up and then hit f6 at the menu) 
of acpi=off and lacpi. No improvement.

I think the best hope is to install using the alternative/text installer and find an xorg.config setup or driver option that fixed issues on earlier ubuntus. Gfx issues are easier to solve when you have an install on your HDD rather than USB boot disk.

If I find a solution I'll post it hwere
.
-jet

---


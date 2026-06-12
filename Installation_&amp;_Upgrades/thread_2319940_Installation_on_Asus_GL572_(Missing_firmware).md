---
title: "Installation on Asus GL572 (Missing firmware)"
date: 2016-04-08
forum: Installation &amp; Upgrades
---

### Post by andre56 on 2016-04-08
I recently bought an Asus GL572, and am having no luck at all installing Ubuntu. 

[http://laptoping.com/specs/product/asus-gl752vw/](http://laptoping.com/specs/product/asus-gl752vw/)

I have tried both 14.04.4 and 15.10, and continue to get the same messages about missing firmware. I was able to install openSUSE, and installed the firmware through there, thinking the Ubuntu installation might then pick it up, but apparently firmware doesn't work like that anymore. 

This is the error screen I get:

[http://i.imgur.com/wN0Dkpx.jpg](http://i.imgur.com/wN0Dkpx.jpg)

Note that that is only visible when I plug in a HDMI cable to the TV. The laptop screen itself goes completely black. 

I am only able to load this screen on boot:

[http://i.imgur.com/T7nsdOg.jpg](http://i.imgur.com/T7nsdOg.jpg)

I have fully messed with all of the different boot settings available in BIOS, to no avail. And I've gone through every thread I could find relating to this issue, none of it has worked. I've also tried several different versions. 

Presumably, I need some firmware integrated into the installation USB, but I have no idea how to do that and can't find the information anywhere. 

I am a longtime Ubuntu user, but as you can probably tell, I don't know a whole lot about how it works. I mostly just set up my computer with it and everything tends to work. I'm usually pretty good at solving problems by reading forums. Six years and this is the first time I have ever posted a thread asking for help. I should be able to follow most instructions.

Presently though, I cannot get to a command line on installation. 

Thanks!

---

### Post by ubfan1 on 2016-04-09
Looks like bug 1496163.  Add yourself to the list, try comment #9's fix:

Line 120 in /usr/share/initramfs-tools/hook-functions:
     cp -a "$firmware" "$target_dir"
change to

   cp -aL "$firmware" "$target_dir"

or maybe
sudo update-initramfs -u -k all

---

### Post by andre56 on 2016-04-09
Sorry, can I edit that on the install USB?

Thank you.

---

### Post by andre56 on 2016-04-13
Does anyone else have any thoughts on this? Apparently it is a Skylake is causing a lot of troubles, but I just can't find any more info. 

Should I just make this a gaming computer until some of these bugs are worked out?

---

### Post by mörgæs on 2016-04-13
Have you tried 16.04?

---


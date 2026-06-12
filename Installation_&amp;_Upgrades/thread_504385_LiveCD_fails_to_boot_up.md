---
title: "LiveCD fails to boot up"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by dhehmann on 2007-07-19
I've burned 7.04 and checked the disc to make sure everything is alright, but when I try to load up the LiveCD, it paused at 68.644639 and goes nowhere from there. I've looked around for similar problems and haven't found any. Any help would be greatly appreciated.

HP Pavilion
Intel(R)
Pentium(R) 4 CPU 3.00GHz, 0.99 GB of Ram
Radeon 9250

---

### Post by splintercellguy on 2007-07-19
What is the message at that particular point?

---

### Post by dhehmann on 2007-07-19
I get a few different messages, each time. Here are some examples.


[IMG]http://i76.photobucket.com/albums/j35/_-___/DSC00013.jpg[/IMG]

[IMG]http://i76.photobucket.com/albums/j35/_-___/DSC00011.jpg[/IMG]

[IMG]http://i76.photobucket.com/albums/j35/_-___/DSC00010.jpg[/IMG]

---

### Post by confused57 on 2007-07-19
Adding extra boot options may help:
[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))

You might also try some or all of these: acpi=off, nomce, nousb, noapic, pci=nommconf...if the above link doesn't provide a solution.

---

### Post by aprad046 on 2007-07-19
I have the same problem, with both  version 6.10 and 7.04. Doesn't work with the 64-bit version either

I am running a P4 524 with HT and an Asus P5P800-MX Motherboard with integrated video.
I also installed an NVidia 5200 (only PCI video card that Vista would like). 

When booting with the 5200, that error appears, and no boot happens.
When I boot using the internal VGA card, it runs smoothly.

As a side note, all the other distros of linux that I've tried that use Debian (DSL, Freespire, puppyLinux, etc) also freeze when booting.  However, FeatherLinux ( an offshoot of Knoppix) and GeexBox ( a linux distro that turns your computer into a media player) boot normally.

Any suggestions?

---

### Post by dhehmann on 2007-07-20
> **confused57 said:**
> Adding extra boot options may help:
[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))

You might also try some or all of these: acpi=off, nomce, nousb, noapic, pci=nommconf...if the above link doesn't provide a solution.

Pardon my ignorance, but how exactly do I try those? I'm assuming I press F6 and just type them in? I tried the suggestions in the link you posted to no avail, so I'm looking to move on to the next step.

---

### Post by dhehmann on 2007-07-20
Update: I've given all of the suggestions a shot, and none of them have solved the problem. In case this may help. I feel I should mention that the orange status bar that scrolls back and forth below the Ubuntu logo flickers as it loads, so I'm thinking it may have to do with my video card. The fact that the guy above me has the same problem because of a video card, adds weight to that notion.

If anyone knows how I can resolve this issue, your help would be greatly appreciated.

---

### Post by dhehmann on 2007-07-20
Sorry to bump this up, but does anyone have an idea how I could solve this problem, or an alternate way that I can install Ubuntu? Any help would be much appreciated.

Update: I've given all of the suggestions a shot, and none of them have solved the problem. In case this may help. I feel I should mention that the orange status bar that scrolls back and forth below the Ubuntu logo flickers as it loads, so I'm thinking it may have to do with my video card. The fact that the guy above me has the same problem because of a video card, adds weight to that notion.

If anyone knows how I can resolve this issue, your help would be greatly appreciated.

---

### Post by Pumalite on 2007-07-20
Why don't you try the Alternate CD?

---


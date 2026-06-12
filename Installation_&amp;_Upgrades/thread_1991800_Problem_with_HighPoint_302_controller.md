---
title: "Problem with HighPoint 302 controller"
date: 2012-05-31
forum: Installation &amp; Upgrades
---

### Post by kmadsen on 2012-05-31
I have been going around in circles with my Ubuntu installation for the last several weeks and I think I just figured out why.  Now I need someone's help to figure out how to fix it.

I have a dual-boot WinXP and Ubuntu installation that's been around since 8.04 or so. I had happily upgraded it until a week or two ago when I upgraded from 10.10 to 11.04.  At that point my system would no longer boot.  I get variations of a white screen, black screen, or one filled with vertical bar characters, sometimes black & white, sometimes flashing red. This led me down the path of diagnosing a video problem. Thankfully, I found instructions in this forum on saving my data before I did the fresh installs.

The mainboard is an Asus P5N-MX with Nvidia GeForce 7050/610i graphics. Windows and Ubuntu are on separate IDE drives.  After the failed upgrade, I have tried full installations of various versions, all with the same results. The Live CD(s) boot up fine, and I'm able to mount the installed system, so somehow the disks are accessible.  However, I think there is a driver or GRUB parameter missing that would allow Ubuntu to boot.

The IDE drives are connected to a HighPoint Technologies HPT302 card, not in a raid configuration.  I don't recall building the driver originally from the CD that came with the card, but I might have.  If I did, that probably won't help because it is for a far earlier kernel than is current, and downloads for this product are no longer available.

Any ideas?  I could buy an SATA drive and load Ubuntu on that -- that might be the quickest way out at this point after considerable grief.

Here is my Boot Info from Boot-repair:  [http://paste.ubuntu.com/1015818](http://paste.ubuntu.com/1015818)
Boot-repair went through its process but it was not able to help.

Any help would be appreciated.

Kent

---


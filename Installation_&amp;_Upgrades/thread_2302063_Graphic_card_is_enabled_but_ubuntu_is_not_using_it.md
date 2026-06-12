---
title: "Graphic card is enabled but ubuntu is not using it"
date: 2015-11-07
forum: Installation &amp; Upgrades
---

### Post by Victor_Gnanaraj on 2015-11-07
Hi All,

I just dualbooted my y510p with Ubuntu 15.04 and was surprised i din't end up with a black screen after i installed NVIDIA proprietary drivers. But then i figured out that it was not working, i can clearly see this if i watch an youtube vido or play a 1080p video in VLC, i would be seeing frames being skipped.

I used many commands foudn in the internet to check if my NVIDIA M755 was working or not. They were all reporting that it was working fine. But in reality my GPU is not used at all by Ubuntu.

Here is the funny thing, if i switch from NVIDIA to my inbuild INTEL HD using PRIME in NVIDIA settings, my system seems to be much better in case of graphic performance. I can watch youtube videos without the framrate issue. But still cannot watch 1080P videos but this thanks to the power of the INTEL HD graphics.

Can someone kindly help me in making the NVIDIA card work, please :cry:.

FYI i have tried 352 & 340, both drivers aren doing the exact same thing.

---

### Post by Vladlenin5000 on 2015-11-07
Hi and welcome.

You mean this [Lenovo Ideapad Y510P]("http://shop.lenovo.com/us/en/laptops/lenovo/y-series/y510p/#tab-tech_specs")? Unless seriously defective, whatever the cause the problem is with your browser (Firefox?) and codecs (local video files). The integrated Intel is more than enough for 4K, let alone 1080P... The cheapest Chinese ARM processors - Rockchip, Allwinner, etc. - do fullHD without breaking a sweat and using 20% or less of their "power".

How does it work in Windows? If it works perfectly for all tasks you mentioned then you're good to go. I strongly suggest you do a fresh Ubuntu 15.10 install (15.04 will run out of support in a few months). Then install the recommend nvidia proprietary driver at System Settings > Software Properties > Additional drivers (the rightmost tab).

---

### Post by grahammechanical on 2015-11-07
So, Ubuntu is using the Nvidia graphic adapter. The issue is dropped frames with 1080p videos. That is not the same as saying Ubuntu is not using the Nvidia adapter. You should change your thread title. Then you may get advice relevant to your actual problem.

 The Nvidia web site recommends the 352.55 driver for the Geforce GT 755M. Go with the latest driver.

Regards.

---

### Post by Victor_Gnanaraj on 2015-11-07
Im sorry for confusing. Im not sure why the Intel Card will not play 1080P it plays fine in windows(i should have checked). Also the reason why im saying ubuntu is not using NVIDIA is because, i can see stuttering in desktop graphics. When i hold on to a file windows and shake it, i can see the window tear. When i am using my intel card tear isnt happening.

Is there any library files as such missing ?

UPDATE: Fixed my VLC 1080p issue with INTEL HD card by enabling VA_API decoder in video settings.

---


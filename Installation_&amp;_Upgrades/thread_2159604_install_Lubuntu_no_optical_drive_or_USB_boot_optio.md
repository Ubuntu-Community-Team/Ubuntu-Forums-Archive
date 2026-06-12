---
title: "install Lubuntu no optical drive or USB boot option"
date: 2013-07-03
forum: Installation &amp; Upgrades
---

### Post by jonawald on 2013-07-03
I am trying to install Lubuntu on an Acer Aspire 3000 laptop. The optical drive on it is shot. It does not have the option to boot from USB. 

I tooke the HD and put it into a different laptop and installed Lubuntu there. When I put it back into the Acer, it would not boot. I am not very surprised, but am wondering if there is a command I can run to get things fixed up.

When I try booting it, I see the Lubuntu logo as if it were booting normally, then I see text across the top with user name and login prompt as if it was getting ready to post the login page. Then I see the background with a curser in the middle. From there it will flash to black then the screen will re-apear. I get stuck in a loop of this. 

Tried going for advanced boot options and fix broken packages, Tried dropping to command line from advanced boot options and ran a bunch of commands I found to try to configure x. xconfigure didn't work. xrandr didn't do anything for me either. 

Any body have an idea for me or is there another way to install Lubunto on this computer that will just work?

Jonathan

---

### Post by The Titan on 2013-07-03
I am no expert in this area, but if you have the option to boot from the network you could try this [https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot).  Sorry if I am of no help, but it is worth a shot.

---

### Post by jonawald on 2013-07-04
> **The Titan said:**
> I am no expert in this area, but if you have the option to boot from the network you could try this [https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot).  Sorry if I am of no help, but it is worth a shot.

Sounds like it could work, another thing I have been thinking about is trying to copy the contents form the Live CD to a small partition on the HD and setting that to boot. Once it's booted, I could install to a larger partition. Wish that could work.

Jonathan

---

### Post by The Titan on 2013-07-04
I dont see why that wouldn't work, it definitely sounds interesting.  If you do try that, will you post your results back here?  May help somebody in the future.

---

### Post by sudodus on 2013-07-05
Your original concept works as well as any other concept would work because installed Ubuntu family desktop systems are portable unless you install proprietary drivers (that are not supported by the next computer).

- What about the original system, that you installed in the other computer: Did you install any proprietary driver?

- What's the graphic chip/card?

- Which version of Lubuntu are you trying (13.04)? In that case you may have better luck with 12.04 (with a short time to end of life, yes I know, but if it works, there are ways to continue, for example Xubuntu 12.04 LTS until April 2015 or LXLE until April 2017).

I am almost sure that the problem is with the graphics. What you need is probably a proprietary driver or some boot option(s) to get the graphics working.

If you have nvidia graphics, it should help with the boot option ***nomodeset***. See this link for details

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

[COLOR=#000000]If you have ATI/AMD/Radeon graphics you might succeed by booting in text mode: use the boot option 'text' (without quotes). And then in text mode, you can install the proprietary driver, like you install another program package in the newest version of Ubuntu. In older versions (I think 12.04 LTS) you can use jockey-text, or in some cases you download a deb package from the manufacturer's web-site and install it according to the instructions within that package. See these links[/COLOR]

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

If you have Intel graphics, it should work well with the built in driver (except very few cases).

-o-

In some rare cases the wifi chip/card can disturb the boot process. If you have one, can you switch it off (with a mechanical switch or a setting in a BIOS menu)?

---

### Post by jonawald on 2013-07-05
Thanks for that informaiton. I as hoping somebody would wade in here and give me some other options. There has to be a way to get it going. I am not sure which graphics the Acer uses, but I can look it up. Will take time later today to figure that out. 

Jonathan

---

### Post by jonawald on 2013-07-05
i did not install any proprietary drivers btw.

---

### Post by grahammechanical on 2013-07-05
You have become familiar with the Advanced options section. Have you tried Recovery Mode>Resume. That sometimes gets us to a desktop using basic video drivers. From there you can activate a video driver. I cannot advise how to do that on Lubuntu. Sorry.

You say you did not install a proprietary video driver but did you tick to install third party software? When we do that we also agree to installing a proprietary video driver. And that could be causing this problem. The OS has a video driver suitable for the other laptop but not for the Acer.

Try re-installing without ticking Install Third Party Software. I always install that way. It avoids issues with proprietary video drivers that seem to be happening a lot lately.

Regards.

---

### Post by TNFrank on 2013-07-05
You could always try to get a replacement optical drive for it. Don't know if this one would work but this is just an example of how cheap they are to replace.
[http://www.electronicscafe.com/acer-travelmate-4070-laptop-cd-rw-dvd-rom-combo-drive/](http://www.electronicscafe.com/acer-travelmate-4070-laptop-cd-rw-dvd-rom-combo-drive/)
I got an upgraded DVD-RW from these guys for my nc8230 for $18 bucks shipped.

---

### Post by jonawald on 2013-07-08
There is no recovery resume option in the advanced menu. I didn't click alow extras because install crashed when I tried that option.

---

### Post by jonawald on 2013-07-08
graphics adapter on the acer is  SIS Mirage 2 M760 64 MB.

---

### Post by sudodus on 2013-07-08
You may need to search for a current linux distro, that has a working driver for that graphics chip/card. I suggest that you try Xubuntu 12.04 LTS, Knoppix, a suitable version of Puppy linux or Crunchbang. See this link: [Old hardware]("http://ubuntuforums.org/showthread.php?t=2130640")

---


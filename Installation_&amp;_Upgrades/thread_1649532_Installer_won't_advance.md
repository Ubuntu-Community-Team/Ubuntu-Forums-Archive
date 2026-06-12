---
title: "Installer won't advance"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by NWC on 2010-12-20
Hello,

This is maybe the 15th time I've installed an Ubuntu OS in the past two years, and it's the first time I've really been stuck.

Not long ago I installed 10.10, with no problems, but a couple days ago I did a fresh install of windows 7, and I planned to re-install ubuntu 10.10 alongside it. Before I installed windows, I created a partition on my 320gb HD, half and half, but while doing this I noticed that gparted would crash if a USB key was plugged in. I mention this because I'm convinced this is related to the problem.

After having installed windows, I went and created a bootable usb key with 10.10 using unetbootin (which I've used once before, but along time ago). I'm unable to make an actual live CD because my disk drive has been broken for the past year - a fact that has never stopped me from installing different distros with a usb key.

So the installer starts as usual, but after the 2nd (or 3rd) step (where it says "for best results, make sure that your computer is plugged in, that you have an internet connection, and at least [...] of free space), I click forward, and the little wheel just spins forever, it never advances. I tried everything again with 10.04.1 and I got the same thing, this time after choosing my keyboard layout.

When I simply go to the live distro and then go to install, I see that at that moment, there's a crash report, something about gparted, which I'm assuming is a built-in part of the next step.

To sum up
-gparted doesn't seem to like USB keys
-installer won't advance to partition table
-can't use a disk because drive is broken!

My computer is an Acer Aspire 4530, AMD64. The 10.10 and the 10.04.1 installations were both 64bit.

Thanks in advance for your help, I don't want to be stuck with just windows!

---

### Post by Quackers on 2010-12-20
Have you checked the MD5SUM of the downloaded iso?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also if you tap the F6 key during boot you will get some options up. One of them is to check the cd for errors. Try that.

---

### Post by NWC on 2010-12-20
Thanks for your response.

I don't think there's anything wrong with the .iso itself, I used the same .iso which I kept on my external HD to install 10.10 a month or so ago. And since I had the same problem with a newly downloaded 10.04.1, it would be overly coincidental for it to stall at the same point.

I will check the key for errors though, as I don't have much experience with unetbootin, I've almost always used the built-in usb live disk creator.

---

### Post by ppv on 2010-12-20
Do you have another USB key to try out with.

---

### Post by sikander3786 on 2010-12-20
An explanation of the F6 bootoptions *Quackers* mentioned above.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

There are 6 options and you need to try all of them one-by-one.

From the same page, it is also worth to "Check Disc for Defects".

And in case your USB chipset has run faulty, try changing the USB mode to 1.0 instead of 2.0 from the Bios menu and try again.

Keep us posted :-)

---

### Post by ppv on 2010-12-20
Dont know if it is possible but when you see the spinning wheel can you hit escape and see the messages appearing on screen.

---

### Post by NWC on 2010-12-20
I checked the disk for defects, and it said I had 1, but didn't say what it was, it just say "press any key to reboot". So I had the idea to borrow my girlfriend's USB key, which I've used before to install 10.10, and I thought I would go on the live 10.10 thing that I can manage from the unetbootin key, then use the ubuntu startup disk creator, which I've always used, to create make my girlfriend's key bootable. I copied the .iso from my external HD to the desktop and tried, but when I rebooted with her key in, it said there was an unknown keyword in ..something (I should have written it down), and then just said "Boot:" but nothing happened. Same thing after trying it again.

I guess now I'll try unetbootin on her key, though I'm expecting the same result. Assuming I get the same result, I'll hit escape when the spinning wheel is there to see what's going on.

Thanks again everyone for your help.

---

### Post by sikander3786 on 2010-12-20
Make sure the image being used to burn the USB discs is in good health. See *Quackers* post above. Post # 2.

If the image is corrupted, obviously anthing created from it will return an error. You might need to re-download then.

---

### Post by NWC on 2010-12-20
> **sikander3786 said:**
> Make sure the image being used to burn the USB discs is in good health. See *Quackers* post above. Post # 2.

If the image is corrupted, obviously anthing created from it will return an error. You might need to re-download then.

Just did that, the checksums are the same. Going to try the installer on my gf's key now.

EDIT: Success! I used unetbootin with my gf's key and it it installed perfectly. The only possible reason I can think of is that I formatter her drive to FAT, which was its default, whereas I had formatted my own to FAT32, which was its default. Both of our keys are new, she got hers a month ago and I bought my new one this weekend.

So happy to have my dual-boot setup back :) thanks for the help!

---


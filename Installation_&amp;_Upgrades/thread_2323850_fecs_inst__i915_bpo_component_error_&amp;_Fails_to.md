---
title: "fecs_inst / i915_bpo component error &amp; Fails to Load GUI"
date: 2016-05-08
forum: Installation &amp; Upgrades
---

### Post by djrobthaman on 2016-05-08
Hello everyone,

I've had a very interesting time with installing the latest version of ubuntu (16.04).

Initially, I could barely get it to work. After a fresh install ubuntu would load only the desktop background but nothing else. The top bar and the unity sidebar were nowhere to be found and the only thing I could do would be to move the mouse.

Then I discovered if I popped out to the shell and installed proprietary drivers for my video card that I would be met with a very ugly (read lo-res) ubuntu login screen (I opted to log in automatically so this really shouldn't happen). Upon logging in I would be presented with only the desktop background followed by being promptly logged right back out to the login screen after about 5 seconds.

A further discovery is that if I then uninstalled the drivers in the shell (using apt-get purge nvidia*), I got a step further than initially. Upon starting up my machine I would still be presented with only with the desktop background. However, I could now right-click on the desktop and get a dialogue box which means I could launch the terminal. From there I could launch programs but the top bar and unity bar were still absent as were any window decorations for the terminal or any other program that I launched.

After a few days I tried another fresh install, immediately popped out to the shell and applied the latest updates to ubuntu and upon reboot it finally seemed to be working. All functionality was there (granted there were bugs but these were the type of things I could handle / took as not indicative of something larger; the default ubuntu store straight up didn't work, I had to do some manual user group management to allow removable media to automatically mount and my media keys were not functional)

A few days later, I turned off the computer and the next time I turned it back on it wouldn't load the gui. Instead I received the following message:


[0.908008] nouveau 0000:02:00.0: gr: failed to load fecs_inst
/dev/sdb6: recovering journal
/dev/sdb6: clean, 210983/15804268 files, 14917072/63519531 blocks
[2.438453] snd_hda_intel 0000:00:1f.3: failed to add i915_bpo component master (-19)


After the above message, it shows text welcoming me to emergency mode and pressing enter pops me into shell. I'm not sure what the issue is and woudl appreciate any help / guidance you may have.

Please see my specs below:

MSI GeForce GTX 960 DirectX 12 GTX 960 GAMING 4G 4GB 128-Bit GDDR5 PCI Express 3.0 x16 HDCP Ready SLI Support ATX Video Card
Intel Core i7-6700K 8M Skylake Quad-Core 4.0 GHz LGA 1151 91W BX80662I76700K Desktop Processor Intel HD Graphics 530
ASUS Z170-A LGA 1151 Intel Z170 HDMI SATA 6Gb/s USB 3.1 USB 3.0 ATX Intel Motherboard
G.SKILL TridentZ Series 16GB (2 x 8GB) 288-Pin DDR4 SDRAM DDR4 3200 (PC4 25600) Intel Z170 Platform Desktop Memory Model F4-3200C16D-16GTZ
SAMSUNG 850 EVO 2.5" 500GB SATA III 3-D Vertical Internal Solid State Drive (SSD) MZ-75E500B/AM
WD WD10EZEX 1TB Desktop Hard Disk Drive - 7200 RPM SATA 6 Gb/s 64MB Cache 3.5-Inch, Blue

---

### Post by djrobthaman on 2016-05-10
And somehow, now it loads without a problem. This after doing nothing but waiting 4 or 5 days before trying to login to ubuntu again.

This is good for now but still a bit distressing since I'm not quite sure what the issue was in the first place and imagine that it will all break again sometime soon.

I would most definitely welcome any suggestions as to what my problem could have been and what to do to try and make sure it doesn't break again.

---

### Post by djrobthaman on 2016-05-23
This error's been plaguing me on and off since the last time I posted. There are days when I boot into ubuntu no problem and days when I get hit with the terminal and that error message. Right now I haven't been able to use the ubuntu UI for about a few days. I'm hoping someone knows what I can do to fix it.

Thanks.

---

### Post by swagrid on 2016-07-01
Hello,

my brother had the exact same issue on his PC:

ASUS Z170-A Pro
i7-6700K
Gainward GTX960 Phantom

EDIT: he also has the latest Ubuntu 16.04 installed

I just solved it for him by setting the iGPU Multi-Monitor setting to enabled in the BIOS as suggested in this thread:

[http://ubuntuforums.org/showthread.php?t=2301908](http://ubuntuforums.org/showthread.php?t=2301908)

Hope this helps you too!

---


---
title: "Install on Google Chrome OS Cr-48 Notebook"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by Dragonbite on 2010-12-28
I have one of the Google Chrome OS Cr-48 laptops and I have read that people are able to install Ubuntu along side of it (dual-boot).

I am tempted, but wonder if anybody else here has done it or are thinking of it so as to get some back-and-forth on pitfalls, methods and experiences.

Like whether or not all components work out of the box (wireless better, there are no NICs installed, but what about video, Verizon 3G, 1-second boot, battery life, etc.?)  I read it has a 16 GB SSD drive, which limits what you can do with it.  I always prefer to attempt something like this if I know I can "roll-back" or restore the system to the original configuration.

That isn't to say the Chrome OS sucks, because it doesn't.  Yet it is different than a typical laptop or desktop in that just about everything has to be online and unlike Jolicloud, local applications are not available beyond a Chrome extension.

---

### Post by Dragonbite on 2010-12-28
Oh, I did find this page which goes over step-by-step how to install Ubuntu on teh Cr-48.
[LIST][*][_How to boot Ubuntu on a Cr-48_]("https://sites.google.com/a/chromium.org/dev/chromium-os/developer-information-for-chrome-os-devices/cr-48-chrome-notebook-developer-information/how-to-boot-ubuntu-on-a-cr-48")[/LIST]At least there is also a page on how to recover the Chrome OS, just in case you screw something up. [LIST][*][_Troubleshoot common issues: Recover Chrome OS_]("http://www.google.com/support/chromeos/bin/answer.py?hl=en&answer=1080595")[/LIST]This all seems a bit trickier than I've gotten spoiled with in regards to Ubuntu and Linux in general, so I'll have to make sure I've got my hacker-hat on tight and be ready for a rough ride! :)

But considering the light weight and 8hr battery life, the idea of running Ubuntu (or any other Linux) on it is enticing even if it means running the Chrome OS Kernel with Ubuntu on top of it.

---

### Post by dizzysoul on 2010-12-28
I can answer any questions you may have.

> I am tempted, but wonder if anybody else here has done it or are thinking of it so as to get some back-and-forth on pitfalls, methods and experiences.

The best guide I have found for installing ubuntu [is here]("http://ubuntuforums.org/showpost.php?p=10273278&postcount=6").

Once you get everything up and running, there aren't any downsides. Installing the chrome browser under Ubuntu will give back 99% functionality of ChromeOS. You have nothing to lose, and everything to gain.

> Like whether or not all components work out of the box (wireless better, there are no NICs installed, but what about video, Verizon 3G, 1-second boot, battery life, etc.?)

From what I can tell, everything seems to work. The WAN modem might require a little [extra configuration]("http://ubuntuforums.org/showthread.php?t=1456735&highlight=gobi+2000"). There's also a secret bluetooth module built into the Cr-48 that ChromeOS doesn't seem to use, but Ubuntu picks it up just fine.

The touchpad installs as a ps/2 device, meaning you can't configure any touchpad-specific settings for it (that might be a 10.10 issue) through the GUI. It also has a mechanical right-click and left-click, even though it's designed as a single pad. If you want to manually disable tap-to-click on your touchpad, or add some multi-touch features, you can try editing the device config files manually. More info [here.]("http://www.bhagwad.com/blog/2010/technology/alps-synaptics-touchpad-configuration-in-lucid-lynx-ubuntu-10-04.html")

The top-row system keys are recognized as F1-F10 keys, so you will have to assign keyboard shortcuts to them. Be sure to add 'xbacklight -inc 15' and 'xbacklight -dec 10' as key binds to raise and lower your screen's brightness. The "search" key is recognized as a mod (or function) key, which is useless. You will probably want to re-bind that key as caps-lock, or some other worthwhile key using xmodmap.

The battery life is about 6-7 hours, depending on usage. The suspend resume time is 1-2 seconds, and the boot from power-off time is about 5-6 seconds.

> I read it has a 16 GB SSD drive, which limits what you can do with it. I always prefer to attempt something like this if I know I can "roll-back" or restore the system to the original configuration.

After everything is said and done, you will end up with about 2.5GB of free space. You might be able to steal more from the ChromeOS partitions, if you really want to. I haven't run into any problems due to the space restrictions, but you will likely want to carry around a flash drive or SD card to offload big files.

> That isn't to say the Chrome OS sucks, because it doesn't. Yet it is different than a typical laptop or desktop in that just about everything has to be online and unlike Jolicloud, local applications are not available beyond a Chrome extension.

The funny thing about ChromeOS, is that because it's based almost entirely off Chrome and linux, and it off-loads everything into the cloud.. there really isn't much to 'test' in terms of bugs and software issues. For its designed purpose, ChromeOS runs beautifully, and is incredibly stable. Evey time I clicked on that little bug icon in the top-right corner, I could only think to bitch about hardware issues or missing functionality, which I don't think is the kind of feedback Google is looking for.

If you have any other questions, let me know!

---

### Post by Dragonbite on 2010-12-28
Thanks! That's a lot of information to read through.

I just tried flipping the switch and it came to that error screen. So I switched it back and ARGH! I had to re-setup the machine and take my picture! I lost all of my previous configuration (which isn't much).

---


---
title: "Please help me install Ubuntu on EEE PC"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by cwklinuxguy on 2010-01-10
Hi there. I have a EEE PC 1005HA computer that I will be using for school. I downloaded UNR and put in on a USB flash drive. I followed the instructions at [http://crunchbanglinux.org/forums/topic/3954/asus-eee-pc-1005ha-crunchbang-installation-guide/ ]("http://crunchbanglinux.org/forums/topic/3954/asus-eee-pc-1005ha-crunchbang-installation-guide/")
to find out how to boot from the flash drive, but it doesn't show up as an option in Windows Boot Manager. Please give me a hand if possible. Can someone take me through EXACTLY what to do?
[]("http://crunchbanglinux.org/forums/topic/3954/asus-eee-pc-1005ha-crunchbang-installation-guide/")

---

### Post by darkod on 2010-01-10
Well if you followed that tutorial I guess this is what you need to do to boot the stick:
By default the 1005HA has something called 'Boot Booster' enabled which might prevent you from booting using a USB-Stick. To disable this go into the BIOS by repeatedly pressing F2 after turning on the Eee PC. Don't change anything and just press F10 to save and exit from the BIOS. After having exited repeatedly press ESC to get into the boot device selection screen. Once there just select your USB-Stick. When the UNetBootin menu pops up you should choose 'Default' and then wait untill crunchbang has started up.

You are aware this seems to be some crunchbang linux and not full ubuntu? Why did you choose that, are you low on space with only small hdd disk?

---

### Post by cwklinuxguy on 2010-01-10
This was referred to me by my dad. I am not using Crunchbag, but theoretically installing it should mostly be the same.

---

### Post by Eskobar on 2010-01-11
If you are not a proficient  Linux user, I would recommend just using NBR (netbook remix). I recently tried to install several different OS's on 1005ha, I was just messing around and seeing how simple it would be.  Basically just comaring and contrasting different distros vs. XP.  Netbook remix installed without a problem and easy peezy went well.  I really was trying to see how easy/hard it would be for someone who has minimal experience with pc's to install different distros, because I have been speakin on Linux to customers and decided to just test before I stuck my foot in my mouth about how "great linux is".  Needless to say........I caught hell with most distro's.  Not to say that its not easy to install them, but I figure if I am a computer tech (mostly familiar with windows environment) with a very little experience with linux/ubuntu (roughly 6 months), then someone with basic computer knowledge at all will have trouble with different distros.  You should try NBR everything worked out of the box for the 10005ha if I remember correctly and if it didn't once it updated everything worked.

---

### Post by cwklinuxguy on 2010-01-11
That is what I'm using. UNR. The instructions are only for the selection of the boot device on that specific model computer. I got the computer to recognize my flash drive, but it won't boot. Help?

---


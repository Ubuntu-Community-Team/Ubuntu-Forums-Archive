---
title: "New to Lubuntu"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by CommuneOfLoon on 2012-04-26
I recently decided I wanted to give Lubuntu a try on my old Dell laptop. I am not computer savvy, and other than running Ubuntu 10.04 for the past year and a half, I have no experience with other Linux distros. 

I used [these instructions]("https://help.ubuntu.com/community/Lubuntu/Documentation/UpgradeToLubuntu") to upgrade from Ubuntu 10.04 to Lubuntu 12.04; I used [these instructions]("http://psychocats.net/ubuntu/purelxde") plus the modifications in the former instructions to supposedly wipe Ubuntu and GNOME from my computer. That said, I have no idea if it actually worked. The output I got was this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package aisleriot is not installed, so not removed
Package apg is not installed, so not removed
E: Couldn't find package appmenu-gtk

Does this mean I have a clean install of Lubuntu, or how would I check if I'm running it on top of Ubuntu still? 

Another issue: in trying to get rid of Chromium, I was prompted that I must remove Lubuntu Desktop Environment (trying to remove Bluetooth also prompted this) and Java plugin; I'm not sure what to make of this. Also, I only found Ubuntu Software Center and Synaptic for a software programs. Should this be changed to a Lubuntu version of these?

One final question: now that I am running Lubuntu, are there programs that I should remove from my Ubuntu install because they will not work as well as the ones provided with Lubuntu?

Might be worth mentioning, the computer is a dual-boot with a small Windows XP partition.

Thanks!

---

### Post by CLCressman on 2012-04-26
In answer to your first question. It is my understanding that the basic difference is the default applications and  look and feel. So if it is doing what you want it to, I don't think you need to worry about it. They apparently coexist fairly peaceably. But if you are a purist, I would guess you don't have a clean install. If you noticed the removal instructions are version specific, and I did not see 12.04. Also, you didn't do a a clean install.

If you look in Synaptic at your Chrome install it will tell you which packages are dependencies, and which are only recommends. There is an option to not treat recommends as dependencies, this sometimes changes what is affected when you uninstall.

For the last 2 questions, I don't know if there is a package manager that lxde prefers over Synaptic. I think that for the most part if you are happy with the programs you have you don't need to worry that one is interfering with another. Unless of course you have something that is not acting right.

---

### Post by Guilden_NL on 2012-04-27
Lubunti 12.04 has a software center, and it is labeled Ubuntu Software Center.  So you're fine.

No idea about the Chromium issue, I left it in all of my systems.

On which apps to use.....it is all up to you.
I run Lubuntu on all of my systems from a 2004 Toshiba Satellite with 1GB all the way to a 24 core 96GB tower.  On the Toshiba, I run all of the lightest apps possible.  No LibreOffice, just LeafPad, no Thunderbird just a very light email client (sorry, can't remember which one.) Midori for the browser.
On "the Beast", I run whatever I want.  I like the LXDE desktop hence why I have it on all of my systems, even the hot machines.

---

### Post by SteveDee on 2012-04-27
> **CommuneOfLoon said:**
> ...Another issue: in trying to get rid of Chromium, I was prompted that I must remove Lubuntu Desktop Environment ...

One of the nice features on Synaptic is "History" which records everything you add/remove when done through Synaptic. So go ahead and use Synaptic to remove chromium-browser and any other "chromium- " packages that are ticked. You can always back-track if you have an application problem.

The "Lubuntu Desktop" thing is a meta package which won't make any difference, so don't worry about agreeing to delete it.

It doesn't look like Psychocats script has completed on your machine, because it would normally show lots of activity then ask if you want to proceed and add/remove stuff. This script is designed to remove and replace specific packages by version number. Since you have a hybrid (and he hasn't produced a 12.04 script yet) you won't have a pure system.

But what you could do is edit the script you have tried by removing from it the packages that it can't find...then run it again. (It might help you to look at this: [http://ubuntuforums.org/showthread.php?t=1966641](http://ubuntuforums.org/showthread.php?t=1966641) which includes removing Chromium from 12.04)

---

### Post by CommuneOfLoon on 2012-04-27
Thanks, all! I will play around a bit more on the system and post back here if I have any issues.

---

### Post by CommuneOfLoon on 2012-04-30
I was initially going through that code from Psychocat, application by application. It was taking forever, and I think I accidentally deleted something I wasn't supposed; I rebooted, and was stuck on a blank screen with a single blinking underscore. Okay, no biggie, I can just do a fresh install of Lubuntu from a USB startup disk.

After the install from the USB, I rebooted but was taken to a screen that says:

error: unknown filesystem
grub rescue>

If I boot from the USB, I can boot properly, am given the option between Lubuntu and my Windows XP partition, can log into Lubuntu, all good; I can do the same for my Windows partition when booting from the USB. But without the USB, I get the grub error. I Googled it, and found [this thread and followed the code in post 6]("http://ubuntuforums.org/showthread.php?t=1930610") (determined the "/" partition is sda6, and subbed that in as appropriate). It didn't work.

If anybody has suggestions for how to fix the grub, I would greatly appreciate it.

---

### Post by CommuneOfLoon on 2012-05-01
I think I found the issue [here]("https://help.ubuntu.com/community/Grub2#External_Drive_Installs_and_MBR_Selection"). I can't run the LiveCd though, since booting from the USB takes me to the Lubuntu partition. Any ideas?

---

### Post by CommuneOfLoon on 2012-05-01
Okay, reformatting the USB startup disk on my desktop (not the comp in question) allowed me to boot from my USB and reinstall Lubuntu. Using the 'advanced setting' for the reformatting and partitions did the trick. I did a swap of 1gb, and used the rest for my "/" partition; everything else I left as is.

---

### Post by marinara on 2012-05-01
what do you think caused your problems?

---

### Post by CommuneOfLoon on 2012-05-03
> **marinara said:**
> what do you think caused your problems?

I assume the issue outlined in the hyperlink in post #7; the description fits the situation I had.

---


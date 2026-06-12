---
title: "Starting computer completely skips GRUB and starts Windows 10"
date: 2020-10-06
forum: Installation &amp; Upgrades
---

### Post by starrt on 2020-10-06
I tried finding any other thread similar to my issue and could not find anything here.

I installed Xubuntu 20.04 as a dual boot with Windows 10.

When I turn on my computer no GRUB menu appears, the computer automatically starts Windows 10.

I then reboot from Windows 10 and the GRUB menu appears with Xubuntu as the first option and then proceeds to load Xubuntu.

I want to start the computer in Xubuntu.

Has anyone heard of this issue? Has anyone been in the same situation? If so, is there a fix for it?

---

### Post by ubfan1 on 2020-10-06
Maybe you didn't turn off the fast startup power option in Windows, which basically puts Windows into hibernation instead of shutting down, so a full reboot is not done, until you select reboot from Windows.

---

### Post by starrt on 2020-10-06
ubfan1,

It has nothing to do with what you wrote about. I close down, power off, my computer from Xubuntu. My issue happens when turning on the computer after having been turned off.

---

### Post by oldfred on 2020-10-06
Not sure if this will show anything or not?
It may also be some setting in UEFI,.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by starrt on 2020-10-06
oldfred,

Thank you for the links. I found one or two that seem to be applicable for Acer computers and I will try it out later today.

I will let you know what happens.

---

### Post by oldfred on 2020-10-06
If an Acer, then perhaps the "trust" issue.
Post that multiple times, where many users with Acer need trust setting.

[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947)

---

### Post by starrt on 2020-10-07
Weel, I am marking this as "resolved" even though it isn't. I went into the BIOS of my Acer desktop and tried all sorts of thing, but since the sections and selections are different from those that others have, it was hit and miss, mainly miss.

For now I will just have to reboot from Windows and get in Xubuntu that way.

Thanks for your help anyways.

---

### Post by starrt on 2020-11-30
HI all,

Even though this is marked was "resolved" about 2 months ago, I have some very important information now regarding this issue.

I had to reinstall Xubuntu, but before doing so, I created a separate and distinct partition on my hard drive with the "ext4" format. I also made sure that the Linux partition was also "ext4".

When installing Xubuntu, I made sure to select the Linux "ext4" drive for the Xubuntu installation, and, more importantly, I made sure to select the distinct and separate "ext4" drive for the Master Boot Record, and GRUB, to be installed on.

Now, when I turn on my computer GRUB shows up and the computer boots into Xubuntu.

So now I can consider this issue really resolved.

Thanks

---


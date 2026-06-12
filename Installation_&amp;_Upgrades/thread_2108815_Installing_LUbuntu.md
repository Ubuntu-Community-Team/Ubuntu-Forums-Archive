---
title: "Installing LUbuntu"
date: 2013-01-25
forum: Installation &amp; Upgrades
---

### Post by MarC2240 on 2013-01-25
I'm trying to intall Lubuntu 12.10 on a Dell Latitude d610. The problem I have is that when I try to install it, it just freezes on the luubuntu screen with the five dots underneath the logo. I don't know what may be causing it.

I copied the iso for Lubuntu to a pendrive using UNetbootin. I verified the Md5Sum of the iso, there's no problem with it. The specifications of my PC shouldn't be a problem either => Intel Pentium M processor, 1.73GHz, 1.2GB RAM, 40GB Harddrive. Here they are on more detail: [http://support.dell.com/support/edocs/systems/latd610/en/ug_en/specs.htm](http://support.dell.com/support/edocs/systems/latd610/en/ug_en/specs.htm)

Any help would be greatly appreciated. Thanks in advance.

---

### Post by TheFu on 2013-01-25
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it) might help. There is an** Ubuntu blank screen troubleshooter** that might also help. Google will find it.

Just to clarify, you can boot using the same ISO file from a flash drive and run off the flash drive without any issues?

---

### Post by MarC2240 on 2013-01-25
> **TheFu said:**
> [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it) might help. There is an** Ubuntu blank screen troubleshooter** that might also help. Google will find it.

Just to clarify, you can boot using the same ISO file from a flash drive and run off the flash drive without any issues?

Not it doesn't freeze, just boots to the black screen.
I don't understand what you're asking me. Do you mean if I can unplug the flash drive after booting?

---

### Post by TheFu on 2013-01-25
> **MarC2240 said:**
> Not it doesn't freeze, just boots to the black screen.
I don't understand what you're asking me. Do you mean if I can unplug the flash drive after booting?

I was unable to tell from the wording of your first post, whether:

a) you installed Ubuntu to the HDD and it boots to the 3 dots

or if

b) you can also run Ubuntu Live off the unetbootin flash drive getting passed the boot and into a normal desktop.

If neither methods work, then it is likely to be 1 issue.
If "b" works, then you've removed the HDD and HDD controller, so that is probably the issue.

Did you look at those links and google those terms for help yet?

---

### Post by MarC2240 on 2013-01-25
> **TheFu said:**
> I was unable to tell from the wording of your first post, whether:

a) you installed Ubuntu to the HDD and it boots to the 3 dots

or if

b) you can also run Ubuntu Live off the unetbootin flash drive getting passed the boot and into a normal desktop.

If neither methods work, then it is likely to be 1 issue.
If "b" works, then you've removed the HDD and HDD controller, so that is probably the issue.

Did you look at those links and google those terms for help yet?

I installed the Lubuntu iso in the flashdrive. I was attempting to install it, it froze on me. Now it just blankscreens me. I haven't tried to install it by any other means (burning a CD or wubi)
From the links, it may have something to do with the installer messing with the graphic card, but I'm not sure yet.

---

### Post by TheFu on 2013-01-25
> **MarC2240 said:**
> I installed the Lubuntu iso in the flashdrive. I was attempting to install it, it froze on me. Now it just blankscreens me. I haven't tried to install it by any other means (burning a CD or wubi)
From the links, it may have something to do with the installer messing with the graphic card, but I'm not sure yet.

Well, that can be either a unetbootin issue - which is common - or your BIOS doesn't support booting from that specific flash drive - or some issue with Ubuntu.

I switched to using Yumi instead of Unetbootin a few years ago. IME, it was easier and worked on almost every flash drive I tried.  Yumi is at the same place as unetbootin.

If that fails, burn a DVD and boot from that.

It really would be best to follow the blank screen troubleshooter. Smart people created that.

---


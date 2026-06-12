---
title: "Upgrading 7.04 to 11.04"
date: 2011-07-23
forum: Installation &amp; Upgrades
---

### Post by LTim on 2011-07-23
Hey,

I have recently moved away from home for the summer, and I have not been able to bring my PC with me, so I have been forced to use my 4 year old Laptop. With just 1GB of RAM, Windows Vista runs like crap, but fortunately I have Ubuntu installed on a partition of the Hard Disk. This runs much more smoothly.

Unfortunately, however, it is a very old version, Feisty Fawn. Support for which,I believe, ran out a long long time ago... making it difficult to even install new software.

I want to upgrade to a newer version of Ubuntu, but any search for upgrades using the update manager returns null. It did once tell me - rightly so - that there was a new version available for download, but any attempts to retrieve it were unsuccessful.

So, is there anyway for me to upgrade? If I download the 11.04 Live CD can I upgrade from that?

---

### Post by Blasphemist on 2011-07-23
Yes, you can do an upgrade using the 11.04 live cd or usb. Do you have anything you want to salvage from the existing 7.04 install? You could loose settings and files doing the upgrade but it doesn't sound like you have used the existing install enough for it to matter. Is that right?

On the allocate disk space screen of the installation, you will be prompted with options as follows. 
1. Erase feisty and reinstall. (I recommend you choose this if you don't need to salvage anything)
2. Upgrade feisty. (Choose this if you need to try and keep files such as pictures, music, documents)
3. Erase disk and reinstall. (This will wipe all existing data and partitions)
4. Something else. (This is the manual option where you do the partitioning yourself and requires a higher level of experience than the other choices)

---

### Post by 2F4U on 2011-07-23
As far as I know, you can only get from one version to the next. Since you are on a very outdated version, going to the next version is not possible. There is a pretty good description on upgrades here

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by LTim on 2011-07-23
> **Blasphemist said:**
> Yes, you can do an upgrade using the 11.04 live cd or usb. Do you have anything you want to salvage from the existing 7.04 install? You could loose settings and files doing the upgrade but it doesn't sound like you have used the existing install enough for it to matter. Is that right?

On the allocate disk space screen of the installation, you will be prompted with options as follows. 
1. Erase feisty and reinstall. (I recommend you choose this if you don't need to salvage anything)
2. Upgrade feisty. (Choose this if you need to try and keep files such as pictures, music, documents)
3. Erase disk and reinstall. (This will wipe all existing data and partitions)
4. Something else. (This is the manual option where you do the partitioning yourself and requires a higher level of experience than the other choices)

You're right, I never used it that much as I got a new PC soon after and began using that instead. I tended to mount my Windows partition for storing files, so my Ubuntu Partition is practically empty.

If you say I can just erase and reinstall, than I shall do that. Will I need to do anything about GRUB... or will the 11.04 install provide a new version itself?

---

### Post by Blasphemist on 2011-07-23
The 11.04 install will upgrade you to Grub2 (version 1.99 but it's called Grub2 compared to your Grub legacy). Just have it write to sda if you have one hard drive.

---

### Post by LTim on 2011-07-23
> **Blasphemist said:**
> The 11.04 install will upgrade you to Grub2 (version 1.99 but it's called Grub2 compared to your Grub legacy). Just have it write to sda if you have one hard drive.

Right. Would it still work if I wanted to install Kubuntu or Lubuntu 11.04 instead?

---

### Post by Blasphemist on 2011-07-23
> **LTim said:**
> Right. Would it still work if I wanted to install Kubuntu or Lubuntu 11.04 instead?

Yes, it would. I wouldn't try to upgrade though, choose the erase feisty and re-install.

---

### Post by LTim on 2011-07-23
> **Blasphemist said:**
> Yes, it would. I wouldn't try to upgrade though, choose the erase feisty and re-install.

Okey Dokey. I think I'll go for Lubuntu. I want it snappy, and I only want to do some web browsing and maybe a little programming.

Thanks for the help!

---


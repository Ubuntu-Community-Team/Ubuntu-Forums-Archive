---
title: "No hard drives detected - 12.04 Live CD"
date: 2012-06-28
forum: Installation &amp; Upgrades
---

### Post by iceman55 on 2012-06-28
Hi All,

I am trying to install Ubuntu 12.04 on my desktop but so far have not been successful. At first I was not able to even boot, I just got a blank screen (I have an nvidia GTX 550 Ti). I was able to get around that by using the setnomode option but now when I go to install no HDDs appear. I have a 1TB disk and a 40GB SSD that is used for caching (Intel Rapid Storage Technology). My primary OS is Windows 7 so switching from AHCI to Compatibility isn't really an option for me. I use Linux almost exclusive at work for development now and would like to have a Linux partition on my desktop but I spent a lot of timing customizing and configuring my Windows 7 setup and I don't want to do anything that might corrupt or damage it. 

If anyone else has encountered this issue and found a workaround can you please share? It's not super important to have Linux on my desktop but it would be nice.

---

### Post by darkod on 2012-06-29
Have you ever used any of these disks in fakeraid before? That is usually when the installer ignores them. You would need to remove the meta data.

Boot into live mode and first check if the disks are detected at all with:
```
sudo fdisk -l
```

That will also show which disk is /dev/sda and which /dev/sdb.

After that, to remove meta data, you need to do:
```
sudo dmraid -E -r /dev/sdX
```

NOTE: You don't run that if you are actually running raid, but doesn't look like it.

Another reason might be if depending on the sata controller model, the disk(s) are not recognized. Sometimes changing to different sata port helps.

As for AHCI, ubuntu has no problem with it. In fact, the sata mode needs to be in AHCI. Just make sure it's not in RAID or similar.

---

### Post by iceman55 on 2012-06-29
Thank you for the reply darkod! Running dmraid -E -r /dev/sda seems to have done the trick. Unfortunately it disabled my SSD cache but I can live with that. I now have Ubuntu 12.04 installed and booting fine. Thanks!

---


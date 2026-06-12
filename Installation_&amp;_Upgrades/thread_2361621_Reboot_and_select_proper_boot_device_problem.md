---
title: "Reboot and select proper boot device problem"
date: 2017-05-18
forum: Installation &amp; Upgrades
---

### Post by drzn93 on 2017-05-18
Hi!

I installed Ubuntu on a Windows 10 UEFI PC. After following the steps from a installation tutorial, GRUB didn't load, so I searched the net and I found this solution to repair the GRUB:

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo sh -c "sed -i 's/trusty/saucy/g' /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list"
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

I did it, and after restarting my computer again, no GRUB. No Operating System, it seems.

It just prompts this message ''**reboot and select proper boot device''.**

I imagine I somehow broke the MBR Windows loader, because Windows 10 and all my data is still there (and I need my data!).

I don't have an installation or repair disk of my Windows 10, and I only have access to my Ubuntu Live CD I mounted on a 16GB USB Memory, so my situation is not exactly the best.

Is there something I can do to repair the MBR load from Ubuntu? I guess I can get a Windows 10 ISO and mount it on another USB drive, but I don't have another PC within reach at the moment.

Thanks in advance.

---

### Post by deadflowr on 2017-05-18
Do it again, but this time
don't do this line
```
sudo sh -c "sed -i 's/trusty/saucy/g' /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list"
```

there is no archive for the boot repair for saucy.
Not sure how it did anything at all.

Also write down the paste link and post it here.

---

### Post by drzn93 on 2017-05-18
Yes, that line didn't do anything at all, forgot to mention that. I continued with the next line after trying that line a few times and realized it didn't work.

I found the tutorial to repair the GRUB in here [http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

---

### Post by deadflowr on 2017-05-18
The first line will automatically create the entry for whatever version of Ubuntu you are using.
Which begs the question, do you know which version of Ubuntu you are using?

---

### Post by drzn93 on 2017-05-18
Hi.

Yes, I'm using Ubuntu 16.04 (last version).

I have the UEFI secure boot and the fast boot settings disabled.

Tried to do all the steps again and did not work.

Message error after starting the computer is:

> 
Failed to open EFI\BOOT\grubx64.efi - Not found
Failed to load image EFI\BOOT\grubx64.efi - Not found
start_image() returned Not Found

This message appear for like two seconds and then the "reboot and select proper device" screen prompts.

I've been trying to repair this the last six hours (since it happened) and I'm going nuts. Not gonna sleep until it's fixed...

Thanks.

---


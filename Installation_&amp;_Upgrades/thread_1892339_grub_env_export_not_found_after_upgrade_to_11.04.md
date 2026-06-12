---
title: "grub_env_export not found after upgrade to 11.04"
date: 2011-12-07
forum: Installation &amp; Upgrades
---

### Post by costanzaG on 2011-12-07
I had been running Ubuntu Netbook Remix on my netbook for about a year now, and finally decided to upgrade to natty from maverick after it reminded me for the 100000th time. It came with windows 7 installed, and I have been booting with GRUB to choose ubuntu. 

After the upgrade, the only thing that appears is the GRUB rescue prompt, with the error
symbol not found: 'grub_env_export' appearing.

I have gone through the forums and attempted some of the suggestions. Unfortunately, the only commands that work in the rescue prompt are set and ls. I was able to see through ls that in (hd0,5), I can find the vmlinuz, initrd.img, and /boot/grub/grub.cfg etc. as suggested in 
[https://help.ubuntu.com/community/Grub2#GRUB_2_Troubleshooting_Preparation](https://help.ubuntu.com/community/Grub2#GRUB_2_Troubleshooting_Preparation)

I had my USB from my original install and attempted to boot from it, but even in this situation the grub rescue prompt comes up as above. Created a 11.04 USB to boot from and it did the same thing. 

So essentially right now, I cannot seem to boot anything.

I can't seem to find a solution in another thread here or elsewhere. Any help would certainly be appreciated.

---


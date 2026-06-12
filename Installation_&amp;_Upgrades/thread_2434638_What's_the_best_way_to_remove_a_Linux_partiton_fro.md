---
title: "What's the best way to remove a Linux partiton from a triple boot?"
date: 2020-01-08
forum: Installation &amp; Upgrades
---

### Post by wiscxrise on 2020-01-08
Hello, 

I have Windows 7, Mint 17.3, and Xubuntu 18.04 installed. The Xubuntu installation handled the boot loader. I'd like to completely remove Mint 17.3 from my drive and just have Xubuntu and Windows 7. 

What's the best way about doing this?

---

### Post by Tadaen_Sylvermane on 2020-01-08
If you are positive that Xubuntu handles grub then it's as simple as logging into Xubuntu and formatting that Mint partition, then running ```
sudo update-grub
```

If you are not 100% sure of that then you should run the grub install from Xubuntu before doing the above step. ```
sudo grub-install /dev/sda
``` assuming sda is the proper drive you are targetting. I'd recommend doing this regardless because there is no harm in being 100% certain. If you are wrong about where the bootloader is coming from it can be a pain to sort out.

I'm unsure about removing the whole partition though. I use LVM so I can create and remove "partitions" with ease and total lack of fear. But I also don't dual boot with Windows so there is that. Partitioning needs to be done with the whole disk unmounted so you would need a live system or something to even attempt it. Then there is the risk of a minor mistake wiping out the whole thing. It happens. Not to be taken lightly.

Of course it should be said that you shouldn't do any of this without making proper backups of irreplaceable data or customized config files.

---


---
title: "Can't boot specific ubuntu kernel"
date: 2016-09-28
forum: Installation &amp; Upgrades
---

### Post by mohammadbagheri2010 on 2016-09-28
Hi.
When i select Ubuntu which is Linux 4.4.0-38-generic  from grub it goes to a blank screen but I select Linux 4.4.0-28-generic (Older one!) it boots normally.Even Linux 4.4.0-31 goes to a blank screen. 
Now I lead you through all steps I've done to my computer that caused this !
I'm dual booting Ubuntu 16.04 with Windows 10 and I wanted to decrease one of my Windows partition's size and give it to Ubuntu partition.
I resized Windows partition with gparted without any trouble. It booted normally after this resizing.
I then used LiveUSB to resize my Ubuntu partition.In order to do so, I had to erase my swap partition.So gparted now  had 3 operations to do.
1- Erase swap partition(8GB).
2- Resize Ubuntu partition.
3- Create swap partition again.
I successfully did first 2 operations but failed to operate third one.
Ignoring failed operation i ran these commands :
```

sudo mount /dev/sda6 /mnt   #/dev/sda6 is my ubuntu partition.
sudo grub-install --root-directory=/mnt /dev/sda 

```
Then I rebooted the system and figured out that when I select ....(said above)
I booted from older kernel and ran 
```
sudo update-grub
```
it only granted me my Windows 10 which wasn't shown in grub list before this.
** All I want is to boot latest Ubuntu kernel.

Thanks for reading and responding.

[EDIT]
I booted the old kernel and made a swap partition by fdisk and changed /etc/fstab file due to changes to my swap and root partition and it fixed everything!

---


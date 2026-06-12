---
title: "Installed Kubuntu; Windows Won't Start"
date: 2013-01-13
forum: Installation &amp; Upgrades
---

### Post by Pocc on 2013-01-13
Hello. First post. Been using ubuntu for years, but am still a newb. I installed Kubuntu 12.10 to my laptop about a day ago, and now, when I select the Windows 7 Partition in grub, I get 

Error: Invalid EFI File Path

I (now) have 2 different versions of ubuntu on different hard drives and both still boot. The files in the Windows partition remain intact.

I used rEFInd, and it did not see the Windows partition.

I checked Boot Repair, and it said to come to a forum. 
This is its output: paste.ubuntu.com/1526461/

Any and all help would be appreciated. Thanks in advance.

---

### Post by 101kitty on 2013-01-13
If i'm not mistaken there is away to install another bootloader to pick from windows and ubuntu, it sounds like that the bootloader is not working right, maybe you can to replace the current bootlaoder or maybe refresh it... this is the only thing it be, i think.

---

### Post by james2b on 2013-01-13
Since you multi-boot with Windows 7 and not 8, you may be able to go into your BIOS setup to change it from UEFI to the normal old style BIOS if possible.

---

### Post by Pocc on 2013-01-14
> **101kitty said:**
> If i'm not mistaken there is away to install another bootloader to pick from windows and ubuntu, it sounds like that the bootloader is not working right, maybe you can to replace the current bootlaoder or maybe refresh it... this is the only thing it be, i think.

Which program would you recommend I use to replace or refresh it?

---

### Post by 101kitty on 2013-01-15
I don't know anything about a boot loaders, you may want to ask a vet about this one, I'm sure someone will comment on this post when they read my msg.

---

### Post by Pocc on 2013-01-24
I ended up solving it by going into the BIOS & resetting it to the default configuration. This changed the GRUB that booted the computer from the Kubuntu on my SSD to the Ubuntu on my HDD.

---


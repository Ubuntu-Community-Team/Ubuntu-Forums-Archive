---
title: "Failed to installed Grub during install !"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by CONCORAN on 2008-03-04
Hello,

I must admit that I should have been a little smarter going into Ubuntu install - since I have faced this problem before. Well, here's the deal.
I have XP, Vista, Fedora 8 on first 3 partitions. First logical 2 GB is swap, and next 6 GB is meant for Ubuntu.
The partition for Ubuntu was created (unformatted) in Windows XP. 
So, I begin to install Ubuntu, but at the end Grub failes to install. This has happened to me before since the Ubuntu partition ID is not 83 (linux) [windows sets it to FAT32]. Hence Grub wouldn't install somehow (I don't know why).

But now that Ubuntu seems to have installed pretty much everything, except Grub, is there a way to install Grub in its own partition? Is it possible to log into Fedora, and be able to install Grub for Ubuntu somehow?

---

### Post by em3raldxiii on 2008-03-04
Since no one else has replied, I'll see if I can offer some little assistance ...

Normally, with Ubuntu, one can edit the grub list to include all your OS entries.  I am thinking you should have that ability under Fedora as well.  I have no experience with editing GRUB via Fedora, but in Ubuntu you would use your favorite text editor to edit your /boot/grub/menu.list and add the appropriate entries (depending on your partitions, etc)

Hope that gets you on the right track :D

---

### Post by zvacet on 2008-03-04
[This](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) can maybe help you.

---

### Post by dstew on 2008-03-04
> This has happened to me before since the Ubuntu partition ID is not 83 (linux) [windows sets it to FAT32]Didn't you format the Ubuntu partition to be ext3 before you got to the grub install step? Anyway, with some hardware there is a funny bug, that grub won't install and gives a "Fatal Error" message. This happens if the format is ext3. The workaround is to format the Ubuntu partition as ext2 during the installation. Then grub goes in fine. Then, the ext2 partition can be converted to ext3 using tune2fs. No data is lost during the conversion, it just adds some jounaling files.

---

### Post by vikasmk on 2008-03-04
Same thing happened to me and i was about to give up , then i heard about the alternate installer and ubuntu installed with no problems , So try the alternate installer:)

---

### Post by designzinthesun on 2008-03-04
This happened to me with the alternate install. I used a different cd drive and it worked. The live cd install worked fine for me with both drives. I had the same problem with Fluxbuntu and changed drives and it installed. I tried to install grub from Mint root on another partition but it wouldn't work for me. I had a bad copy of the live cd when I first got hooked on Linux and I went to the alternate install cd and it worked. Then my cd drive must have worn out a bit. The cd that worked before stopped loading grub. I thought I would give another download and burn of the live cd another try and it worked. Then I thought I would change drives and try the alternated cd again and that worked too.

---

### Post by CONCORAN on 2008-03-14
I guess I realized what the problem was. When installing Grub, the default location is always (hd0). I used to select number 3 since /dev/sda3 had Ubuntu, but it turns out I need to select 2 ( zero based index). Hence all my previous installations failed. Anyways, it works now. Thanks everybody.

---


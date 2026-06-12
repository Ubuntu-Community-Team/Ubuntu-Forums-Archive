---
title: "Gain file permissions via USB live boot?"
date: 2014-05-24
forum: Installation &amp; Upgrades
---

### Post by Shreddie on 2014-05-24
Yesterday I decided to upgrade from 12.04 to 14.04... I started by upgrading to 12.10 and was going to continue further once that was installed, but the installation failed and will not boot, despite all my efforts in recovery mode, it seems that the installation has failed irrecoverably. There were numberous warning messages in the terminal while it was performing the upgrade so I was half expecting problems.

I'm planning to simply wipe the 12.10 partition and install 14.04 in its place, but before I do I'd like to recover some of my documents... While I have been able to copy most of them over to my Windows partition, when I try to open some folders it reads "This location could not be displayed, you do not have the permissions necessary to view the contents of ...". |Is there any way to do this via a live USB stick?

---

### Post by prmurthy on 2014-05-24
If your files are on an ext4 partition, then Windows wont be able to read them.
You should be able to boot into a linux environment (by using your 14.04 USB disk, for example), mount your old folders and your windows (ntfs/FAT) partitions, and copy them across.

Once you boot into 14.04:```

sudo mkdir /tempsrc
sudo mkdir /tempdest
sudo mount /dev/<partition where your document are> /tempsrc
sudo mount /dev/<ntfs partition> /tempdest
sudo cp /tempsrc/<where your files are> /tempdest/<where you want them>
sudo umount /tempsrc
sudo umount /tempdest

```

---

### Post by Shreddie on 2014-05-24
Crikey! That'll take a while as I have about 50 to 60 folders that I can't get access to (yet I have over 100 that I can, which is odd, I'd have thought the permissions would be the same for all)... Is there any way to gain permissions in files/nautilus?

And for what it's worth, I do have separate backups on my NAS of some of it as I back up about once a fortnight, but I've done a huge amount of work this last week (I backed up last weekend) and forgot to back things up before I started with the upgrade... It's my own fault really.

---


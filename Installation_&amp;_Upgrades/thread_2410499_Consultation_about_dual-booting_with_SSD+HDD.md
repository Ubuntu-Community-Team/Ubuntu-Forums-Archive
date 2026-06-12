---
title: "Consultation about dual-booting with SSD+HDD"
date: 2019-01-16
forum: Installation &amp; Upgrades
---

### Post by kriogenia on 2019-01-16
Hi, recently my uncle gifted me a 240gb SSD and I already fresh-installed Windows on it and almost made the full transition, but I also want to have Ubuntu installed on my system. My question is how should I set-up the installation to make better use of those drives. Right now I still have my HDD in the same state, it still has Windows installed (taking the D: partition) and all the files (in E:, which I already saved to the external HDD). How should I format it? Should I make a partition for each OS? Or try to make somehow a partition to install Windows things, other to Ubuntu things and other to store the shared media like images or docs?

I never had more than one drive and I'm kind lost in this regards. I kinda know how I should adapt in Windows changing where the libraries point and changing the default installation paths or something like that but I don't know nothing about this on Ubuntu to be fair. I've read something about installing the /home on the HDD or installing it on the SSD and linking it to the HDD.

Anyway, do you any know guide to make this or could you share how you think I should do it? Thank you so much in advance.

---

### Post by TheFu on 2019-01-16
OS and Apps for all OSes on the SSD.
Data on the HDD.  You can keep the /home on the SSD and use symbolic links from there to directories on the Data HDD. People here have written about symlinking ~/Documents/, Music, Video, etc...  from their HOME to a data disk.  To you and programs, it seems like everything is in the right place, but really stored on the huge spinning disk.  

Whatever you do, don't completely fill the SSD unless you want the storage to fail sooner.  Leave 20-30% unused.

---

### Post by oldfred on 2019-01-16
Post this from terminal in live installer, to see you current partitions:
sudo parted -l

Make sure Windows fast start up is off, mount all partitions (click in Nautilus) and run this:
This will show used space:
df -h

---


---
title: "How can I move my MBR to another HDD"
date: 2006-03-18
forum: Installation &amp; Upgrades
---

### Post by th3james on 2006-03-18
Hi

When i install ubuntu, i install / onto the slave HDD into my computer, which also housed my windows partition. The MBR however, is on the master HDD. The master HDD has Suse 9.3 install on it.
I now want to install slackware, so i can run counter strike thru wine super fast, and so i can play around with slack. I want to wipe the drive with suse on, and replace it with slack. Slack will over write my MBR with its own. As im not that confident with slack, im worried i will screw up my MBR, and not be able to boot Ubuntu.
Therefore, i would like to move my MBR to my slave HDD (/dev/hdb), and install slackwares own bootloader onto the other harddrive, with the intention of switching between the two OSs by changing the boot order of my HDDs. Unfortunatly, im don't really know how to go about this, could someone give me a hand, or point me in the direction of a tutorial, because i really don't want to mess up my MBR

Thanks in advance

James

---

### Post by magisterludi on 2006-03-18
the mbr is the first 512 oktets of the partition or drive

to save it execute:
```
dd if=/dev/hda of=/tmp/mbr.backup bs=512 count=1
```

to restore:
```
dd if=/tmp/mbr.backup of=/dev/hda bs=512 count=1
```

---

### Post by th3james on 2006-03-19
Thanks, i did that to back it up before i did the install, but i ended up not installing a boot loader in slackware, and instead just modifying the existing  one to include slack.

---


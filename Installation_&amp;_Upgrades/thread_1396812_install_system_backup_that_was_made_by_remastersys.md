---
title: "install system backup that was made by remastersys in ext4"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by doron387 on 2010-02-02
hi guys, (please excuse me for my english level...)
i have a question about ext4,remastersys backup :
i have upgraded from 9.04 to 9.10 via the upgrade button in synaptics, so it means that the files system was not touched, which means that my system is still ext3 as it was when i installed the 9.04.
i can make a backup of my system as it is configured right now (that's how i like it) using remastersys.
my question is : can i install my system backup into my machine after formating it into ext4 or when i create a backup using remastersys it must stay in the files system as it was when it was backed up ?
the issue is that right now the 9.10 responds from some reason a little bit slower than my 9.04 responded (to everything e.g. open/close windows etc...) and i read in the forum that ext4 makes 9.10 run faster.

i hope that i was understood and that somebody can help me.

thnx
doron387

---

### Post by Winterbottom on 2010-05-02
[FONT="Arial"]I once did the opposite i.e. downgraded from ext4 to ext3, because I wanted to back up my drive with Acronis TrueImage, which does not as yet support ext4. The downgrade worked well and I suppose you can use Remastersys to upgrade from ext3 to ext4. 
Load your LiveCD made with Remastersys and start the restoration. You must choose to format your ext3 partition to ext4 on the way when you partition your drive. [/FONT]

---


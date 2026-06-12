---
title: "Nedd to clone my system using DD - need help"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by youbuntu on 2009-12-03
Hiya :).

I have Ubuntu 9.10 installed on an old 20Gb hdd, and I have another spare 20Gb hdd (both IDE) and I want to clone the first drive to the second, but the drives are VERY slightly (.1-.2Gb) different in size.

Please tell me - how do I do this?.

What I did so far is try this, where SDA is my old drive and SDB is my new one:

Scenario one:
----------------

I simply did: dd if=/dev/sda of=/dev/sdb

Had some grub error, dropped me to grub prompt


Scenario two:
----------------

I created as near an approximation as possible, of my current drive; single ext4 partition, then swap partition in extended. I then did: dd if=/dev/sda1 of=/dev/sdb1 bs=1k

Nothing at all... just a flashing cursor at top left of screen



I would like some help if possible - please restrict the help to within the scope of the "dd" command, because this is what I need to learn if possible, thanks.


PS: my drive is like this:

[======== 18.3Gb ext4 ========][==== swap ====]
^______________ WHOLE DRIVE_____________________^


thanks guys &/or girls :)

---

### Post by presence1960 on 2009-12-03
[clonezilla]("http://clonezilla.org/")

---

### Post by youbuntu on 2009-12-03
I need "dd" help, as I mentioned.

---

### Post by wojox on 2009-12-03
Use partimage [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage) 
dd will copy all the empty space and its longer.

---

### Post by youbuntu on 2009-12-03
> **wojox said:**
> Use partimage [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage) 
dd will copy all the empty space and its longer.

Thankyou mate :)

---

### Post by presence1960 on 2009-12-03
> **glossywhite said:**
> Thankyou mate :)

I thought you needed dd?

---

### Post by youbuntu on 2009-12-03
> **presence1960 said:**
> I thought you needed dd?

I do - can you help?.

---

### Post by presence1960 on 2009-12-03
> **glossywhite said:**
> I do - can you help?.

I have never used dd. Always use PING (partimage is not ghost) or clonezilla. Was just making an observation that when I suggested clonezilla you replied you wanted help with dd. When someone else suggested partimage you were enthusiastic. Rather inconsistent.

---

### Post by youbuntu on 2009-12-03
> **presence1960 said:**
> I have never used dd. Always use PING (partimage is not ghost) or clonezilla. Was just making an observation that when I suggested clonezilla you replied you wanted help with dd. When someone else suggested partimage you were enthusiastic. Rather inconsistent.

I *would* prefer "dd", which is why I asked for help with it. I don't see the relevance of my consistency - it's a free world and it is my perogative to change my mind. :)

---

### Post by punkybouy on 2009-12-03
There is a better way.  Create a list of installed packages on the current system then copy that list to a base install on the other hard disk and then do a restore by typing cat <your list file> | xargs sudo apt-get install.
I forget the command to create the list.

---

### Post by seeker5528 on 2009-12-03
DD makes an exact copy, if you made a copy and the copy doesn't work, then I think you need to be looking at things that may cause the copy not to be exact.

Bad memory.

Bad drive.

Improper jumper settings on the drives.

The two drives have issues being on the same cable as each other, or cd-rom/dvd if they are on the same cable with one of those.

An IDE related BIOS setting.

Trying to boot the copy on another computer that recognizes the hard drive differently for some reason.

EDIT: In your second scenario where you created partitions, then did partition to partition, it sounds like you also need to do the MBR, in case you want to try that before doing a lot of trouble shooting:

```
dd if=/dev/sda of=/dev/sdb bs=446 count=1
```

to copy the first 446 bytes from sda to sdb.

Later, Seeker

---


---
title: "Ubuntu 10.04 installation went horribly wrong"
date: 2011-06-21
forum: Installation &amp; Upgrades
---

### Post by mISHOOO on 2011-06-21
Hello everyone !


I have a 250 GB hard drive and 6 NTFS partitions: "Local Disk" (C), "Movies" (D), "Music" (E), "Photos" (F), "Applications" (G) and "Documents" (H).

I had Windows 7 installed on C and today I wanted to replace Windows with Ubuntu 10.04. Since I don't keep pretty much important data on C, I transferred what was needed to H. Now, I booted up with my Ubuntu USB stick, went into Ubuntu Live and, after checking and rechecking and rechecking to make sure I was doing the right thing, I formatted drive C (64 GB) as FAT. Everything went fine, the drive was formatted and all of the other drives were unharmed.

I ran the Ubuntu installer and when I got to the point where you are asked where you want to install the OS, I selected the last option (Advanced / Customized - something like that). Two options were displayed: the primary drive (~64 GB FAT) and the logical drive (~180 GB NTFS). I selected the 64 GB FAT drive, rechecking to make sure it was the right disk drive. It asked me whether I wanted to format this 64 GB FAT drive as EXT4. Since I know this is a Linux-specific file system, I selected Yes.

The installation went fine, but when I rebooted my computer I saw that, except for "Music", all of the other NTFS drives were missing. Instead, the "Music" drive's size was now ~180 GB. I could see all my data from the "Music" drive, but none from the other partitions. Strangely, this was the drive I mounted before running the installer -  I don't know if this might be the reason for which it's the only NTFS drive I am able to access or not. 

After some research I made on forums, I found out about that "testdisk" program. I analyzed the disk with it and it didn't find my NTFS drives. I did a "Deeper Search" and after about half an hour or so, it finally found all my partitions. They were there ! I pressed the P key and I could see my directories and files.

Now, the problem is this: when I mark my EXT4 drive as Primary and the NTFS drives as Logical, it says it's a bad structure. What can I do to fix this? I'm afraid I might lose my data. I've done other installations in the past, but none went as wrong as this one. :( If I mark them all as primary, would this work?


Please help !

Mihai

---

### Post by Quackers on 2011-06-21
Welcome to UF.
I wouldn't recommend marking them all as primary. You can only have 4 primary partitions on an mbr partitioned disc.
Can you leave the recovered partitions as they are (ie not change the partition type)?

---

### Post by dFlyer on 2011-06-22
Just for safety, I would backup all my data once I get an functioning OS installed. I believe all recommendations on the web are to backup your data. I'm glad you were able to recovery your data, some people are not so lucky. If I understand you correctly your not going to dual boot, so in the future you might want to use your whole drive as linux. My advice to everyone thats new is to take it slow, have fun, and ask questions when you need help. Welcome to Ubuntu.

---

### Post by mISHOOO on 2011-06-22
@Quakers: Thank you for your reply. I'm not sure I understood your question. I didn't try to change the partition type. testdisk detects my drives and asks me to mark each partition as one of the following: deleted (D), primary (P), logical (L) or bootable (*). This is where I get stuck since I don't know how a "correct structure" should look like. 

@dFlyer: Thank you for your reply. You are right, it is my mistake that I only backed up my data to another drive. I never thought it would go this wrong. :( Yes, I was not going to dual boot, that's why I formatted the drive on which Windows 7 was installed. I haven't recovered my data yet since I don't know how to mark those partitions, how a "correct structure" would look like.

Any help would be greatly appreciated !

---

### Post by Quackers on 2011-06-22
Hmm, from memory I don't think I needed to do that.

I would imagine that as long as only 3 partitions are marked as primary, the others can be Logical (unless one is also an extended partition, which is another type of primary partition).
The small Windows boot partition should be marked bootable (or the main C: drive - depending on how it was set up originally) and should be a primary.

---

### Post by mISHOOO on 2011-06-22
Quakers, this is what I did. I marked the EXT4 partition (which used to be C) as primary and the other NTFS ones as logical. It says it's a bad structure. If I mark the NTFS ones as primary, it says it's ok. :: confused ::

---

### Post by Quackers on 2011-06-22
If you are going back to what you had originally, shouldn't they all be NTFS?
If you want Windows to boot again there needs to be a partition marked as bootable and this should be either the first or second NTFS partition, I would guess. It would depend on how it was set up originally.
I would add the proviso that it needs to be an acceptable structure, though.

---

### Post by mISHOOO on 2011-06-22
Yes, they're NTFS, except for the ex C drive, which he asked me to format as EXT4 at the installation. So now the ex C drive is EXT4 and the rest are NTFS. I marked this EXT4 drive as primary and the others as logical. 

I will post an output of the testdisk program today.

---

### Post by mISHOOO on 2011-06-22
I finally managed to recover everything thanks to the "testdisk" software. I did a "Deeper Search" and it found my partitions. I saw that I could use it to copy my data to another disk drive. I connected an external HDD and transferred my files.

Quackers and dFlyer, thank you for your time and your help. I am relieved now. :)

---

### Post by Quackers on 2011-06-22
I'm glad to hear that :-)
Well searched!
You're welcome.

---


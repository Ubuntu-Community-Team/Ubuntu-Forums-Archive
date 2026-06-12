---
title: "Partition Drive Letter"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by PoisonedV on 2008-02-13
Hey,
I am using SystemRescueCD with Gparted to partition my boot/main hard disk. It says to partition the drive, it will have to assign a drive letter and delete dev/sda/ or something. Will this delete all my files already on it from a windows installation?

---

### Post by Herman on 2008-02-13
That doesn't make any sense to me, are you sure you're really using GParted? not GPart? or something else? There's no such thing as a 'drive letter' in Linux, and yse, probably it will delete your Windows partition!

Please STOP whatever it is you're doing right now and get out of there until you do a little more reading and research first.

Regards, Herman :)

---

### Post by PoisonedV on 2008-02-13
Haha, sorry, I meant label. Is it even unnecessary to use GParted?

---

### Post by Herman on 2008-02-13
Well we normally partition our disks with GParted or any other Lib Parted based partitioner. QTParted is for KDE, Partman is in the 'Alternate' Ubuntu CD.

GParted is asking you to 'set a new disk label', now that sounds more like something I'd expect GParted to say.

Don't do it though! [-X
Not without making a complete backup of everything first, because it will wipe your hard drive and you'll have to install everything all over again, from scatch.

'Setting a new disklabel' means giving you a new empty Master Boot Record!

---

### Post by Herman on 2008-02-13
I'm only guessing, but from my experience GParted is telling you it doesn't agree with or can't stomach whatever some prevous partitioner has written in your partition table, or doesn't recognize it for some reason, so GParted considers this as a raw disk.

If you remember what hard disk partitioner you used before, you could try partitioning with that again, but there's a good chance Ubuntu won't install on those partitions anyway.

You could try using the command 'sudo fdisk -lu' from the Ubuntu Live CD and see if we can see what's wrong with your partition table.
```
sudo fdisk -lu
```
The output from that might be interesting if you can post it here.

---

### Post by Herman on 2008-02-13
>  Is it even unnecessary to use GParted?It's not necessary to pre-partition your hard disks, GParted is included in the Ubuntu 'Desktop' Live CD's installer, and you can partition your disks at the same time as you install. Some people like to partition their hard disks beforehand as a separate operation, and that can be very helpful if it's for a computer that doesn't have very much RAM. So, it's okay to do that if you want to, but not necessary for most normal computers.

Regards, Herman :)

---

### Post by mrsteveman1 on 2008-02-13
If you know for a fact there were partitions on that disk and now they are gone (cant edit them with fdisk/gparted, if windows no longer works etc), you can recover the partition table with gpart (NOT gparted).

It's fairly simple, just run gpart /dev/sda and it should find partitions and show them to you, but don't let it write to the disk unless you know what it says is correct.

---

### Post by Herman on 2008-02-13
I haven't tried out gpart yet but I believe it is very good software when used for doing the work it was intended for. I didn't mean to imply otherwise in any way, just that there's a similarity between the names 'gpart' and gparted' that could mean someone might accidentally choose the wrong one for their intended purpose.
>  you can recover the partition table with gpart (NOT gparted)That's right! GParted wants to make a new partition table, gpart can recover the old one, (if it needs recovering). I agree.

My impression was that PoisonedV's partition table is probably acceptable to some other partitioner such as Windows Partition Manager, or whatever they have in Vista or some such, but it's not acceptable in Linux for some reason. I'm just guessing about that.

What will gpart do, mrsteveman1? Maybe gpart *is* the right thing to use after all, maybe gpart can fix PoisonedV's partition table so it will be compatible with both operating systems.

Regards, Herman

---

### Post by mrsteveman1 on 2008-02-13
I was just pointing out the difference because they are so similar, not because of what you said :D

The partition table, if its not corrupt, should be readable by anything since the format is pretty simple. If fdisk cant read it (with fdisk -l /dev/sda), then its definitely corrupted.

Gpart just scans the disk for partition boundaries and guesses at what the partition table should look like, its usually correct when the partitions haven't been written over.

---

### Post by Herman on 2008-02-13
>  The partition table, if its not corrupt, should be readable by anything since the format is pretty simple.:) The partition table is only 64 bytes in size and it contains up to four sixteen byte partition entries.
Yet there are times when some partition editors seem to think it's fine while other partition editors consider the same partition table to be corrupted.
Apparently it's a matter for opinion and some partition editors are more fussy than others or they do their calculations a little bit differently or something, I'm not sure. I am interested to learn more details about why this kind of thing happens.
I have noticed that sometimes cfdisk will refuse to look at a perfectly good partition table made with GParted. It's relatively common for GParted to reject a partition table for some reason. I presume it's for the protection and safety of the data for a partition editor not to want to touch a partition table that contains something it doesn't like.
Strange why these things happen.  :confused:
> If fdisk cant read it (with fdisk -l /dev/sda), then its definitely corrupted. Yeah, fdisk is great, it will almost always show the partition table and it's often possible to see where there is a partition overlap or something like that. :)
I have read of people resizng a partition by a few blocks with 'Parted or cfdisk and fixing their partition tables that way.
I'm sure there's a lot about partition tables that I don't understand yet.
I usually advise people to try to stick with the same brand of partitioner if they can.

Regards, Herman :)

---

### Post by PoisonedV on 2008-02-14
Ok, so fdisk does recognize the disk... What now?

---

### Post by Herman on 2008-02-14
I didn't think gpart would be in the Ubuntu Live CD but I couldn't remember if it's in the System Rescue CD or not, it's a while since I've used one. I have an .iso for one but I haven't burned it to disk yet, I know it has a lot of good things in it.

Try 'sudo fdisk -lu' and see what that does,
```
sudo fdisk -lu
```
Regards, Herman :)

---

### Post by PoisonedV on 2008-02-14
I tried that, should I try sudo fdisk -lu /dev/sda?

---

### Post by Herman on 2008-02-14
No, if you tried 'sudo fdisk -lu' it should have given you a list of all your hard drives (if you have more than one) and tell you which partitions are in each one including lots of interesting details about what sectors they start and finish on and other things like that.

Well I guess that particular MBR isn't at all compatible with Linux then if fdisk doesn't recognize it either. If your Windows installation is happy with it then it's probably best to leave well enough alone.
If you really want to install Linux (which I really recommend), it will probably be necessary to buy a separate hard disk for it in this case.
The other thing you can do would be to completely back up Windows and all your software and all your files and settings. Double check and triple check that you really have everything all backup up, and then do as GParted wants and set a new disk label.
You'll have to re-install everything again all new. Windows and then Ubuntu.
I have no idea how much work that will be for you. When I was a Windows user I got pretty good at backing up and re-installing Windows XP after a few times. Nevertheless, it's still a very time consuming chore to get everything back the way you like it.

Regards, Herman :)

---

### Post by PoisonedV on 2008-02-14
Oh, no, I already got a list of all my drives with the other fdisk comman you told me to try earlier, they show up that way. I want to know what I can do now that fdisk recognizes it, to make gparted recognize it.

---

### Post by PoisonedV on 2008-02-14
I realize how confusing everything I am saying has been, so let it put it this way:
I have found through some looking that the best way would be to use gpart to get the partition back to normal. Unfortunately I do not understand how to use gpart

---

### Post by Herman on 2008-02-14
I don't know how to use gpart, unless mrsteveman1 can help you. If you want to use gpart, you'll probably need to find more information (gpart users documentation) first.

The program I'm a little bit experienced with for writing new partition tables is [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"), I have a web page about that to try to help people, but it's mainly for rescuing people's systems when they won't work at all and they have to rescue their data. Your system is working at the moment and you have data in it that's okay. There may be something about your partition table that's special that we don't know about. I'd hate to give anyone the wrong advice and see anyone damage their software that they already have.
Probably you should get some expert help or leave well enough alone.

Regards, Herman :)

---

### Post by PoisonedV on 2008-02-14
haha, OK I got the partitions figured out. However, there are 2 partitions marked as swap on my hard drive. They might be from my previous installation of Ubuntu (I stopped after I couldnt get my old network adapter to work) or is it from windows? I am not sure if windows even uses a partition as a swap file, because frankly I am only good with software-level stuff... so I am totally out of my territory here.

---

### Post by Herman on 2008-02-14
Windows doesn't make a swap area, they use something called a 'page file' instead. You can probably delete those if you want.

---


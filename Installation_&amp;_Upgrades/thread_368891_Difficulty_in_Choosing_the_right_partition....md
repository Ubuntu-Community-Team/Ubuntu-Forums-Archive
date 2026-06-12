---
title: "Difficulty in Choosing the right partition..."
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by handyandy16 on 2007-02-23
Hello everyone,

I am trying to install Ubuntu on a dual boot with XP.  I have partitioned my 80GB hard in two parts 15GB for ubuntu and the rest for windows.  I used partition magic and everything went fine.  I now have my two seperate partitions.  Now i go to install ubuntu and the live cd starts up fine, i click on the install icon and follow the instructions.  The issue is that i get to a point where i don’t know what to do.  I can chose to use the entire drive to install ubuntu or (and my memory is a bit foggy) i can manually edit the partition.  I click on manual partition and my partition is there but i'm not sure where to go from there.  I select the partition i want then press next but it then asks me about my other partitions.  I'm sorry if this post is confusing.  

Thanks
andy

---

### Post by Kateikyoushi on 2007-02-23
Two 15GB parts are not really a good partition laytout for ubuntu, what you need is a swap with 1Gb maximum and a / partition where ar your files go that should be bigger.

Read this guide for installation help. [LINK]("http://www.psychocats.net/ubuntu/installing")

---

### Post by handyandy16 on 2007-02-24
Thanks for that page.  ok well i have gone through the page and have come to a place where i dont know what to do.  I do not have have the option to have ubuntu partition my disk for me so i'm going to have to do it manually..... here are some screen shoots...

[IMG]http://i63.photobucket.com/albums/h146/Stephanie86_2006/1-1.jpg[/IMG]

[IMG]http://i63.photobucket.com/albums/h146/Stephanie86_2006/2.png[/IMG]

[IMG]http://i63.photobucket.com/albums/h146/Stephanie86_2006/3.png[/IMG]

As you can see i have a partition for a swap (about 1Gig) and just about 14GB for the rest, can someone help and walk me through this please?  i'm not sure what to do once i get to the last screen shot.  I really dont want to do anything with any of the other partitions.  Do i need more?

---

### Post by confused57 on 2007-02-24
As long as you don't select "Format" for the partitions you don't want affected, they'll be mounted only.
Click the arrow down next to /media/hda5 & select "/" for the root partition, then select to "Reformat"...I assume that's your desired partition to install Ubuntu.
Same for /media/hda6, but select "swap", then select to "Reformat".

You'll still get a summary of what the setup is going to be, where you can click "cancel", if you're unsure.

I'm more familiar with the alternate installer, which I prefer, so you may want to wait on someone more experienced with the desktop installer to confirm this.

---

### Post by handyandy16 on 2007-02-25
Ok thanks....

So you cant screw up the my other drives (which are NTFS) if i mount them?  I dont really want to mount them.  What do i do if i dont want to do anything to them?

---

### Post by Kateikyoushi on 2007-02-25
You can install ubuntu on NTFS partition, you need to change it, I recommend ext3 for the bigger partition the other has to be swap. As the guide writes set the bigger partition as / and the smaller as swap.

---

### Post by Kateikyoushi on 2007-02-25
It won't screw up your other partitions unles you format them, even if you mount them won't screw them as by defult ntfs is mounted read only.

By the way I would resize the last fat partition to take up the empty space behin it as well, of course after a backup.

---

### Post by handyandy16 on 2007-02-25
Do i keep the rest as they are (by which i'm refering to the last screen shot)?

Thanks

---

### Post by Kateikyoushi on 2007-02-25
The rest is ok just the two what you want to use for ubuntu isn't.Change the mount point to / and to swap, but have to change the filesystem on those first.

---

### Post by skennedy1217 on 2007-02-25
Been frantically searching the forums for advice and this seemed like a current thread on the topic (sorry if it's out of place).

I'm about to format a new 200gb drive for dual boot xp/ubuntu.  My current 80gb drive w/ xp is going bad.  Should I format the whole 200gb as NTFS, install xp and then run the Ubuntu Live CD?  Or should I manually set some partitions now?  If the latter, any recommendations on the partition sizes?  The Maxtor utility I'm using to format the drive only allows NTFS and FAT32.

Thanks for your assistance...hopefully my drive won't crash before I can get some help!

---

### Post by handyandy16 on 2007-02-25
Thank you very much for helping me out with this, i'm sure these questions are kind of simple :) .  Can i just click the reformat button to change the files system to the right one?

---

### Post by Kateikyoushi on 2007-02-25
No that won't be enough use gparted to change the filesystem.

---

### Post by skennedy1217 on 2007-02-25
> **skennedy1217 said:**
> Been frantically searching the forums for advice and this seemed like a current thread on the topic (sorry if it's out of place).

I'm about to format a new 200gb drive for dual boot xp/ubuntu.  My current 80gb drive w/ xp is going bad.  Should I format the whole 200gb as NTFS, install xp and then run the Ubuntu Live CD?  Or should I manually set some partitions now?  If the latter, any recommendations on the partition sizes?  The Maxtor utility I'm using to format the drive only allows NTFS and FAT32.

Thanks for your assistance...hopefully my drive won't crash before I can get some help!

Realizing that maybe I should have started a new topic, but just wanted to bump this to see if anyone was around to help.  I'm a total ubuntu newbie, and haven't had a lot of HDD partitioning experience either.

---

### Post by Kateikyoushi on 2007-02-25
I would rather recommend not to make one big ntfs, things could go wrong with the resize uncommon but it is safer to make the partition just as big as you want to use later.
Then from ubuntu install cd make your ubuntu partitions, an ext3 for / and a swap partition. Ubuntu can't be installed on ntfs.

---

### Post by skennedy1217 on 2007-02-25
Thanks!  I'll probably set up 15gb NTFS for Windows, set the rest as FAT32, install XP, and then give ubuntu a go.

---

### Post by handyandy16 on 2007-02-25
ok i have formated the 14 gb to ext 3 and the 1gb to swap.  I choose swap for swap and / for the 14gb but i get a message saying "choose root" i thought that the / was the root....

---

### Post by confused57 on 2007-02-25
> **handyandy16 said:**
> ok i have formated the 14 gb to ext 3 and the 1gb to swap.  I choose swap for swap and / for the 14gb but i get a message saying "choose root" i thought that the / was the root....

There is a bug with the Ubiquity installer, the work-around is here:
[http://www.ubuntuforums.org/showpost.php?p=1700787&postcount=29](http://www.ubuntuforums.org/showpost.php?p=1700787&postcount=29)

---


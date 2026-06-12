---
title: "Some oddball partition questions"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by Redeyes_Gambit on 2007-02-09
}{i,

I'm getting ready to install Windows Vista on my Laptop but have a little problem.

I already have XP, Ubuntu and an Acer default restore partition on my disk and that brings me to the 4 primary partition maximum. Before you correct me, yes, I can count lol. Ubuntu, as you all know, consists of TWO partitions: one for data one for swap.

So I find myself in a little pickle. I don't want to get rid of Ubuntu because it's my primary OS and wouldn't part with it for any of Vista's eye-candy, no matter how cool it is. Removing the Acer restore partition and XP are also out of the question.

So, that leaves me with but two options. 1: remove the Ubuntu swap partition or 2: somehow move both Ubuntu's data partition and Ubuntu's swap partition into an extended logical drive, thus turning my two primary partitions into one primary partition.

I think I could probably safely remove my Ubuntu swap partition since I have 2 gigs of DDR2 system RAM and I don't hibernate my laptop. Any time I try to hibernate I lose my swap partition anyway lol. Is this safe? What issues may I experience if I remove my swap partition? How should I go about it exactly?

The second option sounds preferable to me, but I do not know if it is possible to move two primary partitions into an extended partition and keep a workable system. Is it possible to move Ubuntu's two partitions into a sing extended partition? How would I go about it? What issues might I encounter?

---

### Post by reiki on 2007-02-09
Hold off on Vista until like.... 2008.... maybe. It's got issues.
It would be different (maybe) if you were buying a laptop with Vista on it, but to install on a laptop that didn't come with it? .... no thanks.

Sorry... I know that's not what you asked, but I'm dealing with Vista problems daily. (university environment) and right now we are telling people not to even bring them on campus.

---

### Post by meng on 2007-02-09
You can delete the swap partition, so you have three primary partitions.
Then create an extended partition into which you can place lots of logical partitions (the extended partition itself counts towards your limit of four, so that's why you need to delete the swap first).
This way, you won't even need to move your main Ubuntu partition! (but you will need to redirect it as to where to find the swap)
EDIT:
actually, on second thought, both Vista and XP will want to be on their own primary partition I bet, so yes, you will need to move the Ubuntu partition too. But you will also need to do it in the order I described.

---

### Post by Redeyes_Gambit on 2007-02-09
RE: reiki

Lol, yea I know it will be a hassle (hence keeping the XP partition) but I got a CD free from my college so I figured, why not? Normally I would wait for a good long time but, again, getting it free makes it a lot more appealing :) . Plus, I'm a real tech head anyway and the idea of getting to play with a new bit of any sort of software, buggy or not, grabs my attention.

RE: Meng

I see your point Meng. Good idea! However, I have another question: will Windows Vista install/boot to a logical partition? If it does, fantastic! If not I am again left with the questions I had at first lol.

---

### Post by meng on 2007-02-09
I suspect XP and Vista will demand a primary partition, while Ubuntu will not. But you will still be able to have 3 primary partitions and 1 extended if you follow my instructions.
1. delete swap
2. create extended
3. move swap and Ubuntu to extended

---

### Post by Redeyes_Gambit on 2007-02-09
Yes, BUT an extended partition, though it contains many logical drives, counts as a primary does it not? So, if I were to do as you say I would wind up with:

Primary part 1: Acer Backup
Primary part 2: Win XP
Primary Part 3: Vista
Primary Part 4: Ubuntu Data
Primary part [COLOR="Red"]5[/COLOR]: Extended partition containing Ubuntu swap.

In order to reduce the number of partitions I have to have TWO of my current partitions put into a single extended or there is no gain at all.

(EDIT) OOPS! Lol sorry, I missed your edit saying I need to move the Ubuntu Data as well. OK, the question remains is it possible to MOVE my primary Ubuntu data partition AND swap INTO an extended logical drive and keep it bootable/usable? I know I can install to an extended but *move an existing???*

---

### Post by housam on 2007-02-09
You could burn the acer back-up to a DVDs to free that partition. I think it is the only way to install vista.

---

### Post by Redeyes_Gambit on 2007-02-09
> **housam said:**
> You could burn the acer back-up to a DVDs to free that partition. I think it is the only way to install vista.

Yea, I thought of that and have actually already done so. However, I just don't like the idea of having XP lie entirely on a DVD. Too many OS disks have I seen ruined by a careless scratch.

I may resort to what you suggest Housam. Too bad I didn't just install Ubuntu to an extended partition in the first place but hindsight is 20/20 as they say.

---

### Post by meng on 2007-02-09
My solution depends on you installing Vista LAST. If you've already installed Vista, then you have to get more creative.

---

### Post by barry_r on 2007-09-02
Here is the solution I used to install Feisty32 on an HP laptop:

Considerations: Some manufacturers (such as HP and Sony) will only honour the warranty if the original OS (such as Vista or XP) is left on the hard drive.  Acer (now Gateway) on the other hand has told me that they would give me a Windows rebate (about $30 or so) for refusing the licensing agreement and formatting the drive.  They did not stipulate that the warranty would be affected.

1) Before proceeding, CREATE RESTORE DISKS using the built-in utility to do this.  This will allow you to restore the drive to it's factory condition if you have warranty problems which still allow you to do this.  

2) Unless you are desperate for space, leave the manufacturer's restore partition intact on the hard drive.  It may be possible to burn the image of this partition to DVD's and restore it, but then again...

3) Use Ubuntu/Kubuntu to resize the Vista/XP partition to something manageable (like 40 GB or so), instead of being one big NTFS partition.  Some laptops like Acer still come as XP on FAT32, but you can always resize this and use XP to convert to NTFS afterwards.  Kubuntu resized Vista without incident on my laptop.

4) Now you have 2 primary NTFS partitions on the drive.  Create an extended partition to fill all the remaining space using the Ubuntu/Kubuntu installer.  Create at least 3 logical partitions inside this extended partition: swap, root, home.  I created an additional ext3 data partition as well, for a total of four.

5) Install Ubuntu/Kubuntu and enjoy.  If something breaks on your laptop you can use the system restore disks to get it back into *acceptable* factory condition (may have to manually wipe the ext3 partitions).  If something like the display etc. goes that prevents you from doing this, you can pull the drive, install as a secondary drive in another system, and back up/format the ext3 partitions back to *acceptable* NTFS prior to return for warranty repair.  I do not think that they could object if Vista/XP was still installed (but on a little smaller partition), and grub was removed.

---


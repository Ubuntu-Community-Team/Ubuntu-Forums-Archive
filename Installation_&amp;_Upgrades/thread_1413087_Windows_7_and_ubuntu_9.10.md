---
title: "Windows 7 and ubuntu 9.10"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by mitchewr on 2010-02-22
Ok, I have a laptop that had ubuntu 9.10 as well as windows vista.  I wanted to erase vista and install windows 7 along side of ubuntu.  I went in through G-parted and erased the windows partition (didn't touch ubuntu) and everything worked fine.  I even upgraded to Grub2 and had ubuntu working perfectly after I had completely erased windows vista.  

Well, I then went ahead and installed windows 7 professional 64 bit, and when it came time to pick a partition (by the way this is all on 1 hard drive) I chose the large empty partition that had previously held vista.  I went ahead and installed it and everything went fine.  I got windows working and all updated.  I then went to reinstall Grub2 boot loader via live boot disk.  Well when I went to install it on the ubuntu partion, the ubuntu partion was no longer there!  It was erased and was simply "unallocated free space".  

I have installed windows along side of ubuntu on SEVERAL computers (and multiple times on some of the same computers) and I've never had this happen.  What would cause the computer to erase the linux partition without my telling it to do so.  I'm 100% positive that I didn't accidentally click "erase" on the linux partion, and I know that I didn't get them confused b/c of the massive size difference.  

So basically, I'm looking for an answer as to why my linux partion just up and erased itself.  Any ideas?

---

### Post by aviedw on 2010-02-22
Windows doesn't like to share :D But seriously i would say its usually best to install Ubuntu after you've installed the windows os.

---

### Post by Mark Phelps on 2010-02-22
> **mitchewr said:**
> ... So basically, I'm looking for an answer as to why my linux partion just up and erased itself.  Any ideas?

Sorry ... don't have an answer.  I've done this same thing on several machines, and not once, has the Ubuntu install been touched or damaged, let alone erased.  True, I did have to reinstall GRUB to the MBR, but that's just routine.

So, despite the stupid "nazis" comment, there's no basic intent on the part of MS to erase or damage other OS installations.

---

### Post by jirah on 2010-02-22
I just installed a version of Win 7 on a clean drive yesterday and saw a frightening little note once I had created my partition to install to. It said something to the effect that Win 7 was likely to create another partition, with a size of its choosing to hold system files. Clearly not a direct quote, but you get the picture, I clicked OK on this message, no fear since I had no data on this drive yet. Although I did have a thought as to what might happen if I DID have other data in other partitions and there was no room for that little few hundred megabyte partition that Win 7 created for 'system files'. I am sorry to say that I think you just answered my question for me.

---

### Post by SeePU on 2010-02-22
Sounds like that is what happened.  MikeySoft knows that people install other operating systems so I guess Windows 7 is programmed to enable operations that use up the current partition and any other available partitions for 'additional space' unless you CATCH IT or recognize it when the option comes up to the user.

It's almost better to choose any custom install or to click 'ok' only for the initial install and click 'no' for almost all other options.  At least, click 'no' for anything to do with 'writing' to another partition.  A good rule of thumb is to be alert when installing and READ every option until you're totally familiar with it.  Mikeysoft is trying to be sneaky again!

---

### Post by mitchewr on 2010-02-22
Lol, well as long as I can be of help haha.  Well thanks anyways guys, it's mot a huge deal, I was just really really curious.

---

### Post by meierfra. on 2010-02-22
I would guess that only the partition table is messed up. If you are interested, I can show you how to use testdisk to try to recover the Ubuntu partition.

---

### Post by presence1960 on 2010-02-22
> **jirah said:**
> I just installed a version of Win 7 on a clean drive yesterday and saw a frightening little note once I had created my partition to install to. It said something to the effect that Win 7 was likely to create another partition, with a size of its choosing to hold system files. Clearly not a direct quote, but you get the picture, I clicked OK on this message, no fear since I had no data on this drive yet. Although I did have a thought as to what might happen if I DID have other data in other partitions and there was no room for that little few hundred megabyte partition that Win 7 created for 'system files'. I am sorry to say that I think you just answered my question for me.

Windows 7 may create a second partition labeled "System Reserved" which contains boot files for the windows OS. The size is 100 MB. It will not overwrite or erase any existing partitions unless the operator (you) choose the wrong partition to install to..

---

### Post by jirah on 2010-02-26
My wonder was what would happen if there was no other room for this partition. Would it subtract the 100MB from the space reserved for itself? If an automatic install using an entire disk was selected, then it would have to use that option. What if a partition was present that Win7 partitioner did not recognize, such as ext3 or 4? Would it still only subtract from the space assigned to itself? Or would it take the space from elsewhere?

---

### Post by presence1960 on 2010-02-26
> **jirah said:**
> My wonder was what would happen if there was no other room for this partition. Would it subtract the 100MB from the space reserved for itself? If an automatic install using an entire disk was selected, then it would have to use that option. What if a partition was present that Win7 partitioner did not recognize, such as ext3 or 4? Would it still only subtract from the space assigned to itself? Or would it take the space from elsewhere?

If it is not possible to create that partition then the windows 7 installer will not create it. it will combine all boot files as other windows versions do.

---

### Post by darkod on 2010-02-26
> **jirah said:**
> My wonder was what would happen if there was no other room for this partition. Would it subtract the 100MB from the space reserved for itself? If an automatic install using an entire disk was selected, then it would have to use that option. What if a partition was present that Win7 partitioner did not recognize, such as ext3 or 4? Would it still only subtract from the space assigned to itself? Or would it take the space from elsewhere?

It takes the space from the unpartitioned space you tell it to use. Because it only creates it when you tell it to use unpartitioned space, not existing ntfs partition.
But I don't know what happens if you already have 3 partitions and it can't create boot+system partition, because that would be total of 5.

---

### Post by jirah on 2010-03-11
That is quite relieving to find out. Although my particular machine is too old and decrepid for the likes of Win7, my wifes machine is not. Save for the onboard Ati x200 graphics subsystem. I am relieved to know the scheme under which Win7 operates in choosing the location of its system partition. Now if I could be convinced that this partition was actually necessary and practical, that would be another thing altogether.

---


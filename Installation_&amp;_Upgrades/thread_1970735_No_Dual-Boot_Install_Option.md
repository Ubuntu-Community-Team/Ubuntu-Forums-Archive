---
title: "No Dual-Boot Install Option"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by NerdSource on 2012-05-01
I apologise if this problem has already been posted - and solved - on this forum, I did do a search but either it wasn't there, or my search skills are *that* poor...

I am interested in dual-booting my 1.5TB SATA hard drive with both Windows 7 (64-bit) and Ubuntu, but I am a ***TOTAL*** noob at this. I downloaded Ubuntu 32-bit, burned it to a CD successfully as instructed, re-started my computer and the option to 'install or try' appeared.

However, when I click "Install" I only get two options:

[LIST=1]
[*]Replace Windows
[*]Something Else
[/LIST]

I don't want to replace windows, and the 'something else' section just looks like an alien language with alien options to select to me! How do I get to the dual-boot option where I can create a partition and alter its size by dragging on its visual representation?

*(I am currently downloading the 64-bit version of Ubuntu, as my system is 64-bit and I'm wondering if that's the problem)*

---

### Post by darkod on 2012-05-01
The most common problem is if you are already using 4 primary partitions. You can check this in windows Disk Management.
The maximum on a disk is 4 primary partition so because it can't create new ones, it offers only to overwrite windows.

Also, in Disk Management take a look in your disk layout, and plan how you want it to look. If there is no unallocated space (not belonging to any partition), and usually there isn't, you will have to use Disk Management and shrink or delete some partition that would allow you to create unallocated space with the size you want to allocate to ubuntu.
If the 4 partitions limit is used up, you will have to delete one partition in any case.

After you have unallocated space, the install should go fine.

---

### Post by NerdSource on 2012-05-01
Ok, I have checked windows Disk Management. I have taken a screenshot of it as shown below...now I'm guessing the C: drive has *one* partition? And zero unallocated space?

[IMG]http://doodlesart.weebly.com/uploads/1/0/2/7/10272165/5160022_orig.jpg[/IMG]

How do I create a new partition to install Ubuntu into (*as I said, I'm a noob to the extreme at this*)? I'd like to allocate 500mb for the OS and my files...

---

### Post by darkod on 2012-05-01
500MB, was that a typo? You meant allocate 500GB?

The disk 0 has two primary partitions, so you are OK with the number of partitions. Yes, it has no unallocated space but that can be sorted out with shrinking C:.

But what is not normal is that you weren't given the "install side by side" option. It should, even without any unallocated space.

Sometimes it does this if there are any errors on the C: disk. Usually the advice is to run chkdsk on it, but for 1.5TB it will take many hours... :)

It's up to you if you wanna wait for a chkdsk, or simply do the shrink of C: for 500GB without that.

---

### Post by NerdSource on 2012-05-01
Ha! Yes, that *was *a typo - I did mean 500gb lol.
If there are any errors, will chkdsk be able to repair them? I've used 3rd party software before that are supposed to fix hard drive errors - all to no real advantage or effect. If it will detect AND fix them, then I can afford to wait for chkdsk to scan my hard drive (*it shouldn't take THAT long should it? Considering most of the hard drive is empty?*).

Also, once I have run chkdsk - how do I shrink the c: drive to provide unallocated space?

---

### Post by darkod on 2012-05-01
I think chkdsk passes the empty portion of the disk too, that's why it takes longer on bigger disks. Yes, it can repair errors. I think it was like:
chkdsk c: /r

But you can also ask google. Don't forget to run the command prompt as administrator, I think you need that for win7.

About the shrink, if I remember correctly, in Disk Management you right click the partition, select Resize and drag the right border (end border) to the left until you "cut out" the amount you want.

Then click OK and it will do its thing. Reboot windows few times after it's done, it complains sometimes if it's not rebooted few times.

---

### Post by NerdSource on 2012-05-01
Yay!!
Thank you ever so much for your most valuable assistance, darkod!
I have now successfully installed, and am using, Ubuntu! woot!

---

### Post by NerdSource on 2012-05-01
Can someone tell me (or do it for me) how to mark a thread as 'solved'? I'd like to mark this one up as Solved but haven't got a clue how...thanks!

**Edit:** nevermind, I worked out how to do it.

---


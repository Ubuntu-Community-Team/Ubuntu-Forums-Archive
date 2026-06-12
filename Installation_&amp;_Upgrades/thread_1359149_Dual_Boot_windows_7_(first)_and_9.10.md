---
title: "Dual Boot windows 7 (first) and 9.10"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by alberto.ceccherini on 2009-12-19
Hi, I would Like to install in dual boot Karmic on a new Sony Vaio CW.
It comes with Windows 7

I saw on forums that someones had troubles in dual booting windows 7 and ubuntu.

Is it dangerous? 

I got the CD and when the partition too start it says that there are different OS
Windows vista loader(11gb) ... i think it's wrong because it is windows 7
windows 7 loade (100mb) .. I think is the backup partition for the backup disks... and then a /dev/sda3  free....
Do you think I can proceed? Anyone was successful in doing it?
Thanks
Alberto

---

### Post by lmarmisa on 2009-12-19
If you want to avoid risks, maybe [http://www.virtualbox.org](http://www.virtualbox.org) is the best choice.

Personally, I like virtualization and my personal experience with it has been excellent.

Best regards,

Luis

---

### Post by OrangeCrate on 2009-12-19
> **alberto.ceccherini said:**
> Hi, I would Like to install in dual boot Karmic on a new Sony Vaio CW.
It comes with Windows 7

I saw on forums that someones had troubles in dual booting windows 7 and ubuntu.

**Is it dangerous? **

I got the CD and when the partition too start it says that there are different OS
Windows vista loader(11gb) ... i think it's wrong because it is windows 7
windows 7 loade (100mb) .. I think is the backup partition for the backup disks... and then a /dev/sda3  free....
Do you think I can proceed? Anyone was successful in doing it?
Thanks
Alberto

It's not dangerous, and many people here (including myself) dual boot. Here are a set of instructions to do it right...

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

---

### Post by Mark Phelps on 2009-12-19
> **alberto.ceccherini said:**
>  ... Is it dangerous? ...


YES it is -- if (1) you allow the Ubuntu installer to shrink your Win7 partition to make room for Ubuntu and (2) don't do a full image backup of your Win7 partition prior to doing this install.

While not everyone experiences OS partition corruption using the Ubuntu installer, SOME do, and without an image backup, and especially without a Win7 installation DVD or Win7 Recovery CD, both of which can be used to repair Win7 booting, you're running the risk of ending up with an unbootable Win7 install -- and no way to repair it.

---

### Post by alberto.ceccherini on 2009-12-21
So the suggestion is:
1) Shrink my windows 7 partition by the windows tool.
2) Make a new backup disk with the updated partition
3) install ubuntu in the new partition.

Is it true? Therefore if smoething goes wrong I can come back to the old configuration in the last backup...

ok?
Thanks for the replay, just waiting a confirm to start... :-)
Alberto

---

### Post by oldfred on 2009-12-21
After you shrink the win7 partition within windows make sure it boots ok. It may want to do filechecks since it will see the different size.

If you have a 100mb partition it is from a clean install of windows 7 and is windows 7's boot partition.

If you are going to dual boot you may want another NTFS partition for data that you want to share. While Ubuntu will read (and write) into your windows install partition, it is safer to use a separate partition for the data. If you add separate data partition then you have to use manual install.

[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by presence1960 on 2009-12-21
While you are at it, you should download the iso from [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"), burn it as an image to CD/USB so you have access to Windows 7 Recovery Console without using your recovery partition/DVD as they will restore hard disk to factory image.

For what it is worth I concur with Mark's & oldfred's advice.

---

### Post by alberto.ceccherini on 2009-12-22
Thanks !! it worked perfectly for me.. (sony vaio CW )
marking as solved
Alberto

---


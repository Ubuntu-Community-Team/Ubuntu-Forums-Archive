---
title: "Remove."
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by hombrepajaro on 2008-10-14
This will probably not be a nice post, but sadly I need to remove my Ubuntu Partition on my Dell. 

Could any one suggest what would be the best way to go forward with this?

Thanks in advance!

Adrian

---

### Post by iponeverything on 2008-10-14
Any partition editor will do it.

---

### Post by Elfy on 2008-10-14
It depends on whether you have windows installed or it will be os less once ubuntu is gone.

If you have windows use your win disc to restore the mbr with recovery mode - boot with the disca nd it start recovery, unless it's vista and I'm not sure then.  There is also supergrub which has the recover win boot options.

Then remove the partition that has ubuntu on it.

---

### Post by eragon100 on 2008-10-14
Why do you need to remove it, you don't seem to be very happy about it, maybe we can solve whatever is wrong with your ubuntu installation :wink:

---

### Post by bigken on 2008-10-14
if you have windows boot into windows delete and format the ubuntu partitions 

then use your windows xp cd go to recovery console use these commands 

fixmbr 

fixboot 

exit 

viola you boot strait into windows


also take look [here]("http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php")

---

### Post by lukjad on 2008-10-14
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)
This should be what you are looking for.

---

### Post by hombrepajaro on 2008-10-14
Thank you all. 

I basically dont use ubuntu any more. This is why I want to remove the partition. 

I finally baught a mac:), so I'm using my Dell strictly for work.

---


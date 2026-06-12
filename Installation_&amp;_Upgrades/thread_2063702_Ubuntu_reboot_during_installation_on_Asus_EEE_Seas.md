---
title: "Ubuntu reboot during installation on Asus EEE Seashell"
date: 2012-09-27
forum: Installation &amp; Upgrades
---

### Post by Omizuk on 2012-09-27
Hello,
I am trying to install Ubuntu on my Asus eee, and it goes fine till I need to choose if I want to install Ubuntu alongside windows, installing only Ubuntu or other options. If I choose the first option the system reboot. Anyone has some suggestion?

---

### Post by critin on 2012-09-27
> **Omizuk said:**
> Hello,
I am trying to install Ubuntu on my Asus eee, and it goes fine till I need to choose if I want to install Ubuntu alongside windows, installing only Ubuntu or other options. If I choose the first option the system reboot. Anyone has some suggestion?

No error or info message? Choosing where to install is very close to the beginning of the install and nothing else has been done yet, so 'all goes fine' is really premature.

I would boot the cd again and this time choose TRY LIVE.  That will let you see if ubuntu will work on your machine.  You know, internet and sound--all that.

Why it reboots I don't know.  You have room on the disk, right?  How many primary partitions is windows using?  Check that from Windows.  You can only have four primaries to a disk.

---

### Post by cbanakis on 2012-09-27
Might not be relevant, but the Asus eee's have a hiden recovery partition on them.

So that may be the problem.

If that is the case, deleting all partitions, and doing a clean install of windows should allow you to install Ubuntu along side windows.

But you will lose your recovery partition.

There is probably a better way, but if you don't care about the recovery partition as I don't, it might be worth a try.

---

### Post by critin on 2012-09-27
> by cbanakis:  but if you don't care about the recovery partition as I don't, I'd bet he does--very  much.

I wouldn't advise new ubuntu users to delete either windows or their recovery partition, but that's just me.  They tend to be unappreciative in a short amount of time--like when the novelty wears off.  ;)

Extended partition., logical ubuntu...but I'm not going there.

[http://www.sevenforums.com/tutorials/146694-partition-extended-logical-drives.html](http://www.sevenforums.com/tutorials/146694-partition-extended-logical-drives.html)

---

### Post by Omizuk on 2012-09-28
Yes I guess ¨all goes fine¨ is indeed premature. Anyway, I tried (through USB key) the live version and the Ubuntu works, that is - there are wifi connections, I can surf the internet and see my files on the Windows partitions. I didn't want to delete Windows in order to save my files and not need to backup everything, but if it gets complicated I think I might do it. Windows has made four partitions on this my disk, two of them are c: (/dev/sda1 ntfs) and d: (/dev/sda3 ntfs) and the other I guess is the recovery (/dev/sda2 fat32), the forth is 16 Mb and I don't know what it is (/dev/sda4).

I should have enough space on drive c:, from Windows I see there is about 60 Gb free on it.

After I choose to install alongside Windows it exit from the installation screen of Ubuntu, I can just see the message ¨acpid :exiting..¨ but I don't have enough time to read further and it immediately reboots.

---


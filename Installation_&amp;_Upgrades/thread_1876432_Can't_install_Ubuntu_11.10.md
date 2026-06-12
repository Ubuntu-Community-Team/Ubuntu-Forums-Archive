---
title: "Can't install Ubuntu 11.10"
date: 2011-11-06
forum: Installation &amp; Upgrades
---

### Post by music_man1352000 on 2011-11-06
Hi everyone

I'm having the exact same problem as described here (I think):

[http://ubuntuforums.org/showthread.php?p=11399600]("http://ubuntuforums.org/showthread.php?p=11399600")

My HDD is not flagged as a RAID component, however I strongly suspect that a similar issue (maybe the partition structure???) is to blame. A screenshot from Disk Utility is attached. The 105 GB partition is a Windows partition that I've only just finished installing. I would be *very* unimpressed if I have to reinstall that as it has basically taken me all day to get Windows sorted.

Any suggestions?

---

### Post by darkod on 2011-11-06
Have you ever used this disk in a fakeraid or other type of raid?

---

### Post by darkod on 2011-11-06
If you suspect you have raid meta data on your disk, and if you ARE NOT using raid, it doesn't hurt to execute the command for removing it.
With the ubuntu cd boot into live mode (Try Ubuntu mode), open terminal and execute:

sudo dmraid -E -r /dev/sda

If it asks to confirm to remove metadata that means you did have it. Just confirm and it should be fine.

What is the problem exactly, when trying to install the partitioner can't see any partitions on the disk?

---

### Post by music_man1352000 on 2011-11-06
Hi darkod

Thanks for the comments.
No, I don't think I've ever used this disk in a fakeraid array but I'll try your suggestion just in case it helps.
What happens is that I select a language (English), the next screen shows that I have internet available with an HDD larger than 4.5 GB, then the next screen is the "installation type" screen - I don't get to see the intermediate window offering me the various install options and the partition list in the "installation type" screen doesn't list any of my partitions. I tried to remove all the partitions except the Windows one but that didn't help either...

Thanks once again for your help and I'll get back to you in a few hours...
mm

---

### Post by MAFoElffen on 2011-11-07
> **music_man1352000 said:**
> Hi darkod

Thanks for the comments.
No, I don't think I've ever used this disk in a fakeraid array but I'll try your suggestion just in case it helps.
What happens is that I select a language (English), the next screen shows that I have internet available with an HDD larger than 4.5 GB, then the next screen is the "installation type" screen - I don't get to see the intermediate window offering me the various install options and the partition list in the "installation type" screen doesn't list any of my partitions. I tried to remove all the partitions except the Windows one but that didn't help either...

Thanks once again for your help and I'll get back to you in a few hours...
mm
@darkod

You know that in your first post in the picture you attached from the disk partitioner-- that is said that your disk has bad sectors right?  Did none of you catch that?  Have you dealt with that since your first post?

---

### Post by music_man1352000 on 2011-11-07
@darkod: running that command gave me the following prompt:
> Do you really want to erase "isw" ondisk metadata on /dev/sda ? [y/n] :
...to which I responded 'y'. The Windows partition was unharmed. After recreating all my partitions with gparted I was able to install Ubuntu successfully. Thank you, thank you, *thank you*!!! :)

@MAFoElffen: yes, I'm aware of that. This is a relatively old 250 GB WD drive going into a "test" machine. It doesn't matter if it falls over in a few months. I just don't happen to have any other drives handy right at the moment. Thank you for pointing it out though. :)

---


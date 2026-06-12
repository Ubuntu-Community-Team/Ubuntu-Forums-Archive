---
title: "Disk check at bootup"
date: 2010-04-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Cavsfan on 2010-04-16
Today every time I boot up it says the disks are being checked and this may take a while,
but it is usually quick, except once.

But, it happens every time I boot up, which has been a lot today.

Anyone else have the same issue?

Thanks!

---

### Post by Cope57 on 2010-04-16
Unclean unmount usually causes this.  Been almost a year since I rebooted, so I do not know the cause for your situation.  I am guessing it is from the shutdowm sequence not being properly handled.

You are using a testing version, and not a stable operating system, so bugs are known to exist.  Submit your bugs, and see if there are solutions already available for you.

Quoted from this thread topic.
> This forum is for the discussion of Ubuntu Lucid Lynx. Lucid is in development and will be out in April 2010 and will be a long term support release. Please note: Ubuntu Developers do not usually read the forums, to report a problem found in Lucid please report the bug in [Launchpad]("https://launchpad.net/ubuntu/+filebug").

---

### Post by Owen.C93 on 2010-04-16
Yes I also have this issue.

---

### Post by Cavsfan on 2010-04-16
> **Cope57 said:**
> Unclean unmount usually causes this.  Been almost a year since I rebooted, so I do not know the cause for your situation.  I am guessing it is from the shutdowm sequence not being properly handled.

You are using a testing version, and not a stable operating system, so bugs are known to exist.  Submit your bugs, and see if there are solutions already available for you.

Quoted from this thread topic.

Wow, you have not rebooted in a year! I have never heard of a system going that long. 
I leave my system on 24/7, but I do shut it off during a thunder storm, etc.

Thanks Owen.C93 for the reply! At least I am not alone and am wondering if there are others.

Thanks Cope57

---

### Post by siegi on 2010-04-16
I have this to in plymouth since today. 

I thought i had something to do with disabling encryption on my swap partition. (i want to suspend).

---

### Post by FuturePilot on 2010-04-16
I see the same thing. It only shows up for about 1 second and then disappears. It's not a real fsck though since that takes longer.

Edit: Bug here [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/564434]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/564434")

---

### Post by VMC on 2010-04-16
One thing I now noticed, is if you do a forcefsck:

```
sudo touch /forcefsck
```, it never gets removed.

After a successful file system check, that file should be removed automatically.

---

### Post by Cavsfan on 2010-04-17
After updating today and rebooting, the disk check did not occur.
Hopefully it won't reappear.

---

### Post by RickyCodes on 2010-04-17
Also got this the last reboot

Running updates 2-3 times a day

---

### Post by Cavsfan on 2010-04-17
I just rebooted and got the same error. I had seen an update to plymouth (I thought) this morning and the first reboot did not get
this error, but I guess that was a fluke and it's back. It does just appear for a few seconds and I see it has been reported.

---


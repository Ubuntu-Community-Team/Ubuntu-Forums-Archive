---
title: "dpkg --configure -a"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by eharp1126 on 2008-06-26
When I was updating my HP laptop's Hardy last night, it froze during the update.  I had to do a hard reset.  When it rebooted, it seemed fine and said that it was up to date.  However, I was unable to install any packages.  It said
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

I ran 'sudo dpkg --configure -a' and it froze my computer again.

I hard reset and tried it again, this time running
sudo apt-get install -f as soon as I ran dpkg, but still it froze.

Any ideas?

Thanks

---

### Post by Midwest-Linux on 2008-06-26
> **eharp1126 said:**
> When I was updating my HP laptop's Hardy last night, it froze during the update.  I had to do a hard reset.  When it rebooted, it seemed fine and said that it was up to date.  However, I was unable to install any packages.  It said
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

I ran 'sudo dpkg --configure -a' and it froze my computer again.

I hard reset and tried it again, this time running
sudo apt-get install -f as soon as I ran dpkg, but still it froze.

Any ideas?

Thanks

sudo apt-get update

---

### Post by eharp1126 on 2008-06-26
before or after dpkg?

---

### Post by eharp1126 on 2008-06-26
After running sudo apt-get install -f, I get
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/varlib/dpkg), is another process using it?

After running sudo apt-get update, I get
E: The method driver /usr/lib/apt/methods/ttp could not be found
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/varlib/dpkg), is another process using it?

---

### Post by shoradhi on 2008-06-26
Hi, you got the same problem with me...what i'm done was, I reboot the ubuntu, run it in recovery mode, then i select an option to fix dpkg. and it works. So now, i can download my updates. Give it try.good luck, cheers

---

### Post by tamoneya on 2008-06-26
> **eharp1126 said:**
> After running sudo apt-get install -f, I get
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/varlib/dpkg), is another process using it?

After running sudo apt-get update, I get
E: The method driver /usr/lib/apt/methods/ttp could not be found
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/varlib/dpkg), is another process using it?

okay first make sure that you dont have synaptic open or something.  If not then it was closed down improperly but left a lock on the directory.  Run the following command and then start from the beginning:```
sudo rm /varlib/dpkg/lock
```

---

### Post by Midwest-Linux on 2008-06-26
> **eharp1126 said:**
> before or after dpkg?

I just put in sudo apt-get update after the kernel killed the add/remove. Maybe your computer needs another command instead.

---

### Post by eharp1126 on 2008-06-27
After putting in sudo rm /var/lib/dpkg/lock, running dpkg --configure -a, sudo apt-get install -f it still says the directory is locked.

Also, running sudo dpkg --configure -a results in a kernel statement followed by 'running depmod.'

At this point the system becomes very unresponsive.

Any ideas what to try next?

---

### Post by VMC on 2008-06-27
> **eharp1126 said:**
> After putting in sudo rm /var/lib/dpkg/lock, running dpkg --configure -a, sudo apt-get install -f it still says the directory is locked.

Also, running sudo dpkg --configure -a results in a kernel statement followed by 'running depmod.'

At this point the system becomes very unresponsive.

Any ideas what to try next?

I just had this problem. It was only after I re-booted did the problem clear up.

---


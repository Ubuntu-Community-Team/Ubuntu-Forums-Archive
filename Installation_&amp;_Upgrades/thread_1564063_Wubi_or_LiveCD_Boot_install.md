---
title: "Wubi or LiveCD Boot install?"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by electrox73 on 2010-08-30
Hi, should I install Ubuntu using Wubi or should I boot with the Live CD and install from there? I heard that it is safer with Wubi (didn't know about any risk..) but som have problems with the hardisk when they installed with Wubi.

So what should I do?


Regards

---

### Post by bcbc on 2010-08-30
If you install with wubi, you don't need to partition your drive. If you install via the CD, you do.

I would:
1. Boot the live CD (Try without installing)
This will tell you if Ubuntu is compatible with your computer and give you a good intro to what it is like.
2. Decide whether you want to (or can) partition your drive. If not, then try wubi - it will allow you to get a good feel for Ubuntu by persisting settings etc. - and if you change your mind, you just need to uninstall from windows and it's gone.
3. If you decide to partition and do a direct install, make sure you defrag windows a couple of times before installing. If it's Win7/Vista then use the windows disk utility to shrink the partition before installing. 

Backup your data before installing. Keep a windows repair CD handy. Playing with a new OS carries some risk, whatever method you use.

---

### Post by electrox73 on 2010-08-30
> **bcbc said:**
> If you install with wubi, you don't need to partition your drive. If you install via the CD, you do.

I would:
1. Boot the live CD (Try without installing)
This will tell you if Ubuntu is compatible with your computer and give you a good intro to what it is like.
2. Decide whether you want to (or can) partition your drive. If not, then try wubi - it will allow you to get a good feel for Ubuntu by persisting settings etc. - and if you change your mind, you just need to uninstall from windows and it's gone.
3. If you decide to partition and do a direct install, make sure you defrag windows a couple of times before installing. If it's Win7/Vista then use the windows disk utility to shrink the partition before installing. 

Backup your data before installing. Keep a windows repair CD handy. Playing with a new OS carries some risk, whatever method you use.

So Wubi is safer but what about the slightly reduce disk preformance? And I tryed Ubuntu on Sun VirtualBox, so I know if I like it or not, so no need of trying the LiveCD on bootup.

---

### Post by electrox73 on 2010-08-30
> **bcbc said:**
> If you install with wubi, you don't need to partition your drive. If you install via the CD, you do.

I would:
1. Boot the live CD (Try without installing)
This will tell you if Ubuntu is compatible with your computer and give you a good intro to what it is like.
2. Decide whether you want to (or can) partition your drive. If not, then try wubi - it will allow you to get a good feel for Ubuntu by persisting settings etc. - and if you change your mind, you just need to uninstall from windows and it's gone.
3. If you decide to partition and do a direct install, make sure you defrag windows a couple of times before installing. If it's Win7/Vista then use the windows disk utility to shrink the partition before installing. 

Backup your data before installing. Keep a windows repair CD handy. Playing with a new OS carries some risk, whatever method you use.

And should I do a System Restore Point or a Normal Backup?

---

### Post by bcbc on 2010-08-30
> **electrox73 said:**
> So Wubi is safer but what about the slightly reduce disk preformance? And I tryed Ubuntu on Sun VirtualBox, so I know if I like it or not, so no need of trying the LiveCD on bootup.

Wubi is safer from a partitioning point of view. If you are planning on using Ubuntu permanently, you probably want to partition or either have a plan to migrate to partition. I haven't noticed a huge difference in performance with wubi - but that might be the way I use Ubuntu.

> **electrox73 said:**
> And should I do a System Restore Point or a Normal Backup?

Normal backup. The system restore is a very useful tool on windows, however, it doesn't restore data. I've seen a few posts by people who've made a mistake and done something to destroy their data - those with a backup are a lot happier. The Ubuntu problems (non-user) that I've seen don't destroy data, but sometimes users react to problems with drastic measures.

In any case, you should have a data backup anyway - drives can and do fail.

---

### Post by electrox73 on 2010-08-30
> **bcbc said:**
> Wubi is safer from a partitioning point of view. If you are planning on using Ubuntu permanently, you probably want to partition or either have a plan to migrate to partition. I haven't noticed a huge difference in performance with wubi - but that might be the way I use Ubuntu.



Normal backup. The system restore is a very useful tool on windows, however, it doesn't restore data. I've seen a few posts by people who've made a mistake and done something to destroy their data - those with a backup are a lot happier. The Ubuntu problems (non-user) that I've seen don't destroy data, but sometimes users react to problems with drastic measures.

In any case, you should have a data backup anyway - drives can and do fail.

Well I do not want to use Ubuntu as my main OS, but whats the difference when it is installed without partitioning and with it?

---

### Post by bcbc on 2010-08-30
> **electrox73 said:**
> Well I do not want to use Ubuntu as my main OS, but whats the difference when it is installed without partitioning and with it?

Wubi installs ubuntu onto a virtual disk. It's basically a large file \ubuntu\disks\root.disk that is stored on an ntfs (or fat32) partition, but contains an ext4 formatted file system that is mounted and then used to install and run ubuntu. Since the entire OS is on a single file, it's vulnerable to corruption e.g. if you do a hard shutdown. 

If you install direct, you need to physically create a separate partition (one or more depending on how you install) on your computer. With most computers with windows, the windows install takes up the entire drive, so you need to shrink it first. Also, some already have 4 primary partitions (the max) so you might have to delete one and create an extended partition.

---

### Post by electrox73 on 2010-08-31
> **bcbc said:**
> Wubi installs ubuntu onto a virtual disk. It's basically a large file \ubuntu\disks\root.disk that is stored on an ntfs (or fat32) partition, but contains an ext4 formatted file system that is mounted and then used to install and run ubuntu. Since the entire OS is on a single file, it's vulnerable to corruption e.g. if you do a hard shutdown. 

If you install direct, you need to physically create a separate partition (one or more depending on how you install) on your computer. With most computers with windows, the windows install takes up the entire drive, so you need to shrink it first. Also, some already have 4 primary partitions (the max) so you might have to delete one and create an extended partition.

So it is vulnerable to corruption, but if it corrupts will it effect my data on Windows?
And by hard shutdown, you mean shutting down by the physical power button?
And if I install with Wubi, do I still need to backup? Because I have a large HDD (200GB used).
And you mean that windows takes the whole disk to make a partition for it?

---

### Post by bcbc on 2010-08-31
> **electrox73 said:**
> So it is vulnerable to corruption, but if it corrupts will it effect my data on Windows?
And by hard shutdown, you mean shutting down by the physical power button?
And if I install with Wubi, do I still need to backup? Because I have a large HDD (200GB used).
And you mean that windows takes the whole disk to make a partition for it?

No. If you corrupt the wubi root.disk it won't affect windows.

Hard shutdown - I mean any shutdown that isn't clean, holding down the power button, power failure (assuming no laptop battery). 

You should always backup. With wubi you can either backup the entire root.disk (the entire install on the virtual disk) or just backup select data from within the install. Your choice.

Yes, often windows installs take the whole disk as a single partition (or the remaining space for a single partition, if you have rescue partitions etc.). Not always, but usually you have to split the windows partition to get space to install another OS.

---

### Post by electrox73 on 2010-08-31
> **bcbc said:**
> No. If you corrupt the wubi root.disk it won't affect windows.

Hard shutdown - I mean any shutdown that isn't clean, holding down the power button, power failure (assuming no laptop battery). 

You should always backup. With wubi you can either backup the entire root.disk (the entire install on the virtual disk) or just backup select data from within the install. Your choice.

Yes, often windows installs take the whole disk as a single partition (or the remaining space for a single partition, if you have rescue partitions etc.). Not always, but usually you have to split the windows partition to get space to install another OS.

Wait, so I need to backup Ubuntu and not Windows?

---

### Post by electrox73 on 2010-08-31
> **bcbc said:**
> No. If you corrupt the wubi root.disk it won't affect windows.

Hard shutdown - I mean any shutdown that isn't clean, holding down the power button, power failure (assuming no laptop battery). 

You should always backup. With wubi you can either backup the entire root.disk (the entire install on the virtual disk) or just backup select data from within the install. Your choice.

Yes, often windows installs take the whole disk as a single partition (or the remaining space for a single partition, if you have rescue partitions etc.). Not always, but usually you have to split the windows partition to get space to install another OS.

And how much disk space should I leave for ubuntu, I have 60GB left but I don't wanna take up the whole disk, and I wont install many thing on Ubuntu...

---

### Post by bcbc on 2010-08-31
> **electrox73 said:**
> Wait, so I need to backup Ubuntu and not Windows?

Oh that's what you're asking :)

I advise backup up everything. If you have important data without a backup, you're putting yourself at risk. e.g. a drive could fail at any time.

Playing with a new OS has some risks. I don't want to overstate this but it needs to be said.

---

### Post by electrox73 on 2010-08-31
> **bcbc said:**
> Oh that's what you're asking :)

I advise backup up everything. If you have important data without a backup, you're putting yourself at risk. e.g. a drive could fail at any time.

Playing with a new OS has some risks. I don't want to overstate this but it needs to be said.

But you said that Ubuntu can corrupt but it will not effect Windows...so how is it?

---

### Post by bcbc on 2010-08-31
> **electrox73 said:**
> But you said that Ubuntu can corrupt but it will not effect Windows...so how is it?
> **bcbc said:**
> No. If you corrupt the wubi root.disk it won't affect windows.
I said corrupting the root.disk won't affect windows. I didn't say you can't affect windows.

---

### Post by electrox73 on 2010-08-31
> **bcbc said:**
> I said corrupting the root.disk won't affect windows. I didn't say you can't affect windows.

And how can it effect Windows?

---

### Post by bcbc on 2010-08-31
> **electrox73 said:**
> And how can it effect Windows?

You can affect windows from windows, either by doing something yourself or running a program that does something. You can do the same from Ubuntu. 

I'm not saying it's going to happen - but it's possible. It pays to backup your data - it's common sense.

---

### Post by electrox73 on 2010-09-01
> **bcbc said:**
> You can affect windows from windows, either by doing something yourself or running a program that does something. You can do the same from Ubuntu. 

I'm not saying it's going to happen - but it's possible. It pays to backup your data - it's common sense.

So the chance of something to happen to windows is the same as before i install Ubuntu?

---

### Post by bcbc on 2010-09-01
> **electrox73 said:**
> So the chance of something to happen to windows is the same as before i install Ubuntu?

On the one hand, you'll likely be unfamiliar with the OS, and maybe you're unfamiliar with [multibooting]("http://www.multibooters.co.uk/multiboot.html") OSes. 

On the other hand you're unlikely to be vulnerable to viruses. The security model on Ubuntu is better than XP. Vista/7 have a similar system although I understand many users disable that feature.

That's about the best I can offer - the question you asked has no meaningful yes/no answer.

---


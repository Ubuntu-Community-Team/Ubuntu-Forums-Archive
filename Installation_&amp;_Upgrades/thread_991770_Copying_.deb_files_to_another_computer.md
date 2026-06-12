---
title: "Copying .deb files to another computer ?"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by oygle on 2008-11-24
Have one computer with all 8.04 updates applied. Another computer is (about) 2 months behind (running 8.04 also).

Can I just copy the .deb files from the 'apt cache' path from the first computer, to the second, and then will Ubuntu be able to simply do the updates from the apt cache (i.e. without connecting to the internet) ??

---

### Post by Zaraphrax on 2008-11-24
I don't see why not. Why couldn't you just run the .deb's instead of doing it from apt-get? That would make more sense to me.

---

### Post by Pumalite on 2008-11-24
You can use AptON for that, but is incomplete:
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by oygle on 2008-11-24
> **Zaraphrax said:**
> I don't see why not. Why couldn't you just run the .deb's instead of doing it from apt-get? That would make more sense to me.

Okay, so after I copy them to the other computer in the /var/cache/apt/archives path , and make sure the permissions are okay, what command do I use to run the .debs , and also what about dependencies ?

---

### Post by mal on 2008-11-24
It should certainly be OK to copy the deb files from one computer to the archives directory on another computer, making sure to preserve the permissions.

However, I would recommend you stick with "sudo apt-get update" and "sudo apt-get upgrade".  This will make sure you have all the necessary deb files and all dependencies are met.

It is possible that the first computer might not have all the files needed for the second computer, because it has different applications, or some of the debs might already have been automatically purged from the first computer.

Mal

---

### Post by oygle on 2008-11-24
> **mal said:**
> However, I would recommend you stick with "sudo apt-get update" and "sudo apt-get upgrade".  This will make sure you have all the necessary deb files and all dependencies are met.


Okay thanks. I assume apt-get looks in the cache first then.

> **mal said:**
> 
It is possible that the first computer might not have all the files needed for the second computer, because it has different applications, or some of the debs might already have been automatically purged from the first computer.

Yes, some of the debs have been purged unfortunately.

I assume when the second computer is completely up to date with 8.04, I just run "sudo apt-get upgrade" to go to 8.10

---

### Post by mal on 2008-11-24
> **oygle said:**
> Okay thanks. I assume apt-get looks in the cache first then.

Yes, apt-get will check the cache before it downloads any debs from the repository.

> Yes, some of the debs have been purged unfortunately.

This could be a problem. If you don't have all the necessary debs and your computer is not connected to the net, you won't be able to carry out the upgrade.

> I assume when the second computer is completely up to date with 8.04, I just run "sudo apt-get upgrade" to go to 8.10

No, "sudo apt-get upgrade" will only upgrade your 8.04 installation to the latest version of all packages for 8.04. Upgrading to 8.10 is a different story and you should check the documentation (help.ubuntu.com) for this.

By the way, copying the debs from one computer to the other will only work if they are running the same ubuntu version.

Mal

---

### Post by oygle on 2008-11-24
> **mal said:**
> This could be a problem. If you don't have all the necessary debs and your computer is not connected to the net, you won't be able to carry out the upgrade.


Yes, a network sharing problem I'm trying toget some answers to [here]("http://ubuntuforums.org/showthread.php?t=991778")

> **mal said:**
> 
No, "sudo apt-get upgrade" will only upgrade your 8.04 installation to the latest version of all packages for 8.04. Upgrading to 8.10 is a different story and you should check the documentation (help.ubuntu.com) for this.


Okay, I understand this now.

> **mal said:**
> 
By the way, copying the debs from one computer to the other will only work if they are running the same ubuntu version.


They both are running 8.04, so it should be okay.

Thanks.  :)

---

### Post by oygle on 2008-11-25
> **mal said:**
> Yes, apt-get will check the cache before it downloads any debs from the repository.


I tried "sudo apt-get update" on the second computer, after copying the .debs across, and it said there were 108 updates to do, even though the first computer says 23 updates to do (new ones today).

I ran Synaptic package Manger, marked updates, and saved the download script file, and there are quite a few files it 'thinks' need to be downloaded, but I can see them in the apt cache ?

Can I 'force' apt-get to look in the cache first ?

---

### Post by oldos2er on 2008-11-25
Why not use "sudo dpkg -i filename.deb"?

---

### Post by mal on 2008-11-28
oygle,

Sorry, it's been a couple of days since I've been on the forums.

Some comments in relation to questions from you and Ann:

- It's quite reasonable for there to be more updates on the second computer, since you haven't upgraded it for a couple of months.  The 23 updated packages on the first computer are just the latest updates.

- When you run "sudo apt-get upgrade" it will give you a list of all packages that need to be updated and it will show you the total number of megabytes that it needs to download.  This will not include the packages that are already in the cache.  apt-get will not download a package if the correct version is already in the cache.

- Ann, if you use "sudo dpkg -i filename.deb" to install the updated packages, you will have to make sure you install every package and you will have to install them in the correct order.  You will not be able to install a package that has a dependency that is not yet installed.  This is the beauty of apt-get or synaptic, they automatically take care of all these dependency issues for you.

Regards,

Mal

---

### Post by oygle on 2008-11-28
mal,

> **mal said:**
> 
- It's quite reasonable for there to be more updates on the second computer, since you haven't upgraded it for a couple of months.  The 23 updated packages on the first computer are just the latest updates.

- When you run "sudo apt-get upgrade" it will give you a list of all packages that need to be updated and it will show you the total number of megabytes that it needs to download.  This will not include the packages that are already in the cache.  apt-get will not download a package if the correct version is already in the cache.


Thanks for clarifying that. Despite the dialup connection, I copied all the .deb files from the first computers cache, to the second computer, and then just let it run all day (so slow), and all updates were applied on the second one. Then copied all .deb files to USB stick, compared the file list to apt cache on first, copied the missing ones, and then both computers were all up to date.

However, as dialup took so long, in between all that, another 17 or so updates, so did them, and finally both are up to date again.  :popcorn:

Thanks,

oygle

---


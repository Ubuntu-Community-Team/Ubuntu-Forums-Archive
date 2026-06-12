---
title: "Vista/Kubuntu: Windows thinks HD is corrupted/new hardware"
date: 2008-09-18
forum: Installation &amp; Upgrades
---

### Post by matt_feliks on 2008-09-18
Hi there,

I installed Kubuntu on my Dell Inspiron which had Vista already on it. Before installing Kubuntu I had tried to create a new partition on C, but Windows wouldn't let me resize the partition more than a few MB. 

So during installation I used the Kubuntu partition manager to resize the Windows partition.

Unfortunately, windows doesn't seem to happy with this, and is convinced C is corrupted. It tries to run dskcheck every time I start up (which I've now disabled); defragging doesn't help.

When I first ran vista after installing Kubuntu, it ran the "new hardware" wizard - so it also seems to think I've installed a new hard disk.

Vista is now running pretty sluggishly.

Kubuntu works fine.

What should I do to sort this out?

Thanks for looking!

PS wasn't sure which logs (if any) to post, just let me know the commands and I'll copypasta whatever you think needs to be seen.

---

### Post by pro003 on 2008-09-18
depends on space left for your vista... how much free space you got on c:\
as for reporting for new hdd found never happened to me cause my woman uses vista and am a ubuntu-guy!
try to release some space for your vista or defrag if needed..

---

### Post by matt_feliks on 2008-09-18
Defragging doesn't work.

Here's what disk management says:

The 98GB is Vista, 40GB is Kubuntu, 2GB is (I assume) the swap.

---

### Post by pro003 on 2008-09-18
you have enough free space on vista which means I can't tell wgy is running sluggish...

what is your computer hardware conf?

---

### Post by matt_feliks on 2008-09-18
It's a Dell Insp 6400

Core 2 Duo 1.83GHz
Gig of RAM
160GB HD
Nvidia Go 7300

Tbh I'm mostly concerned with why Vista thinks the disk is corrupted, and why Vista defrag won't work anymore...

---

### Post by timcredible on 2008-09-18
for anyone else thinking of partitioning with windows - don't.  run gparted instead.

for this issue, i think you should run a checkdisk on your vista partition - ntfsfix.  install ntfs-tools from synaptic to get this.

---

### Post by SuperSonic4 on 2008-09-18
Can you repair windows with the vista DVD and then reinstall grub from the kubuntu live cd?

---

### Post by matt_feliks on 2008-09-18
Thanks tim, will give this a try when I get home from work (proxy here doesn't let me get anything from repos!)

---

### Post by matt_feliks on 2008-09-18
> **SuperSonic4 said:**
> Can you repair windows with the vista DVD and then reinstall grub from the kubuntu live cd?

Thanks for your reply.

How exactly would I install grub from terminal? Could you point me to the commands? I've never fiddled with grub itself.

---

### Post by matt_feliks on 2008-09-18
Just to check: do you mean run "startup repair" from the Vista DVD?

---

### Post by perspectoff on 2008-11-10
I can't solve your problem.

However, I can give advice to others how to avoid it.

Windows Vista takes measures to prevent GParted (and some other partition managers) from resizing its partition. In a way, this is meant to protect hackers and provide extra security.

The best way to get around this is to resize the Vista partition from within Vista.

This can be done by accessing the "Disk Management" module of Windows Vista. This can be accessed in various ways:

1) Start --> Computer --> Manage --> Storage --> Disk Management

or

Start Menu --> Control Panel --> System and Maintenance --> Administrative Tools --> Double Click Computer Management --> Storage --> Disk Management

2) In Disk Management is a "Shrink Volume" option. Using this you can shrink your partition.

This is a safe way to do it and not run afoul of Vista's legion security bits.

Once you have shrunk the volume, you will have free space on the hard drive. You can simply install Kubuntu (or other OS), letting it use the "free space" for the OS. It will do the rest automatically.

(You could, of course, then used GParted to arrange the free space manually, but I don't recommend touching the Vista partition with GParted, Partition Magic or any other partition manager.)

This is quite different from Windows XP, where GParted (or Partition Manager) is the only way to resize the partition, (since you can't do it easily from within Windows XP).

---

### Post by Otustelija on 2008-11-10
> **matt_feliks said:**
> How exactly would I install grub from terminal? Could you point me to the commands? I've never fiddled with grub itself.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Your problem of Vista not defragging is probably due to the other problem.

---

### Post by caljohnsmith on 2008-11-10
> **matt_feliks said:**
> Just to check: do you mean run "startup repair" from the Vista DVD?
If I were you, I would go ahead and do the "Vista Repair" option from the Vista DVD/CD. If you don't have a Vista Install CD/DVD, you can download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Afterwards you might have to reinstall Grub to the MBR (Master Boot Record), but that is easy. Let us know how it goes.

---


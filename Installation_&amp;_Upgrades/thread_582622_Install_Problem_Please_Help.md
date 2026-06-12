---
title: "Install Problem Please Help"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by tripp-fan on 2007-10-20
I went and tried to install gutsy after thinking i removed the  feisty partition from my windows. when i start up install it says that fiesty wasn't deleted but grub doesn't load. So i am forced to do a manual partition which i have no idea how to do. Can someone help me with this. After deleting all the partions it looks like this on the prepare partitions screen.
/dev/sda1 ntfs /media/sda1
/dev/sda2 ntfs /media/sda2
free space         57001 MB

Can anyone walk me through this?

---

### Post by tripp-fan on 2007-10-20
can anyone help me this is extremly important that i get it fixed asap.

---

### Post by rsambuca on 2007-10-20
Just select manual partitioning and use the largest free space.

And please be patient.  Do not bump your threads like this.

---

### Post by tripp-fan on 2007-10-20
> **rsambuca said:**
> Just select manual partitioning and use the largest free space.

And please be patient.  Do not bump your threads like this.
 
Don't have that option. The only options i am given are Use all 120 Gb or Manual.

---

### Post by rsambuca on 2007-10-20
Manual.

---

### Post by tripp-fan on 2007-10-20
i do that and it wants me to build the partitions and i do not know how to do that.

---

### Post by R.Bucky on 2007-10-20
Um yeah, make 3 partitions. 
partition 1: 15GB for /root - the OS
partition2: swap - double your RAM
partition3: the remainder of your HD space - this is your /home directory where your personal files are located

partition 1 and 3 will be type ext3 while the swap will be "swap."

---

### Post by tripp-fan on 2007-10-20
will it install grub for dual booting

---

### Post by R.Bucky on 2007-10-20
Sure, I have had no problems with GRUB. It installs fine on my machine. Give it a shot and report back. The install only takes 10 minutes or so. Just make sure that you assign the root partition (/) to the smaller drive space versus the personal data (/home) partition.

However, if you are going to dual boot with Windows? be forwarned that Windows must be installed first. It is picky like that.

---

### Post by tripp-fan on 2007-10-20
is there anyway to bypass GRUB to boot my windows because anytime i try to start my computer up Grub comes up with an error 17

---

### Post by R.Bucky on 2007-10-20
I am not familiar with that error code. you might want to try searching within the forums. 

however, if you really want Windows VMware Server works excellent. I use it to run Windows 2000 and Vista. It is another option for you if switching to Linux completely scares you. VMware server is free, but you have to register to receive a key code. No problems there. 

Sorry that I could not help with that error code.

---

### Post by tripp-fan on 2007-10-20
I got the root ext3 and the swap made but it wouldnt let me make a ext3 home partition?

---


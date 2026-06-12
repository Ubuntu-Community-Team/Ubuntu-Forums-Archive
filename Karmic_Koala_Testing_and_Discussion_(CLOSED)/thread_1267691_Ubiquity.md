---
title: "Ubiquity"
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Bert Mariën on 2009-09-16
There is something wrong with the installer.

When I choose the manually partition the hard disk, selected the partition the root partition and the /home partition should be, it didn't show after clicking OK.

Seemed that no changes had been made.
It does seem to install alright - I'm still installing.

I'll come back after installation.
But it does not work alright!

---

### Post by Bert Mariën on 2009-09-16
Testing on my Dell Inspiron 2200.

---

### Post by Bert Mariën on 2009-09-16
Everything installed okay, only the "mount" option in ubiqity does not really seem to work, meaning: it does not show after one has specified a mount point.

---

### Post by Bert Mariën on 2009-09-16
Didn't work THAT well, because after the second boot and running the file check (automatically), it hung at 51%.

I think it needs looked at.

---

### Post by ruik on 2009-09-16
Filed a bug already? If not, please do so. :)

---

### Post by VMC on 2009-09-16
> **Bert Mariën said:**
> There is something wrong with the installer.

When I choose the manually partition the hard disk, selected the partition the root partition and the /home partition should be, it didn't show after clicking OK.

Seemed that no changes had been made.
It does seem to install alright - I'm still installing.

I'll come back after installation.
But it does not work alright!
I'd be curious to see some screenshots. You would have to use a VM for that though. I've not had this kind of trouble and I only use custom or manual partitioning. Usually though I already have my partition of choice already done before I enter the installer.

---

### Post by Podex on 2009-09-16
> **Bert Mariën said:**
> Everything installed okay, only the "mount" option in ubiqity does not really seem to work, meaning: it does not show after one has specified a mount point.

I had the exact same problem when I installed from a daily live cd (10 September). The checkbox in the Format column doesn't get checked either.
Due to another problem I didn't let it install though, so I can't say if it affected the install.

---

### Post by DougieFresh4U on 2009-09-16
Got the 'ubiquity' crashed box during the 'starting up partitioner' phase of install. But I made all my selections and it installed ok and all 4 partitions are there. This was a few days ago using an alpha 3 install DVD

---

### Post by Bert Mariën on 2009-10-11
I experience a new problem with the installation of karmic:
After installation of karmic ubuntu (i386) and reboot (grub2 on the root partition not mbr), karmic boots into a blank screen, halts, and can not be booted.

Tried it several times.
So I booted one of my other systems, and it started checking every linux system on my computer bacause of:
"contains a file system with errors, check forced".

At first I thought it was a one-time issue, but that changed when I installed Xubuntu karmic i386 two days later, and that installation gave me the exact very same issue.
Not being able to boot xubuntu and booting an other system stated about every linux partition I have: "contains a file system with errors, check forced".

There must be something wrong here!

---

### Post by kansasnoob on 2009-10-11
Are you now trying a new Beta disc?

---

### Post by Bert Mariën on 2009-10-11
Both were daily builds.

---

### Post by Bert Mariën on 2009-10-11
AFTER the beta was released.

---


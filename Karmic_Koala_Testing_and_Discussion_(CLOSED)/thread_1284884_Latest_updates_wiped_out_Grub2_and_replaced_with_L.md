---
title: "Latest updates wiped out Grub2 and replaced with Legacy"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by JCoster on 2009-10-07
Hi, I've just run a partial upgrade (shudder I know) upon request from update-manager and it wiped out my Grub2 and replaced it with Legacy when installing 2.6.31-12 headers.
It's not a problem as I booted up and reinstalled Grub2, but is this a bug or is it just because of the partial upgrade?

---

### Post by hgergo on 2009-10-07
do not force partil upgrades!

---

### Post by emarkay on 2009-10-07
Another one bitten by the "partial upgrade warning that is buried in the read this first sticky"...

I know it's there, but I knew days ago this needed a separate warning...

There are a number of threads on this for now, Just say "NO" to Partial Upgrades!

Let us know if this is fixed, and if it was the partial upgrade, mark this thread as "Solved", too.

---

### Post by rex4u on 2009-10-07
Same here also.
Had to reinstall Grub2. I wonder if they are planning to move back to Grub legacy after user complaints :-k

---

### Post by kansasnoob on 2009-10-07
> I wonder if they are planning to move back to Grub legacy after user complaints

I think that's very doubtful.

---

### Post by rex4u on 2009-10-07
> **kansasnoob said:**
> I think that's very doubtful.

I thought "Don't fix it if it ain't broken" ;)
Probabaly they would like to wait for Grub2 to come out of beta.

---

### Post by ranch hand on 2009-10-07
If you go to synaptic and look in your installed stuff and find "grub", remove it, it is left over from Jaunty.

Sometimes this stuff does not get cleaned up.

I saw that it was going to update that and went and removed it.  Reran apt-get update and there was no more mention of "grub" just the grub2 stuff we need.

---

### Post by kansasnoob on 2009-10-07
> **rex4u said:**
> I thought "Don't fix it if it ain't broken" ;)
Probabaly they would like to wait for Grub2 to come out of beta.

I reverted to legacy grub for now with no real problem, well updates keep hosing the functionality of startupmanager, but a "--purge remove" of grub-common followed by a reinstall of grub-common, grub, and startupmanager always seems to sort it out.

---

### Post by ronacc on 2009-10-07
the replacement of grub2 by grub legacy is not necessairly a partial upgrade , I just updated a brand new box that has a fresh install of karmic (at A4 and updated daily ) , this is on a new drive in a new box , never had any other install , and it still removed grub2 and replaced it with grub and this was a straight update not a partial upgrade .

---

### Post by whoop on 2009-10-07
I reported this as a bug:
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/445653](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/445653)

---

### Post by jppr on 2009-10-07
i have installed only grub-common and grub-pc. synaptic is this text in grub 2... This is a dummy transitional package to handle GRUB 2 upgrades.  It can be
safely removed.

---

### Post by whoop on 2009-10-07
> **jppr said:**
> i have installed only grub-common and grub-pc. synaptic is this text in grub 2... This is a dummy transitional package to handle GRUB 2 upgrades.  It can be
safely removed.
Not sure if you are asking a question :-p but if you are using grub2 and you have upgraded from grub1 and you want to do a safe dist-upgrade, you need to remove "grub".

Or wait until it gets fixed...
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/445653](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/445653)

---

### Post by mick222 on 2009-10-07
> the replacement of grub2 by grub legacy is not necessairly a partial upgrade , I just updated a brand new box that has a fresh install of karmic (at A4 and updated daily ) , this is on a new drive in a new box , never had any other install , and it still removed grub2 and replaced it with grub and this was a straight update not a partial upgrade .

 Same here Installed karmic from beta 6 everything went well until today.I checked it was a distribution upgrade grub2 has gone, had to boot to intrepid on another hdd. How can i boot to Karmic as grub doesn't seem to see it and i cant mount the partition in intreid as it is ext4.

---

### Post by kansasnoob on 2009-10-07
Look here:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

You probably need to apt-get install grub-pc and update-grub.

If that's even slightly puzzling ask more questions!

You must mount the right partition or you'll likely just cause more problems!

Edit, to anyone reading this: it may also be necessary to run "grub-install <proper device>", example:
"grub-install /dev/sda". If you're unsure where to "install" grub ask more questions!

---

### Post by mick222 on 2009-10-08
HI thx for the advice tried to mount my karmic partition get this error
>  can't find /dev/sdb1/mnt in /etc/fstab or /etc/mtab

 I can mount it from places menu

---

### Post by JCoster on 2009-10-08
> **emarkay said:**
> Another one bitten by the "partial upgrade warning that is buried in the read this first sticky"...

I know it's there, but I knew days ago this needed a separate warning..

I read that but the only package it wanted to remove that I questioned was GRUB which I figured that if it gets borked I can just reinstall it.

Fixed now anyway.

---


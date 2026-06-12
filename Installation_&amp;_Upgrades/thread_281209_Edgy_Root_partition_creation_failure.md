---
title: "Edgy: Root partition creation failure"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by Blue1k on 2006-10-20
I wanted to do a clean install for Edgy RC, however, the installer fails to add a root partition even when I designate one. It gives a warning that there is No Root File system.

I tried the 64bit version and the 32bit version of Edgy RC but both give the same error. I made sure to check md5sums and I also tried a slow burning speed but the error is still there.

I thought the RC was free of installer bugs?

P.s. My hard disk is regular SATA.

---

### Post by ReaderRat on 2006-10-20
NooB here - Just a thought:
I believe / is your root partition, and it is created during installation. You don't have to designate it. You can, however, do a /home, etc partitions.

---

### Post by Kateikyoushi on 2006-10-20
Did you select a filesystem for that partition ? Ext3 or whatever you fancy.

---

### Post by Blue1k on 2006-10-21
Yes..I have done about 100 installs so far with a variety of Distros, so I'm pretty familiar with what I have to do:p 

The problem is it won't recognize any reiser partitions. However, if I reformat as ext3 and then select my / , /home, /swap it then will proceed.

But it keeps dying in the middle of the install.

Somethings wrong with this installer. Dapper works perfect with both 386 and 64bit.

---

### Post by eurgain on 2006-10-24
This is a known bug (40287, and others).

WARNING:  Horrid kludge follows.

To install the RC (but not fix the problem) before starting the installer, edit the file /usr/lib/ubiquity/ubiquity/validation.py .

Near the end of the file, you will find the following code:

```
if not root:
  result.add(MOUNTPOINT_NOROOT)
```

Change this to

```
if not root:
  pass
```

For those not familiar with Python, the indentation is required!

This turns off the check for a root filesystem, so make damned sure that you allocate one in the installer!  As I said, it is a kludge, so use at your own risk.

Regards
Alistair

---

### Post by ariel on 2006-10-26
Thanks for the tip. I am installing Edgy final and I had to use it, otherwise the installer kept complaining "no root partition" even if I selected one.

I am kind of disappointed that such a basic problem with the installer went through the quality control. It's really weird, as this just does not seem to be related to hardware detection or anything like that, just a buggy installer script.

---

### Post by airwolf on 2006-10-26
Thank you for that tip. I was doing a fresh install and ran into the same problem as well.

---

### Post by edwin11 on 2006-10-26
[FONT="Verdana"][SIZE="2"][COLOR="Navy"]Thanks for this! It helped me too.

Very disappointed, to say the least. [-( 



Regards,
Edwin
[/COLOR][/SIZE][/FONT]

---

### Post by ariel on 2006-10-26
> **ariel said:**
> Thanks for the tip. I am installing Edgy final and I had to use it, otherwise the installer kept complaining "no root partition" even if I selected one.

I am kind of disappointed that such a basic problem with the installer went through the quality control. It's really weird, as this just does not seem to be related to hardware detection or anything like that, just a buggy installer script.

After installling edgy in my laptop and desktop, I have to say that the thousand new details, updated apps and great usability improvements more than outbalance the initial disappointment. The ubuntu team put a LOT of work here and  this is visible everywhere. And the problem only occured in the laptop, which has a SATA disk.

For example I installed beryl in both machines with essentially three commands...and  I remember well how difficult it was to get compiz working 6 months ago!

---

### Post by Blue1k on 2006-10-29
Well. I tried installing Kubuntu 6.10 and the installer is still crap.

It now fails to read any of my partitions and can't do a manual partition install or "use whole disk" install. 

This is ridiculous to have such an error present in a non-RC release.

This bug has been well noted but yet nothing has been done (at least it seems) to address this problem. 

I have been a long-time Ubuntu/Kubuntu fan and I'm surprised that something like this would happen. Please fix this!!
:mad:

*Edit: whole disk install worked

---


---
title: "No Root Filesystem"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by Veneficus Esculentus on 2010-03-28
Hi, I'm semi-new to Ubuntu, but I'm having trouble installing it on a "new" computer that I found at Goodwill for $60 with no operating system on it. When I go to edit the partitions, it won't let me do anything due to an apparent lack of a root filesystem. (I know this issue has been brought up and resolved in the past, but the usual solution (going into the validation.py file) isn't working for me, as there is no line in this one that says "if not root".) Can somebody please help?

---

### Post by presence1960 on 2010-03-28
highlight the partition. Right click and choose "edit" for 9.04 or older ubuntu or "change" for 9.10 or newer ubuntu. Select filesystem (ext3, ext4, etc). At mount point select / from the drop down box for the partition which ubuntu is being installed onto. You should now be able to proceed with the install for you have just defined the root (/) partition.

---

### Post by Veneficus Esculentus on 2010-03-28
Wait, I should've mentioned that nothing showed up on the partition screen thing during the install. (I'll take a snapshot and upload it ASAP so that you can see for yourself) 

EDIT: Oh, and when I right-click anywhere, it only gives me the option to revert, which basically ends up doing nothing.

---

### Post by stlsaint on 2010-03-28
Boot into the livecd and go to the System>admin>Partition editor application to view all partitions and hdd's on the system. There you can create/delete/edit all partitions that you want specified. Then you dont have to do it on the install portion. Or you could just use the "use whole disk option" at the install menu. It appears you went to setup partitions manually during install. You must AT A MINIMUM have a swap partition and a root (/) partition to install ubuntu.

---

### Post by Veneficus Esculentus on 2010-03-28
The weird thing is that there's no HDD or anything showing up at all. Then again, I have no idea what the previous owner did to this, as I picked it up at Goodwill for $60. Again, I'll get pictures up shortly.

And yes, I've booted into the CD. It's the only thing that I could boot into, as there was no OS on it when I got it. (I realized that when I first turned it on when I brought it home.)

---

### Post by Megafag on 2010-03-28
> **Veneficus Esculentus said:**
> The weird thing is that there's no HDD or anything showing up at all. Then again, I have no idea what the previous owner did to this, as I picked it up at Goodwill for $60. Again, I'll get pictures up shortly.

And yes, I've booted into the CD. It's the only thing that I could boot into, as there was no OS on it when I got it. (I realized that when I first turned it on when I brought it home.)

have you checked if the computer even has a HD?

---

### Post by Veneficus Esculentus on 2010-03-28
Why wouldn't it have one? Well, other than if it was taken from it (which I see no evidence of tampering). Although, perhaps a virus may have completely wiped it out and rendered it completely useless?

---

### Post by Megafag on 2010-03-28
> **Veneficus Esculentus said:**
> Why wouldn't it have one? Well, other than if it was taken from it (which I see no evidence of tampering). Although, perhaps a virus may have completely wiped it out and rendered it completely useless?

For 60 bucks i wouldnt rule out someone leaving **** out of it. are you very good with taking stuff apart?

---

### Post by Veneficus Esculentus on 2010-03-28
Nope.

---

### Post by Megafag on 2010-03-28
> **Veneficus Esculentus said:**
> Nope.

If the computer isnt under warranty or anything then get one of your nerdy friends to get inside it and check if it actually has a harddrive.

i could be completely wrong mind you.

---

### Post by Veneficus Esculentus on 2010-03-28
Under warranty? Hah. This thing's warranty probably expired no earlier than 5 years ago. It's so old that it actually has a built-in floppy drive. But it's not obscenely old. (It has a "Designed for Windows XP" sticker on it.) So, yeah, I think I'll do that.

---

### Post by adam814 on 2010-03-28
Viruses can't render the hard drive useless to the point that it doesn't show up in GParted.  In fact, in every case I've seen even a failing hard drive shows up, just reads/writes fail on it.

I wouldn't rule out the possibility of it having been removed.  People are paranoid enough when selling a computer to someone, let alone donating it to GoodWill.  Sure, overwriting the drive several times with zeros/random data/etc would protect their privacy fine some people either out of ignorance or paranoia actually remove the disk and smash it.

I even saw one case where a machine left on the curb for trash pickup was missing the side panel and it looked like the owner had taken a hammer to every visible part inside.

---

### Post by Megafag on 2010-03-28
> **adam814 said:**
> I even saw one case where a machine left on the curb for trash pickup was missing the side panel and it looked like the owner had taken a hammer to every visible part inside.

:O dont people know that SOME PEOPLE might want to use machines like that to prove to others how awesome linux is!!

The bastards.

---

### Post by Veneficus Esculentus on 2010-03-29
But I thought a computer needed an HDD for it to even start its own BIOS.

---


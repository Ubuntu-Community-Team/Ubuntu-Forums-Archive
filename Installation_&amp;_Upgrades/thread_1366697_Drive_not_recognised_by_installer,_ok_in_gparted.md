---
title: "Drive not recognised by installer, ok in gparted"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by dez93_2000 on 2009-12-28
Hi all. Broke up a 2x500gb sata raid1 mirror into 2 identical drives, formatted the second clean, first still has an xp install. Looking to install ubuntu 9.10 to the second (20gb /, 20gb /home, 2.5gb /swap) with the rest as ntfs for shared files.

I booted into the liveCD, into gparted, set the whole drive as unallocated, went into the ubuntu installer, manually partitioned installer, and it can't see the hard drive, at all. Just ain't there.

Then I went back into gparted and made an extended partition with 3 logicals beneath it ("/", "/home", "/swap"), and a primary partition after it with all of the rest of the space as ntfs. All looked great. Still not recognised.

Tried with the whole thing as ntfs, nothing. Noticed all the other drives were flagged as boot, flagged it as boot, nothing.

Any ideas? Long story short: blank drive recognised & editable in gparted but doesn't show up in ubuntu installer. Thanks in advance.
:confused:

Also, off topic, can i install 64-bit using the standard liveCD or do i need the alternate? The alternate doesn't seem to allow one to try linux. I don't know if i really need to install that way, but i'm following a guide which does it that way...

---

### Post by jSalv on 2009-12-28
Maybe try ext3/4?

Raids are something complicated too, don't understand much about that, so bear with me if I am completely wrong with something :D

---

### Post by dez93_2000 on 2009-12-28
don't know why i didn't try doing the whole thing as ext4 just in case, tho the installer recognises all th ntfs windows drives just fine and they're not ext...

---

### Post by audiomick on 2009-12-28
Hallo.
I have seen a number of posts indicating that RAID "relics" can cause problems. There is a command to remove them, but I don't know it. I will have a bit of a search; maybe I can find something.

---

### Post by raymondh on 2009-12-28
> **dez93_2000 said:**
> Hi all. Broke up a 2x500gb sata raid1 mirror into 2 identical drives, formatted the second clean, first still has an xp install. Looking to install ubuntu 9.10 to the second (20gb /, 20gb /home, 2.5gb /swap) with the rest as ntfs for shared files.

I booted into the liveCD, into gparted, set the whole drive as unallocated, went into the ubuntu installer, manually partitioned installer, and it can't see the hard drive, at all. Just ain't there.

Then I went back into gparted and made an extended partition with 3 logicals beneath it ("/", "/home", "/swap"), and a primary partition after it with all of the rest of the space as ntfs. All looked great. Still not recognised.

Tried with the whole thing as ntfs, nothing. Noticed all the other drives were flagged as boot, flagged it as boot, nothing.

Any ideas? Long story short: blank drive recognised & editable in gparted but doesn't show up in ubuntu installer. Thanks in advance.
:confused:

Also, off topic, can i install 64-bit using the standard liveCD or do i need the alternate? The alternate doesn't seem to allow one to try linux. I don't know if i really need to install that way, but i'm following a guide which does it that way...

Try removing dmraid from the installer.  Boot the liveCD and go live session.  Access terminal

```
sudo apt-get remove dmraid
```

Exit terminal and proceed to install.  See if Ubiquity will recognize.

---

### Post by audiomick on 2009-12-28
> **raymondh said:**
> Try removing dmraid from the installer.  Boot the liveCD and go live session.  Access terminal

```
sudo apt-get remove dmraid
```

Exit terminal and proceed to install.  See if Ubiquity will recognize.

you're too fast Raymond...;) I just spent 10 minutes looking for that.

---

### Post by dez93_2000 on 2009-12-29
Cheers Mick & Ray, will try when I get home Thursday (actually, NYE, no I won't!).
2 quick Qs:
 
1. will "sudo apt-get remove dmraid" screw anything up, possibly? I'm not in RAID anymore so I can't see why it would....but just in case?
 
2. was going to fall into the 'people are replying quickly, this is almost like a conversation' trap of asking what Ubiquity was, without googling first. Cardinal Sin avoided! Apparently it's a jazz, hiphop, funk & soul record label, based out of San Francisco. Imagine the mistakes I might have made if I instaled ithout knowing that - phew! :mrgreen:

---

### Post by raymondh on 2009-12-29
> **dez93_2000 said:**
> Cheers Mick & Ray, will try when I get home Thursday (actually, NYE, no I won't!).
2 quick Qs:
 
1. will "sudo apt-get remove dmraid" screw anything up, possibly? I'm not in RAID anymore so I can't see why it would....but just in case?
 
[COLOR="Red"]If you still had RAID, then removing dmraid will be problematic as the installer cannot/will not define your partitions or bounderies.  Since you don't have RAID anymore, there should be no problems

Sometimes, DMRAID can be buggy and cause the installer NOT TO SEE/IDENTIFY partitions hence the suggestion to try to remove dmraid.[/COLOR].



Regards,

---


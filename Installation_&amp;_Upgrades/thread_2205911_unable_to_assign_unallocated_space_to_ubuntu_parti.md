---
title: "unable to assign unallocated space to ubuntu partition"
date: 2014-02-16
forum: Installation &amp; Upgrades
---

### Post by jrmchess on 2014-02-16
below is my file system. I have xp on sda1 which I have shrunk to get unallocated space to extend my ubuntu partition. Unfortunately I am unable to resize any of the partitions using gparted even though I have booted into live ubuntu from a usb drive. Any solutions??? thanks

[IMG]http://i62.tinypic.com/2nhf2v7.png[/IMG]

---

### Post by grahammechanical on 2014-02-16
Do you see those key icons alongside sda3, sda5 and sda6. You need to remove those key icons somehow. There should be some kind of option in the Gparted menu system. 

Also, sda3 is the extended partition. You cannot resize sda5 until you expand/resize sda3. That will create space inside sda3 for sda5 to be resized into.

Regards.

---

### Post by jrmchess on 2014-02-17
> **grahammechanical said:**
> Do you see those key icons alongside sda3, sda5 and sda6. You need to remove those key icons somehow. There should be some kind of option in the Gparted menu system. 

Also, sda3 is the extended partition. You cannot resize sda5 until you expand/resize sda3. That will create space inside sda3 for sda5 to be resized into.

Regards.

they key icons appear because the drives are mounted. I took the screenshot after logging into ubuntu as I can't save screenshots or access internet while being booted from the live disk. I am trying to partition when I boot from the live usb so the the key icons will not be there. can u pls explain how I can resize sda5 and will it accept the unallocated space?

---

### Post by jrmchess on 2014-02-17
> **grahammechanical said:**
> Do you see those key icons alongside sda3, sda5 and sda6. You need to remove those key icons somehow. There should be some kind of option in the Gparted menu system. 

Also, sda3 is the extended partition. You cannot resize sda5 until you expand/resize sda3. That will create space inside sda3 for sda5 to be resized into.

Regards.

I tried what u said and this what I'm getting...

[IMG]http://i58.tinypic.com/24pfj3c.png[/IMG] 

does this mean I have successfully resized my partition. how do I check it? (I think it's done... Thank you so much but I need you to confirm it)

---

### Post by Bashing-om on 2014-02-17
jrmchess; Hi !

Looks good to me, I can see no faults - the numbers add up !

Have you "looked" at some of the files in various places in the file system ?
Have your tried a few of your applications ?
And the biggy -> if all looks good at this point, have you rebooted ? And came back up ?
--Windows included ! -

If yes to all the above, you done good ! Should be set to go.

[INDENT][INDENT]prior prudent planning preventing pi## poor performance
[/INDENT][/INDENT]

---


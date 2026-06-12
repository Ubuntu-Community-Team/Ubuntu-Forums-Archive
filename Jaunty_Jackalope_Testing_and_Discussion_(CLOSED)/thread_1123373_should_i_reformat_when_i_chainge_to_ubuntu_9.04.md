---
title: "should i reformat when i chainge to ubuntu 9.04"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jarrah-95 on 2009-04-12
i have been thinking about it because it is ment to be faster 
i need to no before i do it through if i can:
         install it to a real partition (as i have only got it in a virtual hard dirve (installed inside windows)) 
         move the programs from the old ubuntu (8.10) to the new one (9.04)
         split the partition the old ubuntu is on now, install the new ubuntu and then merge both partitions into one.

---

### Post by Partyboi2 on 2009-04-12
You can use [[COLOR=Blue]LVPM[/COLOR]]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?") to move ubuntu to its own partition. Then you can do the recommended  network upgrade to 9.04 which will upgrade all the Ubuntu packages to the current version in 9.04.

---

### Post by jarrah-95 on 2009-04-12
if i do that will i still be able to reformat to ext4 before i move it

---

### Post by inobe on 2009-04-12
i would do a fresh install of 9.04, i would never upgrade to a beta !

dual booting is much safer......

---

### Post by Partyboi2 on 2009-04-12
> **jarrah-95 said:**
> if i do that will i still be able to reformat to ext4 before i move it
I would suggest moving it first then afterwards convert to ext4, converting to ext4 should not erase you current data.

---

### Post by raymondh on 2009-04-12
I moved my files first. Actually, I moved them temporarily to an external HD.  Then, I did a fresh install of 9.04 beta with ext4 and moved files back.

So far so good.

Enjoy.

Raymond

---

### Post by jarrah-95 on 2009-04-14
i thorught that if you installed ubuntu then feformatted then you whould have all of your data wiped

---

### Post by Sef on 2009-04-14
> i thorught that if you installed ubuntu then feformatted then you whould have all of your data wiped


You wipe out the partition that you set to be reformat.  If you did not set your home partition to be reformated, then it won't be.

---

### Post by Partyboi2 on 2009-04-14
> **jarrah-95 said:**
> i thorught that if you installed ubuntu then feformatted then you whould have all of your data wiped
Reformatting does wipe your data but if you are converting from ext3 to ext4 filesystem you can do it without loosing your data.

---

### Post by silentrebel on 2009-04-14
> **jarrah-95 said:**
> ...install the new ubuntu and then merge both partitions into one.
Be careful, I don't think you can merge two formatted partitions.  You would probably have to delete one of the paritions then extend the other to take advantage of the freed space.

---


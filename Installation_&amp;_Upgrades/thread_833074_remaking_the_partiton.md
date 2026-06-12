---
title: "remaking the partiton"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by shamguy4 on 2008-06-18
ok so i tried to install ubuntu on an external but i listened to 
So how can i start all over?
when I try to install throgh live cd it gives me errors?
how do i get rid of the old partition so I can make a new one?
please help

---

### Post by Pumalite on 2008-06-18
Use your gparted:
sudo aptitude install gparted
Delete everything in your external, make one large 'free space' and the make a partition of the whole drive formatted ext3. Reinstall.

---

### Post by shamguy4 on 2008-06-18
no wait... i have some vids and stuff under i think ntfs... so i dont want to get rid of everything...
I want to put ubuntu onto my external hard drive but not the whole thing.. just whats needed... I set aside 20 Gb for ubuntu using guided and it worked... but then I wasnt able to boot into my hard drive cause grub claimed it couldnt find partitions... so i played around and messed up...
Now i want to start over but guided says theres an error

---

### Post by Pumalite on 2008-06-18
Make your yourself a partition for Ubuntu with gparted. Install, go Manual and point to that partition.

---

### Post by shamguy4 on 2008-06-18
...and where do i place the boot loadr? on my external right?

---

### Post by Pumalite on 2008-06-18
Right. Step 7 or 8 of the installation: 'Advanced Tab'. Replace (hd0) for /dev/???
Where ??? is your USB
You can find out with:
sudo fdisk -lu

---

### Post by shamguy4 on 2008-06-18
ok.. so i did it all... now when i restart the comp and boot into grub it shows up different ubuntus which is good!! (ubuntu, ubuntu recovery...)
but when i press enter it says error 22 no such partition??
so i pressed "e" to see where im booting and i using hd1,5 ???

---

### Post by shamguy4 on 2008-06-18
i change hd1,5 to hd0, 5 and it worked!!!
nice ..dont even know what i did but yeah!!!

---

### Post by Pumalite on 2008-06-18
Congrats.

---


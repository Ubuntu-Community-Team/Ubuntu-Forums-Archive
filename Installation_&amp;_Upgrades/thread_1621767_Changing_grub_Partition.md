---
title: "Changing grub Partition"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by Giveingitago on 2010-11-14
Hi,
There are many threads on this subject but I'm nervous about changing the boot process without knowing exactly what I'm doing.

I have my main OS 10.04 installed on my netbook and thought I'd test the new 10.10 Netbook remix. I created some new partitions and installed. The new install has taken over the boot process and I want to now return the boot process back my original 10.04 install. i.e 
Running the boot script:

"Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #10 for (,msdos10)/grub."

I want to be able to change the boot process so that Grub 2 looks at partition #5.

Results.txt file attached.

Thanks in advance.

Dave

Results.txt file is to large to upload will trim down.

---

### Post by drs305 on 2010-11-14
Just boot into the Ubuntu version you want, then run the following command:
```

sudo grub-install /dev/sda

```

If you are in the one you don't want to be the default:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda5
```
Don't include the partition number in the second command.

PS: Couldn't find  the attached RESULTS.txt

---

### Post by Giveingitago on 2010-11-14
DRS305,
Thanks the first code item worked fine. Problem solved.

I had a slight problem with the Results text file being 24.5 K in size exceeding the 19.5K upload limit. 

Cheers

Dave

---


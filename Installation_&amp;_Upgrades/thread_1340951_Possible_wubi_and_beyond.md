---
title: "Possible wubi and beyond"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by texas.chef94 on 2009-11-29
My partitioning below may seem laughable and based on what I have learned since I would do it differently. I like the 3 OS systems I have and want to keep them, but I am doing research for the town I live in that would be suited better on its own partition as my data1 cannot stand the space required to accommodate this research.
My question is 2 fold can I delete sda6 which is Ubuntu without disturbing my boot sequence and create an additional data partition?
I know I can reinstall Ubuntu with the wubi process and I have 25 unused GB enough to hold Ubuntu and still have 8 GB leftover.
Please someone answer the above, and I do not need any suggestions about an external as I already have 160 GB one in another endeavor (and not smart enough to deal with a second USB and configuring).
I went into this detail to assure the possible user response know where I coming from. Just call it an almost 80 year olds folly.

sda1 Windows XP                 boot
sda2 Extended
sda3 Lenny
sda5 Swap
sda6 Ubuntu
sda7 Mint
sda4 data1

Please advise and thanks

---

### Post by phillw on 2009-11-29
You seems to have 4 OS's ? XP, Lenny, Ubuntu & Mint ?

Can you post the output of ```
 df -ah | grep dev 
```

Regards,

Phill.

---

### Post by texas.chef94 on 2009-11-29
> **phillw said:**
> You seems to have 4 OS's ? XP, Lenny, Ubuntu & Mint ?

Can you post the output of ```
 df -ah | grep dev 
```

Regards,

Phill.

Here you go Phill. Hope this helps and I know request sounds strange

allen@allen-laptop:~$  df -ah | grep dev
/dev/sda6              11G  6.6G  3.1G  69% /
udev                  470M  248K  470M   1% /dev
none                     0     0     0   -  /dev/pts
none                  470M  1.2M  469M   1% /dev/shm
allen@allen-laptop:~$

---

### Post by phillw on 2009-11-29
> **texas.chef94 said:**
> Here you go Phill. Hope this helps and I know request sounds strange

allen@allen-laptop:~$  df -ah | grep dev
/dev/sda6              11G  6.6G  3.1G  69% /
udev                  470M  248K  470M   1% /dev
none                     0     0     0   -  /dev/pts
none                  470M  1.2M  469M   1% /dev/shm
allen@allen-laptop:~$

Not at all wierd.  can you go into "Places", mount the other areas and repeat the command (They're not automounting - I just what to see what space you've got where)

Or, if you're familiar with partition manager / Gparted - the results from what it says used & free areas are.

Thanks,

Phill.

---

### Post by texas.chef94 on 2009-11-29
> **phillw said:**
> Not at all wierd.  can you go into "Places", mount the other areas and repeat the command (They're not automounting - I just what to see what space you've got where)

Or, if you're familiar with partition manager / Gparted - the results from what it says used & free areas are.

Thanks,

Phill.

OK I mounted EVERYTHING and I thank you

allen@allen-laptop:~$  df -ah | grep dev
/dev/sda6              11G  6.7G  3.1G  69% /
udev                  470M  264K  470M   1% /dev
none                     0     0     0   -  /dev/pts
none                  470M  188K  470M   1% /dev/shm
/dev/sda4              55G  3.5G   48G   7% /media/data1
/dev/sdb1              59G  181M   56G   1% /media/eea39851-3363-4da3-bff6-bc72ace28f69
/dev/sdb2              88G  3.7G   80G   5% /media/d6e1fe6d-2f3f-4da4-9a33-d5e39bd0c632
/dev/sda1              53G  8.3G   44G  16% /media/XP
/dev/sda7              13G  9.7G  2.6G  79% /media/MINT
/dev/sda3              17G  3.2G   13G  21% /media/Lenny
allen@allen-laptop:~$

---

### Post by phillw on 2009-11-29
> **texas.chef94 said:**
> OK I mounted EVERYTHING and I thank you

allen@allen-laptop:~$  df -ah | grep dev
/dev/sda6              11G  6.7G  3.1G  69% /
udev                  470M  264K  470M   1% /dev
none                     0     0     0   -  /dev/pts
none                  470M  188K  470M   1% /dev/shm
/dev/sda4              55G  3.5G   48G   7% /media/data1
/dev/sdb1              59G  181M   56G   1% /media/eea39851-3363-4da3-bff6-bc72ace28f69
/dev/sdb2              88G  3.7G   80G   5% /media/d6e1fe6d-2f3f-4da4-9a33-d5e39bd0c632
/dev/sda1              53G  8.3G   44G  16% /media/XP
/dev/sda7              13G  9.7G  2.6G  79% /media/MINT
/dev/sda3              17G  3.2G   13G  21% /media/Lenny
allen@allen-laptop:~$

Riiiiiiggght ......

sdb, I'm surmising, your usb drive, has about 120GB total free space. between its 2 partitions.

You have generously given XP 53Gb and it is only using 8.3GB of that - I'd be tempted to shave 40GB off that partition - leave it as unallocated space, then reboot into XP (XP is notorious for squealing like a scalded pig when it is resized - defrag it 1st & it'll also want 2-3 chkdsks on botting before it settles down).
You can then grow sda4 into this area boosting it to 95 GB. Your linux installs are only on 11 GB, 13GB and 17GB partitons - which is only 40GB if you got rid of them all !!!

It goes without saying ... backup the XP area before you resize it !!

hope that helps.

One of the best HowTo's I've come accross is here ... [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Have a read through the introduction, then head to 'real life examples' - your'e running on sda and specifically sda1 for the Shrink and sda4 for the Grow

If you're unsure of backing up your XP area - then this will do it for you, hopefully we won't need it !!

```
  cd /media/sda1
cat "tar cvpzf backup.tgz --exclude=/backup.tgz /media/sda1/" > backup.media.sh
sh backup.media.sh
mv backup.tgz /dev/sdb1

```in the cat tar ...   it is **- - exclude** (2 minus signs WITHOUT a space between them !!
the sh backup.media.sh will take a while to run - It'll scroll the files up the screen as it goes !

once everything is up and running you can safely ```
 rm /dev/sdb1/backup.tgz 
```

Regards,

Phill.

---


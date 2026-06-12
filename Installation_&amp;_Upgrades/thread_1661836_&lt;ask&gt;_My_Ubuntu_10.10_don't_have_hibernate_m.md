---
title: "&lt;ask&gt; My Ubuntu 10.10 don't have hibernate mode"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by Matadewa on 2011-01-07
hi all. . .
i wonder why my ubuntu 10.10 don't have hibernate mode, as i remember in my previous install ubuntu 10.10 (in sama notebook) it's available
i already don't have hibernate mode since, i format my last install ubuntu because driver vga. . . so i think it's not because not compatible software
if it's hidden by somethings or bug how to show it again?

---

### Post by plucky on 2011-01-07
> **Matadewa said:**
> hi all. . .
i wonder why my ubuntu 10.10 don't have hibernate mode, as i remember in my previous install ubuntu 10.10 (in sama notebook) it's available
i already don't have hibernate mode since, i format my last install ubuntu because driver vga. . . so i think it's not because not compatible software
if it's hidden by somethings or bug how to show it again?

Most likely you have not mounted the swap partition.Open a terminal and post output of ```
free -m
``` will tell us if the swap partition is mounted.

If not post output of ```
sudo blkid
sudo fdisk -l
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
```


Good luck

---

### Post by sikander3786 on 2011-01-07
Your Swap partition should be greater than or at least equal to the amount of RAM ;-)

Please post the output of this command.

Applications > Accessories > Terminal:

```
free -m
```

---

### Post by Matadewa on 2011-01-07
> **sikander3786 said:**
> Your Swap partition should be greater than or at least equal to the amount of RAM ;-)

Please post the output of this command.

Applications > Accessories > Terminal:

```
free -m
```

i already set my swap 2x ram
my ram is 3gb so my partition for swap is 6gb

this is code for "free -m"
             total       used       free     shared    buffers     cached
Mem:          2688        979       1709          0         82        482
-/+ buffers/cache:        413       2275
Swap:         5999          0       5999

---

### Post by Matadewa on 2011-01-07
i'm waiting for answer :)
sory just for this threat not too deep in list

---

### Post by plucky on 2011-01-08
> **Matadewa said:**
> i'm waiting for answer :)
sory just for this threat not too deep in list

It would be helpful if you posted the information requested in post #2 as it seems your swap partition is mounted > Swap: 5999 0 5999 

---

### Post by Matadewa on 2011-01-08
sory for my bad atitude before
i just read for sintaks free -m

this is the code 
```
matadewa@matadewa-notebook:~$ sudo blkid
/dev/sda1: UUID="a8b0b815-4f1a-4893-b917-4ecbae7ed936" TYPE="ext4" 
/dev/sda2: LABEL="Swap" UUID="8cc28e62-eccc-43e5-8a0d-0f8d3f98927a" TYPE="swap" 
/dev/sda3: LABEL="MyBackup" UUID="44CFF548775F8B19" TYPE="ntfs" 
/dev/sda4: LABEL="Tietha" UUID="6876BC4A76BC1AB0" TYPE="ntfs" 
matadewa@matadewa-notebook:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a8b0b815-4f1a-4893-b917-4ecbae7ed936 /               ext4    errors=remount-ro 0       1
/dev/sda2    none            swap    sw        0        0
/dev/sda3     /media/MyBackup     auto     ntfs,umask=000 0 0 
/dev/sda4    /media/Tietha        auto    ntfs,umask=000 0 0

matadewa@matadewa-notebook:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=47ed0764-0019-4d04-816b-9226db0af5cb

```

i already try check if my OS support hibernate mode or not
with code 
```
pm-is-supported --hibernate
echo $?
pm-is-supported --suspend
echo $?
```

and both of them give return value 0 which mean supported right?

but when i try this code
```
pm-is-supported --suspend-hybrid
```
its' give return value 1, which mean not supported

then i try to enter hibernate mode with terminal by 
```
pm-hibernate
```
and it's works
but in top right toolbar it's still don't have list for hibernate
what is mean?

sory if this post too long
and sory again for my bad atitude

---

### Post by plucky on 2011-01-08
> /dev/sda2: LABEL="Swap" UUID="8cc28e62-eccc-43e5-8a0d-0f8d3f98927a" TYPE="swap" 


> RESUME=UUID=47ed0764-0019-4d04-816b-9226db0af5cb

You need to change the value of /etc/initramfs-tools/conf.d/resume
 to the value specified by the sudo blkid command, as that is what specifies where it should look to resume from hibernate.

Then reboot to use the new values.

Good Luck

---

### Post by Matadewa on 2011-01-08
sory i still don't too understand

this is default value of  /etc/initramfs-tools/conf.d/resume
```
RESUME=UUID=47ed0764-0019-4d04-816b-9226db0af5cb
```

i just change it to this
```
RESUME=UUID="8cc28e62-eccc-43e5-8a0d-0f8d3f98927a
```

or copy all, like this
```
/dev/sda2: LABEL="Swap" UUID="8cc28e62-eccc-43e5-8a0d-0f8d3f98927a" TYPE="swap"
```

thanks for reply

---

### Post by plucky on 2011-01-08
Change it to ```
RESUME=UUID=8cc28e62-eccc-43e5-8a0d-0f8d3f98927a
```
so that it knows where to go to reload the hibernate information.

Then reboot

Good luck

---

### Post by Matadewa on 2011-01-08
finally my hibernate mode back
thanks plucky

---


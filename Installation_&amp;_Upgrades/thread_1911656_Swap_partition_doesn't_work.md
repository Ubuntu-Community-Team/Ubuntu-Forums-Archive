---
title: "Swap partition doesn't work"
date: 2012-01-19
forum: Installation &amp; Upgrades
---

### Post by El Potro on 2012-01-19
Hello folks,

Just before the login screen I get this message:

```
The disk drive for LABEL=SWAP is not ready yet or not present. Continue to wait; or Press S to skip mounting or M for manual recovery

```

If you press M nothing happens, the message goes away an instant after it appears and supposedly it is booting normally after it.

I do have a swap partition, actually, fdisk -l gives:

```
Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0xe7f9e7f9

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1        4628    37174378+  83  Linux
/dev/sda2   *        4629        7941    26611672+   7  HPFS/NTFS
/dev/sda3            7942       11335    27254273    5  Extendida
/dev/sda4           11335       19457    65247997+   c  W95 FAT32 (LBA)
/dev/sda5            7942       11073    25157758+  83  Linux
/dev/sda6           11074       11334     2096451   82  Linux swap / Solaris


```

gnome-system-monitor shows that the swap partition is mounted, with 2 gb but it says that there hasn't been used any bytes. (used: 0 bytes)

I tried to swapoff /dev/sda6 and swapon /dev/sda6, but it's the same, the swap partition is not being used.

I didn't install Ubuntu nor any system on this computer, and I'm not allowed to change the file system, the partitions, etc.

It's strange because if I open gparted it can't read or recognize the partition table. So I see 150 (GB) non partitioned. But fdisk recognizes it, so it's strange really.

I'm using Ubuntu 10.04 on a netbook.

What should I do?

Thank you very much in advance.

---

### Post by BC59 on 2012-01-19
In your case I would backup everything and format the whole drive. These are not good signs.

---

### Post by El Potro on 2012-01-19
I wish I could, but I can't format it. I must keep the system the way it is (more or less), because otherwise I would have to give it back, it's a long story.

So perhaps if it was possible I could re-format only the swap partitions (the others must stay the way they are now). But as long as gparted doesn't recognize them, I don't know how that could be possible.

Maybe there is a way to use the swap partition the way it is?

---

### Post by BC59 on 2012-01-19
Try this from Disc Utility. Check if you can see all the partitions. Then unmount the swap and format it. Then mount it again. But I have the feeling that even Disc Utility doesn't recognize any more your partitions.

---

### Post by plucky on 2012-01-19
Open a terminal and post output of ```
free -m
sudo blkid
cat /etc/fstab
```

---

### Post by BC59 on 2012-01-19
If not, try to recover the partition with TestDsk:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by El Potro on 2012-01-19
Well, with palimpsest (aka Disk Utility) I could format it to ext4 first, rebooted, mounted it, nand worked fie. So I re-formatted it to swap. Now it gives me a UUID (before there was no UUID for this partition). So I added this UUID to the fstab, and viola, the boot up message is no longer showing up.

But anyway it seems that although it is mounted, swap is not being used at all, and I'm getting the feeling that it is not working properly. Nevertheless it is auto-mounted at start, and gnome-system-monitor shows that 0 bytes are being used from 2,0 GB.


This is the output of free -m:

```
            total       used       free     shared    buffers     cached 
Mem:           927        499        427          0         24        252
-/+ buffers/cache:        223        704
Swap:         2047          0       2047

```

Oh and fstab looks like this:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext3    errors=remount-ro 0       1
LABEL=DATOS    /media/DATOS    vfat    rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush    0    0
# swap was on /dev/sda5 during installation
UUID=519d2e96-b15f-4799-9662-ecad7c1f46e5 none            swap    sw              0       0

```

And this is the output of sudo blkid

```
/dev/sda1: UUID="61091c01-5a9d-4681-b1c1-dc95180ea318" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda2: LABEL="Sistema" UUID="7662624A62620F65" TYPE="ntfs"
/dev/sda4: LABEL="DATOS" UUID="4AF3-01B1" TYPE="vfat"
/dev/sda5: UUID="cff05bc6-801b-48ff-84f0-5d8db754ed95" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda6: UUID="519d2e96-b15f-4799-9662-ecad7c1f46e5" TYPE="swap" 
```

---

### Post by plucky on 2012-01-19
> But anyway it seems that although it is mounted, swap is not being used at all, and I'm getting the feeling that it is not working properly. Nevertheless it is auto-mounted at start, and gnome-system-monitor shows that 0 bytes are being used from 2,0 GB.


```
Swap:         2047          0       2047

```
Your swap is now working.Ideally you don't want the system to use swap, as accessing hard drives is slow compared with accessing memory.

Just think of it as a safety net in case you run out of memory.

Good Luck

---

### Post by El Potro on 2012-01-19
Well, are you so sure? Isn't there a way to test it to get sure it works properly?

---

### Post by BC59 on 2012-01-19
Swap is used when you copy something big, like a DVD. Try to copy-paste something with volume to check from the System Monitor if your system is using swap.

---

### Post by El Potro on 2012-01-19
System monitor shows no change when I copy several big (500mb) files through the home net (there is no dvd drive on this netbook), or if I copy all the contents from an entire 1 gb pendrive.

Is there another way? Or perhaps a more professional way to do it? There is memtest to test the ram, is there an automatized program to check the swap?

Thanks

---

### Post by plucky on 2012-01-19
You need to load programs into memory and run them before you get anywhere close to 2GB.

I had to open two operating systems in virtualbox before it got to 2GB as each OS was allocated 1Gb


Good luck

---

### Post by jerrrys on 2012-01-19
in terminal

cat /proc/swaps

---

### Post by El Potro on 2012-01-19
All the virtual machine thing will have to wait, it will take me a long time to set it up.

Meanwhile I typed cat /proc/swaps and this is what I got:

```

Filename                Type        Size    Used    Priority
/dev/sda6                               partition    2096444    0    -1

```

---

### Post by jerrrys on 2012-01-19
The output of that command is offset, but looks to me you have 2G of active swap.  Still getting that boot message?

---

### Post by El Potro on 2012-01-19
How can you tell I'm using two megabytes? I think that the number that starts with 2 is the size, and below used it says 0.

No, I don't get the boot message anymore. But still I never saw the swap being used -not even one byte-. That's what catches my attention. If I saw only one byte being used I'll consider this done. But as far as it is not being used at all, I think it is not working.

For example on my desktop computer I see the swap being used almost always, at least a bit, and the hardware specs are higher.

---

### Post by jerrrys on 2012-01-19
A typo, 2G meant to say

host@host:~$ cat /proc/swaps
Filename                     Type                     Size                       Used               Priority
/dev/sda5                    partition        1047548       11980         -1

I have 1G (1047548 of swap

and like plucky said, load it up for the ultimate test

---

### Post by El Potro on 2012-01-19
is there an alternative to installing a virtual machine? something cleaner, faster, nicer?

---

### Post by BC59 on 2012-01-19
A virtual machine is consuming a lot of resources. I tried it once in a netbook but it was very-very slow. These applications are for big machines.

---

### Post by jerrrys on 2012-01-19
[stressapptest  ]("http://manpages.ubuntu.com/manpages/oneiric/man1/stressapptest.1.html")

I have not used this app so can't tell you its condition.
[]("http://manpages.ubuntu.com/manpages/oneiric/man1/stressapptest.1.html")

---

### Post by jerrrys on 2012-01-19
> **BC59 said:**
> A virtual machine is consuming a lot of resources. I tried it once in a netbook but it was very-very slow. These applications are for big machines.

I run vBox on a dual core machine with good (not excellent) results.  Also could of been not properly setup up, that could give you a big performance hit.

---

### Post by El Potro on 2012-01-19
Thank you **jerrrys**, you are the man. stressapptest got my ram completely used and 200 mb of swap. It means **it works**.

Thank everybody very much, this is officially **SOLVED**.

---

### Post by jerrrys on 2012-01-19
Sorry, but not official yet :D

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---


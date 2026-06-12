---
title: "another Grub Win2k booting problem"
date: 2004-11-01
forum: Installation &amp; Upgrades
---

### Post by Caudata on 2004-11-01
First, I'm a total Linux noob so there might be some things I don't understand. When I get to Grub and select my Win2k partition I get the following, and it won't boot:

Booting 'Windows NT/2000/XP'
root   (hd0,0)
    filesystem type unknown, partition type 0x7
savdefault
makeactive
chainloader +1

Now I do have a strange setup. At the moment I'm having to boot off my slave partitioned as follows:
hdb1: Win2k
hdb2: ext3
hdb3: swap
For my setup would I want to replace the line:
root (hd0,0) with root (hdb,0) or (hdb,1)?

I know it's been mentioned that you should set the hard drive for LBA in the BIOS instead of auto (not sure what LBA is). In my BIOS I see no such setting for a switch to LBA, now is this something found in newer BIOS, and is it something I may have to set with the jumpers on the hard drive.  Thanks in advance for any help that can be provided.

                                                                                     -Caudata

---

### Post by Caudata on 2004-11-01
I found LBA and when I set it in the BIOS Grub won't even load through. I get the following: 
GRUB loading stage 1.5
GRUB loading-please wait...
Error 17

If I interepreted how to set the partition in GRUB to boot from correctly my hdb1 would be (hd1,0) under GRUB. I edited from the boot loader menu by highlighting windows and hitting e. I then edited the line root   (hd0,0) to say root  (hd1,0) and hit b to boot it. When I set that I received this message- error 21: selected disk does not exist.

---

### Post by cacofonix on 2004-11-01
[QUOTE=Caudata]First, I'm a total Linux noob so there might be some things I don't understand. When I get to Grub and select my Win2k partition I get the following, and it won't boot:

Booting 'Windows NT/2000/XP'
root   (hd0,0)
    filesystem type unknown, partition type 0x7
savdefault
makeactive
chainloader +1

Now I do have a strange setup. At the moment I'm having to boot off my slave partitioned as follows:
hdb1: Win2k
hdb2: ext3
hdb3: swap
For my setup would I want to replace the line:
root (hd0,0) with root (hdb,0) or (hdb,1)?

I know it's been mentioned that you should set the hard drive for LBA in the BIOS instead of auto (not sure what LBA is). In my BIOS I see no such setting for a switch to LBA, now is this something found in newer BIOS, and is it something I may have to set with the jumpers on the hard drive.  Thanks in advance for any help that can be provided.

-Caudata[/QUOTE]

Welcome to ubuntu Caudata 8) is windows installed on the first partition of your drive? ie /dev/hd*x*1 if so it would be root (hd0,0) if it is on /dev/hd*x*2 it would need to be root (hd0,1) etc.

Check with fdisk to make sure what partition windows is on. I dont know if this would cause the problem but you have a typo your missing an e in savdefault
good luck

cacofonix

---

### Post by Caudata on 2004-11-02
My win2k was partitioned as being on hdb1, because at the moment I'm booting off my slave drive. Would that still make the GRUB syntax hd0,0? Thanks for the welcome so far I like what I've seen. I'm actually a complete Linux noob, but I'm catching on. FYI-that was a typo. Thanks for the help!

                                                                                                 -Caudata

---

### Post by cacofonix on 2004-11-02
is windows on the slave drive or ubuntu?

---

### Post by Caudata on 2004-11-02
Windows and Ubuntu are on the same drive:

hdb1: windows
hdb2: ubuntu
hdb3: ubuntu swap

At the moment I'm booting only off hdb with those three partitions.

---

### Post by cacofonix on 2004-11-02
[QUOTE=Caudata]Windows and Ubuntu are on the same drive:

hdb1: windows
hdb2: ubuntu
hdb3: ubuntu swap

At the moment I'm booting only off hdb with those three partitions.[/QUOTE]

give this a try 
```

title=win2k
rootnoverify (hd1,0)
makeactive
savedefault
chainloader +1

```

I hope this helps Caudata

cacofonix

---

### Post by Caudata on 2004-11-02
[QUOTE=cacofonix]give this a try 
```

title=win2k
rootnoverify (hd1,0)
makeactive
savedefault
chainloader +1

```

I hope this helps Caudata

cacofonix[/QUOTE]



I tried the above and so far no dice this was the message GRUB gave me: 

Booting command list
title=win2k
Error 27: unrecognized command

What does the title command do? Win2k is the label I have on that partition.  Cacofnix thanks for your patience so far.

---


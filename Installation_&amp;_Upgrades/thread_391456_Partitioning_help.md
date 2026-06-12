---
title: "Partitioning help"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by Huesos on 2007-03-23
If you had 3 hard drives in your computer, (180gb + 80gb + 80gb) how would you mount the partitions? I want to use as much memory as possible for the storing of my own user files, but it seems impossible to combine the drives in this manner. The partitioner wont let me mount them all in "/home" and if I name them they are put there but become inaccessible for the storing of information. Can you help me to combine memory from the different drives and mount them all in /home so I don't have tons of memory not doing anything useful? 'Cause that would bug the hell out of me.

---

### Post by ffxr on 2007-03-23
i dont think that is possible.. not to my knowledge anyway...

you can mount the drives in your home directory after the install tho.. so u could have a something like this

180gb contains your ubuntu install... 

/home/$user/ <----- rest of the 180gb drive
/home/$user/mp3 <-------- pointing at your 1st 80gig drive
/home/$user/documents  <---------------  pointing at your 2nd 80gig drive

---

### Post by Huesos on 2007-03-23
But how do I mount them after the install? I am a total newb so you'll have to explain it to me step by step. :/ Because I went in to "computer", right clicked the hard drives and pressed "mount", but it said it couldn't. Please help me with this, I've been at it trying to figure how to make this work since yesterday.

---

### Post by Huesos on 2007-03-23
The two other hard drives are currently installed in /media... but I can't do **** with 'em... can't paste one single file. How do I change their directories to do what you said and how can I enable them to be used in a way that you would expect to from a hard drive... you know, storing information and stuff..?

Honestly, I thought Linux Ubuntu would be alot easier from what I've heard recently... and now, whenever I try to re-install it... none of my live-cd's work the way they used to. Very dissapointing...

---

### Post by ffxr on 2007-03-23
i dont use GNOME and i think there is a GUI in GNOME to do this, BUT.. ll try to walk you through this manually..  can you paste back here the result of... 

```
 sudo fdisk -l 
```

---

### Post by Huesos on 2007-03-23
It asked me for a password, I wrote it in, it didn't appear. But this did:
Tell me if you need a translation. :)

----------------------------------------------------

Disk /dev/sda: 200,0 GB, 200049647616 byte
255 huvuden, 63 sektorer/spår, 24321 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1               1       24321   195358401   83  Linux

Disk /dev/sdb: 80,0 GB, 80026361856 byte
255 huvuden, 63 sektorer/spår, 9729 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/sdb1               1        9729    78148161   83  Linux

Disk /dev/hdc: 80,0 GB, 80026361856 byte
255 huvuden, 63 sektorer/spår, 9729 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/hdc1   *           1        3311    26595576   83  Linux
/dev/hdc2            9136        9729     4771305    5  Utökad
/dev/hdc3            3312        9135    46781280   83  Linux
/dev/hdc5            9136        9729     4771273+  82  Linux växling / Solaris
------------------------------

---

### Post by ffxr on 2007-03-23
ok your two 80gig disk drives are /dev/sda1 & /dev/sdb1

they seem to be already formatted? can u confirm this.. ?
we might need to go back and od this later if we have problems.. 

ok so.. create 2 folders in your home directory of names you would like eg disk1 & disk2

then open your file systems table settings.. 

```
 gksu gedit /etc/fstab 
```

add these lines to bottom of the file: 
```

/dev/sda1   	/home/$username/disk1     ext3    defaults,errors=remount-ro
/dev/sdb1       /home/$username/disk2     ext3    defaults,errors=remount-ro 
```

$username = your user id & disk1 & disk2 coresponds with the names of them directories you made earlier, can be anything of your choosing remember...

** we might need to go back a format these disks in ext3, if there is a problem, i cant tell if they already formatted in ext3 for sure *** 

save & close the file.

issue this command to reload your disk partitions.

```
 sudo mount -a 
```

hopefully that will give no errors.. then you can paste the results of the following command:

```
 mount 
```

so we can check that everything worked ok..

---

### Post by Huesos on 2007-03-23
"
mount: monteringspunkten /home/$username/disk1 finns inte
mount: monteringspunkten /home/$username/disk2 finns inte
"

Finns inte = does not exist... yet I created the two directories in the home folder, in my user folder. :/

I couldn't do it directly in the homefolder cause it wont allow me to... so I assumed you meant under my user folder.

---

### Post by ffxr on 2007-03-23
your not quite understanding the theory here: 

so imagine this:

you have a system with /home/huesos/

i create two directories for my disks e.g myharddiskone & myharddisktwo

so i have a directory structure like this:

 /home/huesos/myharddiskone
 /home/huesos/myharddisktwo

then in  ```
 gksu gedit /etc/fstab 
```

these have to match this directory structur, so:: 

```

/dev/sda1   	 /home/huesos/myharddiskone     ext3    defaults,errors=remount-ro
/dev/sdb1        /home/huesos/myharddisktwo     ext3    defaults,errors=remount-ro

```

do you understand the idea now..?

if you do, change the directory names or the appropriate directory structure in the fstab file & then try issuing the  sudo mount -a command again...

---

### Post by Huesos on 2007-03-23
I did exactly what you said and then some... it just isn't working. It is becoming clear to me with all these procedures that this kind of os is not for the average user like me. Thankyou for your time and help, I'm grateful. But I finally give up. I'll just get something more user friendly, linux is not quite there yet.

---

### Post by ffxr on 2007-03-23
ach well.. its nothing a little perseverance, thought and effort cant sort out.. , just because it takes 2 hours to cut grass in the garden, does that mean you just leave it to grow.. ? 

but i guess if your not willing to put in a little more effort then maybe ubuntu &/or linux isnt for you.. 

: )

---

### Post by zorkerz on 2007-03-25
Thats a shame i think huesos was close to getting it. An another note ffxr went i type 'sudo mount -a' i get this output > fusermount: mountpoint is not empty
fusermount: if you are sure this is safe, use the 'nonempty' mount option
FUSE mount point creation error: No such file or directory
Unmounting /dev/disk/by-uuid/08C082F6E8D4C961 ()
 im not sure what this means
i am dealing with a different and unrelated problem but for the moment am just trying to reload fstab without rebooting.

---


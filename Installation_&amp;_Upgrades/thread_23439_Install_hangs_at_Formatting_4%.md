---
title: "Install hangs at Formatting 4%"
date: 2005-04-01
forum: Installation &amp; Upgrades
---

### Post by Doctor Orange on 2005-04-01
I am currently installing ubuntu on a Compaq Prolinea 590, and it all seemed to be going ok, but it is hanging at 4% when: 

"Creating ext3 file system for / in partition #1 of IDE1 master (hda)..."

I dont know what to do - it happened last night, and again now on my second attempt.

Any ideas?

Thanks.


**EDIT**

The partition is should be making is 19GB primary ext3. There should also be a 500mb swap coming.

---

### Post by nemin on 2005-04-02
[QUOTE=Doctor Orange]I am currently installing ubuntu on a Compaq Prolinea 590, and it all seemed to be going ok, but it is hanging at 4% when: 

"Creating ext3 file system for / in partition #1 of IDE1 master (hda)..."
[/QUOTE]
Are you sure your HD is allright? Did it work before? Some HD-manufacturers have special programs to check your HD.

---

### Post by Arachnopuppy on 2005-04-02
Not good with ubuntu, but I'm pretty good with windows.  With that said, I'd blame it on the HD rather than the installing system.

---

### Post by feneks on 2005-04-02
Well, I suspect using ext2 results in the same error but you could give it a try.

Is it possible to install ANY other operating system? (Microsoft's things called OS included)

It could be that your harddisk is defect. (I said *could*!)

As nemin said you'll get a diagnostic tool from the manufacturer's homepage. 

The linux program **badblocks** can check too. Boot a Live-CD and get the rights of root. Then type in:
```
badblocks -wvs /dev/hda
```
If Badblocks finds  several bad blocks (It will tell you when it finishs) kick the harddisk and don't use it anymore.

[COLOR=Red]**ATTENTION:**[/COLOR]
**badblocks** with the option -w does destructive dedection. This means that it writes data to the disk and doesn't care if there had been others before. As a matter of fact you will lose the original data stored on the harddisk. If you don't want this to happen just don't use the option -w. Then badblocks runs read-only in a nondestructive way. Further information by typing *man badblocks*

--edit of edit (oh my god ...)   #-o 
I typed in a wrong information (again): badblocks normaly runs in *read-only* mode! (So I was correct first time.) With the option -n its *read-write* dedection is nondestructive. When you use the option -w its *read-write* dedection is destructive. I recorrected it upwards. I'm very very sorry about this.  :cry:

---

### Post by Doctor Orange on 2005-04-02
Yeah, my HDD failed the random seek test.

I put another in there and am currently fighting this compaq for a result :0P

Thanks

---

### Post by SoCal Tom on 2006-11-24
I have a similar problem.  The "formatting hda" hangs after 1%.  I have tried several times to get past that point.

The hard drive is a 60 Gig Maxtor that came from a working computer, with Windoze XP installed.  I have tried an older distro of SuSE, Red Hat and now Ubuntu.  No matter what I try, it hangs at almost the same spot every time; and for hours on end.  It's frustrating.

The hard drive has been checked for bad cylinders, sections, etc, and they're all good to go.

The machine is a new MSI motherboard with an AMD Sempron 2800, and over 500 megs RAM.  Previously used parts include a second hard drive at hdb, a DVD/CD burner, ATI video capture card, and 500 watt power supply.

Now, the funny thing is that Ubuntu runs from the CD ROM and not the hard drive.  I can't save anything to disk because everything disappears when the machine is powered down.

Any ideas on where to look to get past this point.

---

### Post by SoCal Tom on 2006-11-26
Since I can't edit my own messages, I have to add this addendum:

I'm getting an error message that states:  "formatting swap space in partition 5 of IDE1 master (hda)....."

As I recall IDE1 master is the DVD/CD ROM drive.  The master hard drive is IDE0 master; and the storage hard drive is IDE0 slave.

What needs to be formatted, then Ubuntu installed, is IDE0 master, which would make it hda.

Now what?

---


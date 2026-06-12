---
title: "Uninstalling Ubuntu + Grub on Windows 7"
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by bobbymccooscoos on 2011-04-03
A while ago I decided to try out linux. I installed it the standard way (by putting in the CD and partitioning my hard drive). However, I would ow like to uninstall Ubuntu, Grub and anything associated with it. I do, however, want to keep my Windows 7 partition unharmed. How can I do that?

---

### Post by Hedgehog1 on 2011-04-03
First, get your PC to boot directly into Windows again:

To make a Windows 7 / Vista emergency repair disk (in case you don't already have one made):
[IMG]http://img641.imageshack.us/img641/9550/small50createrepairdisk.png[/IMG]

If you are unable to make a recovery disk, you can download the ISO for   [VISTA]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or [WINDOWS7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Boot from the windows 7 / Vista  emergency repair disk, do the following:
[IMG]http://img10.imageshack.us/img10/5826/small51runningrecoveryd.png[/IMG]
[IMG]http://img856.imageshack.us/img856/3690/small52selectingwindows.png[/IMG]
[IMG]http://img826.imageshack.us/img826/3484/small53commandprompt.png[/IMG]
[IMG]http://img215.imageshack.us/img215/9547/small54bootrec.png[/IMG]

---

### Post by Hedgehog1 on 2011-04-03
To remove Ubuntu:
[IMG]http://img718.imageshack.us/img718/7687/small55diskmanagement.png[/IMG]
Remove Swap Partiton
[IMG]http://img97.imageshack.us/img97/4905/small56deleteswap.png[/IMG]
[IMG]http://img231.imageshack.us/img231/2992/small57freespace.png[/IMG]
Remove Ubuntu Partition
[IMG]http://img96.imageshack.us/img96/5986/small58deleteubuntu.png[/IMG]
Remove extended Partition
[IMG]http://img848.imageshack.us/img848/8053/small59deleteextended.png[/IMG]
Expand windows partition to use all the space
[IMG]http://img3.imageshack.us/img3/7880/small61extendwin7volume.png[/IMG]


***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-04-03
Sorry to hear Ubuntu didn't work out for you.

Windows 7 is the best MS Windows yet.  If that is a better fit for you, that is what you should run.


[SIZE="3"]*Thanks for trying Ubuntu!*[/SIZE]


***The Hedge***

:KS

---

### Post by rohitink on 2011-04-03
If You have installed On a separate partition then follow these steps.

If the partition is visible through My Computer.

Then Right Click Format that Drive.

Now, Restart. You will get an error b4 the boot screen. Some Grub Sort of Error.

Restart Again.

When system is booting press F8 and choose system recovery.
In system recovery select command prompt and type:

```
bootrec/fixmbr
```

Congratz, You are Free of ubnutu.

---

### Post by bobbymccooscoos on 2011-04-04
> **Hedgehog1 said:**
> First, get your PC to boot directly into Windows again:

To make a Windows 7 / Vista emergency repair disk (in case you don't already have one made):


I made a recovery cd, however should I use teh windows 7 cd that came with the computer or the 4 part recovery cds?

---

### Post by Mark Phelps on 2011-04-04
> **bobbymccooscoos said:**
> I made a recovery cd, however should I use teh windows 7 cd that came with the computer or the 4 part recovery cds?

To simply restore the MBR, you only need a Repair CD -- but you will need to boot using that.

The 4-part recovery set will probable completely erase the hard drive, reformat it, and reinstall Win7 to the state it was in when you first started the PC.  My guess, based on your original statement, is that this is NOT what you want to do.

---


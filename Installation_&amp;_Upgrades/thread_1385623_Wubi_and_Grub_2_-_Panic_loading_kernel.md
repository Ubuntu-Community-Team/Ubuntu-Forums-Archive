---
title: "Wubi and Grub 2 - Panic loading kernel"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by jgalaxy on 2010-01-19
Running Wubi Ubuntu 9.10 and Grub 2 boot loader.  At boot up Grub lists kernels vmlinuz-2.6.31-14-generic (and recovery) through vmlinuz-2.6.31-17-generic (and recovery).  They all worked previously - but during a recent system lockup (not coming back up from sleep mode) I have encountered some issues.

The issue is that due to the lockup, vmlinuz kernel version 16 and 17 are corrupt and cause kernel panic errors.  Kernels 14 and 15 are fine.  I would like to get 16 and 17 functional again.

I did try a feeble attempt via Synaptic Package Manager to re-install Linux Kernel Images for 2.6.31-16 and 17.  To no avail.

Does anyone know of a way to get vmlinuz kernels 16 and 17 back and bootable by grub?

---

### Post by mocoloco on 2010-02-20
I ran in to this same issue.  I found [Launchpad bug #477169]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169") which seems to explain how to solve the problem.  Look at comments starting at [68]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/68") in particular.

---

### Post by meierfra. on 2010-02-20
Have a look at this:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

Since the lockup might have done some actuall  damage I  not sure that this will work for you, but you should still give it  try.

If this does not solve  your problem, I can show you how to run a file system check.

---

### Post by jgalaxy on 2010-02-20
> **meierfra. said:**
> Have a look at this:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

Since the lockup might have done some actuall  damage I  not sure that this will work for you, but you should still give it  try.

If this does not solve  your problem, I can show you how to run a file system check.

There was some corruption that fsck attempted to fix, but the kernel loads  for vmlinuz..15 and 17 were damaged that would always cause a Panic loading kernel error.  The other kernels on my machine are fine, but older.  I wanted to use the newest ones I had.  I never did find a way to rebuild them or re-install them.  vmlinux..19 and initrd..19 have since come along and works fine and I did manage to figure out how to exclude the damaged kernels from my grub boot menu.

Since this is the 10th or so occurrence of this same problem on various machines on my network, I would truly love to learn how to re-instate/rebuild/restore  one of the damaged kernels.

Open to any tips, suggestions ...

Thanks

---

### Post by meierfra. on 2010-02-20
Did you replace wubildr as suggested in the link I posted?
Even if you have not been hit by that bug yet, you should still do it, to prevent future problems.

To reinstall the other two kernels

```
for ver in 2.6.31-{15,17};do
sudo apt-get install --reinstall --purge linux-{headers,image}-$ver-generic linux-headers-$ver;
done;
```

---

### Post by jgalaxy on 2010-02-20
> **meierfra. said:**
> Did you replace wubildr as suggested in the link I posted?
Even if you have not been hit by that bug yet, you should still do it, to prevent future problems.

To reinstall the other two kernels

```
for ver in 2.6.31-{15,17};do
sudo apt-get install --reinstall --purge linux-{headers,image}-$ver-generic linux-headers-$ver;
done;
```

I did replace wubildr as instructed.

I'll experiment with trying to reinstall 15 and 17 using this method.  Is there anything I need to do grub to re-introduce into grub's boot menu?

---

### Post by meierfra. on 2010-02-20
Reinstalling the kernel should trigger "update-grub" automatically. But if the  reinstalled kernel don't appear on the Grub Menu, do

```
sudo update-grub
```

---

### Post by shadowlands on 2010-02-21
I am having the same problem, and the sudo command does not work 
I typed in ls and this is what i get: (hd0) (hd0,5) (hd0,1).  
the file replacement also did not work.  I hope they find a solution soon!

---

### Post by meierfra. on 2010-02-21
> I typed in ls and this is what i get: (hd0) (hd0,5) (hd0,1). the file replacement also did not work. I
You don't seem to be using Wubi, so the file replacement will do not good.

> I am having the same problem, 

Did you also have a lock up?

> the sudo command does not work 

Which "sudo" command? 

Did you try reinstalling the kernels?  If reinstalling the kernel does not help, I suggest to start a  new thread and describe exactly what is happening during boot up.

---


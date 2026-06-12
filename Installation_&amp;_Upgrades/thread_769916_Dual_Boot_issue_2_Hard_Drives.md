---
title: "Dual Boot issue: 2 Hard Drives"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by karthikb23 on 2008-04-27
Hi,
I currently have XP installed on HD0 and Ubuntu on HD1.

Now on setting the boot device in BIOS, the appropriate Boot Menu comes up (NTLDR or GRUB).

However, each Loader is unable to load the other OS.

i.e. NTLDR cannot load Ubuntu:
I have copied the first 512 bytes (using 'dd') common share location(FAT32 partition).
When NTLDR tries to boot unbuntu using this file, i just get a message:
GRUB _ (blinking cursor).
Then it hangs.

Something similar for GRUB.
On chainloading NTLDR I get a message:

rootnoverify (hd1,0)
savedefault
chainloader +1

Then it hangs too.

Any suggestions anyone please??

---

### Post by sandysandy on 2008-04-27
in ubuntu reinstall grub. this should update ur win XP entry and will give u option for both windows and ubuntu.

have a look here on how to re-install grub

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

regards

---

### Post by sandysandy on 2008-04-27
some links for using windows NTLDR to boot ubuntu

[http://users.bigpond.net.au/hermanzone/p9.html](http://users.bigpond.net.au/hermanzone/p9.html)

[http://ubuntuforums.org/showthread.php?t=208951](http://ubuntuforums.org/showthread.php?t=208951)

regards

---

### Post by confused57 on 2008-04-27
You need map lines to boot Windows on a 2nd Hd:
```
title  Windows
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

---

### Post by karthikb23 on 2008-04-27
Hi,
Thanks a lot guys!!
Half problem solved :)

Solution suggested by confused worked.

Well, the same thing came across my mind in t morning (and fixed it at night), coz suddenly i realized that GRUB had not used 'makeactive', and was using 'chainload' directly.

Besides 'map' command is essential, coz when GRUB boots, it wld always use its HD as HD0. i.e. GRUB as if it is installed on HD0.
So XP becomes HD1.
But NTLDR needs to be told it is on HD0, and GRUB wld pass this info accordingly to it.

Now, the 'root' shd still be passed (hd1), coz again from GRUBs point of view, XP is (hd1). 

So GRUB works fine.

BUT.......   i am still not convinced for any solution for NTLDR loading GRUB.
Yes, the link given by 'sandy' mentions a 'WinGRUB', but i want to do it using GRUB itself, and surely there shd be a way.
Also, noticed that quite a few are getting this problem.

So any more suggestions please?:)

---

### Post by karthikb23 on 2008-04-29
Hi,
can anyone help please?
I have tried searching a lot, and tried different things, but am unable to make NTLDR dual boot.

Is it because of the BIOS not being able to access beyong cylinder 1024?
But then in that case, noether shd i be able to boot ubuntu via GRUB!

Any help is highly appreciated!

---

### Post by ssican on 2008-05-04
**karthikb23**, see this information of the GRUB Manual:

"4.2.6 DOS/Windows
GRUB cannot boot DOS or Windows directly, so you must chain-load them (see Chain-loading). However, their boot loaders have some critical deficiencies, so it may not work to just chain-load them. To overcome the problems, GRUB provides you with two helper functions. 

If you have installed DOS (or Windows) on a non-first hard disk, you have to use the disk swapping technique, because that OS cannot boot from any disks but the first one. The workaround used in GRUB is the command map (see map), like this:
 
     grub> map (hd0) (hd1)
     grub> map (hd1) (hd0)

This performs a virtual swap between your first and second hard drive."
Source:[http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html#DOS_002fWindows](http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html#DOS_002fWindows)
[http://www.gnu.org/software/grub/manual/html_node/index.html](http://www.gnu.org/software/grub/manual/html_node/index.html)

See, this Guide of Forum Tutorials & Tips -DualBoot Two Hard Drives- [http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by lemming465 on 2008-05-04
> **karthikb23 said:**
> Hi,
I currently have XP installed on HD0 and Ubuntu on HD1...

rootnoverify (hd1,0)
savedefault
chainloader +1

If NT is on the first disk, Ubuntu is on the second, and Ubuntu is on the MBR, then the XP entry should be start off *rootnoverify (hd0,0)*

Grub counts from 0, not 1.  See if that helps any.

---


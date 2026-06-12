---
title: "GRUB issue with Win7 SP1 in a dual-boot setup"
date: 2011-09-24
forum: Installation &amp; Upgrades
---

### Post by samfrimp on 2011-09-24
I have had this problem for some time but finally decided to run it to ground today.

I have a dual-boot 11.04/Win 7 setup, with each being on a separate drive. Ubuntu is the first drive to boot. The BIOS only gives a "Hard Disk" boot option in the boot order, not individual hard disks.

Ever since Win7 SP1 came out, I have been frustrated at the inability to install it due to the dual-boot setup I have. It fails with the error 0x800F0A12 (essentially, Win7 can't write to the boot sector). Microsoft has a number of suggested fixes and the forums here have made some other suggestions, to no avail.

It seemed to me the simple thing to do would to be unplug the Ubuntu drive and boot directly to Windows. Doing that gives me:

GRUB Loading Stage 1.5

GRUB loading, please wait...

Error 21

And that's as far as it gets booting into Windows.

I presume some piece of GRUB has been put onto the Windows HD but the fact that GRUB itself has been bypassed via the unplugged 1st drive, it doesn't know what to do with itself.

I'm relatively proficient at the command line, but my experience is a mile wide and an inch deep. I know just enough to get myself into trouble.

Any thoughts?

---

### Post by raja.genupula on 2011-09-24
Hi do this , i hope this gonna help you 

```
sudo apt-get install lilo
```
&
```
sudo lilo -M /dev/sda mbr
```

---

### Post by Blasphemist on 2011-09-24
There is a script you can run that will give us information on how things are configured now. You can either just download the script and run it or better yet, either install boot-repair or get the boot-repair cd. [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) or [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

The boot repair would allow a number of actions but we need to know what to change first. As you can see on the boot repair page it includes being able to get just the boot info results. It will even automatically put in up for us to view, just give us the url.

---

### Post by samfrimp on 2011-09-24
[http://paste.ubuntu.com/696206/](http://paste.ubuntu.com/696206/)

Hope that was the thing to do.

---

### Post by YesWeCan on 2011-09-24
You have done well to install Ubuntu to separate hard disk to Windows. But the Windows disk has an old Grub legacy boot code instead of the standard MBR boot code that Windows expects to see.

So best to restore the standard MBR to the Windows disk. In bootinfoscript the disk is called /dev/sdb so use raja.genupula's lilo commands with sdb. Then tell the bios to boot sdb first.

---

### Post by samfrimp on 2011-09-24
Unfortunately, the BIOS does not permit selection of individual drives for boot. It only gives the option "Hard Disk".

---

### Post by YesWeCan on 2011-09-24
Is it practical to disconnect the Ubuntu drive?
Oh I see you've done that. Ok well once you've restored the MBR using lilo it should do better and then you can run all the updates and so on before reconnecting the Ubuntu drive.

---

### Post by oldfred on 2011-09-24
Only old systems that did not support SATA have BIOS that do not have a way in BIOS to change boot order. Old IDE system choose boot order by setting jumpers on hard drive or location on cable (cable select).

Some early Dells only boot from a IDE drive but allow one SATA drive.

Other BIOS have a way to choose. Some have it as  a menu selection under the hard drive and some have one selection for device and somewhere else (maybe ever a different page) a selection for which hard drive.

Do you have an f12 (or other key) to select boot order as a one time select from the first BIOS loading screen? Does it give hard drive choices? On mine I choose hard drive, then it opens a window for hard drives which strangely includes bootable USB flash drives.

---

### Post by samfrimp on 2011-09-24
Lilo applied. Giving it a whirl.

---

### Post by Mark Phelps on 2011-09-24
> **samfrimp said:**
> Unfortunately, the BIOS does not permit selection of individual drives for boot. It only gives the option "Hard Disk".

The disk selection is typically a different option in the BIOS.  It's often called Hard Disk Boot Priority. You should look to see if you have this different option.

---

### Post by samfrimp on 2011-09-25
Thanks everyone. The lilo commands here worked.

---

### Post by YesWeCan on 2011-09-27
Good. You can mark this thread as solved in [COLOR="Red"]Thread Tools[/COLOR].

---


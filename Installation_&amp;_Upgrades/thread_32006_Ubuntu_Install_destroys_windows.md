---
title: "Ubuntu Install destroys windows"
date: 2005-05-05
forum: Installation &amp; Upgrades
---

### Post by davidmigl on 2005-05-05
Hello,

I recently installed Ubuntu 5.04 on a machine with an existing windows installation.  I installed another hard disk, and put Ubuntu on there, thinking that Ubuntu and Windows could peacefully coexist.  Now, when I select "Windows 2000 Professional" in the GRUB bootloader, I see this on the screen, and nothing else happens.

```
Booting "Microsoft Windows 2000 Professional"

root (hd1,0)
     Filesystem type unknown, partition type 0x?
savedefault
makeactive
chainloader +1
```

What do I need to do to get windows to boot again?  I installed Ubuntu, thinking that it wouldn't be nosy enough to go out of its way, into a totally different piece of hardware, into a totally different partition, to destroy Windows.  Is windows still intact, but GRUB won't load it because of a configuration error, will GRUB not load it because it wants to destroy Microsoft and views windows as evil, or did Ubuntu mess up windows in its plan to completely dominate the world with Linux?

Is there any way to uninstall the GRUB bootloader and simply go into the bios and switch the hard drive's boot priority to switch operating systems (do it the "old fashioned" way)?

I know dual booting is possible!  If only it would work in this instance!

davidmigl

---

### Post by davidmigl on 2005-05-05
Wow.  I just switched the HDD boot priority and voila!  windows came up.   There is now no need for this thread, and I can't delete it, so just ignore this.  I'm so glad I got it to work!  Ubuntu is a great distro!

---

### Post by thaore0 on 2005-05-06
[QUOTE=davidmigl]Wow.  I just switched the HDD boot priority and voila!  windows came up.   There is now no need for this thread, and I can't delete it, so just ignore this.  I'm so glad I got it to work!  Ubuntu is a great distro![/QUOTE]


How did you switch the boot priority? I'm having the same issue.

---

### Post by SteveyDevey on 2005-05-06
[QUOTE=thaore0]How did you switch the boot priority? I'm having the same issue.[/QUOTE]
 Maybe he means he changed the boot order in the BIOS, or possibly even the jumpers on the drives. It could also be an option in the bootloader.

---

### Post by WildTangent on 2005-05-06
we had that problem at work on our demo computer. that soured my boss on linux forever i think :(

-Wild

---

### Post by thaore0 on 2005-05-06
```
Booting "Microsoft Windows 2000/ME/XP"

root (hd1,0)
     Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1
```

I've tried a few combinations using 1's and 0's, but still to no avail?

Hoary is installed on the same HDD as my XP Pro installation...is my XP partition borked?  :???:

---

### Post by davidmigl on 2005-05-07
Yes, I switched the HDD boot order in the BIOS.  When I booted to the Windows drive, it bypassed the Grub bootloader and went straight into Windows.

As for you, I don't know what to do for booting off of same HDD, different partitions.  The culprit seemed to be the grub bootloader, which I had to bypass.  Like your boss, I would be a little soured on Linux if I was unable to get back into windows again.

Hope you get your problem solved,

davidmigl

---

### Post by WildTangent on 2005-05-07
its wierd, i use seperate drives for my dual boot system at home, no probs. i use a partitioned drive at work, and then windows wont boot. oh well. we just reinstall windows, and went on...
we actually reinstall windows quite often, sometimes viruses from customer computers find their way onto our computers

-Wild

---

### Post by crazybill on 2005-05-07
Windows and Ubuntu Linux can coexist if you do the setup correctly. It sounds like you can solve your problem by going into the BIOS (del, F-1, ctrl-alt-enter ... or whatever ... it depends on the bios chip on your motherboard) and changing your boot order.

Frankly, I think it is better to keep only one operating system on a machine... otherwise you are always compromising on setup.

---


---
title: "Boot Repair."
date: 2016-07-27
forum: Installation &amp; Upgrades
---

### Post by wfp on 2016-07-27
So this is the story on installing Ubuntu I choose erase entire disk and install. I installed GParted just to see if there was still a windows hidden recovery partition there is not. Before installing Ubuntu I created the 4 windows back up dvd's. I am guessing the only thing I need to do is run boot-repair to repair mbr, and then try the windows recovery dvd's to install windows again. Does this sound right.

---

### Post by Bucky Ball on 2016-07-28
What you should do is install Windows then install Ubuntu. Much easier than the other way around which can be a brain-twist to fix up. There should be no need to use Boot Repair during any of this if all goes as it should. 

[LIST]
[*]Install Windows. 
[*]Leave unallocated space on the drive to create partitions to install Ubuntu. 
[*]During the Ubuntu install, choose 'Something Else' at the partitioning section and install the Ubuntu / and /swap partitions (and /home if you're using one) in the unallocated space.
[/LIST]

Once installed, reboot the computer. You may get booted straight in to Ubuntu. If this is the case open a terminal and run this:

```
sudo update-grub
```

... then reboot. 

If you get booted directly to Windows, then use Boot Repair. Hopefully this will not be necessary. If you have it on bootable media, disk or USB, just boot from that and run it. If not, boot from the install media of Ubuntu and run it from there in a live session (Try Ubuntu). See [here for how]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu"). This method works fine even with a live session. You do not need a boot repair CD or USB.

Whichever method you use, reboot when you're done. Do you now get a screen with options to choose an OS and is Windows on that list? It should be. If not, post back with where you've gotten to.

Another thing to try is, once you have both installed, if on first boot you don't get a list of OSs to choose from, reboot and try hitting the shift key just after the manufacturer splash. That should bring up the list. If it doesn't, proceed with one of the fixes above. If it does but Windows is not there, ditto. 

Good luck. :)

---


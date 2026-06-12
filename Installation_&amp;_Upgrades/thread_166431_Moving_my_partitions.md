---
title: "Moving my partitions"
date: 2006-04-26
forum: Installation &amp; Upgrades
---

### Post by dcmorris on 2006-04-26
I have installed breezy and everything seems to be running fine. Only problem is I didnt install it on the partition I wanted it on and now lookig at parted only confuses me further. 

Easiest thing would be to just remove the insallation and start over I think. I am dual booting it with WXP. 

Any help would be appreciated.

Don

---

### Post by gondilon on 2006-04-26
did you put it on the partition right after your windows partition or on another partition?

---

### Post by scooper on 2006-04-26
I'll take a stab at it...

Generally in Linux you can just copy partition files and they will work, if you adjust your boot loader.  So here's a rough sequence to guide you.  Please consider your specifics before using, like how many partitions you are using, whether it's a separate boot partition, etc.

- Reboot with a live CD so that data isn't changing on your installation partition.
- Manually mount your partition(s), if not automatically mounted.
- Create and mount new partitions as needed.
- Use "cp -a" to accurately copy files from old location(s) to new.
- If your /boot moved (i.e. it's not on its own partition) add entries to your boot loader by copying appropriate lines and adjusting the disk devices.  E.g. grub configuration is in /boot/grub/menu.lst (wherever it's mapped for the new setup under the live CD).  Change the hd*n* device specs as per the grub documentation to reflect the new partitions.  LILO config is in /etc/lilo.conf (adjust for mount position) and uses a more conventional device syntax.  Remember to run lilo when done.
- Edit /etc/fstab (in the mounted new partition) to reflect the new partition arrangement.
- Reboot and enjoy.  Don't panic if there's a problem.  Use the live CD to get a command line to investigate and fix.

Obviously don't do this if you're not comfortable with fstab, grub, etc.  There is opportunity for error.  OTH I've successfully done this a bunch of times.

Good luck!
Steve

---

### Post by dcmorris on 2006-04-26
I have a C drive and a D drive, each ~26GB. 
I want the ubuntu on the D drive . It is now on the top end of the C drive. 

I made another mistake and installed only the base system so it's pretty bare. 
I have now got a live CD running at boot too and it has Gparted which looks a little easier to use. 
Question still is though, what is the easiest way to remove the installed ubuntu?

Maybe Gparted is the answer. It has been a lot of years since my UNIX admin training so I'm a lot rusty.

Don

---

### Post by Sef on 2006-04-26
> Question still is though, what is the easiest way to remove the installed ubuntu?

1) Use GParted to delete the ubuntu.

or 

2) Use the partitioner in the install disk to delete Ubuntu.

Either way you could install Ubuntu on the partition you wanted it to go on.

---


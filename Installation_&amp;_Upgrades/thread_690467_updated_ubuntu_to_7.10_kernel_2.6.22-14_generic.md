---
title: "updated ubuntu to 7.10 kernel 2.6.22-14 generic"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by knitmom on 2008-02-07
Okay, first help!  Everything was running great prior to getting updates.  Once the computer rebooted, it doesn't work.  It looks like everything is loading and then it says:
[INDENT]Error 22:  No such partition 
click any key to continue[/INDENT]

Then it brings me to the menu to chose which version or recovery mode I want to use.  Well, none of the options work.

So is this a problem with one of the updates????  Or could it be a hardware issue. 

I've tried doing a search for the error message, but nothing comes up.

Thanks!
Knitmom

---

### Post by philinux on 2008-02-07
Seems like the update messed with your grub (menu.lst) . I've seen this before.

You may have a backup copy of menu.lst. It would be called menu.lst~

Boot into recovery and use.

ls -l /boot/grub/menu*

Have a look at the date stamps to make sure which is the latest backup

Then its easy to 

cat /boot/grub/menu.lst
make a note of the root  hd0,0 or whatever it is now that's giving the error 22 then check the backup to see what it was.
cat /boot/grub/menu.lst~

Then gedit /boot/grub/menu.lst and change the root partition.

---

### Post by dstew on 2008-02-07
This is not a hardware issue, but a grub configuration issue. The error you go included the short statement "No such partition", which shows it is a grub stage 2 error. This means the grub booter found its stage 2, and I assume its menu. Then, when you picked the kernel to boot, you got the error, correct?

This is due to the way grub updates its menu.lst file when a new kernel is introduced to the system. There is a value called groot in the menu.lst file that grub uses to create the new kernel statement. Probably, that groot value is not correct.

To fix the problem we need to get some information. From a Live CD system, open a teminal window and enter the command```
sudo fdisk -l
```That will list the partitions on your system. Once we know which partition contains your Ubuntu system, we can mount it and repair the files. Once we fix groot, the next update should go in without problems.

---

### Post by knitmom on 2008-02-08
Thankyou both!  I do have a live CD and will try this asap!  

I realized I had the newest version on my laptop with no problem.

I really like ubuntu, but these little problems won't convince my husband!  Though my daughter is convinced and loves it because it is faster than our other OS, and she can get on myspace and other sites more quickly.

Thanks again!
Knitmom

---

### Post by seventhc on 2008-02-08
I too have a strange problem after that update, figure I'd ask here instead of starting a new thread.
Basically now my comp takes about 10 minutes to boot. I have a backup of menu.lst from day 1 of the install and the UUID is different. I added in a second entry so I could boot from the old, but it still takes 10 minutes.
Also the screen just goes blank during boot, I see the screen with the 3 second timeout, then once it passes that it goes blank and 10 minutes later I am finally offered the login screen.
Any ideas for a fix on this?
I also tried commenting out the ro quiet stuff too, but that did nothing.

---

### Post by emarkd on 2008-02-08
This may not be helpful, but you can check the UUID of a drive or partition by running

```
sudo vol_id /dev/whatever
```

---

### Post by seventhc on 2008-02-08
I checked it using that command and it matches the old UUID not the new one that has changed.
maybe I should use my old grub and overwrite the new one.
But even when I booted to the old value it still took forever. I'm not sure if anything else in grub has changed or if there is anything else in there that could effect it though.

---

### Post by emarkd on 2008-02-08
Those should be short files to compare, but if you object to doing anything the computer can do for you, you can run a diff.

```
diff -y /etc/fstab /etc/fstab.old
```

or whatever your files are called.

---

### Post by seventhc on 2008-02-08
If I'm looking at this correctly, then the only difference would be
```

title           Ubuntu 7.10                                   <
root            (hd0,0)                                       <
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=c87 <
initrd          /boot/initrd.img-2.6.22-14-generic            <
quiet                                                         <
                                                              <

```

---

### Post by zvacet on 2008-02-08
Maybe [this](https://help.ubuntu.com/community/UsingUUID) can help you.

---

### Post by seventhc on 2008-02-08
Thank's, reading it now:)

---


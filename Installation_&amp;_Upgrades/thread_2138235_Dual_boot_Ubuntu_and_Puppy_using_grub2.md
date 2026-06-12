---
title: "Dual boot Ubuntu and Puppy using grub2"
date: 2013-04-23
forum: Installation &amp; Upgrades
---

### Post by vbdanl on 2013-04-23
hi.  first, i want to thank all of the moderators and ubuntu community for all the great support given.
second, i should apologize up front for how messed up this post will seem to most who read it.. sorry, i get carried away sometimes.
i have a couple of issues i am trying to solve, and have spent many hrs researching and trying various options, to no avail.
first, i have been trying to get a Puppy frugal install to boot from my Ubuntu supplied grub2 menu, but have not been able to.
was wondering if anyone does this, and if so, how ?

i am pretty sure grub is loaded into the mbr (i think i chose install to sda).
i have added entries in the 40* custom file, but have never been able to boot into Puppy from the grub menu.
"Invalid extent", and "you must first boot linux" are the messages i am getting when trying to boot puppy from grub menu.
puppy boots fine from CD, and it finds the .sfs file on sda6.  have the boot files in psubdir puppy5.4.

i have Slacko puppy 5.4 installed in sda6.  Ubuntu 12.04 on sda1, and now actually on sda3 as well.
originally i had ubuntu on sda1, but it was a smaller partition with very little freespace, so i copied it to the larger sda3 partition using dd.
if possible i will eventually remove ubuntu from sda1 and use it for something else.
this second problem has to do with update-grub only updates the mbr from the sda1 install.  running it from sda3 does not change what i see when booting.
i ran a command that now shows sda3 as the boot partition instead of sda1, but that does not change "who" updates the grub menu.
i also have added a manual entry for ubuntu on sda3 into the 40* file, since the update-grub was mixing uuid's in the grub file it creates.
i shut off the 30 os-prober for now as well.  update-grub was giving me both uuid's (from sda1 and sda3) in the menu options it created for sda3, so that's why i shut off the 30 os prober.  now i can boot into either ubuntu (sda1 or sda3) without a problem, but still can not get puppy to boot from the grub menu.

The dd copy was done after working with and not being able to boot puppy from grub2, so i don't think that issue has anything to do with puppy not booting.
i do actually get some different error messages than i did before, but i don't have them available right now.. can post later if needed.

thanks for your help.

---

### Post by oldfred on 2013-04-23
This is now older, but I booted puppy from grub. It was in partition 12 on my second drive so (hd2,12). My entry is version specific so you have to change to your version.

 I did have to move lupu-511.sfs to the top level of the partition ( same as /boot not inside /boot) and created /boot/lupu511 with all the other files including vmlinux & initrd.gz.
menuentry "Puppy 511" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos12)'
        linux /boot/lupu511/vmlinuz root=/dev/ram0 pmedia=atahd loglevel=7 pkeys=us 
        initrd /boot/lupu511/initrd.gz
}

---

### Post by vbdanl on 2013-04-24
> **oldfred said:**
> This is now older, but I booted puppy from grub. It was in partition 12 on my second drive so (hd2,12). My entry is version specific so you have to change to your version.

 I did have to move lupu-511.sfs to the top level of the partition ( same as /boot not inside /boot) and created /boot/lupu511 with all the other files including vmlinux & initrd.gz.
menuentry "Puppy 511" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos12)'
        linux /boot/lupu511/vmlinuz root=/dev/ram0 pmedia=atahd loglevel=7 pkeys=us 
        initrd /boot/lupu511/initrd.gz
}
i tried to imitate what you have above, other than the partition # and dir names.
here is what i have so far.  i have sda6 mounted in ubuntu, and made the changes to puppy from there.
updated the grub, and will see what happens..
```
dan@sony:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda1        5034496 3667276   1111476  77% /
udev              239692       4    239688   1% /dev
tmpfs              99952     756     99196   1% /run
none                5120       0      5120   0% /run/lock
none              249876     152    249724   1% /run/shm
/dev/sda6        4585568  333360   4019272   8% /Puppy
dan@sony:~$ cd /Puppy
dan@sony:/Puppy$ ll
total 188560
drwxr-xr-x  4 root root      4096 Apr 23 23:38 ./
drwxr-xr-x 24 root root      4096 Apr 22 21:41 ../
drwxr-xr-x  3 root root      4096 Apr 23 23:38 boot/
drwx------  2 root root     16384 Apr 19 07:47 lost+found/
-rw-r--r--  1 root root 157470752 Apr 19 07:52 puppy_slacko_5.4.sfs
-rw-r--r--  1 root root 536870912 Apr 23 23:19 slackosave-dan.4fs
dan@sony:/Puppy$ ll boot
total 12
drwxr-xr-x 3 root root 4096 Apr 23 23:38 ./
drwxr-xr-x 4 root root 4096 Apr 23 23:38 ../
drwxr-xr-x 2 root root 4096 Apr 23 23:37 puppy54/
dan@sony:/Puppy$ ll boot/puppy54
total 4644
drwxr-xr-x 2 root root    4096 Apr 23 23:37 ./
drwxr-xr-x 3 root root    4096 Apr 23 23:38 ../
-rw-r--r-- 1 root root       0 Apr 19 07:52 ATAHD
-rw-r--r-- 1 root root 1875074 Apr 19 07:52 initrd.gz
-rw-r--r-- 1 root root 2868400 Apr 19 07:52 vmlinuz
dan@sony:/Puppy$ 
```

---

### Post by vbdanl on 2013-04-24
when i tried to boot with the latest changes, i now get "error: out of partition" followed by "error: you need to load the kernel first".
this is what my entry in the 40* file looks like:
menuentry "Puppy Linux Slacko 5.4 Optf" {
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
linux /boot/puppy54/vmlinuz root=/dev/ram0 pmedia=atahd loglevel=7 pkeys=us pfix=fsck psubdir=boot/puppy54
initrd /boot/puppy54/initrd.gz
}

i also tried to manually remove the psubdir entry after it failed, then ctrl-x to boot, and it still gave the same error.
was thinking i read somewhere you don't need the psubdir entry, but it will make it boot faster if you do.
any ideas what i might try next?

---

### Post by oldfred on 2013-04-24
I do not know if the Slackware version uses different names. I often have to examine the file structure of ISO to know what is where.

---

### Post by vbdanl on 2013-04-25
hmmm.. wasn't sure how to look at the iso, or what i was looking for.  i mounted sda6 via ubuntu (which is where puppy is), and moved the various files to look similar to what you had.  i was also able to fix sda3 so it became the primary boot partition and maintainer of the mbr.  still was getting errors trying to boot into puppy via grub2.
i ended up reformatting sda6 and reload puppy to it, setting the boot flag and installed grub (not grub2) in the mbr via puppy.  had read somewhere that it was able to detect all of the installs and should work fine.  guess i borked something up somewhere.. now i am getting a Error 16 after stage 1.5 and it halts.  do not see the grub menu where i normally see all of the boot options.  glad this is just my "old" pc i am trying to revive, and not my everyday one..

---

### Post by oldfred on 2013-04-25
Grub2 is much better at finding other installs. The original complaint before we learned how good grub2 was, was that grub2 could not really be loaded to PBR and chainloaded and that editing menu.lst was easier. But grub2 has 40_custom to add entries to anyway.

Error 16 is some sort of inconsistency. But I have forgotten most of grub legacy.
[http://members.iinet.net.au/~herman546/p15.html#16](http://members.iinet.net.au/~herman546/p15.html#16)

I open ISO with archive manager and look at paths, filenames, and find its boot loader and what settings it has on its boot line(s).

---

### Post by vbdanl on 2013-04-25
> **oldfred said:**
> Grub2 is much better at finding other installs. The original complaint before we learned how good grub2 was, was that grub2 could not really be loaded to PBR and chainloaded and that editing menu.lst was easier. But grub2 has 40_custom to add entries to anyway.

Error 16 is some sort of inconsistency. But I have forgotten most of grub legacy.
[http://members.iinet.net.au/~herman546/p15.html#16](http://members.iinet.net.au/~herman546/p15.html#16)

I open ISO with archive manager and look at paths, filenames, and find its boot loader and what settings it has on its boot line(s).

i downloaded a puppy iso file at work, and also had to download peazip so i could look at it via win7.
file i see:
a folder called [BOOT]
boot.cat
boot.msg
help.msg
help2.msg
initrd.gz
isolinux.bin
isolinux.cfg
logo.16
puppy_slacko_5.5.sfs
README.HTM
vmlinuz

under the boot folder, there is one file, Bootable_NoEmulation.img
the readme file just talks about Windows truncating file names.

the contents of isolinux.cfg:
default puppy
display boot.msg
prompt 1
timeout 50

F1 boot.msg
F2 help.msg
F3 help2.msg

label puppy
kernel vmlinuz
append initrd=initrd.gz pmedia=cd

What file executes when i boot up the CD (or am i seeing the actual file when i explore the .iso file like i currently am) ?
Not sure what i am looking for regarding your stmt about looking at paths, filenames, boot loader, and settings on the boot line, unless you are talking about the contents of the .cfg file shown above..

---

### Post by vbdanl on 2013-04-25
well..after a few days, i am pretty much back to square one.  i re-installed grub2 via ubuntu live cd, and can now boot ubuntu.  i am getting a invalid magic number when i try to boot puppy.

---

### Post by oldfred on 2013-04-25
I tried downloading Puppy to try myself, but it gave errors on the extraction. What version do you have?

---

### Post by vbdanl on 2013-04-26
> **oldfred said:**
> I tried downloading Puppy to try myself, but it gave errors on the extraction. What version do you have?
Slacko 5.4 is what i have on CD.  i downloaded 5.5 at work, but have not burned it.

---


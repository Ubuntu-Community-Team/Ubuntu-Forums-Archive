---
title: "** Nothing works after moving /usr to another partition"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by la1234uk on 2008-06-10
I did a complete migration to Ubuntu 8.04 from windows XP few weeks ago.
Installed in a single partition of about 5 Gbytes. My PC contains other disks where I share files and documents from my former XP system.

To migrate completely and start to work, I had to install several software (wine with applications, Bender, Compilers, TeX editors, etc etc). Soon realized /usr folder was growing big. Decided to move the /usr folder to a larger emty partition.

I got informed using Linux related forums, then after a complete backup, decided to copy all /usr content to a newly created ext3 partition (used gparted).

Then modified fstab adding this line: 
/dev/sdb3     	/usr ext3 defaults 0 1
sdb3 is my new partition on another disk, other parameters I just copied from instructions found using wiki's. 

After reboot the command df -h gives:
/dev/sda6             4.7G  4.2G  242M  95% /
varrun                490M  216K  490M   1% /var/run
varlock               490M     0  490M   0% /var/lock
udev                  490M  100K  490M   1% /dev
devshm                490M   12K  490M   1% /dev/shm
lrm                   490M   38M  453M   8% /lib/modules/2.6.24-18-generic/volatile
/dev/sdb3             3.5G  2.5G  881M  74% /usr
gvfs-fuse-daemon      4.7G  4.2G  242M  95% /home/ruggero/.gvfs
/dev/scd0             696M  696M     0 100% /media/cdrom0

It seems I succeeded. However, as soon as I try for example to mount any of the documents disks I have this depressing result:
"org.freedesktop.DBUs.Error.AccessDenied" 
and 
"A security policy in place prevents thi sender [....]"
"Mount error name (unset) [...]"

Whatever modification I try to do, the sudo commamds gives:
"sudo must be setuid root"
and if I give the command su I obtain a password request, but my root password is not recognized (!)

I feel this is a pretty bad situation.

I think my mistake was that I copied all files from original /usr folder to the new ext3 partition using a simple cp -r command. So -if I understand Linux correctly- the files access mode ("drwx") have changed. 
I suspect that some important file in /usr is now protected and system cannot work properly without full access to it.

I kindly ask help to some expert out there. Do you think it is a problem easily solvable ?
Or I must re-install everything ?

Before doing the /usr copy command, I backed-up all system using  this command:
cd / 
tar cvpzf /media/Rugge_Mails/all.backup.June08.tgz
(plus some --exclude command)

I presume I have only two option:
1) Restore system using my backup (not sure how to do that in present condition, sudo does not work)
2) get a live CD and start over with a new installation.

The third option is that some expert among you have a simpler way to recover control over my system. The original /usr folder have not been deleted, but it is not visible to me. I "see" only the new one in the new partition. If I could only go back to the original /usr everything will work again I suppose. However I cannot modify fstab because system does not allow me without sudo.

Any suggestions that you think it may be useful to me will be greatly appreciated. 

Please consider step-by-step suggestions, I am very new at Linux/Unix.

Thanks a lot in advance for any help !

Greg Ruo

---

### Post by la1234uk on 2008-06-10
:)
I solved my problems... just few minutes later I posted the question.

After further investigation using google I decided to use a live CD and use it to log in the system.

Used a Ubuntu 8.04 live CD. Opened a terminal window and from there I copied al /usr files of the original Ubuntu installation to the new partition.

This time I used cp -a that preserves untouched all modes and privileges of copied files.

then I rebooted and I had my system back !!

In conclusion:

If you want to move your /usr folder to a larger partition, use "cp -a" command to copy the files. Otherwise privileges will be lost and your system will not work properly.

Cheers,
:popcorn:

---


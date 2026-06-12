---
title: "Upgrade to 11.04 problem mounting drive"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by gryall on 2011-04-29
During the upgrade to 11.04 I lost power and my computer powered off. When I restarted it I got the message "The disk drive for / is not ready yet or not present" "Continue to wait: or Press to skip mounting or M for manual recovery"

Pressing s doesn't help.

Pressing M in recovery mode get's me to a comand line.

What should I do next?

---

### Post by riffey#4 on 2011-04-29
I have exactly the same error.
I didn't loose power though, but I did a shutdown because the upgrade was still going to take 5 hours, and I can't keep my PC on during the night. 
Any suggestions?

---

### Post by gryall on 2011-04-29
I don't know if it helps, but the table if I fdisk -l (having selected m) is:

Device Boot Start End  Blocks   Id System
/dev/sda1     1     12   96358+ de Dell Utility
/dev/sda2    13    274 2104515   b W95 FAT32
/dev/sda3 * 275    299  200012+ 83 Linux
/dev/sda4   300  12161 95281515  f W95 Ext'd (LBA)
/dev/sda5   300    620  2578401 82 Linux swap / solaris
/dev/sda6   621  12161 92703051 83 Linux

---

### Post by jimbo99 on 2011-04-29
I have the same problem.  Basically it mounts the partition as read only.  Not sure what to do to solve the problem.

---

### Post by brownthumb on 2011-04-29
I also have the same problem.

Update. So far, I'm thinking this is a problem with the /etc/fstab file. I have gotten to the point where I am able to edit the file. This is what I did:

1. I booted from the live cd.
2. I mounted my / partition by typing:
   mkdir /media/sda1
   mount /dev/sda1 /media/sda1
3. sudo pico /media/sda1/etc/fstab

This is what my fstab looks like (skipping comments since I'm transcribing):

proc              /proc                proc             nodev,noexec,nosuid 0 0
UUID=8b6afc74-cc4b-4ede-bd6f-d1f4fa2710ba /          ext4        errors=remount-ro 0 1
UUID=1aa9fcd5-40e8-4f98-8a99-16f939ff24dc   none      swap         sw      0 0
/dev/fd0       /media/floppy0      auto        rw,user,noauto,exec,utf8                0 0

There are some comments indicating that this was all auto generated at some point: "/ was on /dev/sda1 during installation"

Now if someone either knows how to edit this, or can give some hints as to how to figure that out, we may be back in business. Could it be the wrong UUID? How would one find the UUID?

---

### Post by angus73 on 2011-04-29
Same problem here. I have found something similar, didn't help me but may be useful for someone:  [http://serverfault.com/questions/264710/root-mount-error-while-upgrading-from-ubuntu-10-10-to-11-04/264887#264887](http://serverfault.com/questions/264710/root-mount-error-while-upgrading-from-ubuntu-10-10-to-11-04/264887#264887)  Bye, A.

---

### Post by angus73 on 2011-04-29
> **brownthumb said:**
> How would one find the UUID?

 you can list your UUIDs issuing the command ```
blkid
``` let us know if you progress in something
cheers,
 A.

---

### Post by brownthumb on 2011-04-29
Thanks angus.

I have tried replacing the uuids with the device names to no avail (same result). Using your suggestions, I have verified the uuid's in the original fstab file.

The only other thing that could be wrong with fstab are the options.... I'm looking into that. If that's not it, it may not be fstab after all.

---

### Post by gryall on 2011-04-29
Just checked, my UUIDs definitely match.

---

### Post by gryall on 2011-04-29
The Problem would seem to that the file system is read only (as said above). I have tried edditing the fstab options (by booting a live CD - where I can edit away to my hearts content) to make it otherwise, but that seems to have had no effect. I'm sure once th read only thing is fixed th instalation can be finished OK.

---

### Post by gryall on 2011-04-29
I have now  sort of fixed it maybe

I started up, selected m to get to a comand line
ran
sudo mount -o remount,rw /

then was able to run
dpkg --configure -a
selecting the defaults whenever given a choice.

After that it hung, I restarted and I was able to log in normally, went to update manager and was prompted to do a partial upgrade

---

### Post by ohiknow on 2011-04-30
Remounted / RW, dpkg --configure -a, continuing install.

Thanks Guys!

---

### Post by riffey#4 on 2011-04-30
> **gryall said:**
> I have now  sort of fixed it maybe

I started up, selected m to get to a comand line
ran
sudo mount -o remount,rw /

then was able to run
dpkg --configure -a
selecting the defaults whenever given a choice.

After that it hung, I restarted and I was able to log in normally, went to update manager and was prompted to do a partial upgrade

This worked for me, thanks!

---

### Post by angus73 on 2011-04-30
> **riffey#4 said:**
> This worked for me, thanks!
thanks a lot, comment #11 helped me to solve here too

---

### Post by xkalibur on 2011-05-01
thanks so much, I was having this issue and thought it was fstab.etc but your solution works!  

For me I started the upgrade last night, this morning I turned on the PC and was stuck on the "/ not found".

---

### Post by jusis on 2011-05-04
thank you SO SO MUCH gryall!!!!  I, too, like Riffey#4, had to interrupt the installation, and exactly same lines appeared afterwards on the command line. when I tried gryall's solution above, all was in motion at once again, and likewise after restart all was back there!!!  thank you so much again!!  and, once again yet another reason to be happy about having ubuntu!

---


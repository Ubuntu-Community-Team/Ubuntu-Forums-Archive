---
title: "mdadm not working"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by pmdw on 2008-11-16
Hi

I have a problem with mdadm on
Ubuntu 8.04 LTS with kde 3.5.9

I am trying to get a raid 1 to work on the system
I have been using this link to get me going.
[http://man-wiki.net/index.php/8:mdadm](http://man-wiki.net/index.php/8:mdadm)

I have two disks that I want to put the raid on
/dev/sdb with partion /dev/sdb1
/dev/sdc with partion /dev/sdc1

cfdisk lists both partitions with 
the partition type as **Primary** 
the FS type as **Linux raid autodetect**

In /etc/fsab I have
/dev/md0 /var/raid ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 0
/dev/sdb1 auto nouser,defaults,atime,auto,rw,dev,exec,suid 0 0
/dev/sdc1 auto nouser,defaults,atime,auto,rw,dev,exec,suid 0 0

In /etc/mdadm.conf I have
DEVICE /dev/sdb1 /dev/sdc1
CREATE owner=root group=disk mode=0660 auto=yes
HOMEHOST <system>
MAILADDR root
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=a2ca826a:e390fd74:2ae38843:adf23e8c

I did the following command to get it started

sudo mdadm --create /dev/md0 --level=1 --verbose --raid-devices=2 /dev/sdb1 /dev/sdc1

left it running and came back and iIt all seemed to work 
and I could copy a text file onto /etc/raid.

Then when I rebooted it stopped working

When I try to enable it I get /dev/md0 is not a valid block device. return code 32 mount failure.

If I try to recreate it with
sudo mdadm --create /dev/md0 --level=1 --verbose --raid-devices=2 /dev/sdb1 /dev/sdc1

I get 
mdadm: error opening device /dev/md0 : no such device or address

Does any body know how to fix this?

thanks
Peter

---

### Post by sovietfunk on 2008-11-17
I have the same problem. I have googled and eh.. ubuugled some, and find that this is because the module "md" isn't autoloaded at boot. But not yet how to fix that. I can bring back the RAID by doing "modprobe md" and "mdadm --assemble [...]". 
Others have reported that "dpkg-reconfigure mdadm" rebuilds the boot initrd image and fixes the problem, but not in my case.

Interestingly, this is a system which worked perfectly, but which i reinstalled after an altercation with OSS4. The inly thing which is different from before the OSS4/ReInstall, is that the RAID array was --created then, and rebuilt using --assemble now. 

Is that a hint?

---

### Post by pmdw on 2008-11-18
Hi
Well the "dpkg-reconfigure mdadm" seems to have an effect of some kind. thanks :KS

As after I have run it there is still no raid but at least I can now run
sudo mdadm --create /dev/md0 --level=1 --verbose --raid-devices=2 /dev/sdb1 /dev/sdc1

and not get an error 
but this time it came back very quickly saying
mdadm: array /dev/md0 started

But when I check in the system settings /dev/md0 is disabled

Am I missing some thing here?

Is there another step after mdadm create?
thanks

---

### Post by sovietfunk on 2008-11-18
I'm not the sharpest knife on RAIDs, but I don't believe you should have to do --create more than the first time, after that it should be enough to do something like "sudo mdadm --assemble --scan --auto=md". This should give you a positive response which I can't remember at the moment. Now you should be able to "sudo mount -a" if everything is all right in /etc/fstab. If not, look there for bad settings. If "sudo blkid" does not list /dev/md0, it has not been assembled correctly by mdadm, I believe. Sorry, too tired now to go further. I haven't found out what the problem is on my system, so I'll be back..

---


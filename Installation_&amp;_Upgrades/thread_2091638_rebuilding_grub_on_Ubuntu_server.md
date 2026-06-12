---
title: "rebuilding grub on Ubuntu server"
date: 2012-12-05
forum: Installation &amp; Upgrades
---

### Post by Joespower on 2012-12-05
Hi all, hope I'm putting this question in the right place...

I'm running a hand full of Ubuntu 10.04 servers as VMs in a Vmware environment.  I also just got a new NetApp FAS2240 to use as my central storage.  I'm migrating my Ubuntu VMs to the new NetApp backed datastore, and in the process I've been trying to run NetApp's mbralign program as I do so.  This ensures maximum IO performance for my VMs.  The problem is, mbralign always hoses up grub.  If I mbralign a Red Hat or CentOS based VM, its pretty easy to recover.  In fact, this site has all of the mbralign instructions along with a video n how to rebuild grub for Red Hat and it's variants:

[http://www.sysadmintutorials.com/tutorials/netapp/netapp-how-to-use-mbralign-to-correct-misalignment/](http://www.sysadmintutorials.com/tutorials/netapp/netapp-how-to-use-mbralign-to-correct-misalignment/)

Ubuntu Server on the other hand has proven very difficult.  Can someone provide some instructions on how to rebuild grub in a rescue environment for Ubuntu Server?  I'm sure it isn't that difficult, but Googling hasn't helped much, and I'm getting behind in my work.  Any help would be appreciated...

Joey

---

### Post by darkod on 2012-12-05
Although I haven't tried it, you could simply boot the VMs with the 10.04 desktop live cd into a live session, and simply reinstall grub2 to the MBR. Lets assume the root partition inside the VM is /dev/sda1, in terminal it would be like:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

That should reinstall it onto the MBR inside the VM.

You could probably do it with the server cd in some type of rescue mode too, but I haven't used the server cd like that and can't give exact commands.

Alternatively, you can use any linux rescue cd like the System Rescue CD, chroot into the installation and reinstall grub2 from there. But the live cd procedure above should be easier.

---

### Post by Joespower on 2012-12-05
> **darkod said:**
> Lets assume the root partition inside the VM is /dev/sda1, in terminal it would be like:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

That should reinstall it onto the MBR inside the VM.


See I read something like this and tried it, but I think LVM hoses me up.  You reference the root partition and NOT the boot partition above.  The problem is, my root partition is in a LVM volume.  I think some of my problems stem from this since the LiveCD isn't LVM aware.  What could I do in this case?

Thanks!

---

### Post by darkod on 2012-12-05
OK, if you are using lvm with /boot outside it, first add the lvm2 package and activate the lvm, then mount both the root LV and the /boot partition (lets say in the example it's sda1):
```
sudo apt-get install lvm2
sudo vgchange -ay
sudo mount /dev/<VGname>/<rootLVname> /mnt
sudo mount /dev/sda1 /mnt/boot (if you have separate /boot)
sudo grub-install --root-directory=/mnt /dev/sda
```

Don't forget to use the correct VGname and rootLVname.

---

### Post by Joespower on 2012-12-05
Hmmmm... Maybe I wasn't mounting them both.  That may have been what I was doing wrong.  Awesome, thanks darkod!  I'll try this and report back.

---


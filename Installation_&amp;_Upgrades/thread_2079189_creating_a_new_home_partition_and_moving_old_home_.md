---
title: "creating a new /home partition and moving old /home in LVM disk"
date: 2012-11-01
forum: Installation &amp; Upgrades
---

### Post by attam on 2012-11-01
I just installed xubuntu 12.10 using the LVM option, with the entire system including swap and home on the same partition. I would like to change this so that /home and /swap are on separate partitions. How can I do this without re-installing xubuntu or all my applications, setting up the system from scratch?

---

### Post by jerome1232 on 2012-11-01
What's the output of this command?

```
sudo lvdisplay
```

Likely you can boot from a live cd and do a little finagling to get it right. One of the beauties of LVM is volume management is easier (imo) than messing with partitions.

---

### Post by darkod on 2012-11-01
In LVM you don't work with standard partitions, you work with Logical Volumes inside the LVM. So, depending how you installed, the /home and swap might already be in the LVM. Unless you left them out on purpose.

The lvdisplay mentioned will show all LVs that exist.

---

### Post by attam on 2012-11-01
$ sudo lvdisplay
[sudo] password for matta: 
  --- Logical volume ---
  LV Path                /dev/xubuntu/root
  LV Name                root
  VG Name                xubuntu
  LV UUID                12x0bY-8Wof-TJym-nYbN-4BTj-hwuK-jw291c
  LV Write Access        read/write
  LV Creation host, time xubuntu, 2012-11-01 14:44:04 +0200
  LV Status              available
  # open                 1
  LV Size                462.60 GiB
  Current LE             118426
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Path                /dev/xubuntu/swap_1
  LV Name                swap_1
  VG Name                xubuntu
  LV UUID                KGpZBE-9UlV-wR7D-MZ0Q-UySX-rEh6-EPWlJJ
  LV Write Access        read/write
  LV Creation host, time xubuntu, 2012-11-01 14:44:05 +0200
  LV Status              available
  # open                 2
  LV Size                2.87 GiB
  Current LE             734
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1

Thanks for the reply.
I see that the system partition has 462GB...I would like to have a partition for the OS (/) of about 15GB and have /home on a separate partition taking up about 440GB, the rest can be for swap

---

### Post by darkod on 2012-11-01
First you need to see how much are you using on / so that you know whether it can fit in 15GB. You can do that with:
df -h

If the current / usage is less than 15GB, you can shrink the root LV to 15GB, then create a new home LV with the size you want. Since it's a LV you don't need to give it 440GB right away, you can resize later.

Note that when shrinking the root LV it's VERY IMPORTANT to shrink the filesystem first, and after that the LV.

After creating the home LV and copying the data there, you will have to create an entry in /etc/fstab to mount this LV as /home.

That is the general procedure.

---

### Post by attam on 2012-11-01
I checked the / size (4.7G) so I think I'm in business now. I will try to make the necessary adjustments and submit a report on the thread, but that will have to wait until tomorrow (at earliest)...
I'm amazed how quickly questions are answered here, and appreciate the effort of everyone here sharing their wisdom on a voluntary basis.

---

### Post by jerome1232 on 2012-11-01
> **darkod said:**
> 
Note that when shrinking the root LV it's VERY IMPORTANT to shrink the filesystem first, and after that the LV.


I wanted to note, the way I do it is I shrink the filesystem to smaller than the intended size, shirnk the lv to the real intended size, than grow the filesystem to fit, I do this to avoid accidental truncation and thus breakage of the file system.

[COLOR=Red]Remember, every command I give here is just an example, you will need to adjust the voumes and volume groups and sizes to the real values. Post questions if you are unsure about anything.[/COLOR]


All of this will have to be done from a live cd, since you can't shrink a live file system. (You can grow one however)
Also when I use logical volumes, I tend to leave unallocated, space, since it's a trivial matter to grow them if needed (I also use it to create snapshots while I'm backing up).

Just giving you an example let's say I have a logical volume "backup" 40 GB's on the volume group "ubuntu" and I wanted to shrink it to 20GB's, I would do it like this.


First command checks to see what the minimum size is, let's pretend it's lower than 20GB's so I proceed, the second command reduces the volume to it's minimum size, the 4th reduces the logical volume to 20GB's, the last command causes the filesystem to fill up the logical volume.
```
sudo resize2fs -P /dev/ubuntu/backup
sudo resize2fs -M /dev/ubuntu/backup
sudo lvresize ubuntu/backup -L 20GB
sudo resize2fs /dev/ubuntu/backup
```Now you want to create a home volume on the ubuntu volume group, easy as cake, let's pretend you want it to be 100 GB's
```
sudo lvcreate -n home -L 100G ubuntu
sudo mkfs.ext4 /dev/ubuntu/home
```Then you copy your old home to the new home and add an fstab entry

```
sudo mkdir /mnt/root
sudo mkdir /mnt/newhome
sudo mount /dev/ubuntu/root /mnt/root
sudo mount /dev/ubuntu/home /mnt/newhome
sudo rsync -avr /mnt/root/home/ /mnt/newhome/
gksu gedit /mnt/root/etc/fstab
```when gedit opens, add this line at the bottom, click save then exit.

```

/dev/ubuntu/home /home ext4 defaults 0 2 			 		
```Confirm everything copied by browsing to /mnt/newhome in nautilus and ensuring it looks right, once your sure it all copied.
Clean up what was in your old home and reboot
```
sudo rm -r /mnt/root/home/*
sudo reboot
```

---

### Post by attam on 2012-11-02
Thanks for the steps...I followed your guide, Jerome and it worked well until I rebooted, upon which the boot splash screen displayed a message to the effect that there was a problem mounting, press s to skip or m to recover manually.
at first I was worried that something failed, so I started up from a live CD and used a few commands to mount and confirm that my root and home partitions still existed. Then I realized the problem was with fstab.
I reviewed your suggested line to add in fstab:
> /dev/ubuntu/home ext4 defaults 0 2
and altered it to:
> /dev/ubuntu/home /home ext4 defaults 0 2
which solved the problem, and things working well now.
I will mark this as solved.

---

### Post by jerome1232 on 2012-11-02
Ah sorry about that, I flubbed the fstab entry, I'll fix it to avoid confusion if anyone stumbles onto this thread.

Glad everything worked out for you.

---


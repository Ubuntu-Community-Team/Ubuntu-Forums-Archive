---
title: "update manager error-Not enough free space on the disk"
date: 2011-06-04
forum: Installation &amp; Upgrades
---

### Post by csaniyer on 2011-06-04
Hi all,
 
when i tried to update my ubuntu it gave me the following error:
 
"The upgrade page needs a total of 19.9M free space on /boot. please  free atleast an additional 3624k of disk space on /boot. Empty your  trash and remove temporary packages of former installations using sudo  apt-get clean"
 
please help me to fix this error. why the packages require free space on /boot. 
how to empty trash
how to  remove temporary packages of former installations using sudo apt-get clean"

screenshot attached for reference.
 
Thanks in advance.

---

### Post by Bucky Ball on 2011-06-04
Right click your Trash icon and choose 'Empty Trash'.

Open a terminal (Applications>Accessories>Terminal) and paste in the command you have above:

```
sudo apt-get clean
```

---

### Post by avtolle on 2011-06-04
Also, if the OP has multiple kernels, deleting an older kernel or kernels using Synaptic will clear space on /boot.

---

### Post by dFlyer on 2011-06-04
You can also delete *.gz file in /var/log. To do so you will need to use sudo rm /var/log/*.gz

---

### Post by csaniyer on 2011-06-05
Hi all,
I did all the above steps.
1. Trash is empty
2. sudo apt-get clean
3. removed *.gz files in /var/log

But I dont know how to check if multiple kernels are there. pls guide me.

still the same error comes.

Thanks in advance.

---

### Post by plucky on 2011-06-05
> **csaniyer said:**
> Hi all,
I did all the above steps.
1. Trash is empty
2. sudo apt-get clean
3. removed *.gz files in /var/log

But I dont know how to check if multiple kernels are there. pls guide me.

still the same error comes.

Thanks in advance.

Open Synaptic Manager and search for **linux-image** and mark the older ones for complete removal.
Then search for **linux-headers** and again mark the older ones for complete removal.

Remember not to remove the current working kernel,and if you have enough room in /boot,it is worth keeping at least one extra kernel.

Then select **Apply** and it will remove the older kernels from /boot.

What is the output from a terminal for ```
df -h
```

Also some people suggest installing "Ubuntu Tweak" and using that to clear out older kernels.Personally I use SPM to do the job.

Good Luck

---

### Post by mörgæs on 2011-06-05
You could also boot a live CD, run Gparted and increase the size of the root partition. It is not recommended to be low on disk space for root.

---

### Post by csaniyer on 2011-06-05
Hi all,

I am new to linux, in synaptic package i couldnt find any options for removing linux-image.
moreover i found these many entries in linux-image
linux-image-rt    2.6.31.11.13
linux-image    2.6.32.32.38
linux-image-server-lts-backport-maverick    2.6.35.25.36
linux-image-virtual-lts-backport-maverick    2.6.35.25.36
linux-image-386    2.6.32.32.38
linux-image-virtual    2.6.32.32.38
linux-image-server    2.6.32.32.38
linux-image-generic-pae-lts-backport-maveric    2.6.35.25.36
linux-image-generic    2.6.32.31.37
linux-image-ec2        2.6.32.316.17
linux-image-generic-pae    2.6.32.32.38
linux-image-generic-pae-lts-backport-maveric    2.6.35.25.36
linux-image-generic-lts-backport-maveric    2.6.35.25.36

In headers also some were around 40-50 packages could be found.

output of df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda11             92G   27G   61G  31% /
none                  494M  288K  494M   1% /dev
none                  501M  192K  501M   1% /dev/shm
none                  501M   96K  501M   1% /var/run
none                  501M     0  501M   0% /var/lock
none                  501M     0  501M   0% /lib/init/rw
/dev/sda9             185M  160M   16M  92% /boot
/home/san/.Private
                       92G   27G   61G  31% /home/san

how to proceed further.

thanks in advance.

---

### Post by mörgæs on 2011-06-05
This computer has had a looong and winding history through the releases from 9.10 and maybe earlier. A clean install would be a good investment in order to get a stable system.

---

### Post by plucky on 2011-06-06
> I am new to linux, in synaptic package i couldnt find any options for removing linux-image.
moreover i found these many entries in linux-image

Only the ones with the green marker are installed.If you right click on ones with the green marker,you will get the option to "completely remove".
Be careful about which ones to remove.

The same applies to installed linux-headers.

> /dev/sda9 185M 160M 16M 92% /boot

This is the reason for the original problem.

Good Luck

---


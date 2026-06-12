---
title: "Best ubuntu partition setup?"
date: 2006-08-03
forum: Installation &amp; Upgrades
---

### Post by nosam on 2006-08-03
I have an 80GB hard drive with XP on about 50GB of that space.  At the moment I have Ubuntu installed on about a 25GB space with a 1GB swap.  I would like to re-do my partition setup/ubuntu installation and use maybe only 10-15GB of that space for Ubuntu and leave the rest of the unused space for anytime I may want to try another distribution (leaving my XP partition alone).  How do I do this properly?  

I previously had Ubuntu installed on a smaller partition after XP on the drive, and then installed Kubuntu on what space was left.  I then decided to wipe off Kubuntu but didn't know that I would lose my bootloader in the process (as the grub from kubuntu had taken over, i guess), so that was a little nightmare that I went through.  How do I set this up so I can have XP, Ubuntu, and then a free, smaller partition for any other distribution later on *without* running the risk of losing my ubuntu bootloader?  XP is at the beginning of the drive, do I need to install Ubuntu at the end of the drive to be able to do this?  I still need Windows but I like Ubuntu a lot and would like to use it more.  I just want to be able to occaisonally try other distros without screwing anything up, particularly my bootloader.

Thanks.

Also, when having two linux distros on one drive do you need two swap partitions?

---

### Post by eXisor on 2006-08-03
I'd split the 15gb into 3 partitions:

1) 5 gb for root, ie. the basic system
2) 5 gb for /usr/, ie. for installing new programs
3) 5 gb for /home/, for my download, shares, music, etc.

I'd use a swapfile on /home/ for the swap space, NOT a swap partition. This means I can grow and shrink the swapfile space as I like without having the limits one has with a partition. Once I get the system fully setup with all my goodies, I'd probably move the swapfile to root since root doesn't grow much after the intitial install. 
BTW, this also implies I never install programs to /opt/. I use /usr/local/ for that.

---

### Post by nosam on 2006-08-03
> **eXisor said:**
> 
I'd use a swapfile on /home/ for the swap space, NOT a swap partition.

How would I do this?  In the partition manager during ubuntu installation? 

Also, does doing this keep the bootloader in place should I install another distro?

Thanks.

---

### Post by eXisor on 2006-08-03
Assuming you have enough ram to install without a swap, this is how to go about it..

1) Install to the partition stage
2) delete the 1gb swap partition
3) create 1 bootable partition and set mountpoint to root (it should default to this)
4) create second partition and set mountpoint to /usr/
5) create third parition and set mountpoint to /home/

finish install and when you get in, finally, 

6) cd /home/
7) sudo dd if=/dev/zero of=/swapfile bs=1024 count=65536
Note: 65536 translates to 64mb swapfile, 65536*2=131072 is 128mb etc. Choose the size you need.
8.) sudo mkswap /swapfile
9) sudo swapon /swapfile
10) sudo gedit /etc/fstab
and add the following
11) /home/swapfile swap swap defaults 0 0
which will mount the swapfile on startup.

If you don't have enough memory to install without a swap, then 
in step 5, make a partition of only 4gb, and do
5a) create a 1gb swap partition
Since this is below the 4gb partition you made in 5), you can erase the swap later, after creating the swapfile as above, and easily resize the 4gb parition to use all 5gb.

If you ever want to resize the swapfile, simply goto step 6), cd to where you want it, and proceed with the steps. At the end, also remove the old swapfile line from the fstab file, reboot and then remove the old file to free the space.

---

### Post by az on 2006-08-03
> **nosam said:**
> I may want to try another distribution (leaving my XP partition alone).  How do I do this properly?  

...

Also, when having two linux distros on one drive do you need two swap partitions?

Just shrink your ubuntu partition by however big you want to leave to a new distro.  Then install the new distro on that free space.

I do not reccommend anything other than the all-on-one partition unless youhave specific needs to do so.  Don't make your life complicated.

And a swap file is not very good for performance - avoid it.  You will never really need to change your swap anyway.

Yes, you can use the same swap space for two distros, with one exception.  If you use software-suspend (suspend-to-disk or hibernation) it writes the contents of your ram to the swap space.  You cannot share it without losing your data in that case.

So your solution is pretty simple.  Just shrink the ubuntu partition and you are good to go.

If your new distro rewrites grub, all you will have to do is to chroot into ubuntu and run

sudo grub-install

and you have restored your grub.

---

### Post by eXisor on 2006-08-03
Sorry, I forgot about your bootloader question..

This should not affect the bootloader at all. Grub will make itself the bootloader and it is up to the next distro you choose to play well with grub.

---

### Post by eXisor on 2006-08-03
[quote='Azz']And a swap file is not very good for performance - avoid it. You will never really need to change your swap anyway.[/quote]

I didn't know a swap partition is quicker than a swapfile. Surely they are both mounted and thereafter you're within the mounted filesystem, operating at the speed of the hd? Anyhow, I bow to your greater wisdom, but this is not my experience. (unless the swapfile is fragmented, which with a clean install it shouldn't be?).

As for resizing the swapfile, I admit my noobness, limited hd space and lack of forethought made me need to do this several times. And of course I put the swap partition on hdb1, with /home/ on hdb2, so in the end I had to move /home/ to avoid reinstalling from scratch. Reinstalling isn't so bad, it's the 70+mb of updates that's a bandwidth chewing killer.

---

### Post by nosam on 2006-08-03
Ok, I think I'll stick to what azz suggested since it seems like the easier route for me.  But thanks to both of you for the help, very much appreciated!

---

### Post by eXisor on 2006-08-03
No problem. Azz has given me food for thought as well.

---


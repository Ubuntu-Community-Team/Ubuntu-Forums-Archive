---
title: "Sadly Hardy and I are not in love. . ."
date: 2008-10-02
forum: Installation &amp; Upgrades
---

### Post by brenbren on 2008-10-02
Thanks to an awesome person who helped me fix the problem of updating I updated from fiesty to hardy, with a stop on gutsy in between. Unfortunately I am not in love with hardy, not like I was with that fiesty fawn. Everything is very slow and for some reason I no longer have permissions to edit my hellanzb.conf file. I've checked around trying different solutions to common problems with this type of error and with gedit (my fav editor) to no avail. So does anyone know how I can go back to using fiesty?:confused:

---

### Post by wpshooter on 2008-10-02
IMO, you should have stopped at Gutsy.  Hardy = no fun.

---

### Post by Sef on 2008-10-02
> So does anyone know how I can go back to using fiesty?

It's not recommended.  Its support will run out in about 3 weeks.   Better to wait for Intrepid Ibex to be stable (30 Oct 2008.)  Best way to install it would be a clean install, although you would lose all of your settings.

Also you could do a clean install of Hardy Heron.

---

### Post by brenbren on 2008-10-02
this clean install intrigues me:o please explain, I don't know much but I do learn

---

### Post by SuperSonic4 on 2008-10-02
A clean install would be to download the live cd, burn it to disc and install from the boot menu.

---

### Post by haydnc on 2008-10-02
SuperSonic4 is right about how to do a clean install of Ubuntu 8.04.1.


I can confirm that as long as you had backed up the entire contents of your /home drive you'd be very unlikely to lose anything when doing a clean install. I know I was having issues after upgrading to Hardy and a clean install fixed that up for me.

If you put /home on a separate partition when you first installed Ubuntu you may not even need to back anything up - just make sure you don't format whatever partition has /home on it.

Let us know if you need a more in depth explanation and I'll do what I can to help out.

---

### Post by brenbren on 2008-10-02
so does backing up include programs or is it just the data I use and store like music and .opp? Can I just burn these things to a disk or do I need to trot out rsync or tar? And also, do I need to uninstall current hardy before booting of the cd?

---

### Post by Torquemada28 on 2008-10-02
> **brenbren said:**
> do I need to uninstall current hardy before booting of the cd?

No. During the install you'll have the opportunity to configure the disks you want to use. You will be able to format the drive/partition you are currently using before installing your fresh Hardy on there. That will wipe all traces of the current system. While you have the opportunity, I would suggest that you create a separate partition for /home during the install. There are many threads that can guide you on how this is done, or someone could post instructions here.

The relationship can be salvaged if you just offload your baggage from your previous relationship and start afresh. ;)

---

### Post by brenbren on 2008-10-03
So the good news is that the clean install of Hardy fix all the issues I was having. Hurray!
Sadly, when trying to fallow instructions to back up via a partition I have somehow managed to lose all of my documents, pictures, and music. Sad.
If anybody has any helpful hints, or places in the California Orange County area where I could go and get help, that too would be outstanding.

---

### Post by Sef on 2008-10-03
> If anybody has any helpful hints, or places in the California Orange County area where I could go and get help, that too would be outstanding.

Post a message in Ubuntuforums [California LoCo]("http://ubuntuforums.org/forumdisplay.php?f=188").

---

### Post by brenbren on 2008-10-06
okay. Got photorec, and it looks very promising; got an external drive a 500 GB Freeagent. Now all I need is to get the d*** freeagent to be have read and write permissions so I can us it as where I want the recovered files to go. I've already used gparted to format the drive to ext3. Command df -h output: Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              37G   36G     0 100% /
varrun                502M  104K  501M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   60K  501M   1% /dev
devshm                502M   48K  501M   1% /dev/shm
lrm                   502M   39M  463M   8% /lib/modules/2.6.24-19-generic/volatile
overflow              1.0M   96K  928K  10% /tmp
gvfs-fuse-daemon       37G   36G     0 100% /home/brenbren/.gvfs
/dev/sdb1             463G  199M  439G   1% /media/disk
 but when in photorec /media/disk is not an option. 
Please help, I am so close!!!

---


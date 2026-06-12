---
title: "Install Updates on sevral systems"
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by Jonker on 2011-04-17
Hello all, I hope this is in the wright Forum (if not, please move)

I was wondering if I could download the updates for Ubuntu once, and then install them on sevral systems. I have two systems and with this method, I would half the update amount.

Thanks for you help.

---

### Post by Jonker on 2011-04-19
is this possible?

If not, please tell me, and I'll forget about it.

If yes, please help me.

Thanks!!!

---

### Post by Fire_Chief on 2011-04-19
Since it's only 2 systems, I would simply perform the updates on the first one, then copy the downloaded deb files to the second box. If you put them in the same location as on the first box, the Update Manager shouldn't download them again.

If you had many systems to manage like this I'd suggest looking into Landscape Dedicated Server from Canonical ([http://www.canonical.com/enterprise-services/ubuntu-advantage/landscape/dedicated-edition]("http://www.canonical.com/enterprise-services/ubuntu-advantage/landscape/dedicated-edition"))

Cheers!

---

### Post by garvinrick4 on 2011-04-19
Not that I have seen to make sure you get all the right packages upgraded and new ones installed but you can mount another partiiton to /mnt and bind, /dev , /dev/pts , /proc and /sys to /mnt then cp /etc/resolv to mnt and chroot and then update and upgrade for there.
Saves rebooting if that is any help. Can do this in Ubuntu to any yum or zyppers that I have tried also as long as same architecture. Then umount all. Can make yourself a couple of strings of code to do this with and copy and paste as not to have to type so much. Would be nice to have a script to use and just change the sda# but cannot write script.
I got some time so here is code: Use your own sda# (dpkg and -f install is just to make sure dependencies are cool.) Have a good day. ```

                                 [CODE]sudo mount /dev/sda9 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
``` ```
apt-get update && apt-get upgrade
``````
dpkg --configure -a
``````
apt-get -f install
``````
exit
```[/code]  Do not forget to unmount                               ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
```

---

### Post by Jonker on 2011-04-19
Ok, thanks both

I think, that I'll first try out the from Fire_chief, and if that doesn't work, I'll try out the second one. (Nothing against you method, but it just seems a little complicated for me).

So, where dose Ubuntu save the Updates?

Thanks!!!

---

### Post by Fire_Chief on 2011-04-20
They should be located at /var/cache/apt/archives.

Have a look at this article. It may help ease the update process long term.
[https://help.ubuntu.com/community/Repositories/Personal]("https://help.ubuntu.com/community/Repositories/Personal")

Cheers!

---

### Post by Elfy on 2011-04-20
apt-cacher-ng worked well here when I used it.

The machines need to be networked though.

Copying the cache works though

[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)

---

### Post by Fire_Chief on 2011-04-20
Ah...now that's pretty spiffy too!

---

### Post by Jonker on 2011-04-20
So, if I copy /var/cache/apt/archives from one machine to the other, it should recognise them auto, or do I have to run some 'update' command'?

The problem is, the one system is on an ext. HDD and the other one is on a Desktop-PC. So it would be difficult connecting them...

Thanks!!!

---

### Post by testarap on 2011-04-20
> **Jonker said:**
> Hello all, I hope this is in the wright Forum (if not, please move)

I was wondering if I could download the updates for Ubuntu once, and then install them on sevral systems. I have two systems and with this method, I would half the update amount.

Thanks for you help.
Update you Ubuntu regularly. It will automatically clear old updates. or u can use System > Administration > computer Janitor to clean up.

**clean up commandline**
[http://unixblack.blogspot.com/2011/02/cleanup-ubuntu-linux-command-line.html ]("http://unixblack.blogspot.com/2011/02/cleanup-ubuntu-linux-command-line.html")

**new stable distribution update graphically:**
[http://unixblack.blogspot.com/2011/04/ubuntu-version-update.html](http://unixblack.blogspot.com/2011/04/ubuntu-version-update.html)

---

### Post by Elfy on 2011-04-20
If the OP runs apt-get clean or autoclean they'll have to download the packages again - exactly the opposite of what they are hoping to achieve :)

---

### Post by Elfy on 2011-04-20
> **Jonker said:**
> So, if I copy /var/cache/apt/archives from one machine to the other, it should recognise them auto, or do I have to run some 'update' command'?

The problem is, the one system is on an ext. HDD and the other one is on a Desktop-PC. So it would be difficult connecting them...

Thanks!!!

Copy them and run an update.

---

### Post by Jonker on 2011-04-20
How?
 With the update-manager?
or with 'sudo apt-get update'?

---

### Post by Elfy on 2011-04-20
> **Jonker said:**
> How?
 With the update-manager?
or with 'sudo apt-get update'?

sudo apt-get update always worked for me when I was copying cache

I've no idea about the update manager as I tended not to use it.

---

### Post by Jonker on 2011-04-20
> sudo apt-get update always worked for me when I was copying cache
even, when I'm not connected to the internet?

---

### Post by Elfy on 2011-04-20
It still needs to know the packages are available.

You might though need to disable all the repos it will try and search for. 

Not sure never done it on a netfree machine.

If it's not connected to the net why do you need to update it? As long as it works it should be fine without.

---


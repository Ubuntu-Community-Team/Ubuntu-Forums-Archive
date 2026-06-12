---
title: "mdadm fails to load after upgrade to 7.10"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by keb on 2007-10-19
After upgrading to 7.10 using the graphical update-manager and rebooting, my system doesnt automatically load the md module and mount the raid partitions.

Because it is only my /home directory in raid it is not critical for booting and i can recover each time i reboot the machine with the following sequence of commands:

```

(switch to text console)
sudo -s
modprobe md
mdadm --assemble --scan --auto=md    # array is defined in /etc/mdadm/mdadm.conf
mount -a                              # /home is mounted on /md0 in /etc/fstab
/etc/init.d/gdm restart
(login as normal)

```

Putting those commands in /etc/rc.local did not work, but anyway i would like to fix my system so that raid is supported first thing during boot and i don't have to type that stuff, and so that it works smoothly next time i upgrade to 8.04...

I checked the threads with similar keywords and didnt find this problem.

---

### Post by spetko on 2007-10-21
Thanks, this saved me from a small heart attack!!!

But on the serious side. I have exactly the same problem. I'm just posting this to let you know that this is not isolated incident. I have no idea how to resolve it, unfortunately.

Hope to see a solluton soon. 

spetko

---

### Post by triplep on 2007-10-22
This saved my bacon as well!!!

To me, it looks like my UUID no longer matches the superblock, after manually assembling, it was still a no go. I had to remove the UUID and specify the drives using a comma delimited list in the ARRAY line.

Thanks again!

Now we just need to know the cause!

---

### Post by OliW on 2007-11-20
I'm in the same situation too. I installed mdadm after getting gutsy and it never loads it. Serious bug? It's certainly very annoying having to modprobe, assemble and mount each time!

---

### Post by OliW on 2007-11-23
Well I fixed it.

I ran:
sudo dppg-reconfigure mdadm

Accepted all the defaults. If you've never played silly-buggers with your kernels, this *might* fix it for you, but as it was, I have built a couple of kernels before and the initramfs-update was trying to write to one of those (that I don't use). So I had to remove all the custom kernels and reinstall 2.6.22-14-generic in synaptic. I then ran dpkg-reconfigure again, it wrote the to correct kernel image, I rebooted, and my RAID works. Woo!

Oh one important (I think) note, my mdadm.conf contains the UUID of my HDs, not names because the names seem to be quite fluid (they kept changing name every boot). If you're not set up like this, I suggest doing so.

---

### Post by loserratio on 2007-12-05
same problem here. dpkg-reconfigure doesn't change the behaviour.
did anyone find a solution yet?
@OliW: Could you post your mdadm.conf?

---

### Post by OliW on 2007-12-05
Sure. ```
DEVICE partitions
ARRAY /dev/md0 UUID=c377ed58:de1672ad:ca121d7f:e5e85cce
```

Does "mount -a" provide any error messages?

---

### Post by loserratio on 2007-12-05
Thanks for the quick answer.


The main problem occurs when I try to assemble my raid1:
```
root@w00tcube:~# mdadm --assemble --scan --auto=md
mdadm: error opening /dev/md0: No such device or address
mdadm: error opening /dev/md/0: No such device or address

```

This command only works when I use "modprobe md" before I execute it. Seems like the md module isn't loaded by default!? That's why I tried up to add "md" to /etc/modules which didn't work again...
Is there another way to load the md module or do you see any other probs?


additional info:
mount outputs the following status (which is normal cause the raid device /dev/md0 isn't there):
```

root@w00tcube:~# mount -a
mount: special device /dev/secure/projects does not exist
mount: special device /dev/secure/documents does not exist
mount: special device /dev/secure/pics does not exist
mount: special device /dev/secure/albums does not exist
```

note: I use lvm to partition my /dev/md0 again. my vg is called "secure"

---

### Post by loserratio on 2007-12-05
ok. I've given up.

I'm currently copying all my data to non-raid devices since my simple raid1-setup doesn't work with gutsy on startup anymore.

I guess that the following bug was the problem:
[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/103177](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/103177)
This is the workarround for the bug (which I don't use cause I don't want to wait 10 seconds more at startup):
[http://ubuntuforums.org/showpost.php?p=2236181&postcount=5](http://ubuntuforums.org/showpost.php?p=2236181&postcount=5)

---

### Post by OliW on 2007-12-05
Sorry I didn't get a notification to the first reply or I would have been here sooner! 

When you dpkg-reconfigure mdadm, does it [initramfs-update] write to the correct boot image? That was my initial problem which led me onto reinstalling my kernel (far less painful than it sounds, through synaptic). I'd say you should give reinstalling the kernel a go before you start dismembering the array.

---

### Post by loserratio on 2007-12-06
no problem. I'm always happy about replies, no matter WHEN they are posted ;)

I had to switch to a non-raid solution cause the system is really important for some folks in my company and they would be a little shocked if startup fails because of disks errors ;)

I'll uprade my test system to gutsy now and see if the same error occurs. if yes, I'll try the kernel reinstall :)

---

### Post by defaulk on 2008-05-21
I have the same problem, only with the upgrade to 8.04.  I have to do modprobe md and so on to get my raid up.

sudo dpkg-reconfigure mdadm doesn't do anything for me and I did check to see if initram was updating the proper entry.  I'm pretty sure it is.

---


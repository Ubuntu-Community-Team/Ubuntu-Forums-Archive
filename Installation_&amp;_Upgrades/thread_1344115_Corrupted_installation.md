---
title: "Corrupted installation"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by Alan502 on 2009-12-02
Good day everyone and thanks for your desire of helping me with my problem, i'll try to describe it with the best detail possible.

Basically, i've got a corrupt kubuntu installation for being impatient. Last night i edited some partitions, moving them, what eventually crashed my grub. I knew that i needed to reinstall it, but my internet connection was down and i wasnt able to review the commands. So, i decided to try today morning. For my surprise, my connection was not working today neither. So, i remembered i read about a guy explaining how to reinstall grub by running the ubuntu installation and then quiting at some point. I was a little bit desperate and decided to try it, something that was really dumb. I ran the ubuntu installation, but when the dialog said "removing old files" (or something similar) i quickly quited and rebooted to see if, at least, grub had restored. Nothing had changed so my only hope was to wait until my internet connection came back, and it did at noon. Then i could visit ubuntu help and successfully restore my grub. But now, that i have my grub restored, i noticed that i cannot longer boot into kubuntu. I think this might be because of the error i did quitting at mid ubuntu installation. I notice that im missing some directories in the root of my kubuntu installation (such as /bin) and that's what might be causing the problem.

Is there any practical way i can fix this? Is formating my only option?

Thanks:D and i will wait for your replies.

---

### Post by dhavalbbhatt on 2009-12-02
Some additional information will be helpful - what version of Kubuntu are you trying to install? 9.10 has a different version of GRUB than 9.04 and below.

For 9.10, you can learn all about GRUB 2 here:
[http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305](http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305)

For upto version 9.04, learn all about GRUB here:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Hope it helps.

---

### Post by ibuclaw on 2009-12-02
As per the conversation in IRC,

Can you boot into a LiveCD, open a terminal, and paste in the following commands:
```
sudo mount /dev/sda6 /mnt
```
```
sudo chroot /mnt
```

If you can chroot into the broken system, it may be recoverable - if you cannot, your only option is to rebuild.

Regards
Iain

---

### Post by Alan502 on 2009-12-02
Thanks tinivole, i cant chroot to my directory but my home files and most of my stuff is still there. Do you think formatting is my ultimate solution?

---

### Post by ibuclaw on 2009-12-02
> **Alan502 said:**
> Thanks tinivole, i cant chroot to my directory but my home files and most of my stuff is still there. Do you think formatting is my ultimate solution?

If it were my own setup - I'd probably do some mischievous just for testing whether or not something works.
But tbh trying to do anything which will make the current installation boot and run up to the point of you logging in may have bad repercussions in future upgrades of software.

You have the following directories to backup:
```

/home
/var/cache/apt/archives

```
And you should be all OK to reinstall the system.

It generally doesn't matter how you backup your personal files.
For the archives though:

**Backup**:
```
cp /mnt/var/cache/apt/archives/*.deb **/path/to/backup/**archives
```
**Restore**:
```
sudo cp **/path/to/backup/**archives/*.deb /var/cache/apt/archives
```

Regards
Iain

---

### Post by Alan502 on 2009-12-02
Thanks for all your help! i'll reinstall as you say, i think its the best option. Thanks for the information about how to back up my apps, i will copy them. However, i think i'll rather change to 64 bit since it was somehting i wanted to do for some time. I know my apps wont work but i'll download their 64 bit versions and the 32 bit libs anyway.

Your advice was really helpful. Thanks!

---

### Post by efflandt on 2009-12-02
As you found out, aborting or shutting down in the middle of installation is not the way to restore a system.  Certain main directories are removed and replaced, and if you abort before those are replaced, they do not exist.  And that would not restore grub, which I believe is one of the last things done during installation (and grub version varies for most recent Ubuntu release depending whether you upgrade or fresh install).

If you have your home dir on a separate partition, or from live CD or bootable USB can back that up to cdrom, dvdrom, or USB drive or device, you could reinstall your system, whatever programs, and move on.

Grub can be intimidating, especially when you are not familiar with the command line and two different version.  But practice under adverse conditions can sometimes be the best teacher to become familiar with the system.  I knew nothing about grub until I had some issues to resolve.  So when I recently accidentally put grub on the mbr of my main hard drive, instead of the USB device I was installing to, I knew what I had to do.

---


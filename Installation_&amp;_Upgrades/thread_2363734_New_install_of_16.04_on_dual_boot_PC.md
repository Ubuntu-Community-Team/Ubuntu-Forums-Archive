---
title: "New install of 16.04 on dual boot PC"
date: 2017-06-13
forum: Installation &amp; Upgrades
---

### Post by Panawe on 2017-06-13
Hi,

I have installed Ubuntu 16.04 on a friend's PC where it lives side by side with Windows XP. There was an existing, though unused, version of Ubuntu, 10.04, already there and I chose to upgrade this rather than do a fresh install. Boot screen OK and can boot into either OS with no problem.

But: whenever 16.04 loads it always checks the hard drive (sda5) and seems to take a long time. Then it briefly goes into a command line login before, when no action is taken, going into the familiar Ubunutu opening screen. Can anyone suggest what might be wrong and how to fix it?

TIA

---

### Post by ubfan1 on 2017-06-13
Try running sudo systemd-analyze  and take a look at the /var/log/Xorg.0.log.

---

### Post by Panawe on 2017-06-14
Thanks, will do. I won't be seeing the owner of the PC until next week so I'll do it then.

---

### Post by RobGoss on 2017-06-14
I would recommend doing a fresh installation of the latest Ubuntu 16.04.2 only to avoid problem you will have if you try upgrading from 10.04 . 

You you attempt to upgrade the current OS of Ubuntu on that machine I'm almost certain you'll run in to issues

---

### Post by Panawe on 2017-06-14
If I do that how can I keep the bits that are working okay like Thunderbird and Firefox? Is it just a matter of saving the Home directory?

---

### Post by RobGoss on 2017-06-14
You can choose to backup the home directory, I don't think it would be hard to get Thunderbird and Firefox as it was with the new Installation

I would strongly advise to fresh install

---

### Post by sccman on 2017-06-15
To me it sounds like you have a mounting problem on one of your partitions/hard drives. sda5 signifies Drive A, Partition 5. It should be an easy fix without reinstalling Ubuntu.

Run:

```
cat /etc/fstab
```

And:

```
df -Th | grep /dev
```

And copy and paste the output of those two commands.

---

### Post by Panawe on 2017-06-22
Have reinstalled 16.04 but the problem persists. Everything else works so I'm going to try sccman's suggestion.

There will be delays between posts as I only get access to my friend's computer once a week.

---

### Post by Panawe on 2017-06-27
Okay, here goes.

$ cat /etc/fstab 
# /etc/fstab: static file system information. 
# 
# Use 'blkid' to print the universally unique identifier for a 
# device; this may be used with UUID= as a more robust way to name devices 
# that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type> <options>       <dump>  <pass> 
# / was on /dev/sda6 during installation 
UUID=31f645b9-e869-451b-a86b-e2b4d34309c8 /               ext4  errors=remount-ro 0       1 
# swap was on /dev/sda5 during installation 
UUID=bc338ba9-69f2-4d3f-9511-9e1dea8c94ba none            swap  sw              0       0 

$ df -Th | grep /dev 
udev           devtmpfs  1.9G     0  1.9G   0% /dev 
/dev/sda6      ext4      254G  8.4G  233G   4% / 
tmpfs          tmpfs     1.9G  220K  1.9G   1% /dev/shm 
$

Make any sense? Still goes into command screen before booting into the Ubuntu start screen.

TIA

---

### Post by johndough2 on 2017-06-29
Hi

The delay brings things to mind.
My opensuse holds in 2 places while my Debian doesn't.
One is while the network manager brings up the network, and the other is a device check.  This I think is when it is reading a swap file for the previous settings.  In grub there is an option on where to store this.  So if you have several partitions with settings / desktop / data on there will be a delay.

In your case I don't have a definitive answer.

---

### Post by sccman on 2017-07-02
Okay it sounds like the problem is with the swap partition (sda6). Ubuntu uses the swap partition if you run out of RAM memory space while using your computer.

In most cases, you may be able to get away without needing the swap partition if you have enough RAM. How much RAM do you have right now?

---

### Post by Panawe on 2017-07-04
Checked today and the RAM is 4Gb - 3850Mb (or thereabouts).

---

### Post by sccman on 2017-07-07
Okay your friend's RAM should be fine for general, non-gaming use. We'll disable the mount for the swap partition (sda5). 

```
$ cat /etc/fstab 
# /etc/fstab: static file system information. 
# 
# Use 'blkid' to print the universally unique identifier for a 
# device; this may be used with UUID= as a more robust way to name devices 
# that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type> <options>       <dump>  <pass> 
# / was on /dev/sda6 during installation 
UUID=31f645b9-e869-451b-a86b-e2b4d34309c8 /               ext4  errors=remount-ro 0       1 
# swap was on /dev/sda5 during installation 
UUID=bc338ba9-69f2-4d3f-9511-9e1dea8c94ba none            swap  sw              0       0 

```

Based on the information you gave above, edit the file in nano as root:

```
sudo nano /etc/fstab
```

Type in your friend's password, and find the line that says:

```

# swap was on /dev/sda5 during installation 
UUID=bc338ba9-69f2-4d3f-9511-9e1dea8c94ba none swap sw 0 0

```

And put a hashtag (#) in front of UUID like this:

```

#UUID=bc338ba9-69f2-4d3f-9511-9e1dea8c94ba none swap sw 0 0

```

Save it (Ctrl + O, then Enter), exit (Ctrl + X), and reboot. The waiting should be gone now.

Have your friend use the computer as they normally would for a week or so. It should fix the issue, but if they experience any lagging, crashes, or other problems let us know.

---

### Post by Panawe on 2017-07-07
Jolly good. Will do on Tuesday and report back.

Thanks.

---

### Post by Panawe on 2017-07-12
This hasn't made any difference, I'm afraid. Just for luck I tried #ing out this line:

> UUID=31f645b9-e869-451b-a86b-e2b4d34309c8 /               ext4  errors=remount-ro 0       1 

Disaster! I managed to recover the system and the situation now is *status quo ante*.

---

### Post by sccman on 2017-07-18
Go ahead and remove the # I told you to add.

Can you upload a picture of your screen when you have to wait?

---


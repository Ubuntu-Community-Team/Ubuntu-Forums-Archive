---
title: "Ubuntu 10.04.1 mandriva 2010spring dual boot..."
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by geirknappen on 2010-11-09
I have used ubuntu for som years now, I thought It could be nice to try a kde focused linux distro, so I installed mandriva spring.

The problem is that only the ubuntu LTS boots, and the mandriva part just stops after (and I don't know where to start, and what is relevant to write)

"Bios edd facility v.0.16 2004-jun-25, 0 devices found, 
Edd information not available,
md: skipping autodetection of RAID arrays. (raid= autodetect will force)
VFS: cannot open root device "UUID (lots of numbers and letters)" or unknown
Please append correct "root=" boot option here are the available partitions:
Kernel panic - not syncing: VFS Unable to mount root fs or unknown block (0,0)
Pid: 1, comm: swapper Not tainted 2.6.33.7-desktop586-mnb #1

Call trace:
 (this looks chaotic)

_  "


What to do? Ask Mandriva forum?

---

### Post by tommcd on 2010-11-10
Are you still using Ubuntu 9.04, as it says in your profile? Ubuntu 9.04 reached end of life in October:
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
Also, and more to the point, 9.04 used grub-legacy. Ubuntu 9.10 and beyond use grub2.
Since your post referenced LTS, I will assume you are using 10.04.
When you installed Mandriva, did you allow it to install grub to the MBR, or did you keep Ubuntu controlling the MBR?
The error you are getting is likely due to the Mandriva entry in grub not being configured correctly.
It looks like a problem with those annoying UUIDs. Ironically, this was the very thing that those UUIDs were supposed to save us from!
Run "*sudo blkid*" from the terminal. Ensure that the UUID for Mandriva in your /boot/grub/grub.cfg file configuration file matches the UUID for Mandriva.
Or change the UUID to the old way: /dev/sdXY, where X is the hard drive # and Y is the partition # in grub. Remember, grub2 counts hard drives starting from 0, and partitions starting from 1.
Here is how to setup custom boot entries in grub2 for booting other distros:
[https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries](https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries)
I have used this method for booting Slackware's generic kernel ever since Ubuntu switched to grub2 and it has never failed me.
NOTE: The (better) tutorial I actually used was at [http://wiki.ubuntu.com/Grub2](http://wiki.ubuntu.com/Grub2), but that has mysteriously vanshed! It now redirects to the the first link I posted.
Also, did you try simply running: "*sudo update-grub*" from the terminal after you installed Mandriva?
Write back if you need more help.

---

### Post by geirknappen on 2010-11-10
> **tommcd said:**
> Are you still using Ubuntu 9.04, as it says in your profile? 
...

Also, did you try simply running: "*sudo update-grub*" from the terminal after you installed Mandriva?
Write back if you need more help.

Using 10.04.1... I do like this system. Updated my profile now. 

Sudo update grub... For a litte second I felt like a child on Christmas eve thinking there would be an easy solution to this, but unfortunatly this did not work.

The blkid gives me this:

/dev/sda1: UUID="8901a0ae-2841-4c44-b26b-a04948811d4d" TYPE="ext4" 
/dev/sda5: UUID="ece97fa9-f102-42d5-b2cc-e0e55cc0384c" TYPE="swap" 
/dev/sda6: UUID="84fc37e0-d014-4282-9527-d9aedf4f1528" TYPE="ext4" 
/dev/sda7: UUID="224e9950-c005-4de5-ab64-be9d3265b92d" TYPE="ext4" 
/dev/sda8: UUID="4aad708b-cdc8-48cb-a91e-d6ea595271ec" TYPE="swap" 

Custom boot entries sounds difficult, and I do have alot of schoolwork to do, so I think I will try to find a solution later.

---

### Post by tommcd on 2010-11-10
So what happened when you ran "*sudo update-grub*"? 
Post your: */boot/grub/grub.cfg* file here. Posting just the latter part of the file that has the operating systems is fine.
For reference, here is my custom boot entry for Slackware that I created in my */etc/grub.d/* directory:
```

menuentry "Slackware32-13.1 on /dev/sda5" {
        set root=(hd0,5)
        linux  /boot/vmlinuz-generic-smp-2.6.33.4-smp root=/dev/sda5 ro 
        initrd  /boot/initrd.gz
}

```
I named this file **31_Slackware32-13.1** so it would be listed after the Ubuntu entries in grub2. You can use it as a guide. 
Just change the **menuentry** to Mandriva. 
Then change the **set root=** entry to your partition number for Mandriva.  
Then change the **linux** line to Mandriva's vmlinuz kernel number that will be found in Mandriva's boot directory. (Notice that I did not even bother with those annoying UUIDs. I just used root=/dev/sda5).
Add the **initrd** line if Mandriva has an initrd in it's boot directory.  
All custom boot files must be made executable, like this:
```
sudo chmod +x 31_Slackware32-13.1
```
Then just run "**sudo update-grub**" and you should be able to boot Mandriva if you created the custom boot file properly.

FYI: You only need 1 swap partition. You do not need a separate swap for each distro. I have Ubuntu (32bit), Slackware (32bit), and Salix (64bit) all sharing the same swap partition.

---


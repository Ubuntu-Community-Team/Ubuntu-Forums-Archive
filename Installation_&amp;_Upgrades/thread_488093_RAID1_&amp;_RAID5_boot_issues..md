---
title: "RAID1 &amp; RAID5 boot issues."
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by Qumefox on 2007-06-29
Here's my setup. 3 500gb sata2 drives on a promise SATA300 TX4 running feisty

1st device - 30mb RAID1 partition (/boot), 160mb swap partition, rest of drive is RAID5 (/)
2nd device - 30mb RAID1 partition (/boot), 160mb swap partition, rest of drive is RAID5 (/)
3rd device - 190mb swap partition, rest of drive is RAID5 (/)

After having to play stupid grub tricks to get the install to boot due to the SATA300 reversing the 1st and 3rd device to the kernel compared to the order the bios displays them to grub, I finally got the system to load grub and try to boot the system, regardless of if any individual drive was unhooked (simulating failure) The problem i'm running into is with the raid5 array. 

with any single drive unhooked, it doesn't recognize the RAID5 array that / resides on.  It stops here at boot.

Starting up ...
Loading, please wait...
mdadm: No devices listed in conf file were found.


I don't really want to actually start using this machine until i'm certain it can run with a failed drive. So any help would be appreciated

---

### Post by Pumalite on 2007-06-29
If you want to run Ubuntu without problems; get rid of Raid arrays. If you insist, there is this:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Qumefox on 2007-06-29
I forgot to mention that it runs fine if all drives are present. It only has problems when one drive is missing

And Pumalite, i've had enough HD's die, that i'm not building a fileserver without some form of redundancy, and 1 TB is a hell of alot of dvd's to burn, or one expensive *** tape drive.

And no, i'm not using fakeraid. Actually the Promise SATA300 tx4 isn't even capable of fakeraid. It's flat out just a SATA2 controller, nothing else. 

The RAID1 and RAID5 arrays are both software.

The RAID is mandatory, so if anything goes, it'll be ubuntu. I'll switch back to fedora. But I imagine my problem here has nothing to do with the particular flavor of OS, and is just in the configuration.

---

### Post by Qumefox on 2007-06-29
I just realized that one of the RAID5 partitions is out of sync. This might be the cause of my problem. I'll post an update tomorrow after it finishes resyncing and I try again to see if the machine will boot with a failed (missing) drive.

---

### Post by Pumalite on 2007-06-29
You might be right. Somebody more experienced than I will have to jump in. Good luck.

---

### Post by Qumefox on 2007-06-30
After reading the many bug reports for mdadm tonight, I think what i'm seeing is just a behavior of mdadm failing to start the array due to missing devices. Apparently it won't automatically start a degraded array if one of the array members is missing completely. 

It seems that, while I thought the system was hanging, it's really not, and if I let it sit long enough, it'll eventually timeout and dump me to the initramfs prompt, and I can assemble the array manually in a degraded state, then continue booting. 

I'll have to test this tomorrow when I go back to work and can get to the machine.

If this is indeed how it works, then, while being a pain in the butt, I guess i'll just have to live with it. So long as I know the machine will still be usable, and bootable, with a failed drive.

---

### Post by Qumefox on 2007-06-30
It was just as I thought. Dumped me to initramfs and both md0 and md1 were inactive. Though I couldn't make it boot even after starting them manually in a degraded state with a device missing. As before, it works ok with all drives present.

---

### Post by Qumefox on 2007-07-01
Ok, this is getting frustrating. Anybody know where the scripts that load mdadm in initramfs are? I looked at the mdadm.conf, as well as mdadm-raid in init.d. Couldn't find anything that looked like it would stop it from building the array in a degraded state and continue to boot. 

rebuilt the initramfs image, thinking it might be something in the prebuilt one, but it still acts the same.

---

### Post by CescoAiel on 2007-07-01
Only thing I found to work is to wait in the initramfs environment until rebuild is complete and then reboot again...

BIG Pain it the butt, but there it is!  :(

---

### Post by Qumefox on 2007-07-01
Ok I found it.

build scripts are in /usr/share/initramfs-tools. Stuff I needed was in /scripts/local-top under that.

In the mdadm script, In the line : "${MD_DEGRADED_ARGS:= --no-degraded}"

I just deleted the --no-degraded part, then ran update-initramfs -u to rebuild. 

Shut the machine down, unhooked a drive, and viola, it booted with the arrays in degraded states.

I noticed that when I shut down though, and hooked the drive back up and restarted, that the arrays were still degraded. I used mdadm --add to put the partitions on the drive I pulled back in their respective arrays, and it started rebuilding them. 

After it finishes resyncing, i'll reboot it again and see if it comes up normally. If it does, then I solved my problem. If it tries to start the arrays in a degraded state again, even with all drives present, I guess i'll have to try something else.

---

### Post by peachy on 2007-07-02
I'm giving up with Ubuntu and RAID, I have raid 5 running at it is less reliable than non raid. Now I have the difficult problem of jigging files around to move them off onto a non raid partition so i can scrap the lot and install Solaris 10 with ZFS.

It's such a shame because everything else abut Ubuntu server is excellent.

---

### Post by Qumefox on 2007-07-02
Still haven't found a stable working solution. 

Taking the --no-degraded out of the mkadm-raid script lets it boot with missing devices, however the raid5 partition allways comes up as degraded, even with all devices present. 

this thing is becoming a pain in the rear.

---

### Post by Qumefox on 2007-07-03
The answer is no. I had to put the --no-graded back in. It kept only starting the raid5 array with 2 devices without it. 

Still looking for a solution, even a dirty one, to this. An extra menu in grub, etc, that'll let me boot with a missing device, so I can get to the partition tools to recreate it.

So if anyone has any suggestions, i'm quite open to them.

---

### Post by RoboJ1M on 2007-12-04
Hi,

What were the stupid tricks to get it to boot?

I have a very similar (er, identical) setup here: [http://ubuntuforums.org/showthread.php?t=624739](http://ubuntuforums.org/showthread.php?t=624739)

I can't get a working bootloader, my linux knowledge is too slim.

Could you post the steps to get a working system first?

Thanks,

J1M.

---

### Post by SBFC on 2007-12-12
Sorry for posting on such an old thread, but it's the only one I could find that had someone actually booting off of a raid using a promise sata300 tx4.

Qumefox, if you read this, how in the world did you install to your drives connected to the promise card? I bought the exact same card so I could use an older box I have but the mobo is old enough it has no sata ports.

I hooked up two 500G sata drives and tried to install Gutsy but at installation no drives could be detected. I dropped to a shell and issued 'lspci' and the card is detected, but the installer doesn't seem to see the two drives hooked up to the card.

Any advice at all would be greatly appreciated.

---


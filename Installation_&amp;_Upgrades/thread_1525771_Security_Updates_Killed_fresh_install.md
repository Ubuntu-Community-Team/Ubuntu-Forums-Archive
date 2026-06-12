---
title: "Security Updates Killed fresh install"
date: 2010-07-07
forum: Installation &amp; Upgrades
---

### Post by AvinThat on 2010-07-07
Hi all,

I'm completely new to Ubuntu and only installed yesterday for the first time.

The install worked fine. After booting it asked me to install updates. I did this and now when I boot i get:

------------------
Gave up waiting for root device. Common Problems:
- Boot args (cat /proc/cmdline)
     - Check rootdelay= (did the system wait long enough)
     - Check root= (did the system wait for the right device)
- Missing modules (cat /proc/modules: ls /dev)
ALERT! /dev/disk/by-uuid/blah blah does not exist. Dropping to a shell!

BusyBox....etc etc

(inittramfs)
-----------------------

Now I've tried searching through the forums and I've seen people with similar problems however none of the solutions suggested to them have worked. The only thing that may work if it is explained to me how to do it is in Grub 2 it is looking for a UUID. Now I tried editing this on startup to /dev/sda5 instead and it loads. Only thing is I read that this is temporary and would have to do it each time which means it's a workaround not a solution.

Any suggestions?

As I explained at the start, first time of using Ubuntu and so far haven't been particularly impressed as I have another problem with the processor being used up by loads of 'udevd' ----if you have a solution to this would be nice too!

Cheers

---

### Post by tommcd on 2010-07-07
> **AvinThat said:**
> The only thing that may work if it is explained to me how to do it is in Grub 2 it is looking for a UUID. Now I tried editing this on startup to /dev/sda5 instead and it loads. Only thing is I read that this is temporary and would have to do it each time which means it's a workaround not a solution.
To find the UUID of each partition on the hard drive run this command from the terminal:
```
blkid
```
This will list the partitions and their UUIDs like this:
```

bash-4.1# blkid
/dev/sda1: UUID="9AD8D8F9D8D8D51B" TYPE="ntfs" 
/dev/sda2: UUID="c2936c06-eec2-4ff8-9c42-6ef6f2c5bfc6" TYPE="ext4" 
/dev/sda3: UUID="028eee49-4ffa-456e-bf2b-e8372934296f" TYPE="swap" 
/dev/sda5: UUID="825d396e-4e04-477f-83e6-c8121e219a31" TYPE="ext4" 
/dev/sda6: UUID="2b3b0853-1c60-4b07-a3bc-eda812f5b961" TYPE="ext4" 
/dev/sdb1: UUID="628b326a-b0ef-4cd6-93a1-6b46de3ba2bd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="1c82c3df-d1de-4d0a-a20c-2321803b4410" TYPE="ext3

```
You will need to check the UUIDs outputted from blkid against the UUIDs listed in your */etc/fstab* file. If they are different, you can edit fstab and change the UUIDs in fstab to match those from blkid.
First backup your current fstab file.
```
sudo cp /etc/fstab /etc/fstab.orig
```
Then edit fstab with a text editor like gedit:
```
sudo gedit /etc/fstab
```
Just copy and paste the correct UUID(s) from blkid to fstab, then save the file, exit and reboot.
Note that the output of blkid has the UUIDs in quotes; but fstab does not use quotes around the UUIDs. I don't know if it matters or not, but I never included the quotes in fstab when I have done this.
This has happened to me when I installed another distro that also shares the swap file. Somehow, the UUID for the swap partition changed, and I had to change it in fstab.
> **AvinThat said:**
> 
 I have another problem with the processor being used up by loads of 'udevd' ----if you have a solution to this would be nice too!

The command ```
top
``` will list a realtime output of what is hogging your CPU. Also, note the **load average** numbers listed at the top of the top command output. The load averages are listed for 1, 5, and (I think) 15 minutes.  A good rule of thumb is that your load average should be equal to or less than the number of CPU cores on your system. So if you have a singe CPU with one core, the load average should be <1. A dual core machine should be <2, etc.

And welcome to the Ubuntu forums!

---

### Post by AvinThat on 2010-07-07
Without wanting to sound particularly dumb I've stumbled at the first instruction.

I've gone to terminal (within ubuntu) and typed blkid......and nothing happened.

Thanks for the quick response by the way!

---

### Post by tommcd on 2010-07-07
> **AvinThat said:**
> Without wanting to sound particularly dumb I've stumbled at the first instruction.

I've gone to terminal (within ubuntu) and typed blkid......and nothing happened.

Sorry, I thought that blkid would work on Ubuntu without sudo, but I just booted up my Ubuntu system (I am using Slackware at the moment) and it turns out that you do need sudo for blkid, so try running:
```
sudo blkid
```
Input you password when prompted, and you will get an output similar to what I posted.

---

### Post by AvinThat on 2010-07-07
Perfect, worked. In the file you asked me to edit it was set to '/dev/sda5/', so swapping to the UUID worked.

Thanks!

I'll post another thread for the processor query to keep the format correct.

---

### Post by tommcd on 2010-07-07
Glad you got it fixed!
Ironically, the problem that you had, and the problems that I have had with UUIDs, are exactly the type of problems that switching to UUIDs was supposed to *prevent*.
These problems never happen in distros that still use the /dev/sdXY names in fstab, like Slackware.

---

### Post by AvinThat on 2010-07-08
Hi all,

This solution has 'unfixed' itself and is back to where I started - strange system this Ubuntu.

---

### Post by tommcd on 2010-07-08
> **AvinThat said:**
> 
This solution has 'unfixed' itself and is back to where I started - strange system this Ubuntu.
So you can not boot Ubuntu again? Is that correct? Are you getting the same error messages that you had in your first post?
Try reinstalling grub2 to the MBR from the live CD as per the first method listed here:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
Then boot into Ubuntu if you can and run:
```
sudo update-grub
```

---

### Post by AvinThat on 2010-07-12
Right, seems there is a solution. Don't know why it affects it, however I've upgraded the BIOS and all seems to be good.

I re-installed ubuntu 64 afterwards just incase, and when I booted to install the load up time was significantly faster.

After install every fine, updated the OS, still all good.

So it's worth checking your manufacturers website for BIOS upgrades.

---


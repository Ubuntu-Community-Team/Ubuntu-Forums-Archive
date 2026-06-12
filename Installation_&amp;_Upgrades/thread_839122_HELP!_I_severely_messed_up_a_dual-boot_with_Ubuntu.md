---
title: "HELP! I severely messed up a dual-boot with Ubuntu/XP"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by mdawg414 on 2008-06-24
So for the last couple of weeks, I have been transitioning from XP to Ubuntu and for the most part it has been pretty seamless. However, I quickly found that there were several programs that pretty much just work on Windows. I played around with 'wine' a little bit but wasn't too impressed. So basically here was the setup I had on my 90GB HD:
/dev/sda1 was 10GB formatted to ext2 (this is where my windows installation was going to go)
/dev/sda2 was an extended filesystem of 80GB with the following sub-filesystems:
/dev/sda5 (linux-swap) 260 MB
/dev/sda6 (ext3) 83GB

/dev/sda5 had the boot flag set and then all of the operating system files for ubuntu and whatnot were put in sda6. This was working fine and I even set up a virtual machine with vmware that was running windows off of the 10GB other partition i had but found that it was just too slow. So I went to install windows xp the correct way (i.e. booted from the installation disk) and it installed fine but the problem is that it overwrote my boot drive or something and now only boots to XP. Ideally, it would go to the GRUB boot loader and let me choose, but frankly, I have nothing on the 10GB partition and everything on the 80GB one so I really don't care at this point if the 10GB one works or not. 
I tried booting from the ubuntu CD and going into test mode from the CD. From there I could play around with the partition manager and found that the boot flag had in fact been removed from sda5. In the partition manager, I deleted the 10GB partition (so now its just unallocated space) and left sda5 and sda6. The data is still there on sda6 btw. So basically, I need to figure out a way to reinstall GRUB or some sort of boot loader on sda5 so that I can load the operating system on sda6. I tried setting the boot flag on sda5 and restarting but I get the error "Operating System not found"

Any brilliant ideas out there? Thanks a million.

---

### Post by sys_alpha on 2008-06-24
thing that you should have done is grub-install ; do you have ubuntu still on hard drive ? if yes , just do grub-install --root-directory=your ubuntu partition .

this you can do by just running livecd and using terminal.

---

### Post by mdawg414 on 2008-06-24
Ok perhaps I am not inferring something that I should be but here is what happens when I try this:
#sudo grub-install --root-directory=/dev/sda5
install_device not specified

I looked around for a bit and think that I am probably supposed to be doing this:
#sudo grub-install /dev/sda5  (where sda5 is my swap partition)
But then it just throws back 'Could not find device for /boot: Not found or not a block device.

I think I might have to mount the drive or something but like I said, I really have no idea what I am doing and am slightly hesitant to experiment with things when my hard drive is at stake. 

Also, I am doing all of this from the terminal inside the livecd but I cannot see my linux files from my hard drive. I can see that the hard drive is full but cannot actually access the file. This might also be a mount thing

---

### Post by mdawg414 on 2008-06-24
Ok heres an update. I figured out that to see my actual hard drive files I just have to mount /dev/sda6 to something (in my case /hd). So I can see that all of my files are still there but I am having trouble booting to that hard drive. I reinstalled grub every way that I could think of or have seen but every time I boot it up, it gets the 'Operating System not Found' error. Here is how I have been installing grub:
After mounting sda6 to /hd, I ran '#grub-install --root-directory=/hd /dev/sda5' but no luck.
Then I went into the grub terminal by typing '#grub' and tried 'grub> setup (hd0,4)' and 'grub> setup (hd0,5)' but neither work.
It seems to me that my problem is just that my computer is not booting to the correct hard drive partition. How do I fix this? I tried going into the Partition Manager and setting the boot flag on the drive I wanted but no luck there either. Thanks for your help guys

---

### Post by mdawg414 on 2008-06-24
well it appears that no one is reading this thread but in case anyone is, i figured it out and thought i would put what i did for reference.

In the grub console, I had to do 'setup (hd0)' instead of 'setup (hd0,4)'

The first one puts grub in the MBR (which is what I wanted to do) while the second one puts grub on a specific partition's boot loader from what I can tell

---


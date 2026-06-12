---
title: "Cannot boot after installing 7.04"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by whatever_really on 2007-09-02
I'm having a problem I'm hoping someone can help me with.

I have 2 identical SATA drives, both WD 250gig. I want the first drive to hold my swap partition (made it 2gig) and the rest of the disk to be my root (/). The second disk is mounted on /home/.

First time I installed I just told Ubuntu (installing version 7.04) to automatically partition one of the disks and install Ubuntu on it, but after reboot I get the message Disk Boot Failure ...

So, I manually partitioned the disks as described above and re-installed Ubuntu, but again I got the same error, Disk Boot Failure etc... and it won't boot from my HD.

After getting this problem and doing some searching, I tried installing grub manually (and it looked like I managed to install it just fine on hd0,1), I went into GNOME Partition Editor and set the bootflag on sda1, none of this made any difference though :(

Anyways, now I have no idea what to do anymore, I did try to find a solution but with no luck so this forum is my last chance as it currently stands, so I really appreciate any help anyone is able to give me.

I can also add that it looks like Ubuntu installed just fine, booting from the liveCD I can see all the folders etc and it looks pretty normal, and I am installing the AMD64 bit version of Ubuntu.

EDIT: I have re-installed Ubuntu a total of six times now, each time with the same result. Also downloaded the alternate install CD and tried running the rescue operation from there, to re-install GRUB. Still no luck.

My system at the moment is a 6gig swap partition on sda, followed by a 240ish gig ext3 partition that is mounted at /, and sdb is just one bit ext3 partition mounted on /home. Still cannot boot though :(

Could really use some help here, im completely lost and have no idea what to do anymore...

---

### Post by moore.bryan on 2007-09-02
*could you post your /boot/grub/menu.lst file?  that might give a better idea... chances are the loader isn't loading from the right disk/partition.*

---

### Post by whatever_really on 2007-09-02
I have since my last post reinstalled Ubuntu again (im actually at 11 re-installs, having tried every configuration I can think of when it comes to disks), this time I installed it on sdb instead of sda just to see if it would make a difference, which I assume is why it says hd1 in the menu.1st file.

I did check through the paths after you asked me to post menu.1st and all the files are in the correct place in the /boot folder (vmlinuz, initrd etc).

Seems to me like nothing is getting written into the MBR, although I'm not going to pretend that I'm any good at this, just based off what I've read.

My idea right now is to try and install Lilo instead of Grub, just wish I could find out how :)

I was using Windows XP and then it crashed after changing NIC's, and since my CD is ancient it didn't have SATA drivers. Thinking it was time to upgrade anyway I installed the 30 day trial of Windows Vista, this was three days ago.
Vista was completely horrible, and I figured that if I have to sit and spend hours trying to get things to work I might as well do it in Linux, seeing how its free, instead of spending 200 - 300 dollars on an OS and then having the same headache. 

However, after spending over a day trying to get Ubuntu to boot I am leaning towards Vista not being the worst idea. It is horrible yes, but atleast it boots.

I am of course not going to argue that this may very well be because of myself, but to make it fair I know Vista about as well as I know Ubuntu.

Anyways, file attached below:

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=e869e2fb-be6d-4f9d-be5d-3e4446e59b1b ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=e869e2fb-be6d-4f9d-be5d-3e4446e59b1b ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by moore.bryan on 2007-09-02
[I]just my opinion, but lilo sucks and is antiquated.  

if you answered "yes" when it asked you to install grub into the mbr, it installed grub onto your first hd, but your grub menu has it looking on your second one.  try editing it to have root on (hd0,0):
```
[/I] ## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=e869e2fb-be6d-4f9d-be5d-3e4446e59b1b ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=e869e2fb-be6d-4f9d-be5d-3e4446e59b1b ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by whatever_really on 2007-09-02
got it to work :)
you got me on the right track when you had me checking the hard drives, thanks for that.

The problem was this (in case anyone else does the same thing I did).

I was using Windows before trying to install Ubuntu, and I was running disk striping (RAID) on my disks with Nvidia's on the motherboard fake raid controller.
When I was going to install ubuntu I read about the fake RAID and decided it was fairly useless, so I broke the RAID and then installed ubuntu (and this was done correctly).

However, in the main BIOS there is a setting that says RAID Enabled or Disabled, and I had left this enabled. Disabling this option got it working :)

---

### Post by moore.bryan on 2007-09-02
*glad to hear it... happy ubuntu-ing...*

---


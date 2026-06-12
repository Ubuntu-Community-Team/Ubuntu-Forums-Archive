---
title: "Installed with Windows"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by Touch.Code on 2008-03-15
About 1 hour ago I installed Linux about to try and give it another shot!

I have Windows XP installed already. I installed 7.10 but when asked if the settings were correct, I clicked advanced settings and clicked something about a boot installer.

Everything installed ok, but when restarting it booted into Windows.

What do I do now?

Thanks,
James

---

### Post by Pumalite on 2008-03-15
You can boot Ubuntu with Super Grub if you have a live installation>
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Boot your Ubuntu Live CD and from the Terminal, post>
sudo fdisk -lu

---

### Post by Touch.Code on 2008-03-15
Will this let me dual boot?

---

### Post by Pumalite on 2008-03-15
For that post what I asked you for.

---

### Post by Touch.Code on 2008-03-15
OK, I shall post it soon I hope.

---

### Post by MONODA on 2008-03-15
super grub is great, keep the cd you burn for it somewhere safe. It has saved me SOOO many times when I was trying different distrobutions.

---

### Post by Touch.Code on 2008-03-16
So, if I boot into the Live CD, what do I do next? I only have one DVD drive.

---

### Post by Touch.Code on 2008-03-16
Oh, I see, I just put in Super Grub and it will then let me boot into Linux :)

---

### Post by Touch.Code on 2008-03-20
Super grub tells me there is an error. I shall find the exact one later. For Pumalite, I shall go and get the output now :)

---

### Post by Touch.Code on 2008-03-20
So, this is what it outputed:
> 
Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd56fd56f

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *     4096575   156280319    76091872+   7  HPFS/NTFS

Disk /dev/hdd: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders, total 40020624 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8f800000

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *          63    38266829    19133383+  83  Linux
/dev/hdd2        38266830    40017914      875542+   5  Extended
/dev/hdd5        38266893    40017914      875511   82  Linux swap / Solaris


---

### Post by Pumalite on 2008-03-20
OK., mount your partition:
sudo mkdir /media/hdd1
sudo mount -t ext3 /dev/hdd1 /media/hdd1
Now, post the output of the following:
cat /media/hdd1/boot/grub/menu.lst

---

### Post by Touch.Code on 2008-03-20
Will I still be able to access Windows?

---

### Post by Pumalite on 2008-03-20
We are trying to figure that out.

---

### Post by Touch.Code on 2008-03-20
Ahh right :P

I shall post back in a minute :)

---

### Post by Touch.Code on 2008-03-20
/media/hdd1 is busy.

---

### Post by Pumalite on 2008-03-20
Go back to Windows and shutdown properly

---

### Post by Touch.Code on 2008-03-20
I have done :)

---

### Post by Pumalite on 2008-03-20
Run my commands again

---

### Post by Touch.Code on 2008-03-20
I did, it gave me that error, but previously I did shut down windows correctly.

---

### Post by Pumalite on 2008-03-20
Go to /media and check if you see hdd1 there.

---

### Post by Touch.Code on 2008-03-21
Well I decided I would install Linux over the previous installation. It worked for a while, but when I reset Grub told me Error 15: Missing file ??

---

### Post by Pumalite on 2008-03-21
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by Touch.Code on 2008-03-21
Thanks Pumalite, I shall have a read now :)

---

### Post by Touch.Code on 2008-03-21
I can't even boot into Ubuntu from Super Grub :S

---

### Post by teryowen on 2008-03-21
boot from live cd.

go into terminal and reinstall grub.

```

sudo grub
root (hdx,y)
setup (hdx)
quit

```

where x is the hard drive which ubuntu is on 0 being the first, 1 being the 2nd and so on.
and y is the partition which ubuntu is on 0 being the first of that hard drive, 1 being the 2nd of that hard drive and so on. (i think your x should be 3 and y 0, if that doesnt work try x being 1 and y being 0)

try this out.

Also make sure that in your BIOS the boot priority is correct so that the hard drive with ubunut on it has priority.

---

### Post by Touch.Code on 2008-03-21
Thanks teryowen, I shall try that out shortly :) Just running some things on XP at the moment!

---

### Post by Touch.Code on 2008-03-21
I tried to follow your command teryowen, but I got nothing.

I got as far as sudo grub, but when doing root hd3, 0 it said it was an invalid parameter.

---

### Post by teryowen on 2008-03-21
once you're in ubuntu

post the contetnts of /boot/grub/menu.lst

just do:
cat /boot/grub/menu.lst

copy and paste output.

but i think its a problem with the BIOS make sure the hard drive with Ubuntu on it is set to boot before the one with windows on it.

---

### Post by Touch.Code on 2008-03-21
Alrighty :)

I have tried o change my BIOS settings but cant load stage 1. I just found something, so I shall it and then post the output you asked for.

---

### Post by teryowen on 2008-03-21
ok so lets look for stage one. 

do thsi in terminal

```

sudo grub
find /boot/grub/stage1

```

what ever it spits back out type in the rest so say it gave back (hdx,y)

then you type
```

root (hdx,y)
setup (hdx)
quit

```

now when you choose in you're bios to boot from the ubuntu hard drive you shouldnt get a stage 1 error.

---

### Post by Touch.Code on 2008-03-21
That's what I found :)

I now see the GRUB boot menu, but when I try and boot Windows or Linux it gives me an error.

I tried to do cat /boot/grub/menu.lst but it doesn't work.

---

### Post by Touch.Code on 2008-03-21
YAY! I fixed it!

Here is what I did:
On the grub menu I pressed 'e' on Ubuntu, then 'e' on root, I then changed hd1,0 to hd0,0

Works great!
Now to fix my Wireless issue :(

---

### Post by teryowen on 2008-03-21
EDIT:

Ok now that you did that, from ubuntu you want to make the change permanent (unless you want to do the whole 'e' thing everytime)

for this you will have to edit the menu.lst file which is found under /boot/grub

change the location for ubuntu from hd1,0 to hd0,0 (as you previously stated)

---

### Post by Touch.Code on 2008-03-21
Thanks :)

Any suggestions on my wireless?

---

### Post by teryowen on 2008-03-21
whats the problem with the wireless?

---

### Post by Touch.Code on 2008-03-21
[Looky here]("http://http://ubuntuforums.org/showthread.php?t=730009")

I have tried lots of things.

---

### Post by teryowen on 2008-03-21
Ok i will discuss as best as i can in the post you provided, but for this one if you dont have anymore questions mark as solved.

---

### Post by Touch.Code on 2008-03-21
Thanks! You steered me in the right way!

---


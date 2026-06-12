---
title: "Expand root partiton into unallocated space?"
date: 2017-08-24
forum: Installation &amp; Upgrades
---

### Post by hiloguy on 2017-08-24
New install: dual boot W7 & 14.04 on a Dell E6420 laptop.  W7 is on 125 GB SSD and 14.04 is on a 500 GB drive in a CD drive caddy.  It was all working sweetly until I got a notice that my 5.3 GB root directory was nearly full and no more updates were possible.  I have 8.3 GB of unallocated space on that drive.  Can I expand my root directory into that space? Here's the Gparted view:
[http://imgur.com/a/57Awk](http://imgur.com/a/57Awk)

I can use all of that 8.3 GB.  I really have worked hard to find an answer to doing this.  Please help!!

Thank you!

---

### Post by Bucky Ball on 2017-08-24
Yes, you can. No hard fix. Boot from Ubuntu install media, launch Gparted, right click the partition you want to resize and unmount (if not already), expand the partition (right click> 'Resize' from memory). Done.

You should also try running this to see if it makes a bit of space.

```
sudo apt autoremove
```

Any shrinkage? Either way, you can't resize a mounted partition, therefore you can't resize the / partition without booting from USB or DVD.

There are other ways of cleaning your install which, once you have resized, you can look into. You no doubt have a heap of garbage accumulated, unless you made the partition too small in the first instance and have installed heaps of software. :)

---

### Post by Impavidus on 2017-08-24
There is a slight problem though: your sdb5 is not adjacent to the unallocated space. To expand sdb5 you first have to expand sdb2, then move sdb7 and sdb6, which is rather time-consuming and a bit risky. If something goes wrong, you could loose everything on your /home partition.

5.3GiB is really tiny for a root partition these days. 13.6GiB is small, but doable. Still, it may be best if you don't only move your sdb6, but also shrink it a bit. Make the root partition about 15 to 20GiB. It's more comfortable and you won't notice the 5GiB difference on that huge /home partition.

Also keep an eye on your /boot partition. When it fills up, your kernel upgrades will fail, which is a problem best prevented. In fact, on systems without encryption or LVM a /boot partition is rarely useful.

---

### Post by ajgreeny on 2017-08-24
It will not, unfortunately, be quite as easy as Bucky Ball suggests as the unallocated space is not adjacent to the root partition that you want to enlarge.

Do everything from a live system or you will get nowhere with this.  You will need to move swap and /home as both are sitting between the root and unallocated space that you want to merge.

It may be easiest to delete swap and later create a new swap partition once you have dealt with the rest.

[LIST=1]
[*]Delete current swap, sdb7.
[*]Enlarge  the existing extended partition, sdb2, to the far right of the disk.
[*]Create a new swap of chosen size at far right hand end of disk.
[*]Move the /home partition to the right, up to the new swap. This will probably take a long time but do not interrupt this or you will lose everything in it.  **Make sure you have backups!**
[*]Now with the unallocated space next to root you can enlarge sdb5 into the space.  Again, it may take a while to do, so leave well alone until finished.
[*]From live system edit the /etc/fstab of the hard disk OS, not the live OS, changing the UUID of the swap to the new partition ident which you can get from command ```
sudo blkid -c /dev/null
```
[/LIST]

Incidentally, is there a good reason for you having a separate /boot partition?  In most situations it is not needed and just adds extra problems; only if using encryption or LVM partitioning is it required.
I have also just noticed impavidus's remarks and fully support his comment  about the size of root even after my suggested enlargement; it is well worth considering his idea.

---

### Post by Bucky Ball on 2017-08-24
Now you have more detailed, and duplicate, explanations of what to resize when, I'll just reiterate: make sure you are booting from live media and not your currently installed OS, as mentioned in post 2. You can't resize your / partition while you're running the OS on it. ;)

Good luck.

---

### Post by hiloguy on 2017-08-24
> **Impavidus said:**
> There is a slight problem though: your sdb5 is not adjacent to the unallocated space. To expand sdb5 you first have to expand sdb2, then move sdb7 and sdb6, which is rather time-consuming and a bit risky. If something goes wrong, you could loose everything on your /home partition.

5.3GiB is really tiny for a root partition these days. 13.6GiB is small, but doable. Still, it may be best if you don't only move your sdb6, but also shrink it a bit. Make the root partition about 15 to 20GiB. It's more comfortable and you won't notice the 5GiB difference on that huge /home partition.

Also keep an eye on your /boot partition. When it fills up, your kernel upgrades will fail, which is a problem best prevented. In fact, on systems without encryption or LVM a /boot partition is rarely useful.

============================================

The separate root and boot partitions were done on the advice of the same person who assured me that 5GB was more than enough for the root partition. This was all part of the advice on setting up 14.04 on a separate drive (/sdb)in a dual-boot setup with W7 on /sda.  So should I now combine these two partitions, and if so, how is this done?  This in-depth partitioning thing is still new to me and now that I have this machine running so well, I'd sure hate to blow it!

---

### Post by ajgreeny on 2017-08-24
> **hiloguy said:**
> ============================================

The separate root and boot partitions were done on the advice of the same person who assured me that 5GB was more than enough for the root partition. This was all part of the advice on setting up 14.04 on a separate drive (/sdb)in a dual-boot setup with W7 on /sda.  So should I now combine these two partitions, and if so, how is this done?  This in-depth partitioning thing is still new to me and now that I have this machine running so well, I'd sure hate to blow it!
I suspect the person who gave you that advice was more used to Linux installation from a long time in the past, or was thinking that you were using just the command-line OS. You certainly need more space than 5.3GB for your root partition, so I would reiterate my suggestions above with the detail of what to do. 

Using separate disks for each OS is a very handy way to dual boot, so I would keep things that way and not worry too much though you will not be able to read any files in your Ubuntu /home partition with Windows without adding an ext#fs driver to your Windows OS, and I do not know how good they are nowadays; when I tried them about 10 years ago they were very flaky.  There are alternative ways to have data files availability to both OSs by using a shared NTFS partition and have symbolic links between the data file folders and your Ubuntu OS's /home, but that would mean no large /home partition was needed, and will take a lot of setting up if you are not fully aware of partition management activities.

You can not at this stage easily move the /boot partition into root, so I would leave /boot as it is at present, but you might want to think about an upgrade to 16.04 now, or perhaps 18.04 next April.  When you do upgrade I recommend a clean installation where you can more easily make changes to your partition layout.  Do keep a separate /home partition as you have now; it makes life a lot easier when reinstalling the OS as you can keep /home untouched to retain all your personal files and settings.

However, **you must always have backups when managing partitions** just in case things go wrong.

---

### Post by hiloguy on 2017-08-24
Thank you for your patient reply to my questions.  I'll just go ahead and attempt to expand my root partition into the unallocated space and leave it at that.  Regarding not being able to access W7 files from Ubuntu, that's never an issue.  My only reason for even having W7 on this machine is for a few needs like GPS updates, access to my automotive diagnostic equipment, etc. Other than that, I use only Ubuntu.  And love it.

---

### Post by ajgreeny on 2017-08-24
OK, that's fine, but do consider what I said about setting up when you next upgrade your OS version.
[LIST=1]
[*]Keep /boot just as a folder in the root partition.
[*]Make root partition 20GB in size.
[*]Retain your current /home partition by choosing "Something Else" at partitioning stage of installing, click in the /home partition and choose the Change button.
[*]Choose "Use as ext4", mountpoint /home, **but make sure the *Format* selection box is not selected**.
[/LIST]

Good luck with the current enlargement; come back again if necessary when you move to the next Ubuntu version to double check your action.

For now please mark as SOLVED from the Thread Tools menu up-top, assuming this is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by hiloguy on 2017-08-24
Just this one more detail:  I keep reading: "make sure you are booting from live media and not your currently installed OS."  How do I create this live media?  Are we referring to booting from the usb 14.04  install drive?

---

### Post by ajgreeny on 2017-08-24
> **hiloguy said:**
> Just this one more detail:  I keep reading: "make sure you are booting from live media and not your currently installed OS."  How do I create this live media?  Are we referring to booting from the usb 14.04  install drive?

Yes, that's right.

---

### Post by hiloguy on 2017-08-24
OOPS  I posted my question in a way that you missed the part about "How do I create this live media? Are we referring to booting from the usb 14.04 install drive?"

---

### Post by Bucky Ball on 2017-08-24
You need to have the Ubuntu install media. [Go here]("https://www.ubuntu.com/download/desktop"), download the ISO (grab 16.04.3), create the media (USB or DVD), boot from the media and choose 'Try Ubuntu'. When you're at a desktop, launch an app called 'Gparted' and resize. ;)

Instruction for creating install media are on that site a bit further down under 'Easy ways to switch to Ubuntu'. You'll find how to create USB or media on Win, Ubuntu or Mac linked there.

You can also go to[ the Gparted site]("http://gparted.org/") and download an ISO of just that and boot from that. Gparted is also included in various other bundles, notably SystemRescueDisk (always handy to have a copy around).

---

### Post by hiloguy on 2017-08-28
Thank you all for your help here!  I keep running into gotchas, though, like this>  I was going to do the suggested process to delete the swap partition and then follow through moving things around to where I could expand the now-full root partition into the unallocated space.  So I booted into "try Ubuntu" from a 14.04 install usb drive, opened Gparted, and found the swap partition was mounted!  
[http://imgur.com/a/Tqomw](http://imgur.com/a/Tqomw)
Rather than to keep patching this thing up, would I be better off to just start over, even though it means losing the hours I spent setting this thing up?  My home partition is duly saved; no worries there.

If starting over is suggested, PLEASE give me the straight scoop on recommended partition sizes for everything!  I carefully set this installation up on old advice I had saved, and apparently that advice had reached its best-if-used-by date.

---

### Post by ajgreeny on 2017-08-28
No need to start over at this stage.

Just right click in the swap partition in the gparted window and choose **Swapoff**.
You can then delete the partition and start going through the other actions needed one by one.

Good luck!

---

### Post by ubfan1 on 2017-08-29
Actually, gparted uses resize2fs to expand the filesystem into the larger partition, and that may be done (expanding on the right/end) on a running system.

---

### Post by riverguy99 on 2017-09-02
I want to thank everybody who offered assistance here!  After another few hours of frustration, I finally figured out the little Gparted secret of clicking on the hidden "APPLY" button to effect the partition changes I tried for so long to make.  I saved the HOME partition and made new ROOT, BOOT and SWAP partitions per instructions.  It's all back together and running sweetly.

Thank you all!

---

### Post by riverguy99 on 2017-09-02
> **ajgreeny said:**
> OK, that's fine, but do consider what I said about setting up when you next upgrade your OS version.
[LIST=1]
[*]Keep /boot just as a folder in the root partition.
[*]Make root partition 20GB in size.
[*]Retain your current /home partition by choosing "Something Else" at partitioning stage of installing, click in the /home partition and choose the Change button.
[*]Choose "Use as ext4", mountpoint /home, **but make sure the *Format* selection box is not selected**.
[/LIST]

Good luck with the current enlargement; come back again if necessary when you move to the next Ubuntu version to double check your action.

[I][B]For now please mark as SOLVED from the Thread Tools menu up-top, assuming this is now solved to your satisfaction. It is a great help to users searching the forum.


[/B][/I]I'd love to mark this thread as "solved," but there's no such option in the "Thread Tools" drop-down.  Some say to go to the first posting in the thread and click on "Advanced."  Darned if I can find that, either.  THIS THREAD IS SOLVED, THANKS TO ALL, so how do I mark it as such?  :)

---

### Post by Bucky Ball on 2017-09-03
If you are not seeing 'Mark as solved' in 'Thread Tools' and don't see 'Adv Reply' or 'Go Advanced' as options for your posts, then post a new thread about it in 'Forum Feedback and Help' if you need help with that.

(Goes without saying, but you need to be logged in to the forum to see those options. ;))

Good luck.

---

### Post by Impavidus on 2017-09-03
> **Bucky Ball said:**
> 
(Goes without saying, but you need to be logged in to the forum to see those options. ;))


Not just logged in, but even logged is as the user who started the thread. As this thread was started by hiloguy, it's logical that riverguy99 cannot mark it as solved.

---


---
title: "Partition marker doesn't show which OS is on which side"
date: 2012-05-14
forum: Installation &amp; Upgrades
---

### Post by daisyflower on 2012-05-14
I am about to install Lubuntu on my netbook, but I am at the point where I choose how much I want for each partition.  It doesn't indicate if Windows is on the left or if Lubuntu is on the left of the slider bar.  Any ideas which is which?

---

### Post by Bucky Ball on 2012-05-14
If you choose 'Something Else' and do a manual install it is all quite clear. I would'nt know with the slider. If it is showing the disc, Windows would be on the first part which is generally the left, but DON'T take that as gospel. I'd make certain first.

---

### Post by daisyflower on 2012-05-14
I googled some images and Windows or Mac is always on the left, so I gambled.  It's true.  I'll send Lubuntu about this issue.

I tried do the other options, but it only listed the NTFS drives (I think I am citing this correctly).  It didn't give me any options to partition.

---

### Post by wilee-nilee on 2012-05-14
> **daisyflower said:**
> I googled some images and Windows or Mac is always on the left, so I gambled.  It's true.  I'll send Lubuntu about this issue.

I tried do the other options, but it only listed the NTFS drives (I think I am citing this correctly).  It didn't give me any options to partition.

You would have to have an unallocated space or partitions formatted for linux for the custom to work effectively I believe. Not sure you can resize the windows from there safely.

The method you used is made a little more clear if you have a unallocated space as well.

---

### Post by daisyflower on 2012-05-14
> **wilee-nilee said:**
> You would have to have an unallocated space or partitions formatted for linux for the custom to work effectively I believe. Not sure you can resize the windows from there safely.

The method you used is made a little more clear if you have a unallocated space as well.

I am not sure I understand your statement.  I loaded it up and it presented me with a slider bar.  I have installed Ubuntu several times so I know what it was asking, but I didn't know for certain which was on which side.

It wasn't a matter of unallocated space but choosing where the partitions would be.

---

### Post by SonnyE on 2012-06-29
It's true it doesn't show or say which side is which for the slider. It says install Lubuntu alongside another operating system. Lubuntu is earlier in the sentence, which is on the left in English, but I'll take your word Lubuntu is on the right for the partition slider.

I just ran into this as the last thing in the way after spending a week getting ready to install Lubuntu as my first ever Linux, so I'm in the live CD right now. I've been taking so long because I had to learn about keycodes and keysyms to get a Ctrl key on my broken keyboard in XWindows, so that I could get to a console, so that I could learn to run keymap using sudo to make it so I have a Ctrl key in console and in XWindows.

If I don't return within 3 hours and tell how the install worked, and which side is which, then it didn't work.

---

### Post by SonnyE on 2012-06-29
After my post above, I've got far enough along in the installation to say for sure that when it's an installation of "Lubuntu alongside Windows XP" the partition on the left is what will be left for Windows. The installer from the Live CD desktop chose to divide my hard drive into 47.7 GB left, which went to Windows, and 32.3 GB right, which went to Lubuntu. I didn't move the slider in case that would make the installation take longer.

I think I accidentally erased a hidden 5.48 GB partition of software that was built-in to my computer that I had never accessed. Windows always told me the harddrive was 74.52 GB, but the partition amounts the installer gave add up to 80 GB. I think that happened because I chose to reset or restore or whatever the installer called it about the partition, because the installer used some Linux-type folder names in describing what the partition was, so I thought for a moment that it was just a Linux file-system thing and clicked Continue.

I'll come back when I've booted both ways to check what's going on with my hard drive.

---

### Post by darkod on 2012-06-29
> **SonnyE said:**
> After my post above, I've got far enough along in the installation to say for sure that when it's an installation of "Lubuntu alongside Windows XP" the partition on the left is what will be left for Windows. The installer from the Live CD desktop chose to divide my hard drive into 47.7 GB left, which went to Windows, and 32.3 GB right, which went to Lubuntu. I didn't move the slider in case that would make the installation take longer.

I think I accidentally erased a hidden 5.48 GB partition of software that was built-in to my computer that I had never accessed. Windows always told me the harddrive was 74.52 GB, but the partition amounts the installer gave add up to 80 GB. I think that happened because I chose to reset or restore or whatever the installer called it about the partition, because the installer used some Linux-type folder names in describing what the partition was, so I thought for a moment that it was just a Linux file-system thing and clicked Continue.

I'll come back when I've booted both ways to check what's going on with my hard drive.

Don't forget the difference between a true GB (commonly called GiB) and a GB how hdd manufacturers calculate it.

For hdd manufacturers, 1GB is 1000x1000x1000 bytes.
Bit since computers work in binary format, the true 1GiB is actually 1024x1024x1024 bytes. That's why a hdd of 80GB will never be 80GiB.

To make sure which partitions you have, you can use linux tools (because windows often doesn't show some partitions in Computer). Just boot live mode, open terminal and run something like:
```
sudo fdisk -l
sudo parted /dev/sda unit GiB print
```

The second command will print the partitions on the disk with GiB as a unit. You can use MiB, GB, MB, s (for sectors), etc.

---

### Post by SonnyE on 2012-06-29
The slide show was only two slides, and there was no message that said the installation was completely done, so maybe something went wrong. That's when I wrote my last post. I tried to "reboot" because I thought it was finished installing. Then when it shut down, it said on a black screen something about sending a message to all running processes to terminate, with the line ending [OK], then just waited there, until I pressed the power button. I don't know if that's what Lubuntu is supposed to do when it shuts down, but that doesn't seem like a reboot.

So now I'm in Windows, with a hard drive that has been cut from the previous 74.52 GB to a current 44.4 GB. Those numbers compared to what Lubuntu reported clearly suggest that Windows XP is using the RAM definition of GB = 2^30 bytes and Lubuntu is using the hard drive manufacturer definition of GB = 10^9 bytes. That quirk about Windows was mentioned on the Wikipedia page "Binary prefix" which I studied a little recently, but I guess not enough. So the hidden partition had already been erased a long time ago, and it's not possibly Linux's fault. It's a good example of Linux being more correct than Windows even if it causes some confusion between the two.

Windows ran chkdsk (a DOS "check disk" program) before it finished booting, and I'd never seen it do that before. That seems to mean it was surprised by the amount of changes on the hard drive.

At this point, I don't expect to have a dual-booting system any time soon.

---

### Post by darkod on 2012-06-29
There is another way which may be even easier. Boot into live mode and open Gparted or similar, and check the partitions. Are there linux partitions prepared or it didn't get that far?

You said XP was shrinked indeed so the linux partitions might be there or not depending when the install process froze.

If there are any linux partitions, delete them (there is nothing on them right now anyway). Just make sure you don't delete the XP. :)

After you have the space as unallocated, start the install again. This time I think it doesn't show the slider since it has unallocated space to use and no partition resize is needed.

That might work out better than resize + install in one go.

---

### Post by SonnyE on 2012-06-29
I solved it and I'm now running Lubuntu in a dual boot system. I tried your suggested fdisk and parted commands and all the numbers were right for the partition sizes in different units, so no problem with that. I found the problem by "cat syslog" it showed the next to the last line included "IOerror (errno 32) broken pipe" so I Googled those words and found the page at bugs.launchpad.net for bug 968216. It was a problem with Ubiquity and AMD processors around the number of mine (mobile AMD Athlon XP2800+)

There was a solution listed which was "sudo apt-get purge ubiquity-slideshow-ubuntu" then install from live desktop, and I tried that, which didn't work, because the package was not present. So I changed it to ..."ubiquity-slideshow-lubuntu" and it worked. I also watched the slideshow at [http://people.ubuntu.com/~dylanmccall/ubiquity-slideshow-ubuntu/preview/](http://people.ubuntu.com/~dylanmccall/ubiquity-slideshow-ubuntu/preview/) (which lets you select the slideshows for flavors such as Lubuntu) so that I wouldn't be missing anything.

Then it took over an hour for the computer to do all the actual installing. I selected the option to write over the existing Linux partition, since it hadn't been finished anyway.

Yea! Thank you, darkod, and the forum and the whole Linux community for putting out so much good free stuff.

______________
hp pavilion ze4805us 432 MB ram
Lubuntu 12.04 desktop / Windows XP Home edition dual boot

---


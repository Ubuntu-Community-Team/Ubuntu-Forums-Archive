---
title: "Is the Swap File Partition necessary?"
date: 2011-11-16
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2011-11-16
I was wondering if Swap is needed?

Just went back to 64 bit Natty on my laptop after trying out 64 bit Ocelot and finding it slower and still buggy. Plus Banshee would freeze up too often. Ocelot has some nice improvements but I still think too many things have to be ironed out. Natty OTOH seems rock solid.

Anyways I dual boot with Windows and my Linux partition was getting a bit cluttered. It had 2 swap files, for some reason and another small partition that I have no idea why it was there. When I reinstalled Natty the Linux partition was formatted to clear everything and Natty installed flawlessly. However I didn't create a Swap file because I have 4 GB of RAM and 64 bit Natty recognizes 3.7 GB of that RAM. 

So the question is, was this OK? 
So far 64 bit Natty seems to be running fine and rock solid again, a bit better than my experience with 64 bit Ocelot.

---

### Post by Frogs Hair on 2011-11-16
It is my understanding that if you want to hibernate you will need swap .

---

### Post by WasMeHere on 2011-11-16
Hi cybrsaylr,

Short answer: No, if you have enough RAM for your applications, it is OK.

Longer answer: If you want to save your state (hibernate): Yes, at least as much as your RAM. If you sometimes run a memory-intensive application: yes, you might need some swapping and if you have a huge disk, you could put it at 'the end' and make it twice the size of your RAM. But I think many people now say it is not necessary. There are also people who use a swap file (like in Windows) instead of a partition (but I don't know the details how to do that).

Have fun continuing to find out :-)
Olle

---

### Post by cybrsaylr on 2011-11-16
To tell you the truth, not sure or noticed if I ever wanted to save my state (hibernate) in the past.

Before with Natty there was a 3.7 GB 'swap' partition and when Ocelot was installed I noticed another 3.7 GB 'swap' partition was created so there were 2 swaps! Not sure why this occurred. 

Don't really run any memory-intensive applications.
But I did have a problem with a couple buggy games in the past that used up all RAM and then almost all of the swap! Ended up just removing them.

Can a swap partition still be easily created if desired or not?

---

### Post by An Sanct on 2011-11-16
Well, if you have no swap and run out of memory, then you have problem. I have 8GiB of ram and 32Gib of swap (I personally set it to such a high amount). Even with 8G of ram, I still run out and have to swap at times, but that is mostly because of my Virtual Machines and non-optimal SQL queries...

---

### Post by An Sanct on 2011-11-16
> **cybrsaylr said:**
> To tell you the truth, not sure or noticed if I ever wanted to save my state (hibernate) in the past.

Before with Natty there was a 3.7 GB 'swap' partition and when Ocelot was installed I noticed another 3.7 GB 'swap' partition was created so there were 2 swaps! Not sure why this occurred. 

Don't really run any run memory-intensive applications.
But I did have a problem with a couple buggy games in the past that used up all RAM and then almost all of the swap! Ended up just removing them.

Can a swap partition still be easily created if desired or not?
Yes, you can create swap any time you wish.

Use a Live USB/CD and gparted to do so, AFAIK you have to put it inside the fstab and enable it.

---

### Post by WasMeHere on 2011-11-16
Yes, with Gparted from a live Ubuntu CD or USB drive you can create and delete swap partitions as well as other kinds of partitions.

At least you can delete one of your swap areas (check in /etc/fstab which of them your present system is using).

---

### Post by bluexrider on 2011-11-16
You don't need more than one swap file on your partition and as it goes the rule of thumb has always been 1.5 times the machine's memory. I would delete the swap with the lowest uuid leaving the other closest to the end of the hard drive.

 

Can a swap partition still be easily created if desired or not? 	

Yes, it is. By using Gparted or some other partitioning software.

---

### Post by cybrsaylr on 2011-11-16
Thanks for the help guys.
Need a little more.
This is what GParted shows me:

[IMG]http://i.imgur.com/QCf72.png[/IMG]

Where should I create the swap partition?
When trying to create a swap in either sda3 or sda5, GParted blocks it saying it can't be done. GParted reports: 1 partition is currently active on device /dev/sda.
 What am I doing wrong? I never did this with GParted before and am not sure what I'm doing.

---

### Post by WasMeHere on 2011-11-16
Do you intend to keep both systems (Windows as well as Ubuntu)? Or are you going to erase Ubuntu and start with a fresh install? Are you planning to keep your personal data (documents, pictures, media files ...) on the big NTFS partition?

The big NTFS partition seems a little oversized compared to the extended partition, so the perfect solution would be to shrink and delete the extended partition, then make a new extended partition filling all the unallocated space. Then you can make a swap partition and an ext3 partition for linux as logical partitions. But it is risky, so you need to backup your drive (make a clone or image) before doing anything like that.

The simple solution would be to wipe the ext4 partition and make a swap partition and an ext3 partition for linux as logical partitions. It means that the linux partition will be small, say 15 GB, but it is enough if you keep your data on the Windows partition. If you are really fond of your present system, you could also shrink the ext4 partition (to give space for the swap), but again it is risky, you need a backup.

*Edit: You should boot from another drive when editing partitions and you should **not** mount the partitions to edit*

---

### Post by cybrsaylr on 2011-11-16
> **Olle Wiklund said:**
> Do you intend to keep both systems (Windows as well as Ubuntu)? Or are you going to erase Ubuntu and start with a fresh install? Are you planning to keep your personal data (documents, pictures, media files ...) on the big NTFS partition?

*Edit: You should boot from another drive when editing partitions and you should **not** mount the partitions to edit*

Was worried about that. 
Thanks for the tips Olle.

Yeah I pretty much use the Windows partition for storage. When upgrading I move the 'Home' File to the Windows side, upgrade Ubuntu, then bring Home back to the Linux side after the upgade not losing a thing.

---

### Post by WasMeHere on 2011-11-16
Watch out for permissions when moving /home to an NTFS drive. It is ok if you make an image of it (tarball or whatever), but if you copy the files, there might be problems because the *read,write,execute bits* of linux are not supported by NTFS, where the permissions are set when mounted and the same for all files seen from linux.

---

### Post by philinux on 2011-11-16
> **An Sanct said:**
> Well, if you have no swap and run out of memory, then you have problem. I have 8GiB of ram and 32Gib of swap (I personally set it to such a high amount). Even with 8G of ram, I still run out and have to swap at times, but that is mostly because of my Virtual Machines and non-optimal SQL queries...

I'm afraid that much swap is probably a waste of disk space. [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by matt_symes on 2011-11-16
Hi

> Is the swap partition necessary ?In your case i would just create a swap file, not a swap partition, in your root partition. 

Then just edit your fstab to use the swap file.

Messing with partitions is dangerous at the best of times and i suggest backing up before hand.

Just my thoughts.... and, of course, it gives you another option :)

Kind regards

---

### Post by cybrsaylr on 2011-11-16
> **matt_symes said:**
> Hi

In your case i would just create a swap file, not a swap partition, in your root partition. 

Then just edit your fstab to use the swap file.
Makes sense but I have never done this.
Is it easy and can you post how it is done?

---

### Post by An Sanct on 2011-11-16
> **philinux said:**
> I'm afraid that much swap is probably a waste of disk space. [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
I believe you, but at a certain point of installing I decided to spare 32G off my second 1T HDD and delete the auto-generated swap, that was dwelling on my precious (*tiny* 64GB) SSD

If it is too much, may the gods have fun with it ;) (just not on my SSD)

PS. thanks you for the link ... will read it through ...

---

### Post by An Sanct on 2011-11-16
> **cybrsaylr said:**
> Makes sense but I have never done this.
Is it easy and can you post how it is done?

This [guide]("http://ubuntuguide.net/howto-expand-swap-space-by-adding-a-swap-file-in-ubuntu") should help :)

---

### Post by matt_symes on 2011-11-16
Hi

> **cybrsaylr said:**
> Makes sense but I have never done this.
Is it easy and can you post how it is done?

The general idea is here.

[http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)

Have a read of it. You need to create the file to be at least the size of you ram if you want to hibernate.

Also, if you want to hibernate you need to update your initramfs. The process is easy though.

If you want to use it to hibernate then post back. Any questions then post back.

Kind regards

---

### Post by cybrsaylr on 2011-11-16
> **matt_symes said:**
> Hi

The general idea is here.

[http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)

Have a read of it. You need to create the file to be at least the size of you ram if you want to hibernate.

Seems simple enough.

Therefore is this the correct procedure to create a 4 GB swap file:

 If you; Type following command to create 512MB swap file (1024 * 512MB = 524288 block size)
 Then I assume you; Type following command to create 4GB swap file (1024 * 4096MB = 4194304 block size) 

Therefore the b) code should be:

> # dd if=/dev/zero of=/swapfile1 bs=1024 count=4194304

Is this correct?



Then I wonder if those 5 lines of code namely, b, c, d, e, and Append code, should be entered 1 line at a time or all 5 together when putting those code lines in terminal?

I'm not a real expert at using command line.....

---

### Post by matt_symes on 2011-11-16
> **cybrsaylr said:**
> Seems simple enough.

Therefore is this the correct procedure to create a 4 GB swap file:

 If you; Type following command to create 512MB swap file (1024 * 512MB = 524288 block size)
 Then I assume you; Type following command to create 4GB swap file (1024 * 4096MB = 4194304 block size) 

Therefore the b) code should be:

     Quote:
                                                 # dd if=/dev/zero of=/swapfile1 bs=1024 count=4194304                                 
Is this correct?

That looks good; yes.

> 
Then I wonder if those 5 lines of code namely, b, c, d, e, and Append  code, should be entered 1 line at a time or all 5 together when putting  those code lines in terminal?They should be entered on five separate lines one after another hitting enter after each step.

In the line

```
vi /etc/fstab
```i would suggest using nano and not vi.

So to sum up.

1.  ```
sudo  dd if=/dev/zero of=/swapfile1 bs=1024 count=4194304
```Enter your password. It will not be echoed to the screen

2. ```
 sudo mkswap /swapfile1
```      This will format the file as a swap file.

3. ```
sudo swapon /swapfile1
```          This will start using the swap file. Check this by typing

```
free -m
```or 

```
swapon -s
```4.  ```
sudo nano /etc/fstab
```to start editing you fstab file

5. Add the line 

```
/swapfile1    none    swap   defaults 0 0

```Press ctrl + o to save and ctrl + x to exit.

If you then want to hibernate you have to update your initramfs. Post back if interested or any problems.

Kind regards

---

### Post by matt_symes on 2011-11-16
Hi

Be double sure to read my last post as i just fixed some typos

Kind regards

---

### Post by cybrsaylr on 2011-11-17
Hi, 
Success I believe.
Got this in terminal:
[IMG]http://i.imgur.com/CtopO.png[/IMG]

Was wondering since this is a swap file and not a partition, where is it located for view? Since it will not show up as a partition in GParted.

Also you posted, "If you then want to hibernate you have to update your initramfs."

 Is this as easy to do?

---

### Post by An Sanct on 2011-11-17
> **cybrsaylr said:**
> Hi, 
Success I believe.
Got this in terminal:
[IMG]http://i.imgur.com/CtopO.png[/IMG]

Was wondering since this is a swap file and not a partition, where is it located for view? Since it will not show up as a partition in GParted.

Also you posted, "If you then want to hibernate you have to update your initramfs."

 Is this as easy to do?
The picture you posted suggests, that its location is [B]/swapfile1

[/B]To update the 'initramfs', the command **update-initramfs** should do the trick. (I'm almost 99.99% you have to be root, so **sudo** will help :))

PS. here is a nice [manpage about intiramfs]("http://man.he.net/man8/update-initramfs") (worth reading)

---

### Post by Elfy on 2011-11-17
> **matt_symes said:**
> ... i would suggest using nano and not vi... I prefer to use nano as well for this type of thing - I use the nano -B so it creates a backup though.

---

### Post by matt_symes on 2011-11-17
Hi

It's a tiny bit more complicated than just calling update-initramfs to get Ubuntu to use the swap file for hibernation.

You need the offset of the file in the partition and you need to update the file /etc/initramfs-tools/conf.d/resume and then call update-initramfs.

From the terminal type

```
filefrag -v /swapfile1
```and also 

```
cat /proc/cmdline
```These two should give the UUID of your root partition and the offset of the swap file in that partition.

Post the results back here.

BTW: Update initramfs does require sudo privilege elevation.

I am also assuming you are using kernel hibernate and not any user space hibernation.

Kind regards

---

### Post by cybrsaylr on 2011-11-17
hi,

Finally got around to doing that.
Here's the results:
[IMG]http://i.imgur.com/QoTqz.png[/IMG]

Did it work?


BTW I can't find this newly created **/swapfile1**

Just where is it located?

---

### Post by WasMeHere on 2011-11-18
The swapfile is located in the root directory /

```
cd /
ls -l
```
should show it.

It is not in use yet. ***matt_symes*** was waiting for the output you just posted, and I think he will soon give you instructions.

---

### Post by matt_symes on 2011-11-18
Hi

From the terminal type.
[FONT=monospace]
[/FONT]```
sudo bash -c 'echo resume=UUID=22dc431a-e72e-4524-a470-01dfdf3fe806 resume_offset=3377152 > /etc/initramfs-tools/conf.d/resume'

```Enter your password. It will not be echoed to the screen.

Then type

```
sudo update-initramfs -u
```My original notes were taken from here. 

[http://www.kernel.org/doc/Documentation/power/swsusp-and-swap-files.txt](http://www.kernel.org/doc/Documentation/power/swsusp-and-swap-files.txt)

It suggests updating the kernel command line. I have also just come across this tutorial as well.

[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

It also suggests updating the kernel command line.

I expect i used the above two tutorials when i created my last swap file as my notes are similar. I'm pretty sure i had to update legacy grub last time i did this. The first one was written by the guy who wrote swsusp. So kudos to both of them.

So  let's update grub..

```
sudo nano -B /etc/default/grub
```Look for the line that says

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```and change it to

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash resume=UUID=22dc431a-e72e-4524-a470-01dfdf3fe806 resume_offset=3377152"
```Then type

```
sudo update-grub
```Next reboot your PC.

You should, hopefully, be good to go.

Be very careful typing in the uuids and the offsets. Check, double and then triple check them again.

A tip for you. You can copy and paste text from the terminal by highlighting it, right clicking on it and selecting copy. You can then paste it into a post. You can also do the converse and paste into the terminal.

It's better than taking a screen shot.

EDIT: Nice nano tip forestpiskie :)

Kind regards

---

### Post by cybrsaylr on 2011-11-18
Hi,
I got to the part:

Code:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
and change it to


but I am having problems changing that line to:
 > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash resume=UUID=22dc431a-e72e-4524-a470-01dfdf3fe806 resume_offset=3377152"

as you instruct.  
Haven't done this before or very often.....




BTW, To avoid typos doing this I usually copy and paste the code. Have found this more reliable than attempting to type in the code and missing a letter or stroke in long code lines. Hope this a OK.

---

### Post by matt_symes on 2011-11-18
Hi

> but I am having problems changing that line to:

 [QUOTE]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash resume=UUID=22dc431a-e72e-4524-a470-01dfdf3fe806 resume_offset=3377152" as you instruct. [/QUOTE]No problem. Let's try it with gedit instead.

In the terminal close nano b pressing ctrl + x. Don't save the file.

Press alt + F2 and type 

```
gksudo gedit /etc/default/grub
```Enter your password as usual.

Edit the line and save.

You may find gedit easier than nano.

Then continue the steps from my last post.

Kind regards

---

### Post by cybrsaylr on 2011-11-18
OK, 

Followed that, then ran 
> sudo update-grub

and got this output in terminal:
> rr@rr-Satellite-A215:~$ sudo update-grub
[sudo] password for rr: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-12-generic
Found initrd image: /boot/initrd.img-2.6.38-12-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda2
done


Did it work?

---

### Post by matt_symes on 2011-11-18
Hi

> Did it work?Looks like it.

Reboot your PC. Open a terminal and type

```
free -m
```and 

```
cat /proc/cmdline
```Post both results back here.

Kind regards

---

### Post by cybrsaylr on 2011-11-18
After reboot here are the results:
> rr@rr-Satellite-A215:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3835        692       3142          0         43        238
-/+ buffers/cache:        409       3425
Swap:           40          0         40
rr@rr-Satellite-A215:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-2.6.38-12-generic root=UUID=22dc431a-e72e-4524-a470-01dfdf3fe806 ro quiet splash resume=UUID=22dc431a-e72e-4524-a470-01dfdf3fe806 resume_offset=3377152 vt.handoff=7

I will have to study this because it's all greek to me....lol...
Never did this before.

---

### Post by matt_symes on 2011-11-18
Hi

> **cybrsaylr said:**
> After reboot here are the results:
> 
rr@rr-Satellite-A215:~$ free -m
total used free shared buffers cached
Mem: 3835 692 3142 0 43 238
-/+ buffers/cache: 409 3425
**Swap: 40 0 40**
rr@rr-Satellite-A215:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-2.6.38-12-generic root=UUID=22dc431a-e72e-4524-a470-01dfdf3fe806 ro quiet splash resume=UUID=22dc431a-e72e-4524-a470-01dfdf3fe806 resume_offset=3377152 vt.handoff=7 I will have to study this because it's all greek to me....lol...
Never did this before.

Well. It's almost correct. The swap file is too small. I have just run through the steps on my PC to make sure they work.

Take a look at this.

This created the file for me (in different location than yours)

```
sudo dd if=/dev/zero of=/media/sda2/swapfile1 bs=**1024** count=**4194304**
```This was the file created.

```
matthew@matthew-Aspire-7540:~$ ls /media/sda2/ -l
-rw-r--r-- 1 root    root    **4294967296** Nov 18 17:55 swapfile1
matthew@matthew-Aspire-7540:~$
```I then formatted it.

```
sudo mkswap /media/sda2/swapfile1
```Set it as the swap file.

```
sudo swapon /media/sda2/swapfile1
```and these are my results from free.

```

matthew@matthew-Aspire-7540:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2771       2615        156          0         27       1180
-/+ buffers/cache:      1407       1364
Swap:         **4095        1            4094**
matthew@matthew-Aspire-7540:~$ 
```My swap file is larger than yours for some reason.

Can you run this command

```
swapon -s
```and these two

```
cat /etc/fstab
``````
ls -l /swapfile1
```and post back results.

Kind regards

---

### Post by cybrsaylr on 2011-11-18
Hi, 
Ran it, here's the results:
> rr@rr-Satellite-A215:~$ swapon -s
Filename				Type		Size	Used	Priority
/swapfile1                              file		41936	0	-1
rr@rr-Satellite-A215:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
/swapfile1    none    swap   defaults 0 0

rr@rr-Satellite-A215:~$ ls -l /swapfile1
-rw-r--r-- 1 root root 42949632 2011-11-16 23:25 /swapfile1


---

### Post by matt_symes on 2011-11-18
Hi

Your swap file

```
rr@rr-Satellite-A215:~$ swapon -s
Filename      Type          Size       Used    Priority
/swapfile1   file          **41936**       0         -1
```My swap file.

```
matthew@matthew-Aspire-7540:~$ swapon -s
Filename                Type        Size    Used    Priority
/media/sda2/swapfile1  file        **4194300**    0    -1
matthew@matthew-Aspire-7540:~$
```I'm not sure what happened there. I thought we both used the same sizes for dd.

You have a 40Mb swap file and not a 4Gb.

I am just going to eat. We can continue later if you like.

Kind regards

---

### Post by cybrsaylr on 2011-11-18
OK, enjoy your meal....

---

### Post by matt_symes on 2011-11-19
Hi

Turned into a rather long meal that one. Well it was Friday night here.

Anyway back to the problem in hand. The swap file is too small. 

The issue is i don't know any way to increase the size of the swap file whilst keeping it in the same location *(anybody else know ?)*. It needs to stay in the same location because resume uses the resume-offset (the postition of the swap file in the filing system) to find the swap file after hibernation. The resume-offset value has already been plugged into your initramfs and grub.

You can have multiple swap files but i don't think they play well with hibernation.

Therefore i think the safest way is to start again if you like. Now you have completed the steps once it should be easy.

Let me sum them for you.

1. Disable swap

```
sudo swapoff -a
```2. Remove your existing swap file.

```
sudo rm /swapfile1
```We will keep your entry in fstab as we will use the same file name.

3. Create the new swap file.
[FONT=monospace]
[/FONT]```
sudo dd if=/dev/zero of=/swapfile1 bs=1024 count=4194304
```4. Format it as a swap file
[FONT=monospace]
[/FONT]```
sudo mkswap /swapfile1
```5. Add as swap file
[FONT=monospace]
[/FONT]```
sudo swapon /swapfile1
```6. Check the swap file size
```
swapon -s
```and look for this

```
Filename                       Type        Size           Used    Priority
/swapfile1                      file          **4194300**           0       -1
```Once we are sure this is correct we will set up hibernation again. That should also be pretty quick.

Kind regards

---

### Post by cybrsaylr on 2011-11-19
Hi again, 
Finally got around to it and it appears OK.....I think.

Here's terminal output:

rr@rr-Satellite-A215:~$ sudo swapoff -a
[sudo] password for rr: 
rr@rr-Satellite-A215:~$ sudo swapoff -a
rr@rr-Satellite-A215:~$ sudo rm /swapfile1
rr@rr-Satellite-A215:~$ sudo dd if=/dev/zero of=/swapfile1 bs=1024 count=41943044194304+0 records in
4194304+0 records out
4294967296 bytes (4.3 GB) copied, 172.322 s, 24.9 MB/s
rr@rr-Satellite-A215:~$ sudo mkswap /swapfile1
Setting up swapspace version 1, size = 4194300 KiB
no label, UUID=85ac7f5e-3969-4c57-9087-032e90ddedc0
rr@rr-Satellite-A215:~$ sudo swapon /swapfile1
rr@rr-Satellite-A215:~$ swapon -s
[b]Filename				Type		Size	Used	Priority
/swapfile1                              file		4194300	0	-1[/b]



Ran:   > sudo update-grub

Rebooted PC then ran the following and got this in terminal:

> rr@rr-Satellite-A215:~$ sudo update-grub
[sudo] password for rr: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-12-generic
Found initrd image: /boot/initrd.img-2.6.38-12-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda2
done

 
rr@rr-Satellite-A215:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3835        705       3129          0         45        229
-/+ buffers/cache:        430       3404
Swap:         4095          0       4095

rr@rr-Satellite-A215:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-2.6.38-12-generic root=UUID=22dc431a-e72e-4524-a470-01dfdf3fe806 ro quiet splash resume=UUID=22dc431a-e72e-4524-a470-01dfdf3fe806 resume_offset=3377152 vt.handoff=7



I took a look at this with GParted which shows an extra ~4GB of space being used in the Linux partition which I assume is due to this newly created Swapfile.

---

### Post by matt_symes on 2011-11-21
Hi

That's looking much better :)

To make sure hibernation will work please post the output of
[FONT=monospace]
[/FONT]```
filefrag -v /swapfile1
```It is most possible the offset of the file will have changed and we have to update initramfs and GRUB.

Kind regards

---

### Post by cybrsaylr on 2011-11-21
Hi, 
Here's that requested output:
> rr@rr-Satellite-A215:~$ filefrag -v /swapfile1
Filesystem type is: ef53
File size of /swapfile1 is 4294967296 (1048576 blocks, blocksize 4096)
 ext logical physical expected length flags
   0       0   114688            2048 
   1    2048   120832   116735   2048 
   2    4096   131072   122879   2048 
   3    6144   147456   133119   2048 
   4    8192   460800   149503   2048 
   5   10240   501760   462847   2048 
   6   12288   618496   503807   2048 
   7   14336   665600   620543   4096 
   8   18432  4296704   669695  32768 
   9   51200  4329472           32768 
  10   83968  4362240           32768 
  11  116736  4395008           32768 
  12  149504  4427776           32768 
  13  182272  4460544           32768 
  14  215040  4493312           30720 
  15  245760  4526080  4524031   4096 
  16  249856  4534272  4530175  32768 
  17  282624  4567040           32768 
  18  315392  4599808           32768 
  19  348160  4632576           32768 
  20  380928  4665344            2048 
  21  382976  4669440  4667391  32768 
  22  415744  4702208           16384 
  23  432128  4751360  4718591  32768 
  24  464896  4784128           32768 
  25  497664  4816896           32768 
  26  530432  4849664           32768 
  27  563200  4882432           32768 
  28  595968  4915200           32768 
  29  628736  4947968           10240 
  30  638976  4960256  4958207  32768 
  31  671744  4993024            2048 
  32  673792   684032  4995071   2048 
  33  675840   671744   686079   8192 
  34  684032   688128   679935   2048 
  35  686080   712704   690175   2048 
  36  688128   692224   714751   4096 
  37  692224   727040   696319   4096 
  38  696320   739328   731135  32768 
  39  729088   772096           32768 
  40  761856   804864           14336 
  41  776192   821248   819199  32768 
  42  808960   854016           30720 
  43  839680   886784   884735  32768 
  44  872448   919552           32768 
  45  905216   952320           32768 
  46  937984   985088           32768 
  47  970752  1017856           30720 
  48 1001472  1140736  1048575   6144 
  49 1007616  1148928  1146879  32768 
  50 1040384  1181696            8192 eof
/swapfile1: 25 extents found


---

### Post by matt_symes on 2011-11-21
Hi

Copy and paste each of these command from this post into a terminal one after another.

```
sudo bash -c 'echo resume=UUID=22dc431a-e72e-4524-a470-01dfdf3fe806 resume_offset=114688 > /etc/initramfs-tools/conf.d/resume'
```Double check it's correct by looking with

 ```
cat /etc/initramfs-tools/conf.d/resume
``````
sudo update-initramfs -u
``````
sudo sed -i 's/resume_offset=3377152/resume_offset=114688/g' /etc/default/grub
```Double check again.

```
cat /etc/default/grub
``````
sudo update-grub
```Reboot your PC and  you should (hopefully) then be able to hibernate.

Kind regards

---

### Post by cybrsaylr on 2011-11-21
Hi,
Just completed instructions in your last post and rebooted PC.

Hopefully that did the trick.
Is there any way to confirm?

---

### Post by matt_symes on 2011-11-21
Hi

Try to hibernate and resume.

Good luck. This has worked on my machine so it should also work on yours.

Kind regards

---

### Post by cybrsaylr on 2011-11-21
Hi,

Well I clicked hibernate on laptop and it went black after a few seconds.
 I waited a few minutes and tried to resume but nothing happens....

How do you resume? 
I never went into hibernate by clicking on hibernate before.
Am posting this from my desktop.





OK, I then closed laptop cover.
Waited a short bit, then opened lid and laptop reboots on its own.
Upon reboot I open Opera browser.
Opera asks if I want to go back to where I previously was.
I click yes and Opera takes me to exactly where I left off before clicking hibernate. (This is a feature of Opera I have used in the past and like.)

So did hibernate work or did Opera merely do its thing?

---

### Post by matt_symes on 2011-11-21
Hi

From your description i am not sure if the laptop is suspending or hibernating.

Open a terminal and type

```
sudo pm-hibernate
```

That will make it hibernate. You will need to hit the power button to wake it up.

Kind regards

---

### Post by cybrsaylr on 2011-11-21
Hi, 

Thanks for everything matt, will do.

Thanks again.

---

### Post by cybrsaylr on 2011-11-21
> **matt_symes said:**
> Hi

From your description i am not sure if the laptop is suspending or hibernating.

Open a terminal and type

```
sudo pm-hibernate
```

That will make it hibernate. You will need to hit the power button to wake it up.

Kind regards

Hi, 

Did the above in your last post and this is what occurs.

Laptop appears to shutdown. I hit power button and laptop seems to go through a normal reboot, only sound is muted. I just turn on the sound. When Opera browser is opened Opera asks if the previous session should be restored. I click yes and Opera restores the last session.

Same thing occurs when clicking on the top far right corner symbol, then clicking on hibernate from the drop-down choices. Laptop appears to shutdown. I hit power button and laptop seems to go through a normal reboot, only sound is muted. I just turn on the sound. When Opera browser is opened Opera asks if the previous session should be restored. I click yes and Opera restores the last session.

When I do a normal restart or shutdown laptop will shutdown. Then it restarts normally without the sound being muted. 

Just thought of posting this because I'm not sure what is going on since I have never put laptop directly into hibernate mode before. I would just let it go through the normal screen-saver then suspend mode. Then when any key is hit, all of where I was at last is restored. 

Just curious on what is happening here?

---

### Post by matt_symes on 2011-11-21
Hi

> **cybrsaylr said:**
> Hi, 

Did the above in your last post and this is what occurs.

Laptop appears to shutdown. I hit power button and laptop seems to go through a normal reboot, only sound is muted. I just turn on the sound. When Opera browser is opened Opera asks if the previous session should be restored. I click yes and Opera restores the last session.

Same thing occurs when clicking on the top far right corner symbol, then clicking on hibernate from the drop-down choices. Laptop appears to shutdown. I hit power button and laptop seems to go through a normal reboot, only sound is muted. I just turn on the sound. When Opera browser is opened Opera asks if the previous session should be restored. I click yes and Opera restores the last session.

When I do a normal restart or shutdown laptop will shutdown. Then it restarts normally without the sound being muted. 

Just thought of posting this because I'm not sure what is going on since I have never put laptop directly into hibernate mode before. I would just let it go through the normal screen-saver then suspend mode. Then when any key is hit, all of where I was at last is restored. 

Just curious on what is happening here?

When you hibernate all your programs will be written to the hard drive so it will go 
through the normal boot process. During hibernation everything is powered off. When you startup all your applications you had open when you hibernated will still be there when you come out of hibernation.

When you suspend almost everything is shutdown apart from just enough charge to keep the memory refreshed (and a couple of other things). When you restart all you applications will also still be open. Because there is still a trickle charge going to the memory then your battery will still lose charge but much slower than with normal running.

Hibernation uses no power as everything, including the memory, is powered off.

Let's see how hibernation went.  From the terminal...

```
sudo rm /var/log/pm-suspend.log
```

Hibernate your laptop. Bring it back around, open a terminal and type

```
cat /var/log/pm-suspend.log
```

Post back results here.

Kind regards

---

### Post by cybrsaylr on 2011-11-21
Hi,

Here's the results:
> rr@rr-Satellite-A215:~$ cat /var/log/pm-suspend.log
Initial commandline parameters: 
Mon Nov 21 20:04:32 EST 2011: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux rr-Satellite-A215 2.6.38-12-generic #51-Ubuntu SMP Wed Sep 28 14:27:32 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_realtek   336771  1 
arc4                   12529  2 
snd_hda_intel          33176  4 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_intel,snd_hda_codec
radeon                982182  4 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
binfmt_misc            17565  1 
ath5k                 155612  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
ttm                    76664  1 radeon
ath                    23773  1 ath5k
mac80211              294370  1 ath5k
drm_kms_helper         42394  1 radeon
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73535  0 
edac_core              53845  0 
soundcore              12680  1 snd
r852                   18246  0 
sm_common              16817  1 r852
drm                   227534  6 radeon,ttm,drm_kms_helper
serio_raw              13166  0 
k8temp                 13016  0 
joydev                 17606  0 
nand                   55112  2 r852,sm_common
nand_ids               12723  1 nand
nand_ecc               13230  1 nand
mtd                    27900  2 sm_common,nand
sp5100_tco             13744  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_piix4              13303  0 
edac_mce_amd           23464  0 
video                  19438  0 
cfg80211              178528  3 ath5k,ath,mac80211
sparse_keymap          13898  0 
i2c_algo_bit           13400  1 radeon
shpchp                 37297  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
firewire_ohci          40370  0 
usbhid                 46956  0 
hid                    91020  1 usbhid
ahci                   25951  1 
sdhci_pci              13989  0 
sdhci                  27387  1 sdhci_pci
libahci                26642  1 ahci
firewire_core          62646  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
r8169                  48022  0 
pata_atiixp            13165  0 
             total       used       free     shared    buffers     cached
Mem:       3927104     958744    2968360          0      54228     348444
-/+ buffers/cache:     556072    3371032
Swap:      4194300          0    4194300

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Mon Nov 21 20:04:34 EST 2011: performing hibernate


---

### Post by An Sanct on 2011-11-21
There is only one "Fail"

> Having NetworkManager put all interaces to sleep...**Failed**.

Are you using wifi or any other wireless communication solutions?

---

### Post by cybrsaylr on 2011-11-21
I use a wireless router.

---

### Post by An Sanct on 2011-11-22
Well, you can try to disable wireless and then suspend the machine.

Note, that I am just guessing here :) So if you have time to spare, its a shot, with a small chance of being the right answer.

---


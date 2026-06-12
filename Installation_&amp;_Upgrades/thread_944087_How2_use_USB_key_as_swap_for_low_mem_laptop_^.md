---
title: "How2: use USB key as swap for low mem laptop ^"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2008-10-11
How can I successfully set my Xubuntu 8.04 to use a swap file residing on a USB key ?

At the office, they gave me a laptop that was in a drawer but they didn't botter checking it. It only has 256Mb of memory. That is the only way that I can have a laptop at the office: take an old one and that is the only one left.

I installed Xubuntyu 8.04 on it. It has only one HD so I had originally created 1 partiton for the O/S and 1 partition for the swap. But it doesn't go fast enough.

So I thought, I have this 8Gb USB key that I do not use. Why not create 2 partitions on it: 1 4gb swap and 4gb Ext3. I removed the swap file on the laptop (formatted it as ext3 with the Xubuntu install CD).

But even with the USB key plugged in, it seams to go even slower then before and the USB key doesn't flash often (light).

How can I make sure my laptop is using the swap from the USB key ?

Will it go faster then with a 2nd partitioned Swap ?

USB key is an 8Gb, OCZ Rally-2 480Kb/s

---

### Post by cariboo on 2008-10-11
Using your usb device will not make the computer any faster when using it a a swap partition. Are you sure you are even using swap. What is the output of:

```
free -m
```

This will show us home much ram and swap is being used.

Jim

---

### Post by kerry_s on 2008-10-11
with 256mb ram you just need to trim the desktop, swap on the disk is fine. ubuntu is not light, debian is faster.
i'm running debian etch on a 450mhz 256mb ram laptop right now.
you can setup gnome for lower resource or try a window manager.
it really depends on your needs, theres tons of ways to make it work.

gnome net install:
[http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-businesscard.iso)

xfce4:
[http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-xfce-CD-1.iso)

dsl:
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by Browser_ice on 2008-10-11
Using the System Monitor and constantly opening new applications, I could see the amount of memory rising but the swap amount stayed at zero at all times. I eventualy winded up freezing the whole thing as all local memory was used but swap was still = 0

So I guess it really was not using any swap at all.

Should I set up the USB as swap on re-installation time ?

---

### Post by paxmark1 on 2008-10-11
I could be wrong, but for /swap or /tmp on a usb you might get better performance with ext2.  If it crashes or power goes out and battery is out, etc., etc., then you probably don't need the journaling of ext3.  

Of course, as previously noted, you might not need much swap.  

Etch, sounds good.  Possibly the oldest supported LTS of Ubuntu or Kubuntu would be sufficient, it is an older laptop, and then there is always Xubuntu.  Enjoy.

---

### Post by celticbhoy on 2008-10-13
Ubuntulight is another option. If it makes you feel better I am running Xubuntu on an old Compaq Presario 1246 with 128MB of ram with 8MB used for onboard graphics!!!
It works fine if you use common sense on what apps you use. I use opera for browsing. I still use OOo though, but it does run slow. If you manage to get your swap on usb issue working and you notice a difference please post and let us know.

Have a look here for some info and instruction :-

[http://ubuntuforums.org/showthread.php?t=395435&highlight=readyboost](http://ubuntuforums.org/showthread.php?t=395435&highlight=readyboost)

---

### Post by snowpine on 2008-10-13
On old computers, USB read/write is painfully slow. Putting your /swap on a usb device will definitely not make your computer any faster. For that matter, using swap in general will not speed your computer up, since swapping to/from a drive of any sort is about a thousand times slower than using ram. For optimum performance, you should use as little swap as possible by not exceeding your total ram. 

I think what you're experiencing is simply that Xubuntu is not the "fast, lightweight OS for old computers" that it's claimed to be. Try installing a truly lightweight windows manager (Openbox, Fluxbox, IceWM) and/or being selective about which applications you use (and not having lots of apps open at the same time). If all else fails, there are non-Ubuntu distros such as DSL or SliTaz that are much, much faster on old hardware.

---

### Post by celticbhoy on 2008-10-13
The problem is thhat on some old laptops (mine) the amount of ram you can put in is limited. My old presarion can only handle 128M in total. Therefore any other way of speeding up swap, and possibly freeing some disk space is an advantage (only got 4G)

---

### Post by jheaton5 on 2008-10-13
I have debian on an old old desktop with only 128mb ram.  Debian works a lot faster than XP(Whistler) that came on the box.  Ice Weasel(the debian version of Firefox) is not Firefox. And there is no flash player available for Ice Weasel, but for all other surfing Ice Weasel is fine.

---

### Post by tribaal on 2008-10-13
I concur with previous posts - you're better off choosing another window manager / lighter distro on you laptop.

Did you consider moving the data to the USB drive instead of putting the swap there? Even a slow hard drive will be faster than a thumb drive, and you can read/write as many times as you want on a HDD...

You could format to have a / and swap partition on the HDD and simply move all your data to the thumb drive (maybe even encrypted?)

Just a thought...

- Trib'

---

### Post by snowpine on 2008-10-13
If it's an old Pentium 2 with 128mb of ram and a 4gb hard drive, well, let's just say you have to be really selective what software you use! :) I think you made a good choice with Debian Etch. Personally I am currently using SliTaz on my old 500mhz Pentium 3 with 384mb of ram. I have used Ubuntu and Xubuntu on this laptop before, but found them very slow. It's all about having the right tool for the job...

Believe me, if you could double the performance of your computer using a $10 flash drive, we'd know about it by now. ;)

---

### Post by celticbhoy on 2008-10-13
is there a utility for testing the speed of a drive - as mem cards / drives differ in performance

---

### Post by Herman on 2008-10-13
bonnie++ is the benchmarking program I have tried in Ubuntu for testing  read/write speeds to file systems in various drives.

Flash memory is quick to read, but is generally slow to write to.

The speed and quality of flash memory varies a great deal between models, both within a manufacturer's range of products, and also between manufacturers.

Some flash memory available today is adversized as 'ReadyBoost' compatible, implying that it is okay to use as a swap area.

Flash memory is known to have a limited number or rewrites per block, but almost all modern flash memory has 'wear leveling' software which means the operating system writes to a fake hard disk but the real flash memory blocks are shuffled and rotated quietly in the background by the flash memory's controller software so we're really writing to different blocks each time to spread the wear. 

The endurance of flash memory varies a great deal between models and brands, and flash memory has improved a lot in recent times in both speed and endurance.
You need to find out the manufacturer's specifications and claims, (and warranty), for the exact make and model of flash memory you have or are thinking of buying.

ReiserFS has the ability to write small files up to fifteen times faster than ext2, and for large files it's the same speed. Depending on the flash memory controller you have, you may not notice much difference if you use ReiserFS, but in some flash meory sticks there is quite a big speed advantage from using ReiserFS.

---

### Post by snowpine on 2008-10-13
> **Herman said:**
> Some flash memory available today is adversized as 'ReadyBoost' compatible, implying that it is okay to use as a swap area.


Hi Herman, this is an interesting fact, thanks! Will I get a performance boost from a ReadyBoost stick on an old computer with USB 1.0, and do I need any special software?

---

### Post by Herman on 2008-10-13
> Will I get a performance boost from a ReadyBoost stick on an old computer with USB 1.0, and do I need any special software? You would not need any specail software to try it, just edit your /etc/fstab in Ubuntu to make it use the swap area in the USB instead of the swap area in the hard drive to try it out.

I will need to look up the speed for USB 1 and USB 2 to see how much difference there is.
EDIT: [USB 2.0, Hi Speed USB FAQ]("http://www.everythingusb.com/usb2/faq.htm")

I think that tribaal will be right though, generally you will probably be better off having the swap area in your hard disk, but it will be interesting to explore this question a little more. Flash memory can be very quick to read, so it might actually be better. Who cares if it's slow to write to, I think the read speed would be the most important for swap area.
I'm not sure, we should some tests and find out.

---

### Post by Herman on 2008-10-13
Another (simpler) way to benchmark the performance of your flash memory stick is to use the 'dd' command to make a backup copy of the entire disk.
```
sudo dd if=/dev/sdb of=/home/herman/usb.backup bs=4096 conv=notrunc,noerror
```Where: '/dev/sdb' is your flash device, (use GParted or 'sudo fdisk -lu' to find out). 
You will see that the dd command will show you the speed the operation was performaed at. That might not necessarily be an indication of the flash memory's speed though, but an indication of the speed of the slowest link in the process. (possibly the USB1 interface, or the speed of your hard disk or something).
```
974927+1 records in
974927+1 records out
3993304576 bytes (4.0 GB) copied, 391.608 s, **10.2 MB/s**

```At the same time, you will be making a backup of your USB, so you can erase it in order to use bonnie++, (if you want to).

To restore your flash memory again after you're finished,
```
sudo dd if=/home/herman/usb.backupe of=/dev/sdb bs=4096 conv=notrunc,noerror
```I won't have time right now to explain how to use bonnie++, but I'll be back later. :)

---

### Post by Herman on 2008-10-13
The best way to find out if having the swap area in a USB device is better or worse would probably be simply to try it in a slow old computer, I can't think of any better test for that.
I have an old computer here to. I'll try it myself sometime soon and see what happens and report back here.

---

### Post by celticbhoy on 2008-10-13
I think it will all come down to the quality and rating of the flash drive, as I say I am on an old, old laptop my flash drive is at least eight years newer, so it is not as though it is up against a modern hard drive.

---

### Post by Browser_ice on 2008-10-15
But since the tests I did proved that my USB swap was not used at all, how do I successfully set up my xubuntu to use the swap on my USB ?

No one answered !

---

### Post by Herman on 2008-10-15
> You would not need any special software to try it, just edit your /etc/fstab in Ubuntu to make it use the swap area in the USB instead of the swap area in the hard drive to try it out.:) Yes I did, or I thought I had. maybe I wasn't verbose enough. 
I'm sorry, that was my fault, I was being lazy and assuming you'd already know how to do that. It is quite an interesting question actually. :)

You should be able to create a swap area in your USB drive with Gnome Partition Editor.
If you don't already have Gnome Partition Editor installed, you can install it with, 'sudo apt-get install gparted'
```
sudo apt-get install gparted
```Here's a link about how to edit your /etc/fstab file, [Edit /etc/fstab Method for Mounting]("http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu").

So, you run 'sudo blkid' or '[COLOR=#000000][FONT=Bitstream Vera Sans Mono]ls /dev/disk/by-uuid/ -alh' [/FONT][/COLOR]to find out what your swap area's UUID number is. 
```
sudo blkid
``````
ls /dev/disk/by-uuid/ -alh
```Either of those two commands should give you a list of partitions with file systems and their UUID numbers.
Now you copy that output to clipboard, (just hilight and click 'copy').

Better make a backup of the file for safety's sake before editing,
```
sudo cp /etc/fstab /etc/fstab.backup
```Next, open your /etc/fstab file with gedit text editor,
```
sudo gedit /etc/fstab
```For convenience, you can temporarily paste the contents of your clipboard to an un-used area at the bottom of the file.

Now you edit the file with a new line for your new swap area something like this, 
```
# /dev/sdb5
UUID=a08d44f6-d681-4901-a7cc-345fc9fa9eb6 none            swap    sw              0       0

```Where: 'a08d44f6-d681-4901-a7cc-345fc9fa9eb6' is the actual UUID number for your particular USB disk's swap area.

If you see a swap are already registered in your /etc/fstab file for a swap area in your hard disk and you do not want to use it for the time being, just 'comment it out' for now.
We 'comment out' (make the operating system ignore information in a file or program), by placing a 'comment' mark before the line, in this case it's a 'hash' mark #.
Like this, 
```

[SIZE=-1][FONT=Bitstream Vera Sans Mono]# /dev/sda5
**#** UUID=[/FONT][/SIZE][FONT=Bitstream Vera Sans Mono]cf4f7390-4243-43b6-abef-30ad6f906b4a[/FONT][SIZE=-1][FONT=Bitstream Vera Sans Mono] none            swap    sw              0       0[/FONT][/SIZE]
```That's how to do it,  that should work.

Whether or not it's a good idea or will improve performance are yet to be explained.

Regards, Herman :)

---

### Post by Herman on 2008-10-15
One of the USB flash memory sticks I use is the [SanDisk Micro Cruzer]("http://usbtests.com/2008/03/sandisk-cruzer-micro-8-gb.html"), I have two of them.
They are advertised as 'ReadyBoost Compatible'.
Read speed for an ext2 file system tested at about 5 MBps, and write speed tested at around 27.5 MBps.
Most of the USB's that most people can afford would be about that speed or slower.

Any internal hard disk with an ATA-4 IDE interface or better would beat that.
ATA-4 came out in 1998, so if you computer is less than ten years old you probably will get best performance with your swap area in your hard disk.

 ATA-6, ATA-7 and ATA-8 (IDE) hard drives can handle transfer speeds of up to 100 or 133 MBps, but their read and write heads can still only achieve an actual media transfer rate of 60 MBps. The reason they can handle the faster interface is that they cache the data, so if you're writing small files to disk they'll seem faster, but for very large files they're still only about 60 MBps. 
A very fast hard drive might get up to 80 MBps, but those would be more expensive than average.

The USB 1.1 interface had low speed transfer rate of only 0.1875 MBps, and the 'full speed USB 1.1 was able to do 1.5 MBps. Both of those are much slower than the slowest hard disk interface, ATA-1, with a transfer speed of 8.33 MBps.
It would be no good having your swap area in one of those, you would be better off with the swap area in the hard disk.

With USB2, we can transfer files at 60 MBps, which is about equal to an ATA-5 capable hard drive, made from around the year 2000  onwards.
Not too many USB devices can read that fast, and they're very much slower to write to, so it wouldn't be sensible to make your swap area in one of those unles you have a particularly fast and high quality flash memory stick.
[Not all USB drives are created equal]("http://www.computerworld.com/action/article.do?command=viewArticleBasic&taxonomyName=management&articleId=323413&taxonomyId=14&intsrc=kc_feat") - Computerworld.

Something like an [8GB OCZ ATV Turbo USB Flash Drive]("http://www.memoryc.com/usb/flashdrives/8gboczatvturbo.html") might do it, or a Corsair.

---

### Post by snowpine on 2008-10-15
As I posted earlier in this thread, the best thing you can do to boost your speed is to use your ram efficiently. If you can keep your ram from filling up, you won't have to use swap, which will always be slow whether it's on a usb or regular hard drive.

---


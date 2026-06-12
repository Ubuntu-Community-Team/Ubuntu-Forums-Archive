---
title: "Wanting to make more permanent switch via external HD. Help please!"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by scialen on 2010-06-10
Hello all! This is my first post.

The idea is that I got to grips with Linux a couple of times in the past; most recently in a Radio Astronomy class (where we had to use openSUSE and terminals 24/7). I loved it so much that I fired up Wubi on my laptop and I am having a play.

Then I loved it even more.

So here's the plan:

Find Windows (Vista) CD *sigh*
Get 500 GB external Hard Drive
Backup files to HD (60 GB max)
Reformat Laptop & Reinstall Windows
====
To my understanding, this gives me a blank slate with a lot of room to play with because of the external HD. I want your help to help me through my ideal scenario. If this is not possible/too risky etc. then what are the best alternatives? Thank you in advance!

The plan is to make my primary OS Ubuntu. The way I figured, to keep things simple, is to keep the laptop's HD with Windows as 'normal'. I would thus install Ubuntu to the external HD, and put my files etc. on that.

Now, is that possible for a clean installation? Ideally, it would be fantastic if the boot can be configured so it would boot Ubuntu if the HD is connected, and Windows if not.

Is this possible?

---

### Post by darkod on 2010-06-10
Yes, but you only have to watch out where the bootloader, grub2, will go. In most cases it will install on your int hdd MBR and in that case you won't be able to boot without the ext hdd because grub2 needs its config files.

When installing to the ext hdd, in step 4 note down the name of the ext hdd, most probably /dev/sdb. Then in the last screen of the installer, before clicking Install, click on Advanced button and tell grub2 to install on the same disk, /dev/sdb in my example.

There should NOT be a number, just the name of the disk, /dev/sdb. A number means a partition on that disk.

That's it.

---

### Post by scialen on 2010-06-10
Thank you for that, darkod!

A couple of queries: I am doing this process in my head, so I assume "step 4" is the installation step?

Secondly, I take it what this does, is create an entire drive partition which is my external HD. After it does this, I take it I can put files, photos and all that via Ubuntu as you would expect. Can I still plug in when connected to Windows and use it as a HD, or will it see it as a completely full hard disk?

Thank you again, and it seems then that the key dynamic is watching out for the grub2 bootloader; putting it on the external hd will ensure the Ubuntu option only occurs when the HD is connected yes? I.e. effectively isolating ANYTHING to do with Linux/Ubuntu to the external HD.

---

### Post by darkod on 2010-06-10
Yes, it will load grub2 only when the usb hdd is connected and if you select to boot from it, otherwise it just loads windows from your int hdd automatically.

If you want to use the usb hdd for data trough windows too, you will have to make a ntfs partition on it first, and install ubuntu into the rest of the space. Windows can't see linux filesystem, so if the whole usb hdd is linux filesystem you can't use it for windows.

I suggest this:
Make a plan how much space to allocate to ubuntu. Ubuntu doesn't need too much for the system files, and if you keep your personal files on a shared ntfs partition so you can access them both from ubuntu and windows, it doesn't need much space for your personal files too.
Usually you install ubuntu on two partitions. One larger, the root partition (or /), like C: in windows, and smaller swap partition to substitute swap file in windows (linux uses swap partitions usually, not files but it's possible too). A third partition, separate /home partition is recommended to make future clean installs easier.

Swap size depends on your memory size, because if you plan to hibernate regularly it needs to be 1.5 x RAM memory. If not, 2GB is enough.
With a separate /home partition, the / partition needs only about 10-15GB.
If all your larger personal files like videos, photos, music are on the ntfs partition, you can make /home 20-25GB.
So that would be max 40GB + swap size for ubuntu.

So, depending how much space you allocate for swap, depending on your RAM size and hibernation need, boot windows and create one primary ntfs partition on your usb hdd which will be 500GB - 40GB - swap.
Leave the rest of the usb hdd as unallocated, don't create any other partition from windows.

Then boot with your ubuntu cd, in the step 4 of the installer select Manual Partitioning, and create the three mentioned partitions as LOGICAL partitions:

For /
size 15GB
filesystem ext4
mount point /

For swap
size xGB
filesystem swap area
there is no mount point for swap

For /home
size 25GB (or the rest remaining)
filessytem ext4
mount point /home

That's it. And don't forget clicking on Advanced and selecting grub2 to be installed to the same disk.

Ubuntu can read/write ntfs so you can access anything on any ntfs partition. That's why better keep smaller /home, and share the important data with windows on separate ntfs partition.

---

### Post by Joe of loath on 2010-06-10
Could you set Ubuntu to install to the USB HD using syslinux as the bootloader? Because then you set the laptop boot priority to boot from USB where possible, and it will boot ubuntu when the hard drive is plugged in.

However, why not just dual boot the laptop hard drive? It's much easier to do, although not quite as fun :p

---

### Post by scialen on 2010-06-12
Okay thank you again for the replies, and sorry about the delay.

I have the external HD, and I am thinking about a change in plan: not installing Windows.

Now to my understanding when it comes to backing up my files on the external HD there is a potential problem: would partitioning the drive in the manner you described also wipe the data from it? If that is the case, is it better to do the following? :

Create Ubuntu install CD
Boot the CD, create partitions and install Ubuntu onto the E-HD.
Backup Windows and Wubi Documents/files onto the free (and shared) partition.
Reformat laptop with nothing on.

This would then mean that my only OS is going to be Ubuntu, and it is isolated to the E-HD. The only reason I am doing this is so I can have my system with me in a more portable and permanent fashion; it is easier to simply switch laptops/desktops/netbooks and whack in the E-HD and carry on, than it is to reinstall Ubuntu etc. every time I switch. That is my goal anyway - a modular/plug-n-play OS (for lack of a better term).

I don't want Windows or Mac anymore. I want the open-source route because of its philosophy.
===
Darkod, can you explain in more detail the partitions? I am a little rusty on what you mean by it all. I think what you're saying is:

>>> The / partition = Ubuntu OS
>>> swap = something to do with RAM (I'll set it to 2GB)
>>> The /home partition = the space where I can put on documents, programs, pictures, whatever.

---

### Post by darkod on 2010-06-12
Yes, you got it right about the partitions.

There is no problem installing on the ext hdd as your only OS, but you're probably aware it will run slower from there than the int hdd. Plus, plugging in on another computer is good idea but in some cases there might be hardware incompatibility so ubuntu won't run properly on some computers.

---

### Post by X-Windows on 2010-06-12
I'll throw in my 2 cents here. When you create your partitions, I would recommend making them all *logical* instead of primary. This way if you ever need to repartition your system you will still have 3 free primary slots.

---

### Post by darkod on 2010-06-12
> **X-Windows said:**
> I'll throw in my 2 cents here. When you create your partitions, I would recommend making them all *logical* instead of primary. This way if you ever need to repartition your system you will still have 3 free primary slots.

We are talking about the ext hdd here. When creating all partitions from scratch, I see no reason all of them to be logical. I hate when I see a hdd with all logical partitions. Besides, the whole hdd will be allocated so where will the space to create 3 new primary partitions come from later? Yes, you could shrink partitions, but that's whole new layout again.

I stick to my plan. :) One primary ntfs and the linux logical partitions. Still able to create 2 primary later if needed.

---

### Post by scialen on 2010-06-12
Awesome. Nearly there for what I think I need to do. I made the Ubuntu CD and a final query:

the / partition; you mentioned it only needs to be 10-15 GB for the system files, but it is better to make it ~40GB because of... stuff.

Now, is this stuff the user profiles and applications/packages? I was hoping to put that sort of thing on the /home partition (akin to having C:\Program Files on Windows).

---

### Post by scialen on 2010-06-12
> **darkod said:**
> We are talking about the ext hdd here. When creating all partitions from scratch, I see no reason all of them to be logical. I hate when I see a hdd with all logical partitions. Besides, the whole hdd will be allocated so where will the space to create 3 new primary partitions come from later? Yes, you could shrink partitions, but that's whole new layout again.

I stick to my plan. :) One primary ntfs and the linux logical partitions. Still able to create 2 primary later if needed.

Whoa whoa whoa you threw me off my game here now!

I thought you said to make those three partitions LOGICAL anyway? Where did the idea of primary partitions come in?

BTW here is an image of the disk via disk utility:

[[IMG]http://imgur.com/eAPRil.jpg[/IMG]](http://imgur.com/eAPRi.png)

So it seems by default, what I have here is a primary partition. Are you saying I then create 3 LOGICAL partitions and thus have the primary still there? OR would it be preferable to have only the root and swap logical partitions and leave the rest as a primary for storage?

---

### Post by darkod on 2010-06-12
> **scialen said:**
> Awesome. Nearly there for what I think I need to do. I made the Ubuntu CD and a final query:

the / partition; you mentioned it only needs to be 10-15 GB for the system files, but it is better to make it ~40GB because of... stuff.

Now, is this stuff the user profiles and applications/packages? I was hoping to put that sort of thing on the /home partition (akin to having C:\Program Files on Windows).

User profiles and app settings would go into /home. I am not aware of any linux software that needs 40GB root. Linux is not as demanding for space for the system partition as windows is.

If you have the space make root 20GB, but you will soon see that you will use around 20% of that. But anyway, that's how you learn. :) I can't guess what you will install in ubuntu but rarely something needs 40GB. The other 20GB will be better utilized in /home.

---

### Post by darkod on 2010-06-12
> **scialen said:**
> Whoa whoa whoa you threw me off my game here now!

I thought you said to make those three partitions LOGICAL anyway? Where did the idea of primary partitions come in?



Things are getting complicated with no reason.

At the time when you said you want to use the ext hdd for windows too, I said:

1 primary ntfs partition (ntfs can be read from both windows and linux)
3 logical partitions for ubuntu as explained, /, swap and /home

If you don't want to create ntfs now any more, it's up to you how you want to create them. In that case I would say:

1 primary ext4 for /
2 logical for swap and /home

---

### Post by scialen on 2010-06-12
Thank you. My bad!

With the new scheme (1 Prim; 2 LOGIGAL) my bet is the /home cannot be read as a standard disk-space (meaning Windows, Mac cannot access /home).

---

### Post by darkod on 2010-06-12
> **scialen said:**
> Thank you. My bad!

With the new scheme (1 Prim; 2 LOGIGAL) my bet is the /home cannot be read as a standard disk-space (meaning Windows, Mac cannot access /home).

I'm not sure about Mac but windows won't be able to see any partitions on the ext hdd in that case. Hence the suggestion about primary ntfs partition.

Whether it's primary or logical it doesn't matter for windows. What matters is that windows can't read LINUX FILESYSTEMS, like ext4. Windows won't be able to see /, swap and /home partitions.

If you don't create any ntfs partition on the ext hdd, when you plug it in any windows computer it will just say unknown. You can't save files to it, or read from it.

So if you plan to use it as backup storage, temporary storage, or similar, for windows computers too, take that into account. You need at least one ntfs partition on it then. The size of that partition depends what amount of data you plan to keep on it.

---

### Post by scialen on 2010-06-12
Thank you very much for your help. I am thus going to set up the following:

1 15GB primary ext4 for Ubuntu
1 2GB logical for swap (should this be ext4 as well?)
1 (rest) NTFS logical for storage (which can thus be used on both Windows and Ubuntu).

Again, thanks for this. This is my first foray into such a thing.

Scialen

---

### Post by darkod on 2010-06-12
> **scialen said:**
> Thank you very much for your help. I am thus going to set up the following:

1 15GB primary ext4 for Ubuntu
1 2GB logical for swap (should this be ext4 as well?)
1 (rest) NTFS logical for storage (which can thus be used on both Windows and Ubuntu).

Again, thanks for this. This is my first foray into such a thing.

Scialen

Again, we are going backwards. The suggestion for 15GB / partition was when we were discussing separate /home partition and I thought you already decided to use separate /home.

If you have no separate /home, you should give / more than just 15GB unless you keep really only small files in your Home folder.

---

### Post by scialen on 2010-06-12
ok so how about

primary ext4 25GB for / (which now includes /home and /home/username) which will be for installing the Ubuntu OS

logical 2 GB swap partition - is ext4 okay for this?

The rest will be left, and thus will be seen as an external USB disk.

---

### Post by darkod on 2010-06-12
> **scialen said:**
> ok so how about

primary ext4 25GB for / (which now includes /home and /home/username) which will be for installing the Ubuntu OS

logical 2 GB swap partition - is ext4 okay for this?

The rest will be left, and thus will be seen as an external USB disk.

That's fine. The swap partition doesn't have specific filesystem, it just says swap area. It's not ext4. You will see when creating the partitions with the ubuntu installer.

In this case no need to create them in advance with Gparted. Just run the installer and create them with manual partitioning.

You will add the ntfs partition later or during the install, doesn't matter.

---

### Post by scialen on 2010-06-12
okay so that didn't quite work. It wasn't recognized; skips the hard drive and goes to the Windows Loader as usual (where I would select Ubuntu).

I also see on the desktop the 25GB partition that has Ubuntu installed.

On disk utility the partitions are there:
[[IMG]http://imgur.com/Zo52Kl.jpg[/IMG]](http://imgur.com/Zo52K.png)

Is it possible to wipe the external hard drive and try again?

---

### Post by darkod on 2010-06-12
What didn't work? If you used the Advanced button and set grub2 to install on /dev/sdb, you are aware that you need to enter BIOS or the Quick Boot menu and select to boot from the usb hdd right?

Otherwise if booting from your int hdd windows will load directly. It can't see linux partitions/OSs.

Yes, you can wipe the hdd and install again, but I think it's installed just fine. It's just that you are not booting from it.

---

### Post by scialen on 2010-06-12
Installing again. Bootloader on /dev/sdb/ or /dev/sdb1?

---

### Post by darkod on 2010-06-12
> **scialen said:**
> Installing again. Bootloader on /dev/sdb/ or /dev/sdb1?

/dev/sdb

---

### Post by scialen on 2010-06-12
Well it did seem to install, and I uninstalled Wubi to see if there were conflicts, and now either the BIOS doesn't recognise the hard disk, or Ubuntu does not boot.

I wonder if it is something to do with GRUB2. I installed it to what you said.

When the installation was finished and the CD ejected, I got a ton of I/O errors streaming. Just a thought.

Can you think of anything? Are there other topics that have this sort of problem?

Just to reiterate: it installed, but it is not booting.

---

### Post by darkod on 2010-06-12
Hmmm... ton of I/O errors? Doesn't sound normal.

Also, have you confirmed you can boot from usb at all? Have you booted any usb stick or similar on that computer?

PS. Also sometimes BIOS checks for boot files too fast and an ext usb hdd doesn't have the time to spin up. Try to enter into BIOS, no need to do any changes (if usb-hdd is set first to boot), just wait few seconds and exit.

---

### Post by scialen on 2010-06-13
Okay never mind.

I have actually just opted-out and installed Ubuntu onto the internal HDD; leaving the external hard drive as a nice storage device.

Thank you for your assistance!

---


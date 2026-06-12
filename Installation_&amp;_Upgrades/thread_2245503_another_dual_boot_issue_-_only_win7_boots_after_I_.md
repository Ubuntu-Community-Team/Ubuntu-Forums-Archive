---
title: "another dual boot issue - only win7 boots after I installed Kubuntu"
date: 2014-09-24
forum: Installation &amp; Upgrades
---

### Post by jerome11 on 2014-09-24
Hello,

Quite new to dual boot systems, i'd like to install a dual Win7/Kubuntu on a ASUS eee pc.
My aim was to get on a single HD:
one Partition with Win7
one partition with Kubuntu
and, if possible one partition as NTFS (for my data, so I can reach them from both OS)
Sorry for the long post, but I wanna show things as precise as I can.

I've read a lot of posts here, and found a few methods with some "must do" I tried.
One "must not do" I've read everywhere is that the boot loader shouldn't be on sda, but on sdaX (partition with /) because there are some problems... I didn't kow it and I and tried method 0

Method 0 (without partition Data)
- Install Windows 7 first - check
- Install Kubuntu:
I get sda divided in
sda1 ntfs - 100Mb - Win reserved
sda2 ntfs - 89Gb - Win OS
create
sda3 swap
sda4 /
ticked "boot loader on sda"
Installation goes on well - check
Reboot
Grub with Kubuntu and Windows - check
Work then on Kubuntu, all right - check
Work on Windows, all right - check
Power off
New day, Power on - blinking underscore...
(I know that one can repair the grub with Kubuntu Install CD and boot-repair, but, in my case, i had to do it at least twice in a while, so it can't be a long term solution)

So I tried the following:
Method 1:
- Install Windows 7 first - check
(I know that Win will use 2 primary partitions)
- Create third Partition NTFS - check
- Create one extended Partition under Windows with 2 logical Partitions in it (L1 for swap, L2 for /) - check
- Install Kubuntu:
I get sda divided in
sda1 ntfs - 100Mb - Win reserved
sda2 ntfs - 89Gb - Win OS
sda3 ntfs - 200Gb - Data
create (in L1/L2)
sda4 swap
sda5 /

ticked "boot loader on sda5"
Installation goes on well - check
Reboot
Only Windows reboot, no Grub

I thought there may be a problem with my way to create logical partitions, so I tried without Data and logical Partitions, choosing 4 primary partitions:
Method 2 (without logical partition and partition for Data)
- Install Windows 7 first - check
- Install Kubuntu:
I get sda divided in
sda1 ntfs - 100Mb - Win reserved
sda2 ntfs - 89Gb - Win OS
create
sda3 swap
sda4 /
ticked "boot loader on sda4"
Installation goes on well - check
Reboot
Only Windows reboot, no Grub

And now I have no clue.
Should I have to use /boot instead of / for the second linux partition?

Unfortunately, I need Windows for the softwares I use for my work (and a few others like spotify, and so on..)
I do all the rest on Linux.
I have an old Macbook Pro that now only runs Kubuntu, perfectly :-)

May be I have overseen something obvious to long time users, and I'd be thankful for help. 
 
Thanks,
JR

---

### Post by westie457 on 2014-09-24
Try it this way.
Install Windows 7 so you get 
boot partition 100 MB
Windows partitions - OS 89GB, data partition the rest apart from about 30GB. **Leave the last of the space 'unallocated'**.

Start the Live media in 'Try' mode, check things like wireless and graphics are working okay. Click on install.
At the main install screen choose 'Something Else'. A window opens with your current partitions listed. Select the unallocated space and click 'Change'.
In the pop up click New, make this - **very important** - 'extended'. Click Apply and agree to all prompts as they appear.
Now to get to the good stuff.
In your newly created Extended partition select 'new' > Use as ext4 > size is 'all' apart from 2GB > check the box to format > Mount Point / > click 'Okay'
Back to the small amount of free space > make this the Swap partition > Okay.
Look at the bottom of the partitioning window. Make sure the Boot-loader is to be installed to sda - **not sda with a number** which is a partition.
Once all that is done click on 'Install Now'
Looks complicated but is quite simple really.
See you on the other side

One thing about doing it this way is you can be doing things on your computer rather than just watch a slide-show while the installation progresses.

---

### Post by jerome11 on 2014-09-24
Hi Westie,

Thanks, I'll try right now. For me just to be sure, with 
" boot partition 100 MB Windows partitions - OS 89GB, data partition the rest apart from about 30GB."
you mean, for example on my 500Gb:
boot partition 100 MB
Windows partitions - OS 89GB, 
Data partition 380Gb
Unallocated about 30GB
Right?

---

### Post by westie457 on 2014-09-24
Hopefully there is a screen shot attached which shows my partition layout on a 500GB drive.
It might be slightly different to the sizes posted earlier. The general idea is the same.

---

### Post by jerome11 on 2014-09-24
Ok, got it :-)
thanks for the screenshot.
I work on it and keep you posted.

---

### Post by mastablasta on 2014-09-24
> **jerome11 said:**
> Hi Westie,

Thanks, I'll try right now. For me just to be sure, with 
" boot partition 100 MB Windows partitions - OS 89GB, data partition the rest apart from about 30GB."
you mean, for example on my 500Gb:
boot partition 100 MB
Windows partitions - OS 89GB, 
Data partition 380Gb
Unallocated about 30GB
Right?

right and while a that you should be able to install into largest empty disk space. or not...depends it hsould work in my case it didn't.

by the way - why does Windows 7 need boot partition? i also have it on preinstalled OS. i didn't add an extra data partition but just resized Windows os partition and changed it into secondary/estended. so now i think it's something like this:
/boot - primary
/windows - the os root partition (c:\) - secondary about 250 GB or so
/ 180 GB or something like that I forgot
/swap - I think I set it at 6 GB or something like that. 
/recovery - from windows - primary - bootable
/tools - I think it is called tools, but this linux thing that came on laptop. yeah it actually boots on fat32 partition into kind of live Linux session (called quick web or something like that). - primary bootable

---

### Post by jerome11 on 2014-09-24
Hi Westie,
So it took quite a time coz all seems to get somehow slow.
I got till line 
>At the main install screen choose 'Something Else'. A window opens with your current partitions listed.
>Select the unallocated space and click 'Change'.

But when I select the unallocated part, I only got the "add"-option, not "change"
It offers the usual options: ext4, ext3, ext2, btrfs, xfs, fat16, fat32, swap, physical...
But not: "extended" only

---

### Post by jerome11 on 2014-09-24
So, I've tried to set the unallocated partition to extended under Win7
When I do Kub install again I see the (now) usual "empty space" partition
I could again only choose new once selected, so I choose logical - ext4 - 79Gb - mount point on /
Then, for the last 4Gb, I didn't have a logical/primary choice, only how much (i took the rest) and what (I selected swap) 
then I put the boot loader on sda, without number, as you said.
Let see what's happening

---

### Post by yancek on 2014-09-24
> But when I select the unallocated part, I only got the "add"-option, not "change"

That's correct and as expected.  Unallocated has nothing on it so your need to "add" a partition with a filesystem.  If you already have a partition you want to use then you would select "change".  The default filesystem is ext4.

---

### Post by jerome11 on 2014-09-24
Hi Yancek,
Thanks for the Info.
So it means, I have to 
- "split" this unallocated space in logical - Ext4 - mount point / and Rest as swap
- put the boot loader to sda without number.
I'm trying that again, my Kub Installer crasched (probably too much tries :-)

---

### Post by jerome11 on 2014-10-12
Soooo,

An update on this story.
After a few different tries, I completely renewed my HD

Installed Win7 on a partition (it made 2, as usual)
Installed Ubuntu 14.4.01 : choosed "installation near Windows" and all default options
All right.

shutdown computer
computer on
grub
choosed Ubuntu: all right

shutdown computer
computer on
grub
choosed win7 all right
made changes in Win7 (installed programs I need for my job)

shutdown computer
computer on
no grub!!!!

Would it be possible that, when making changes (in my exemple installing programms) after ubuntu installation, Win7 rewrite mbr/grub?
I'm now trying to repair grub.

---

### Post by jerome11 on 2014-10-12
Yet used boot repair.
all works, just never understood why at once the 100Mb Windows partition is now shown in Grub.
Anyway, first tries seam to work again.
I gonna install another program in Win7 and see what happens.

For now to resume:
Same problem, whatever solution I try.
Thanks anyway to all inputs I got ;-)

Maybe it's my computer (asus eee pc seashell)
I have another one (asus Pro PV55) where i'd like to use the same configuration but I'm not sure if it wish to go again through the same problems.

Let's see...

---

### Post by oldfred on 2014-10-12
Is any of the software you install using some sort of proprietary DRM.

Grub writes its core.img right after the MBR with BIOS/MBR systems. And Windows will write some proprietary info into that same area.
We used to have lots of issues with flexnet, and usually sector 32. But grub was updated to work around flexnet so that issue is not valid, but perhaps you are using something different? Or maybe they changed things?
And it could be if grub is installed first, flexnet still overwrites sector 32, and a reinstall of grub will find it used and install correctly?

 Adobe Photoshop, CAD/CAM, Rosetta Stone, Matlab others 
 see google search on others with same issue: flexnet site:ubuntuforums.org
Sector 32 is already in use by FlexNet
[http://www.amazon.com/Adobe-Photoshop-Extended-CS4-VERSION/product-reviews/B001EUDGO2](http://www.amazon.com/Adobe-Photoshop-Extended-CS4-VERSION/product-reviews/B001EUDGO2)
The problem turned out to be Adobe's digital rights management software [DRM]. Do your own search for "FlexNet," formerly known as "SafeCast." What I have read is that FlexNet is a viral rootkit that replicates in multiple locations whenever a CS3 or CS4 product is installed, including trial versions.
Erase flexnet, if not using protected windows software anymore:
[http://ubuntuforums.org/showthread.php?t=1661254](http://ubuntuforums.org/showthread.php?t=1661254)
Grub2 bug Natty, overwrites windows boot in sector 63, recover backup & chkdsk to fix.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/730225](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/730225)

One advantage of UEFI/gpt is that grub has its files and Windows with UEFI creates its own 128KB partition for its own data so there is no overlap of where systems want to write data. Other issues, but that one was eliminated.

---

### Post by jerome11 on 2014-10-12
Hi!

Thanks for your hints.

> **oldfred said:**
> Is any of the software you install using some sort of proprietary DRM.


No I don't have any of them, only one CAT software called Traods Studio. and Office 2010 (both cracked:-/)
But may be they are responsible. I gonna check deeper.

When I used grub-repair, it actually told me that flexnet should be ewritten/retrieved (sorry I don't remember the word...)
I still don't understand why now grub shows me both win Partitions with win Loader, but I guess it's ok so, and I'm too new to Linux to dare to work on it, and get all things wrong.. :-)

My linux is working at the moment, so I can't check again.
but I keep you updated.

thanks again
K

---

### Post by jerome11 on 2014-10-18
Sooo here an update,

That's what you thought oldfred, except that, in my case, the "convict" seams to be one of Windows updates, not a program.
It p.... me off, because grub was once again broken, and I had to stop with my job till I had time to repair my PC, but at least I know now, with the best probability why.
Then id happended again after Win installed the new updates.
It's one of the one in the attached list.
Which one, and why it happened, I dunno.
(I'm not good enough in that stuff to find out)
But at least we have a f.... "lead"

The only solution was to use grub-repair again :-)

Let's see if it happens again.

(a lot of again in this post, unfortunately...)
Cheers,
Jerome

---

### Post by oldfred on 2014-10-18
Not a solution but a work around.

I prefer mulitple drives, then you can have the Windows boot loader on one drive and grub on the other. But if laptop that is not feasible, but you can install grub to a flash drive to boot your Ubuntu on your hard drive.

There are several ways to install grub to flash drive.

During install or after booting into it, you just reinstall grub to sdb's MBR. Rest of flash can still be used for data in any format. Only MBR is used. Set BIOS to boot from flash drive. 
If flash drive is sdb and you are booted into a working install:
 sudo grub-install /dev/sdb

You can install grub to flash drive as a grub only bootable drive. It creates a /boot with grub files but no kernel or any of the auto maintenance features like os-prober. You have to manually create a grub.cfg, but that can be as simple as just copying the boot stanzas from a working install. I also use this to directly boot several ISO from one flash drive as both emergency boot and repair tool.

If a larger flash drive you can put a full Ubuntu install onto it. I also have one of these more for emergency boot of my laptop. It also then has os-prober and will add boot stanza to boot all systems. You can also add ISO for repair and use it for that also.

---


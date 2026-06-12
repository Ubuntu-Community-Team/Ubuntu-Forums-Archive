---
title: "urgent! command-line interface at startup"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by jrockpunk1 on 2010-02-04
So I just partitioned my hard-drive, one side with windows the other to set free for ubuntu. It all worked fine. I put in the liveCD of ubuntu 9.10 and installed on to the partition. However, I have a problem. When it boots up it asks me to either boot into linux 2.6 or windows 7. Windows 7 works fine, but when I boot into ubuntu, the loading screen comes up and then it doesn't seem to boot into GDM. It's all command-line interface. I've tried sudo apt-get update and upgrade, but it isn't connected to my network yet so I can't do that. What can I do?

---

### Post by snowpine on 2010-02-04
Try typing:

```
startx
```

Does that work, and if not, what are the error messages?

---

### Post by jrockpunk1 on 2010-02-04
more erros than I can see, but here's the main ones:

```

-BELOW IS IN XORG.CONF-
(EE)Failed to load module "fglrx" (module does not exist, 0)
(EE)no drivers available.
Fatal server error: no screens found
xinit: no such file/direc - unable to connect to Xserver
xinit: no such process (errno3): server error.

```

Faulty install? Should I boot up and install from the liveCD again over this partition? (note the 'CD' is actually a USB. It does work though because I installed it on my notebook, which I'm typing this on now).

---

### Post by snowpine on 2010-02-04
I think fglrx is a driver for ATI video cards; I do not have personal experience with this type of card so I can't be much help. :( You may need to install a driver for your video card, but I don't know the answer myself. Good luck though! I'm sure one of the other experts will be along soon to help you out. :)

---

### Post by jrockpunk1 on 2010-02-04
I think it may be because on the liveCD i wanted to test if i could install my ATI driver, so i installed it on the liveCD and it said I needed to reboot, then I installed the OS. I'm guna try reinstalling and tell you if it happens again. Thanks for the help.

---

### Post by jrockpunk1 on 2010-02-04
Working :)

Installed again.

Now, whats the easiest way to delete the old ubuntu that does't work? (I have the 40GB ubuntu that works, 420GB win7 and 5GB ubuntu that doesn't work).

---

### Post by jrockpunk1 on 2010-02-04
Nobody?

---

### Post by morrcahn on 2010-02-04
Try using gparted on your working Ubuntu. That should work, although you should have deleted it when you re-tried so you could use that for you working Ubuntu.

---

### Post by jrockpunk1 on 2010-02-04
Well I tried that whilst installing, but it only deleted the space allocated for ubuntu and not the space the kernel was stored on (thus it's only like 2GB now). Let me go and try.

---

### Post by jrockpunk1 on 2010-02-04
OK here's gparted:

[img]http://i46.tinypic.com/103j30k.png[/img]

I'm scared I'm going to delete my current kernel or something. Which do I delete? :S

---

### Post by SecretCode on 2010-02-04
/dev/sda5 is the earlier ubuntu installation (and /dev/sda6 is an earlier swap partition that you don't need either). (The ones with key symbols are mounted - so you can tell those are the ones you are running from.)

You could delete them in gparted ... but then your good partition would be seen as /dev/sda5. We'd need to check that your working installation doesn't reference those partitions by sda-number ... can you post the contents of the file /etc/fstab?

(NB after deleting those partitions you would want to move and resize the good partitions - but you won't be able to do this while they are mounted. So at that stage - not yet - you will have to boot from the Live CD and run gparted.)

---

### Post by jrockpunk1 on 2010-02-04
I don't have an fstab file. Should I go ahead and delete sda5 and sda6?

[edit]
Sorry, was looking for a folder, silly me:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=469506d1-88db-4153-be50-279a5c64fa96 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=890f3e8d-5ad7-42c5-9e6b-8f05c996d552 none            swap    sw              0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by SecretCode on 2010-02-04
That's like saying you don't have an IP address. I don't know any ways of installing Ubuntu that would not have a file at 
```
/etc/fstab
```
 Check again.

---

### Post by jrockpunk1 on 2010-02-04
Read my edited post...

---

### Post by jenaniston on 2010-02-04
> **jrockpunk1 said:**
>  . . .Faulty install? Should I boot up and install from the liveCD again **over this partition?**
 (note the 'CD' is actually a USB. It does work though because I installed it on my notebook, which I'm typing this on now).

Answer . . . NO, not yet.
You are in pretty good shape - all fears aside.

I am in a Ubuntu9.04 USB Live 1GB booted on a campus computer in the library . . .
**nothing needs to be installed to run the live OS to partition** 
so you can partition to make free space or other filesystem . . . for which to then - later,  like in an hour  - do the install to if you want.

If you want to try this first, 
run the live USB as a live version and then run commands # df -h and # sfdisk -l 
Post results if you want to try my recommendation. 

Good luck.

P.S. -
that **1** (the pass character) in fstab for the ext4 partition means you will be getting an automatic filesystem check after 25-30 mounts
and since the errors=remount-ro is set,
when the filesystem check finds errors you will have a read-only partition there.

While you can hold off on changes to that yet, don't expect great things happening if you wait past 25 mounts of this filesystem.
Just thought you should know what to expect - and not be ***too*** *freaked* out.

---

### Post by jrockpunk1 on 2010-02-04
Ehhh.... this is confusing. So shouldn't I delete any of the other partitions yet?

---

### Post by morrcahn on 2010-02-04
It is safe to assume that your usable Ubuntu is on the larger ext4 (33.05GiB) and the 1.46 swap was made with that. You can tell by the numbers: sda5 and sda6 were created first so those are the first Ubuntu. And then sda7 & 8 is for the working one. Your kernel is stored in root which would be in your sda7 ext4 partition.

Also, nice 1 MiB unallocated. Random. Haha.

---

### Post by sailthesea on 2010-02-04
> **jrockpunk1 said:**
> Ehhh.... this is confusing. So shouldn't I delete any of the other partitions yet?

Just don't rush into anything yet!
As already advised you can delete the unwanted partitions and tidy things up Take the time to understand what you are doing and not only will you fix thing you will gain valuable experience in managing a Disc environment ;)

---

### Post by jrockpunk1 on 2010-02-04
Well, I'm not going to rush it, but I can't see what I'm going to gain by waiting. I'll boot up and delete the 2 old partitions in a while, then post how it goes.

---

### Post by jenaniston on 2010-02-04
Also, btw **sda7** (ext4) is usually ***NOT*** a primary partition.

Yes, you will have to probably re-install -
but I always prefer to install to free space -
and you could make that with a live (not-installed) version first.

So you can run Ubuntu Live from just the USB live version - to test out everything first.
(It mounts in what I'll call "ramdisk space" only - 
nothing is overwritten - except for USB overlay if you have it.)

Orders of sda 2, 3, 4 can certainly be made ***AFTER*** extended partitions like 5, 6, 7 were made - but yes, /dev/sda1 is always first.

---

### Post by jrockpunk1 on 2010-02-04
OK, I've tried deleting the partitions on both this OS and the liveCD. They both say this:

```

Unable to delete /dev/sda5!
Please unmount any logical partitions having a number higher than 5

```

Also, on the bootup screen when I choose my OS it has 6 options:

1) ubuntu
2) ubuntu repair or whatever
3) memory check or something
4) windows 7
5) ubuntu (on /dev/sda5)
6)ubuntu repair (on /dev/sda5)

---

### Post by jrockpunk1 on 2010-02-04
Anyone? :(

---

### Post by jenaniston on 2010-02-04
> **jrockpunk1 said:**
> Also, on the bootup screen when I choose my OS it has 6 options:

1) ubuntu
2) ubuntu repair or whatever
3) memory check or something
4) windows 7
5) ubuntu (on /dev/sda5)
6)ubuntu repair (on /dev/sda5)

OK, that's great . . .you want to keep windows 7 

So try choice 2 . . . but will you have another computer to be online with or not . . .?
scroll down to about the second or so from bottom then -tab- to go to OK choice and enter to go in recovery mode terminal.

to go out enter exit . . .

you will be in a command terminal first line starts at very bottom . . .
hopefully not off the screen completely but if it** is** - then just keep pressing enter several times to scroll it up.

make a command like 
```
uname  - a
```let me know what you get.

also for some experience try
```
cfdisk -l 
```just see what you have -
but press arrow keys over to quit - I realize you won't be able to cut and paste results.

Also, you probably won't have to delete - but it may be easier for you.
But let's see how all this goes for ya'

---

### Post by jrockpunk1 on 2010-02-04
```

Linux jacob-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/linux

```
says that twice when I do uname -a

```

sda1 Primary - NTFS - 104.86
sda2 Primary - NTFS - 400000.00 (something like that)
sda5 Logical - Linux ext3 - 3117.39
sda7 Logical - Linux ext3 - 35483.86
sda8 Logical - Linux swap / Solaris - 1571.03
sda6 Logical - Linux swap / Solaris - 1768.44

```
That's roughly what cfdisk prints (-l is an invalid option :S)

---

### Post by jenaniston on 2010-02-04
> **jrockpunk1 said:**
> ```

Linux jacob-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/linux

```says that twice when I do uname -a

```

sda1 Primary - NTFS - 104.86
sda2 Primary - NTFS - 400000.00 (something like that)
sda5 Logical - Linux ext3 - 3117.39
sda7 Logical - Linux ext3 - 35483.86
sda8 Logical - Linux swap / Solaris - 1571.03
sda6 Logical - Linux swap / Solaris - 1768.44

```That's roughly what cfdisk prints (-l is an invalid option :S)

glad to see you can work cfdisk ok - it's not hard.

I don't see any good reason for you - or the Ubuntu Live "Install to Hard Disk" installer (unless you tried a custom config of partitions) 
to give you **no primary partition for linux** ext3 partition(s).

If you want to be even better than cfdisk - try parted

once in parted it will give you a parted prompt and print free
```
[liveuser@localhost ~]$ su -
[root@localhost ~]# parted
GNU Parted 1.8.8
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print free 
```But we already know you should delete those linux partitions -
and we could use cfdisk,
but see what parted says too.

**Be sure to quit parted with q** - it is ***not ***forgiving asking to write to disk like sfdisk and cfdisk.

So, if your live USB boots up fine you can do this all from there from now. 

Live works well and is what you want to install from ?

---

### Post by jenaniston on 2010-02-04
Hah . . . yes it IS **sfdisk -l ** and **fdisk -l**, 
and then you need to choose the
 device with **cfdisk /dev/sdX** . . .

My bad , so yes better check all partitions with 
```
sfdisk -l
```and it will safely return to prompt.

---

### Post by jrockpunk1 on 2010-02-04
now I have another problem. It keeps giving me "authentication failure" when I type su. I'm typing in my login password when it asks me for authentication. What could the su password be?

[edit]
Eh, I'm tired of all this messing. I just want to go ahead and delete it, and deal with the consequences if it fails. How can I do that? Use chdisk?

---

### Post by jenaniston on 2010-02-04
> **jrockpunk1 said:**
> now I have another problem. It keeps giving me "authentication failure" when I type su. I'm typing in my login password when it asks me for authentication. What could the su password be?

[edit]
Eh, I'm tired of all this messing. I just want to go ahead and delete it, and deal with the consequences if it fails. How can I do that? Use chdisk?

yeah, I kinda thought you were doing that -
I'd start at the highest number partition in cfdisk since it didn't like you deleting the lowest
 logical partition before the upper extended partition -

Windows does that too.

scroll up/down to partitions and delete - be sure move arrows to write in cfdisk
you will enter yes at yes/no
then you can enter quit

delete all but your windows partition I guess

Let Ubuntu 9.10 then Install to free space . . .
when live installer runs . . . it should go really easy with live installer onto free space.

It is slooow from USB live -
I played chess while waiting - it doesn't bother the install.

At end . . . it will show you installing grub / bootloader . . .
that is good.

Good luck.

---

### Post by SecretCode on 2010-02-05
OK, your fstab references the partitions by UUID so there will be no problem with the partition numbers changing when we delete the others.

> **jrockpunk1 said:**
> OK, I've tried deleting the partitions on both this OS and the liveCD. They both say this:

```

Unable to delete /dev/sda5!
Please unmount any logical partitions having a number higher than 5

```
I didn't expect that, but I think it's because the live CD is grabbing the swap space on the disk. In gparted from the live CD, right-click the swap partition and click 'swapoff'. If any of the partitions still have key icons, right-click and 'unmount'.

> **jrockpunk1 said:**
> Also, on the bootup screen when I choose my OS it has 6 options:

1) ubuntu
2) ubuntu repair or whatever
3) memory check or something
4) windows 7
5) ubuntu (on /dev/sda5)
6)ubuntu repair (on /dev/sda5)

1, 2 and 3 are all standard. 4 you definitely need! 5 and 6 will disappear after you have removed those partitions and run
```
sudo update-grub
```
- but I would definitely recommend rebooting into both windows and the good ubuntu, after deleting the partitions and before moving any of them, and only update grub last.

In other words
- boot live cd
- run gparted
- make sure all disk partitions are swapoff'd and unmounted
- **delete** the partition sda5 2.90gib and the partition sda6 1.65gib (and leave them as unallocated space)
- strongly recommended: boot into windows to check, boot into the working ubuntu to check
- boot live cd again and run gparted; again swapoff and unmount if necessary
- **move** the swap partition of 1.46GiB (it will probably now be called sda6) to the end of the drive. Allow a few minutes.
- it can't hurt at this point to check booting the installed OSes again
- once again, go into live CD & gparted
- **move and resize** the ubuntu partition to use all the available space. This can take quite a while, and is potentially destructive (not likely but there's always a risk)
- reboot and check everything
- then run *sudo update-grub*


---

@jenaniston - Are you making this more complicated that it needs to be? There's no need for primary partitions. And I'm guessing that jrockpunk1 is going to be more comfortable with the gui gparted, and will get everything he needs there.

---

### Post by jenaniston on 2010-02-05
> **SecretCode said:**
> 
 
 @jenaniston - Are you making this more complicated that it needs to be? There's no need for primary partitions. And I'm guessing that jrockpunk1 is going to be **more comfortable with the gui gparted, and will get everything he needs there**.
Hah . . .   gparted was giving him a HEADACHE.

 Nah . .  I made it ***extremely EASY*** in reality.
 
 The  gui gparted is not as easy . . . in fact, that ***was*** what was obviously confusing him -
 already he had tried it - and **already he WAS confused by gparted**.
 **gparted** is what was** complicating things for him**.
 
 In asking for anyone out there, the poster wanted help.
> **jrockpunk1 said:**
> Anyone? :(
 
 So once I was aware that the very easy command line was available for him  . . . 
the** cfdisk** utility was thought of as the ***easiest*** way to suggest to him to easily delete the partitions -
 and then start a new install from a live U9.10 USB.
(**cfdisk **has it's issues - but it is ***extremely easy*** to use -
it's deficiencies are beyond the scope here **as long as it worked for him** to understand both what he was deleting and the free space he made . . .
and then **write** his changes (or *not* if he wanted to back out - VERY safe for a newbie partioner).
 
 While you may need to defend the gparted utility - with the gparted pretty colored screen 
 the poster was begging for help **not wanting to delete the wrong partition**.
But it was all up to the poster to try what was easiest - no qualms to anyone really about making suggestions.

> **sailthesea said:**
> Just don't rush into anything yet!
As already advised you can delete the unwanted partitions and tidy things up Take the time to understand what you are doing and not only will you fix thing you will gain valuable experience in managing a Disc environment ;)
 I was not the only contributor that was pretty sure that there was ***nothing easier ***than a fresh start deleting partitions and starting anew.
 He has probably learned a bit from cfdisk deleting his partitions.
 But no, not the only way - although I maintain other fixes are the more complicated variety.

 
 The post above by **SecretCode** is possibly the more confusing to him, but *whatever* -
it doesn't matter - whatever sticks.
 
 But this should all be solved already anyway, as he didn't want to wait . . .
so the post above was really all for naught.  But thanks anyhoo.
 
 And with installer in the Live U9.10 creating and **installing to an ext3 primary partition** - 
it will be easier for grub bootloader - and** easy** for the poster.

the one thing that complicated my posts . . .
I had logged in Ubuntu Live in a foreign language choice ( where I'll visit in Europe this summer)
 and the keyboard punctuation characters were in different keys all over.
***Hah*** . . . I had more difficulty typing my posts than the poster had making free space with **cfdisk** for the fresh U9.10 install.


So, it's Debian Linux to the rescue again - simplifying things for new linux users for over a decade now - 
Thanks Ian.

---

### Post by jrockpunk1 on 2010-02-05
> **SecretCode said:**
> 

In other words
- boot live cd
- run gparted
- make sure all disk partitions are swapoff'd and unmounted
- **delete** the partition sda5 2.90gib and the partition sda6 1.65gib (and leave them as unallocated space)
- strongly recommended: boot into windows to check, boot into the working ubuntu to check
- boot live cd again and run gparted; again swapoff and unmount if necessary
- **move** the swap partition of 1.46GiB (it will probably now be called sda6) to the end of the drive. Allow a few minutes.
- it can't hurt at this point to check booting the installed OSes again
- once again, go into live CD & gparted
- **move and resize** the ubuntu partition to use all the available space. This can take quite a while, and is potentially destructive (not likely but there's always a risk)
- reboot and check everything
- then run *sudo update-grub*


OK I deleted the 2 partitions, rebooted, and instead of going to the screen where I choose which OS to boot in to, it says:

```

GRUB loading
error: no such partition
grub rescue>

```
After grub rescue> is a prompt, I can type stuff.

I can't get into any of my OS's :(
What should I do?

---

### Post by jenaniston on 2010-02-05
> **jrockpunk1 said:**
> OK I deleted the 2 partitions, rebooted, and instead of going to the screen where I choose which OS to boot in to, it says:

```

GRUB loading
error: no such partition
grub rescue>

```After grub rescue> is a prompt, I can type stuff.

I can't get into any of my OS's :(
What should I do?

Deleting the partition like you wanted was very easy with cfdisk rather than the confusion you had with gparted - wasn't it?

Now, just run a** Live** version of **Ubuntu** . . . or live version of Fedora or FreeBSD or any operating system you want . . 
Install **from a Live Ubuntu** using the "Install to Hard Disk" installer" - all very easy . . 
The grub bootloader will install with this method . . .
and give you the choice of Ubuntu and other operating systems including the recovery kernel and Windows.

All OS kernels will then be available to boot all the time from grub - all ***too*** easy.

---

### Post by jrockpunk1 on 2010-02-05
I used Gparted to uninstall, but cfdisk taught me a lot. And my problem is, I have my linux OS, windows, and unallocated space. However, when I boot up it takes me to the grub rescue prompt. I want to keep both my current linux OS and definitaly windows with which I have about 50 games that take up 350GB on. I don't want to do any reinstalling now that I've deleted the other OS.

---

### Post by SecretCode on 2010-02-05
> **jenaniston said:**
> Install **from a Live Ubuntu** using the "Install to Hard Disk" installer" - all very easy . . 

You want him to reinstall Ubuntu just to fix GRUB? Maybe you are not very good at explaining yourself ... the alternative is that you are very thoughtless.


jrockpunk1, boot to a Live CD (that part is good!) and reinstall the grub files as described here: [Grub2 - Community Ubuntu Documentation](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by jenaniston on 2010-02-05
> **SecretCode said:**
> You want him to reinstall Ubuntu just to fix GRUB? Maybe you are not very good at explaining yourself ... the alternative is that you are very thoughtless.


jrockpunk1, boot to a Live CD (that part is good!) and reinstall the grub files as described here: [Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

How so . . . thoughtless?

He wanted an easy way to delete partition - **DONE**. doesn't matter how

He wants to install Ubuntu again - and grub comes very easy with the Live Install.

So run the live version - and install.
**grub will be added** . . . so ***very easy*** . . . 
yes - it *could* be done even thoughtless - it is that so very ***easy***,

But instead, I just play the chess game against the GNU chess monster to waste time I guess 
all while waiting for the really easy grub to be installed effortlessly.

But if there are any easier ways to just install grub **then let's here about them**.

---

### Post by jrockpunk1 on 2010-02-05
> **SecretCode said:**
> You want him to reinstall Ubuntu just to fix GRUB? Maybe you are not very good at explaining yourself ... the alternative is that you are very thoughtless.


jrockpunk1, boot to a Live CD (that part is good!) and reinstall the grub files as described here: [Grub2 - Community Ubuntu Documentation](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Thanks :) It works

Now, when I boot up, it still shows 3 OS's. It shows linux 2.6, another linux 2.6 and windows. I've updated GRUB too. Will that go when I assign the unallocated space to this OS?

Also, can you tell me the best way to do so? I don't want to sound like I'm being spoonfed but I really don't want to mess this up.

[edit]
Also, should I delete my swap files?

---

### Post by SecretCode on 2010-02-05
The two linux boot entries are normal - one of them is a recovery option and worth keeping.

By "swap files" do you mean the swap partitions?

Post your current disk layout - either a gparted screenshot or the output of 
```
sudo fdisk -l
```
so we know how far you have got.

---

### Post by jrockpunk1 on 2010-02-05
It has 3 literal OS's in GRUB boot. From memory, it's something like this:

```

linux 2.6____ generic
linux 2.6____ generic recovery mode
linux 2.6____ generic
linux 2.6____ generic recovery mode
memory check
memory check____
windows 7

```

the ____ are things I can't remember. So it still thinks I have 3 OS's, but GParted shows different:

[img]http://i47.tinypic.com/sdo6f5.png[/img]

---

### Post by SecretCode on 2010-02-05
Can you boot into the 'good' one? And run
```
sudo update-grub
```

What happens if you boot into the other one?

---

### Post by jrockpunk1 on 2010-02-05
Updated GRUB again, still the same. I booted into it and it's exactly the same as this OS... all files and programs, and compiz settings.

Could it be that I'm booting into the swap partition or something?

---

### Post by SecretCode on 2010-02-05
Hmm. Post your /boot/grub/grub.cfg

---

### Post by jrockpunk1 on 2010-02-05
```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 469506d1-88db-4153-be50-279a5c64fa96
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 469506d1-88db-4153-be50-279a5c64fa96
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=469506d1-88db-4153-be50-279a5c64fa96 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 469506d1-88db-4153-be50-279a5c64fa96
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=469506d1-88db-4153-be50-279a5c64fa96 ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 469506d1-88db-4153-be50-279a5c64fa96
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=469506d1-88db-4153-be50-279a5c64fa96 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 469506d1-88db-4153-be50-279a5c64fa96
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=469506d1-88db-4153-be50-279a5c64fa96 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 2eb46ff5b46fbdc9
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```

---

### Post by SecretCode on 2010-02-05
OK, that should have been obvious! You have multiple kernels installed. GRUB allows you to boot to older kernels in case problems crop up with new ones. It's generally good practice to keep at least one old kernel.

So this too is normal.

---

### Post by jrockpunk1 on 2010-02-05
OK, so everything's good now?

Right, now for the next part:

a) boot up into liveCD
b) unmount/swapout partitions
c) Add unallocated space to current installed partition

That right? If so, whats the best way to do c?

---

### Post by SecretCode on 2010-02-05
At most you are going to regain 4.5GiB to add to your 33GiB partition. At worst you will lose the entire drive including the windows partitions and have to reinstall from scratch. 

Are you sure you want to proceed? (Y/N)

Seriously, don't do this unless you have backups, at least of your ubuntu partition. I recommend clonezilla for partition backups.

---

### Post by jrockpunk1 on 2010-02-05
Point taken, I'll leave it as it is.

Thanks SecretCode and thanks to everybody in this thread that's helped me :)

---

### Post by SecretCode on 2010-02-06
On the other hand, I strongly recommend backups anyway (of the drive/partitions). **Anything** can happen to a drive or a file system. So sort out your backups - of course you'll need a big external drive to hold them.

Then resizing the partition is less risky, and still a worthwhile thing.

---


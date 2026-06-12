---
title: "dapper &gt; edgy; swap broken"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by martijndenerd on 2006-10-28
Hello there, 

I have another (serious) upgrade problem; my swap is not mounted. And the good news is; you might have the same problem! I discovered it by accident (using 'top'), because the new edgy startup procedure doesn't show any errors, just a nice blue kubuntu logo :-| . 

I upgraded my kubuntu dapper to edgy using apt-get, and since then I can' t mount my swap anymore. I think it has something to do with the UUID system. 
Have a look at the errors I get:
```

martijn@Inspiron-MB:~$ sudo swapon -a
swapon: /dev/disk/by-uuid/3b7d2890-f753-404b-8e3a-a36e9b1d0daf: Invalid argument

```

And now manually, same problem:
```

martijn@Inspiron-MB:~$ sudo swapon -U 3b7d2890-f753-404b-8e3a-a36e9b1d0daf
swapon: /dev/disk/by-uuid/3b7d2890-f753-404b-8e3a-a36e9b1d0daf: Invalid argument

```

Then I tried to restore the fstab file to the old form (/dev/sda5 instead of a very long UUID string) ([see]("http://ubuntuforums.org/showthread.php?t=271331&highlight=swap+uuid") ], but that gave me this error:
```

martijn@Inspiron-MB:~$ sudo swapon -a
swapon: /dev/sda5: Invalid argument

```

Anyone an idea?

thanks, 

Martijn

---

### Post by trash-can on 2006-10-29
I can confirm this. This is actually HUGE problem. I noticed it after disabling "user friendly" startup screen.

Trying to figure out the cause of this.

Dont have working linux box to check if swap partition type should be listed in  /proc/filesystems. Can anyone check, please?

---

### Post by trash-can on 2006-10-29
Ok, seem a manual mkswap was needed.

Steps:

# Ofcourse replace hda2 with your swap partition
sudo mkswap /dev/hda2

edit /etc/fstab ang replace UUID crap with /dev/your_swap_partition

sudo swapon -a

# And now check with

sudo swapon -s

---

### Post by steko on 2006-10-29
Had this problem too, and it seems solved now. What's all this UUID crap?? Too bad it's breaking working environments like mine and yours.

---

### Post by SirPecanGum on 2006-10-29
I had a similar problem but it involved all my partitions. I removed the UUID entries in the fstab file and now all seems well. Not sure if it is the 'correct' solution or what other problems it may cause but all is well so far.

[http://www.ubuntuforums.org/showthread.php?p=1681793#post1681793](http://www.ubuntuforums.org/showthread.php?p=1681793#post1681793)

---

### Post by highneko on 2006-10-29
Yes, "swapon" without "mkswap", is like "mount" without making the "/directory" you want to mount to. I learned all about mkswap when using a gentoo minimal installation cd.

---

### Post by oysteine on 2006-10-29
A detailed description and solution is available here: [https://launchpad.net/distros/ubuntu/+bug/66637](https://launchpad.net/distros/ubuntu/+bug/66637)

It worked for me :)

---

### Post by martijndenerd on 2006-10-29
> **trash-can said:**
> Ok, seem a manual mkswap was needed.

Steps:

# Ofcourse replace hda2 with your swap partition
sudo mkswap /dev/hda2

edit /etc/fstab ang replace UUID crap with /dev/your_swap_partition

sudo swapon -a

# And now check with

sudo swapon -s
Great!! this works for me, I hope someone will fix the bug soon, because this is both serious and invisible...

---

### Post by lemino on 2006-11-03
I followed the guide that oysteine referred to, and it seems all is working well nog. Just two questions:

1. How do I know for sure? The swap (sda2) doesn't come up when I typ "mount" but when giving the command "swapon -s" I get this:

lemino@Angelica:~$ swapon -s
Filename                                Type            Size    Used    Priority
/dev/sda2                               partition       1461904 0       -1
lemino@Angelica:~$ 

And both top and the gnome-system-manager reports that there is swapspace, allthough both claims that none of it is in use. 

2. What is this new UUID-system for fstab good for anyway? Wasn't thing easier and more functional as they were? (Aren't Linux supposed to be easy and functional? ;))

---

### Post by joehill on 2006-11-04
My swap broke seriously on upgrade to Edgy too.  The swap partition appeared to be unformatted. So I used gparted to remake the swap partition and did swapon and  changed fstab to the standard filname (/dev/hda6) so it would be recognized at boot (I don't know what the long numbers are all about).  I thought I had fixed everything.

But when I rebooted it was again unformatted and not swapon-ed.  So it seems I have to reformat and swapon every time I boot my computer!  (Which, of course, means I can never hibernate, because swap is lost between hibernate and restore.)

Strange, hibernate worked well in Breezy, 50% in Dapper, zero in Edgy.  Some things get better and others get worse.

---

### Post by PhilipGanchev on 2006-11-05
Are you sure you have to reformat?  What happens when you do

sudo mkswap /dev/<devicetouseforswap>
emacs /etc/fstab # Edit /etc/fstab with the new UUID device
swapon -a

---

### Post by jnoreiko on 2006-11-08
I'm trying to follow the instructions in comment 23 of that bug -- [https://launchpad.net/distros/ubuntu/+bug/66637/comments/23](https://launchpad.net/distros/ubuntu/+bug/66637/comments/23)

I get stuck on the very first one!

> 1, determine your swap with 'fdisk -l'

For the clueless newbies like me -- you need to do sudo with that.

---

### Post by joehill on 2006-11-08
> **PhilipGanchev said:**
> Are you sure you have to reformat?  What happens when you do

sudo mkswap /dev/<devicetouseforswap>
emacs /etc/fstab # Edit /etc/fstab with the new UUID device
swapon -a

I'm not sure about terminology, but I have to "mkswap" every time--that's what I meant by formatting.  In any case, what once was swap is no longer recognized as swap.  I tried following the instructions on the Launchpad bug page but I still have the same problem.  Even if I put the correct UUID in /etc/initramfs-tools/conf.d/resume, I still get "Cannot find swap signature" or whatever on reboot.  The UUID is still the same, but then it changes when I do mkswap.

I'm sure there's a good reason why things simple like /dev/hda1 that have worked for decades are now being tossed for this UUID system that's incomprehensible to most people and doesn't seem to work yet.

---

### Post by joehill on 2006-11-08
I tried following the instructions on Launchpad and I think I'm giving up on making it work with the UUID system for now.  I have work to do.

But, it does work if you hack it back to the old system:
in /etc/fstab list the swap as /dev/hda6 or whatever,
make /etc/initramfs-tools/conf.d/resume read "RESUME=/dev/hda6"

and it works as it did before the upgrade.

---

### Post by jnoreiko on 2006-11-09
> **jnoreiko said:**
> I'm trying to follow the instructions in comment 23 of that bug -- [https://launchpad.net/distros/ubuntu/+bug/66637/comments/23](https://launchpad.net/distros/ubuntu/+bug/66637/comments/23)

Done.
And it works -- just hibernated and resumed successfully :)

---

### Post by aev on 2006-11-10
> **oysteine said:**
> A detailed description and solution is available here: [https://launchpad.net/distros/ubuntu/+bug/66637](https://launchpad.net/distros/ubuntu/+bug/66637)

It worked for me :)


I had the same problem. Just happened an hour ago. My laptop simply froze and after restart showed "Activating swap - FAILED" . Now it seems OK after I followed the instructions from the link. Here I post the message with the full instructions as described by **jens_acamedia**

By the way - prefer the dapper load screen. I could follow the loading and correct if any mistakes happened. Now with this "user friendly" screen I can't see a thing.[-( :???: ](*,) 

> 

Re: [Bug 66637] Re: swap not being mounted on boot from jens_acamedia at 2006-10-31 18:55:09 UTC

ben - uuid changes are not always reflected until after a reboot...

follow THESE instructions and report back

1, determine your swap with 'fdisk -l'
2, do mkswap on your swap partition - RECORD THE UUID WHICH THIS COMMAND
OUTPUTS
3, now use this UUID to put into fstab and resume
files...(RESUME=UUID=<the-swap-partition-uuid-from-vol_ID
should go in /etc/initramfs-tools/conf.d/resume
4, update-initramfs -u
5, reboot normally after this finishes

when the system has restarted again - do 'swapon -s' to check if your
swap is active...and do 'ls -la /dev/disk/by-uuid/'

dont change any symlinks etc. just try these instructions



---

### Post by jnoreiko on 2006-11-11
I'm curious about this bit:

> do 'ls -la /dev/disk/by-uuid/'

what's it meant to show (in the context of these instructions)?

---

### Post by stebrepar on 2006-11-12
> **jnoreiko said:**
> what's it meant to show (in the context of these instructions)?

That the swap partition's UUID being used after the reboot is still the same as the one given to it in the instructions before the reboot. One of the people in that thread was saying that it kept changing, such that he'd have to keep fixing it every time he rebooted; these instructions were meant to fix it for good, and the last bit was to verify that it worked.

I had the same problem from the 6.06->6.10 upgrade (which I wouldn't have realized but for one memory hogging program I occasionally run). The instructions quoted above seem to have fixed it for me. Thanks, everybody, for pointing me in the right direction!

BTW, for the one who asked about this new UUID thing, the discussion in the linked thread said: > It's related to the future switch to libata (kernel 2.6.18 ). If I
understand it correctly, ubuntu devs will probably switch to libata for
the next release.
libata is a new framework for the ata drivers (both sata and pata), when
you activate it, your devices will be renamed to /dev/sd* instead of
/dev/hd* so using UUID instead of device name will make the transition
not painful.

---

### Post by mr_byte on 2006-11-15
Hi all,

Well, this information fixed my issue with hibernation, but in the end I used the old fashioned /dev/hd?? method for /etc/fstab and the resume file. 

My UUID was the same after a boot without hibernating, but when I'd hibernate, the swap would fail, and the hibernate never woke up.

But, as I said, this info did the trick, just a few tweaks to make it work for me. YMMV.


Jeff

---

### Post by Brando569 on 2006-11-16
what should the swap entry in fstab look like? i dont have one in my fstab (guess it got erased when i upgraded)

---

### Post by 56phil on 2006-11-17
Hibernate seems to corrupt the UUID info for my swap partition. Every time I hibernate my Gateway M680 I have to 

```

sudo mkswap /dev/hda5
sudo startswap -va

```
to get swap back in action. Additionally, I have to replace the old UUID with the new UUID generated by mkswap in /etc/fstab. ](*,) I don't think I'll do much hibernating, at least until feisty comes out. I'll try it again then.

---

### Post by 56phil on 2006-11-17
I found a fix for the above hibernate problem. Here's what needs to be done once you get swap back in trim: ```
  
gksudo gedit /etc/initramfs-tools/conf.d/resume

```
and put your new swap UUID in the file like this:
```
RESUME=UUID='your new swap UUID'
```
Finally, make this entry:
```
sudo update-initramfs -u
```
My system will now hibernate!:D

---

### Post by Sionide on 2006-11-19
Hm...

I think I've just figured out why my system goes incredibly slow sometimes. Ever since I tried out hibernating, it must have mucked up my swap partition. Well I've tried the instructions from this thread so hopefully it's fixed now.

Thanks for the pointers.

---

### Post by Chazall1 on 2006-11-21
I have tried all the methods on this post and I still have swapoff on boot up. here is my FSTAB info, My swap is /dev/hda7 this is without the mkswap UUID Output, I was trying this method last.
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6 -- converted during upgrade to edgy
UUID=8bd36f06-7967-47e4-9933-669abf52b03f / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=18c79eac-b4e4-4fea-a502-786ce82af86e /home ext3 defaults 0 2
# /dev/hda1 -- converted during upgrade to edgy
UUID=07D4-0C0C /media/hda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda2 -- converted during upgrade to edgy
UUID=CAF012F3F012E58B /media/hda2 ntfs-3g silent,umask=0,locale=en_US.utf8,no_def_opts,allow_other 0 0
/dev/hda3       /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda7 /swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
What does the (sw) after swap mean?

In my initramfs RESUME=/dev/hda7

I update-initramfs -u   and re-boot and my swap is not mounted I use G-parted to swapon. I must be missing something??????????

---

### Post by Yango on 2006-11-25
Hi,

> **Chazall1 said:**
> # /dev/hda7 /swap sw 0 0
Maybe you should try uncommenting this line? ;)
Also in my fstab I dont have slash before "swap".

---


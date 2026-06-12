---
title: "[SOLVED] Is there a way to install Jaunty as ext4?"
date: 2008-12-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by inxygnuu on 2008-12-31
This might sound dumb, and unstable, but is there currently a way to install Jaunty with ext4? I know you need GRUB 2, but from the cd is there an option?

---

### Post by plun on 2008-12-31
Nope you don't need Grub2 for non boot partitions.

I have one test partition for EXT4.

```
plun@plun:~$ sudo blkid
/dev/sda1: UUID="9E7864E67864BEA1" TYPE="ntfs" 
/dev/sda2: UUID="431b36fe-46dd-4ee6-94ce-ab65eabdc770" TYPE="ext3" 
**/dev/sda3: UUID="1bd53d0e-a190-4358-a24f-cdea59941581" TYPE="ext4"** 
/dev/sda4: UUID="ea60a35d-3a50-4b02-8eda-60da18ad08fd" TYPE="ext3" 
/dev/sdb1: SEC_TYPE="msdos" UUID="BABA-9F89" TYPE="vfat" 
```


Info
[http://ext4.wiki.kernel.org/index.php/Main_Page](http://ext4.wiki.kernel.org/index.php/Main_Page)


Still a unsolved bug about blkid or vol_id for Ubuntu....but it works without any fixes, just to convert a partion and add it to fstab.

---

### Post by inxygnuu on 2008-12-31
well, it looks very unstable, so I am simply going to leave it alone for now.

---

### Post by Technophobia on 2008-12-31
The newest release of the Kernel included a stabilized ext4. I'm not sure what that exactly means, and if JJ will use it.

[http://www.phoronix.com/scan.php?page=news_item&px=Njk1Nw](http://www.phoronix.com/scan.php?page=news_item&px=Njk1Nw)

---

### Post by pressureman on 2008-12-31
I just installed Jaunty on a spare laptop using ext4 as the root filesystem, and a separate ext3 /boot partition. I think messing about with both ext4 and grub2 simultaneously is tempting fate a little bit ;-)

Running ext4 as your root filesystem gets a bit fiddly with initramfs (which doesn't correctly identify the filesystem as ext4, and then fails to mount it as ext3 (if you have enabled extents or some other new ext4 filesystem feature)).

I needed to add a custom script in /etc/initramfs-tools/scripts/local-bottom:

```

#! /bin/sh
mount -t ext4 /dev/sda1 /root
mount -t ext4 /dev/disk/by-uuid/[ADD YOUR ROOT PARTITION UUID HERE] /root

```

If you're not using sda1 as your root partition, obviously replace it with what you are using. Then execute ```
sudo update-initramfs -u -k all
```

The kernel now has ext4 (and others) compiled in directly (no longer a module), so the FS support is there right from the start - it's just that the initramfs scripts try to mount it as ext3.

Note: you will not need the above custom script if you're not going to enable extents.

---

### Post by inxygnuu on 2008-12-31
Okay, I just got all of that, but I don't know how to move the /boot to another partition. I <3 _***[COLOR="Red"]BLEEDING EDGE[/COLOR]***_

---

### Post by Quikee on 2008-12-31
> **pressureman said:**
> 
Running ext4 as your root filesystem gets a bit fiddly with initramfs (which doesn't correctly identify the filesystem as ext4, and then fails to mount it as ext3 (if you have enabled extents or some other new ext4 filesystem feature)).


I have solved this by adding "rootfstype=ext4" to boot options (manualy in grub but later in temporary in grub's "menu.lst").

---

### Post by Quikee on 2008-12-31
> **pressureman said:**
> 
Running ext4 as your root filesystem gets a bit fiddly with initramfs (which doesn't correctly identify the filesystem as ext4, and then fails to mount it as ext3 (if you have enabled extents or some other new ext4 filesystem feature)).


I have solved this by adding "rootfstype=ext4" to boot options (manualy in grub but later permanent in grub's "menu.lst").

---

### Post by pressureman on 2008-12-31
> **inxygnuu said:**
> Okay, I just got all of that, but I don't know how to move the /boot to another partition. I <3 _***[COLOR="Red"]BLEEDING EDGE[/COLOR]***_

If you haven't already converted your root partition to ext4, or if you have converted it but not yet enabled extents, you should be able to use gparted to resize the partition, creating space to sneak in a small /boot partition, formatted as ext3. 200 MB should be plenty big enough.

Once you've created the /boot partition, mount it somewhere temporarily, copy the contents of your existing /boot directory onto the new /boot partition (wherever it's mounted), and update your /etc/fstab accordingly.

---

### Post by pressureman on 2008-12-31
> **Quikee said:**
> I have solved this by adding "rootfstype=ext4" to boot options (manualy in grub but later in temporary in grub's "menu.lst").

Perfect! A much more elegant solution than my suggestion. Thanks!

For anyone reading this who isn't quite sure what Quikee meant, edit your /boot/grub/menu.lst file (as root), find the "kopt" option, and append "rootfstype=ext4" to that line, eg.

```

# kopt=root=UUID=422cead6-da03-473f-a2dc-1a551da53d2f ro rootfstype=ext4

```

Then run "sudo update-grub".

---

### Post by scradock on 2009-01-01
How does one "convert" a partition to ext4? Last time I looked gparted didn't include ext4 as an option for fs type.....

Running Jaunty with the 28-4 kernel, but no special fstab entries yet.

---

### Post by cariboo on 2009-01-01
Have a look [here]("http://ext4.wiki.kernel.org/index.php/Ext4_Howto"), for more info on setting up an ext4 partition.

Jim

---

### Post by Slug71 on 2009-01-02
Was blkid added to Jaunty?

output of blkid in Terminal gives me

> /dev/sda1: UUID="A22AA8492AA81BF3" LABEL="ACER" TYPE="ntfs" 
/dev/sda5: UUID="9672-D88B" TYPE="vfat" 
/dev/sda6: UUID="f4acf0e5-27d9-414c-9773-9d417dc33c46" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="854df7f2-54aa-4639-9932-9355ed512f6f" 
/dev/sda8: UUID="d04c2d7f-bb6c-427d-821d-c15e83a7d0d4" TYPE="ext3"

---

### Post by ShirishAg75 on 2009-01-02
Slug71, 
 the output of blkid has been since ever (I remember being able to use that command since 7.10 if not before.  This is output of the same on kernel  2.6.27-7-generic (On Intrepid)

```

~$ blkid
/dev/sda1: UUID="9560c727-a052-43ff-a097-b6af01287f7c" TYPE="ext3" SEC_TYPE="ext2" 
/dev/loop0: TYPE="squashfs" 
/dev/sda2: UUID="fc24631b-c156-4beb-bf61-be84e24bc946" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="7c003381-39d7-4126-8b9b-dbdbf3955eea" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="baa0d92f-3112-42ab-aaf7-b2e416dea782" TYPE="swap" 
/dev/sdb1: UUID="9560c727-a052-43ff-a097-b6af01287f7c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="4c1d6e5a-a103-4522-9fc5-df415c8be53d" TYPE="ext3" 
/dev/sda6: UUID="86810a59-20f1-47df-a599-a518d0cb7add" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="27f332fa-fb24-41c3-9f7a-5a1e96f093e5" TYPE="swap" 

```

---

### Post by plun on 2009-01-02
> **ShirishAg75 said:**
> Slug71, 
 the output of blkid has been since ever (I remember being able to use that command since 7.10 if not before.  This is output of the same on kernel  2.6.27-7-generic (On Intrepid)



Yes but Theodore points to this changelog


[http://changelogs.ubuntu.com/changelogs/pool/main/u/util-linux/util-linux_2.12r-19ubuntu1/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/u/util-linux/util-linux_2.12r-19ubuntu1/changelog)


[http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto)

> For people who are running Ubuntu, it is *highly* recommended that you download a set of modified util-linux packages and install them. Packages for Ubuntu Hardy are available here. These packages revert a change made by Ubuntu to use the volid library instead of the blkid library. The volid library has a number of shortcomings, including that they don't work on freshly created filesystems or swap devices until after you reboot (since it is tied to udev probing) and the volid library doesn't understand ext4dev filesystems. The blkid library is much better, and Debian uses the blkid library for util-linux. **Unfortunately, ****Ubuntu chose to make this reason for some unknown reason**. For other versions of Ubuntu, the patch that was applied can be found here. 



Nevertheless a **big mystery** for me that this cannot be sorted out...:confused::confused::confused:

And I am no developer.....:D

---

### Post by Slug71 on 2009-01-02
Thanks guys.

So this 

> For people who are running Ubuntu, it is *highly* recommended that you download a set of modified util-linux packages and install them. Packages for Ubuntu Hardy are available here. These packages revert a change made by Ubuntu to use the volid library instead of the blkid library. The volid library has a number of shortcomings, including that they don't work on freshly created filesystems or swap devices until after you reboot (since it is tied to udev probing) and the volid library doesn't understand ext4dev filesystems. The blkid library is much better, and Debian uses the blkid library for util-linux. Unfortunately, Ubuntu chose to make this reason for some unknown reason. For other versions of Ubuntu, the patch that was applied can be found here. 

still applies if i want to convert my Ext3 partitions to Ext4?

---

### Post by plun on 2009-01-02
> **Slug71 said:**
> Thanks guys.

So this 

still applies if i want to convert my Ext3 partitions to Ext4?


Until this is commented within a bug report **from a real developer** I am not going to run a system partition with EXT4.

[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/197311](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/197311)

And I also finds it unpolite to leave a bug report from one of the most famous open sorce fighters in this shape...:(  just a disgrace !


I have a test partition with stolen media junk which I test with...:D

---

### Post by Slug71 on 2009-01-02
> **plun said:**
> Until this is commented within a bug report **from a real developer** I am not going to run a system partition with EXT4.

[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/197311](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/197311)

And I also finds it unpolite to leave a bug report from one of the most famous open sorce fighters in this shape...:(  just a disgrace !


I have a test partition with stolen media junk which I test with...:D


Agreed plun, 
That bug report is nearly a year old now.

---

### Post by plun on 2009-01-02
> **Slug71 said:**
> Agreed plun, 
That bug report is nearly a year old now.

Well... its like a Gentoo "child"...  "f--k upstream"

I also cannot find the blueprint for this which Mr Remnant wrote for UDS...:confused:

---

### Post by Slug71 on 2009-01-02
I was just trying to find the UDS blueprint too??

---

### Post by ShirishAg75 on 2009-01-02
maybe either of you guys can raise this question at ubuntu-devel-discuss. That might get some of the developer's attention as well as response on the same as to how they are going to deal with this situation going future.

---

### Post by plun on 2009-01-02
> **ShirishAg75 said:**
> maybe either of you guys can raise this question at ubuntu-devel-discuss. That might get some of the developer's attention as well as response on the same as to how they are going to deal with this situation going future.

Nope... they "inner-circle" seems to not read something from the "mob"...

You must be a "member"....

---

### Post by Slug71 on 2009-01-02
I dont get half this of what goes on though. There plenty of us that are willing and want to test thing and we have Brainstorm and the Forum to discuss and ask for these things yet a deaf ear is given to most.

---

### Post by inxygnuu on 2009-01-02
Hey Guys, is there a way for me to install Grub onto my external drive? I know this so far: 'sudo grub' -> 'root (hd1,7) -> 'setup (hd1). Is that right? because the terminal is saying "invalid device requested on 'root (hd1,7)' and 'setup (hd1)'.

---

### Post by plun on 2009-01-02
> **inxygnuu said:**
> Hey Guys, is there a way for me to install Grub onto my external drive? I know this so far: 'sudo grub' -> 'root (hd1,7) -> 'setup (hd1). Is that right? because the terminal is saying "invalid device requested on 'root (hd1,7)' and 'setup (hd1)'.

Well maybe you are totally off-topic....

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by Fintan on 2009-01-24
Hello out there.

I am running Kubuntu II and installed the latest JJ daily formated as ext4 and followed these instructions using the correct uuid.

> Perfect! A much more elegant solution than my suggestion. Thanks!

For anyone reading this who isn't quite sure what Quikee meant, edit your /boot/grub/menu.lst file (as root), find the "kopt" option, and append "rootfstype=ext4" to that line, eg.

Code:
```

# kopt=root=UUID=422cead6-da03-473f-a2dc-1a551da53d2f ro rootfstype=ext4
```

Then run "sudo update-grub".


Unfortunately update-grub sets my menue list back to the default (unless I am missing something;)

I tried uncommenting the kopt line. 

Either way grub is dying with the stage 1.5 error.

I would install Grub2 but am a bit apprehensive about doing that.

Any ideas?

---

### Post by taavikko on 2009-01-24
> **Fintan said:**
> Hello out there.
.

I tried uncommenting the kopt line. 

Either way grub is dying with the stage 1.5 error.
.
Any ideas?

# isn't a comment on that particular file,

Anything before this line is normal 
### BEGIN AUTOMAGIC KERNELS LIST

After that
Like it says on that file
"## DO NOT UNCOMMENT THEM, Just edit them to your needs"

Just a little messy clarification...

---

### Post by Fintan on 2009-01-24
Thank you Taavikko

Just to clarify. I created a sepeate partion /boot with 300MB.

I then used the JJ live CD to copy the contents of its /boot to the new /boot.

I then edited it as described above and re-added the "#" to look like this:
> # kopt=root=UUID=642f5951-7b8d-4b9a-aabd-794a2e4f3091 ro rootfstype=ext4

This is the JJ part of my new /boot/grub/menu.lst:
> title		Ubuntu jaunty (development branch), kernel 2.6.28-4-generic
uuid		642f5951-7b8d-4b9a-aabd-794a2e4f3091
kernel		/boot/vmlinuz-2.6.28-4-generic root=UUID=642f5951-7b8d-4b9a-aabd-794a2e4f3091 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-4-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-4-generic (recovery mode)
uuid		642f5951-7b8d-4b9a-aabd-794a2e4f3091
kernel		/boot/vmlinuz-2.6.28-4-generic root=UUID=642f5951-7b8d-4b9a-aabd-794a2e4f3091 ro  single
initrd		/boot/initrd.img-2.6.28-4-generic

The UUID "642f5951-7b8d-4b9a-aabd-794a2e4f3091" corresponds with the JJ root partition.

This is the respective part of my main grub/menu.lst:

> title		Kubuntu jaunty (development branch), kernel 2.6.28-4-generic
uuid		7475478e-f97e-491f-b93a-495f2cacb762
kernel		/boot/vmlinuz-2.6.28-4-generic root=7475478e-f97e-491f-b93a-495f2cacb762 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-4-generic
quiet

title		Kubuntu jaunty (development branch), kernel 2.6.28-4-generic (recovery mode)
uuid		7475478e-f97e-491f-b93a-495f2cacb762
kernel		/boot/vmlinuz-2.6.28-4-generic root=UUID=7475478e-f97e-491f-b93a-495f2cacb762 ro  single
initrd		/boot/initrd.img-2.6.28-4-generic

whereby:
"7475478e-f97e-491f-b93a-495f2cacb762"
represents UUID for the new /boot partition.

Grub is still dying with the stage 1.5 error.

What am I missing here?

---

### Post by taavikko on 2009-01-24
@ Fintan

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
this should clarify few things.

basically can't find stage*** means it cannot find /boot partition.

---

### Post by Fintan on 2009-01-24
Thankx for the link. I had seen that before but can't see how it will help me. (I don't really understand grub that well).

Anyway my main OS (Kubuntu II) is on sda. This is also where my main grub resides.

The created /boot partition is on sda3 and the "/" for JJ is on sda10.

So how do I get the menu.lst to boot sda3 which in turn is supposed to boot sda10 (as far as I understand it)

Also. How do I rung update-grub on sda3? Do I need to? Do I need a separate /boot on sda3 as I am using my main grub on sda1 to boot my systems?
In my original effort it just returned my menu.lst to its default without the "rootfstype=ext4".

If I got that wrong please clarify.

Thank you for your effort.

---

### Post by pressureman on 2009-01-24
After adding "rootfstype=ext4" to your "# kopt=root=UUID=blahblahblah" line, you need to run re-run update-grub, so that the "rootfstype=ext4" gets appended to all "kernel /boot/vmlinuz..." lines. Think of it like a template that update-grub reads, in order to construct the actual kernel command lines.

However, if you're using a fairly up-to-date Jaunty, you don't need to manually specify rootfstype anymore (as it's now properly detected), and the current version of grub in Jaunty supports booting from ext4 now also.

---

### Post by Fintan on 2009-01-25
Well, I re-edited my grub in MBR to try and boot directly to the Jaunty grub on sda10 (JJ root) as I am using my Intrepid Grub in MBR to boot my systems. I don't feel comfortable with using the Jaunty grub in MBR just yet. Will it see my other systems? Is it stable?

Running sudo update-grub (in Intrepid) just seems to return my grub (in MBR) to its default state.

This is the output:
> fintan3@fintanws2:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-9-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

fintan3@fintanws2:~$

It doesn't seem to see the JJ kernel:(

and this is kopt BEFORE update:> 
#kopt=root=UUID=642f5951-7b8d-4b9a-aabd-794a2e4f3091 ro rootfstype=ext4 
and after
> # kopt=root=UUID=149ae850-fbce-4cee-9bf3-c48e4c636846 ro

Can I not append the lines for Jaunty manually?

What am I missing?

---

### Post by Gina on 2009-01-25
Yes you can - it's mentioned in an earlier post in this thread I think.

Using ext4 when installing is simple - just choose ext4 in the "use as" option with manual partitioning.  Works fine with existing or new partitions.  It reformats to ext4, wiping previous data, if using an existing partition.

---

### Post by Fintan on 2009-01-25
Yes I can. What?

append manually? 
Okay, I will try that and get back.

I have my Jaunty installed as ext4 I just can't boot it.

Edit:
Appended like this:
> title		Kubuntu jaunty (development branch), kernel 2.6.28-4-generic
uuid		642f5951-7b8d-4b9a-aabd-794a2e4f3091
kernel		/boot/vmlinuz-2.6.28-4-generic root=642f5951-7b8d-4b9a-aabd-794a2e4f3091 ro quiet splash rootfstype=ext4
initrd		/boot/initrd.img-2.6.28-4-generic
quiet

title		Kubuntu jaunty (development branch), kernel 2.6.28-4-generic (recovery mode)
uuid		642f5951-7b8d-4b9a-aabd-794a2e4f3091
kernel		/boot/vmlinuz-2.6.28-4-generic root=UUID=642f5951-7b8d-4b9a-aabd-794a2e4f3091 ro  single rootfstype=ext4
initrd		/boot/initrd.img-2.6.28-4-generic

Same effect: No boot

UUID according to:
sudo blkid

/dev/sda10: UUID="642f5951-7b8d-4b9a-aabd-794a2e4f3091" TYPE="ext4"

I am at a loss

---

### Post by Rob-e on 2009-04-03
> **Gina said:**
> Yes you can - it's mentioned in an earlier post in this thread I think.

Using ext4 when installing is simple - just choose ext4 in the "use as" option with manual partitioning.  Works fine with existing or new partitions.  It reformats to ext4, wiping previous data, if using an existing partition.

this doesnt work for me, there is no ext4 option in the "use as" this is a jaunty daily build, downloaded today

---

### Post by gunnar123 on 2009-04-06
> **Rob-e said:**
> this doesnt work for me, there is no ext4 option in the "use as" this is a jaunty daily build, downloaded today

I can't find that option either, in any of the latest install ISO's, be it advanced command line modes or the simpler ones. No mention of EXT4 anywhere.  Whats up ?

---

### Post by MaX on 2009-04-06
Could someone update the first post with the correct instructions?

It's not nice with a [Solved] thread that you have to read through all of it to find the solution...

---

### Post by megamania on 2009-04-06
> **MaX said:**
> Could someone update the first post with the correct instructions?

It's not nice with a [Solved] thread that you have to read through all of it to find the solution...
I don't know if I'm missing something, but when I clean-installed Jaunty I selected ext4 for the root partition, and that was it.

---


---
title: "Linux partition fails to boot"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by Yesideez on 2008-08-17
SATA drives, two boots of XP already running.

I've tried running the "dd" command in Linux to make bootsect.lnx, copied it to my C: drive and modified boot.ini to include this at the end:
```
c:\bootsect.lnx="Linux"
```
When run, Linux appears on the menu but when selecting it the machine just reboots.

I also tried using bootpart.exe but selecting it in the menu when booting results in the screen going black and the menu appearing again - no reboot though.

btw, this is my boot.ini file as it stands now:
```
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Battlefield 2" /noexecute=optin /fastdetect /usepmtimer
c:\bootsect.lnx="Linux"
```
Any idea how I can get Linux booting?

---

### Post by Yesideez on 2008-08-17
I've done something different (not sure what exactly but tried "dd" again) and this time when selecting "Linux" from the boot menu I get a black screen with the cursor flashing away in the top-left and nothing else. No hard drive lights flashing or anything.

---

### Post by logos34 on 2008-08-17
boot from the ubuntu live cd and post the output of

sudo fdisk -l

Did you run something like this:

sudo dd if=/dev/sd?? of=bootsect.lnx bs=512 count=1

?

AND did you write grub to the root partition beforehand (won't work otherwise--you'll just end up with empty 'bootsect.lnx' file (check to see what I mean in any hexeditor--there will just be a lot of zeros)

sudo grub-install /dev/sd??

---

### Post by Yesideez on 2008-08-17
sudo fdisk -l
```
Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd9dbd9db

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9327    74919096   83  Linux
/dev/hdb2            9328        9729     3229065    5  Extended
/dev/hdb5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeefeeefe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36923   296583966    7  HPFS/NTFS
/dev/sda2           36924       38913    15984675    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x0ce12682

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      969018   488385040+   7  HPFS/NTFS
```

Yes, the dd command was similar to that but I used hdb1.

GRUB? Isn't he a TV presenter? (erm... no)

I tried GRUB and this is what I got:
```
ubuntu@ubuntu:~$ sudo grub-install /dev/hdb1
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
```

---

### Post by logos34 on 2008-08-17
What drive are you booting from, sda?

> **Yesideez said:**
> 
I tried GRUB and this is what I got:
```
ubuntu@ubuntu:~$ sudo grub-install /dev/hdb1
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
```

hmm, odd...try

> sudo grub

find /boot/grub/stage1
(enter output in next command)
root (hd**?**,0)
setup (hd?,0)
quit


---

### Post by Yesideez on 2008-08-17
OK that ran smoothly and this is what I received:
```
grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> 

```

---

### Post by logos34 on 2008-08-17
ok, now run the dd command again, copy it to c:\ and try again

WAIT! stop the presses...

> grub> setup (hd0)

You were supposed to run 

setup (hd0,0)

!

You've just overwritten the windows bootloader.  Use the windows cd recovery console to do **fixmbr** or use Super Grub Disk.

---

### Post by Yesideez on 2008-08-17
Thank-you so much!

Fingers crossed...

---

### Post by Yesideez on 2008-08-17
Unfortunately it still does exactly the same :'(

I'm wondering if the noapic thing can be causing problems - I had to add this onto the command line by pressing F6 while booting the Live DVD...?

---

### Post by logos34 on 2008-08-17
On second thought maybe you didn't overwrite the windows bootloader...Can you reboot to xp?  You may have just written grub to the mbr of the ide linux disk, in which case no prob.

If you can still boot windows then do like I said and run the dd command again, etc.  Hopefully that will sort things out

---

### Post by logos34 on 2008-08-17
> **Yesideez said:**
> Unfortunately it still does exactly the same :'(

** I'm wondering if the noapic thing can be causing problems** - I had to add this onto the command line by pressing F6 while booting the Live DVD...?

possibly...that's my best shot...you write grub to root, then run dd, then copy it over to c:\.

But you have a mixed IDE/SATA system, and that always seems to throw grub for a loop.  (grub seems to be coded to scan the IDE channels first regardless of boot order, so it frequently gets '(hd0)', '(hd1)' all wrong.

---

### Post by logos34 on 2008-08-17
why ARE you using windows bootloader anyway?  

Now that you've written grub the mbr of the linux drive hdb, why not try booting from that and use grub?  

You'd just need to adjust your [windows boot entry like this]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").

---

### Post by Yesideez on 2008-08-17
Just a quick update...

I've booted with the Live DVD and tried the last option which was to boot using the first hard drive.

I got a black screen with a list of hard drives and from there I was able to boot using my HD installed Ubuntu which I'm using now so at least I know the install is there and working. I've been a bit quiet as I've just downloaded and install all 286 updated for Ubuntu.

About to reboot with the DVD not in the drive to check the status of the Windows boot - it was working before, let's hope it still does :)

---

### Post by Yesideez on 2008-08-17
> **logos34 said:**
> why ARE you using windows bootloader anyway?  

Now that you've written grub the mbr of the linux drive hdb, why not try booting from that and use grub?  

You'd just need to adjust your [windows boot entry like this]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").

To be completely honest that lost me completely!

I'd much rather add Linux to the boot loader than play with other stuff and risk losing everything - I cannot afford to lose my main XP boot as I do a lot of work on it!

---

### Post by logos34 on 2008-08-17
> **Yesideez said:**
> To be completely honest that lost me completely!

I'd much rather add Linux to the boot loader than play with other stuff and risk losing everything - I cannot afford to lose my main XP boot as I do a lot of work on it!

Ok, I understand, whatever way you want to do it...But if you boot instead to hdb and chainload windows from grub then you won't touch the windows disk/windows bootloader

About grub and hdb: What I meant was, if windows still boots up then all I think happened when your ran 'setup (hd0)' was you wrote grub to the MBR of the same drive as your ubuntu root is on (-->hdb), because it's reporting root as '(hd0,0)'.   

Let me know how it's going.

---

### Post by Yesideez on 2008-08-17
I re-did the "dd" thing while booted from the hard drive and now when I try booting from the Windows bootloader I get "GRUB" in the top left, a space, a flashing cursor and nothing else...

---

### Post by logos34 on 2008-08-17
> **Yesideez said:**
> I re-did the "dd" thing while booted from the hard drive and now when I try booting from the Windows bootloader I get "GRUB" in the top left, a space, a flashing cursor and nothing else...

you might try running a filesystem check on ubuntu from the live cd

sudo fsck /dev/hdb1

I'm out of ideas...the problem in situations like this is usually that people forget to write grub to the first sector of the linux root partition before running dd.  But like I said before, in systems with ide and sata drives grub can get confused too--it's looking for root at the wrong Bios address.

You could try [Wingrub]("http://users.bigpond.net.au/hermanzone/p9.html")--basically it's just a fancy gui app that automates the process of booting linux from windows.  But it might work, never know.

---

### Post by Yesideez on 2008-08-18
Thanks for all your help logos34, I don't know what on Earth is going wrong here, it's got me completely baffled.

I used to code assembler for around 10 years writing lines and lines and lines of meaningless-looking code and I'm stumped by this :)

I think I'll buy another 500GB SATA drive and partition that off for Windows/Linux and see how that goes.

What size do you recommend giving to Ubuntu?

---

### Post by logos34 on 2008-08-18
> **Yesideez said:**
> 
I think I'll buy another 500GB SATA drive and partition that off for Windows/Linux and see how that goes.

What size do you recommend giving to Ubuntu?

As much as possible!  What else do you expect a linux fan to say? :)

Seriously, I'd make a / and a separate /data or /home.  So for root, ~6-8 GB.  The bulk of the remaining space for data or home partition.  When I dualbooted with XP I always separated the system partition, c:\, and My Documents, giving ~10 GB to the former (which allowed space for ~500 MB hibernation file, system restore, and ~15% free space so defrag could run). 

That's already 4, not counting /swap, so you might want to put ubuntu inside an extended partition.

Those are just my personal preferences

---


---
title: "Grub2 found grub legacy, gives error"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by Tovam on 2010-01-10
Hey
I recently dual booted Ubuntu Karmic with Windows 7, using grub2. Everything worked fine until just now.

I have installed the two on a 320GB HD.

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1958    15727603+  83  Linux
/dev/sdb2   *        1959       20234   146801970    7  HPFS/NTFS
/dev/sdb3           20235       38913   150039067+   5  Extended
/dev/sdb5           20235       20756     4192933+  82  Linux swap / Solaris
/dev/sdb6           20757       36302   124873213+  83  Linux
/dev/sdb7           36303       38913    20972826   83  Linux
```

But before that, I had another Ubuntu Hardy - WinXP dual boot on a 500GB HD.

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19581   157284351    7  HPFS/NTFS
/dev/sda2           19582       24444    39062047+  83  Linux
/dev/sda3           24445       25417     7815622+  82  Linux swap / Solaris
/dev/sda4           25418       60801   284221980    5  Extended
/dev/sda5           25418       26633     9767488+  83  Linux
/dev/sda6           26634       60801   274454428+  83  Linux
```

I set in the bios to boot from sdb, so no problem, grub2 would just find Karmic and Win7.

```
Ubuntu karmic
Ubuntu karmic (recovery mode)
Windows Vista SP3
```

But somehow, it found my old grub again, and my grub now looks like this.

```
Ubuntu karmic
Ubuntu karmic (recovery mode)
Ubuntu karmic
Ubuntu karmic (recovery mode)
Microsoft Windows XP Professional
Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (on /dev/sda2)
Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode) (on /dev/sda2)
Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (on /dev/sda2)
Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (recovery mode) (on /dev/sda2)
Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (on /dev/sda2)
Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode) (on /dev/sda2)
Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (on /dev/sda2)
Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode) (on /dev/sda2)
Ubuntu 8.04.3 LTS, kernel 2.6.24-22-generic (on /dev/sda2)
Ubuntu 8.04.3 LTS, kernel 2.6.24-22-generic (recovery mode) (on /dev/sda2)
Ubuntu 8.04.3 LTS, kernel 2.6.24-21-generic (on /dev/sda2)
Ubuntu 8.04.3 LTS, kernel 2.6.24-21-generic (recovery mode) (on /dev/sda2)
Ubuntu 8.04.3 LTS, kernel 2.6.24-16-generic (on /dev/sda2)
Ubuntu 8.04.3 LTS, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda2)
Ubuntu 8.04.3 LTS, memtest86+ (on /dev/sda2)
Windows Vista SP3
```

With the exception of having two Karmics (only one is installed), it looks exactly like they just added the lists of my grub2 and grub legacy together.

The first 'Ubuntu Karmic' gets me to my normal Karmic install, the second (not the recovery mode, second 'Ubuntu Karmic') gets me to some kind of low-graphics Karmic. The 'Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic' gets me to my old Hardy install.
The 'Windows Vista SP3', my new Windows 7 install, however gives me this.

```
error: invalid signature

Press any key to continue...
```

Pressing the key brings me back to the grub.

I first noticed this when rebooting after installing linux-backports-modules-wireless-karmic-generic.


Anyway, my question. Is there a way to get my grub back to the old one, so that my Win7 can boot again. If possible, I don't want the entries from grub legacy either.
I figured removing the OSes, or at least grub from sda would work, but that is not an option right now, I still want to be able to boot my Hardy boot for now (by changing the bios to boot from sda, it's not like I use it a lot these days).

Anyway, thanks in advance.

---

### Post by drs305 on 2010-01-10
For starters, you can look at your /boot/grub/grub.cfg and look at the various sections (###) to see where the entries are coming from (10_linux, 30_os-prober, etc). 

Grub 2 probably found your old menu.lst with 30_os-prober. You could try locating that menu.lst file and renaming it to something else. I believe Grub 2 wouldn't inspect the actual contents and would ignore the menu.lst if it was renamed. 

Of course, if all these versions were actually still installed on your system Grub 2 would probably find and report them, which is what 30_os-prober is designed to do.

If these old installs still exist, you don't want to delete them, yet you don't want them to display, you can tweak the 30_os-prober script to disregard certain entries (titles, partitions, etc). This link provides some basic edits of the scripts to rename/hide certain entries. It's a bit geekish, so be forwarned.  [Grub 2 Title Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602")

For problems after installing Ubuntu/Windows, I generally refer users to this excellent guide:
[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by Tovam on 2010-01-10
Hey, and thanks for the reply.

I followed the link on how to restore the bootloader, did what it said (mounting and "sudo grub-install --root-directory=/media/sdb1 /dev/sdb"), and I got this.

```
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
```

Also, when I do a "sudo update-grub2", I get

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-17-generic-pae
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

Found Microsoft Windows XP Professional on /dev/sda1
Found Ubuntu 8.04.3 LTS (8.04) on /dev/sda2
Found Windows Vista SP3 on /dev/sdb2
grub-probe: error: Cannot find a GRUB drive for /dev/sdb2.  Check your device.map.

done
```

No other changes. Any idea how to fix this?

Oh, and as long as I can use all my boots, I don't really care if there's a bit of junk in my grub list, I'll just clean it up later then.

---

### Post by kansasnoob on 2010-01-10
Really need to see the results of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

It works fine from a live CD.

---

### Post by presence1960 on 2010-01-10
> **kansasnoob said:**
> Really need to see the results of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

It works fine from a live CD.

+1

The boot info script is an excellent tool to troubleshoot setup & boot problems. I always insist on having it run before troubleshooting those type problems. The reason is simple: (OP don't take this the wrong way) many times what people say they have on their computer and what the boot info script reveals they they actually have are not the same. Run the script please so we can see your setup & boot process.

---

### Post by Tovam on 2010-01-11
I changed "(hd0) /dev/sda" to "(hd0) /dev/sdb" in my "/boot/grub/device.map", thereby fixing my Win7. I can now boot in it again.

However, I still don't know why it didn't work earlier, and why my grub is so clutched, so here is the result of the script.

---

### Post by presence1960 on 2010-01-11
GRUB2 did not "find" GRUB legacy. You have GRUB Legacy (0.97) on MBR of sda and GRUB2 on MBR of sdb. A simple switch in BIOS to put sdb as the first hard disk to boot in hard disk boot order should do the trick. This will bring up GRUB2 which has entries for karmic & hardy in it. Boot into karmic and open a terminal & run ```
sudo update-grub
``` to refresh the GRUB menu. Then reboot & see what happens when you boot windows.

---

### Post by kansasnoob on 2010-01-11
Well, first observation:

> => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub.

So legacy grub is still on sda and grub2 is on sdb. From your OP you know quite well how to switch boot order in BIOS.

I'd assume that Karmic's grub2 os-prober failed to find Hardy and Win XP because that drive was disconnected when you installed Karmic???????

Then probably a kernel update in Karmic triggered "update-grub" (which it should) so it's os-prober found the Hardy and Win XP OS's. That's actually good.

As far as operating systems we have:

```
Karmic --------- sdb1
Win 7 ---------- sdb2
Win XP --------- sda1
Hardy ---------- sda2

```
Now, just a very brief explanation about legacy grub vs. grub2 numbering. In legacy grub both disc and partitions began with 0 (zero). In grub2 discs still begin with 0 (zero), but partitions begin with 1 (one). So in legacy grub sdb2 = (hd1,1), whereas in grub2 sdb2 = (hd1,2).

So in /boot/grub/grub.cfg where it shows:

```
menuentry "Windows Vista SP3" {
	insmod ntfs
	set root=**[COLOR="Red"](hd0,2)[/COLOR]**
	search --no-floppy --fs-uuid --set 3ad5077a160a949f
	chainloader +1
}
```

Hmmmm, (hd0,2) = sda2 in grub2 speak????????

Of course if you look at grub.cfg it says:

> # DO NOT EDIT THIS FILE

And we wouldn't want to! Also consider the grub-probe errors you encountered earlier.

Basically there are 3 ways I can think of to "fix" this (in order of my personal preference):

Option #1. Try to fix grub2 in Karmic so it just works right and updates properly in the future.

Option #2. Hand boot off to Hardy's legacy grub or revert Karmic to legacy grub.

Option #3. Add a custom entry to Karmic's grub.cfg for Win 7 in **/etc/grub.d/40_custom**.

> But before we even begin I want you to know how to restore grub2 from a Live CD, hopefully it won't be needed but best to be prepared. You must have an Ubuntu Live CD. **[COLOR="Red"]Note: these steps are only necessary to restore grub2 if something goes wrong![/COLOR]**

There are other methods but I've sometimes had them fail (not sure why) so I use mine because it always works for me. The commands appear to be ridiculously long, just double click within the code tags to highlight, then right click to copy, then paste into terminal.

Note this is specific for your Karmic on sdb1:

```
sudo mount /dev/**sdb1** /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

Then we install grub2 to the mbr of whichever drive, ie:sda or sdb:

```
grub-install /dev/sda
```

Then:

```
exit
```

And:

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```



So to do what I'd prefer (re: option #1), set the BIOS so you can boot Karmic. If this works you should not have to fiddle with it again. Then we'll install Karmic's grub2 to the mbr of both drives.

While booted into your installed Karmic run:

```
sudo grub-install /dev/sda
```

```
sudo grub-install /dev/sdb
```

If your BIOS is set to boot sdb first that should be right, what we want to do is "grub-install" to the "non-boot" drive (or drives) first and then to the "boot" drive last!

Anyway then just run:

```
sudo update-grub
```

Wait until it says "done", it may take a couple of minutes. Hopefully you won't see all the grub-probe errors. You could then compare the new grub.cfg against that in RESULTS2.txt, to display:

```
cat /boot/grub/grub.cfg
```

If that appears to have worked then we could get on with some "clean-up" of the grub2 menu. Even though the older karmic kernel only boots into low graphics mode I'd keep it, but you can look at the **Removing Entries from Grub 2** here:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Just take your time and be careful, ask more questions if need be!

To clean up the Hardy kernel list just boot into Hardy and install Startup Manager:

```
sudo apt-get install startupmanager
```

Then under the Advanced tab you can select how many kernels to display. Grub2 in the other OS does seem to respect that choice, just note you will have to run "sudo update-grub" for the changes to be recognized.

Should you choose option #2 I don't have the time to type specific commands for you right now but I wrote this HowTo:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Certainly if you choose that option send me a PM and I'll be glad to help ASAP, but I must do some things at the moment.

If you should choose option #3 look at the **Adding Entries to Grub 2** section here:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I hope you find this helpful :)

---

### Post by Tovam on 2010-01-11
Thanks for the replies.

To simplify, I configured the grub of sda with startupmanager first, and got to reduce the list to this.

```
Ubuntu karmic
Ubuntu karmic (recovery mode)
Ubuntu karmic
Ubuntu karmic (recovery mode)
Microsoft Windows XP Professional
Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (on /dev/sda2)
Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode) (on /dev/sda2)
Ubuntu 8.04.3 LTS, memtest86+ (on /dev/sda2)
Windows Vista SP3

```

When I do a "sudo grub-install /dev/sda", however, I get

```
grub-probe: error: Cannot find a GRUB drive for /dev/sda.  Check your device.map.

Invalid device `/dev/sda'.
Try ``grub-setup --help'' for more information.

```

I assume I need to make it "sudo grub-install /dev/sda  --device-map=/boot/grub/device.map", but do I need the device.map on sda or sdb?
I guess I need the one on sdb for sdb, but I'm not sure about the one on sda.

For the record, the device.map on sda contains "(hd0) /dev/sda" and that on sdb contains "(hd0) /dev/sdb". Well, I guess that was to be expected though.

---

### Post by kansasnoob on 2010-01-13
> **Tovam said:**
> Thanks for the replies.

To simplify, I configured the grub of sda with startupmanager first, and got to reduce the list to this.

```
Ubuntu karmic
Ubuntu karmic (recovery mode)
Ubuntu karmic
Ubuntu karmic (recovery mode)
Microsoft Windows XP Professional
Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (on /dev/sda2)
Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode) (on /dev/sda2)
Ubuntu 8.04.3 LTS, memtest86+ (on /dev/sda2)
Windows Vista SP3

```

When I do a "sudo grub-install /dev/sda", however, I get

```
grub-probe: error: Cannot find a GRUB drive for /dev/sda.  Check your device.map.

Invalid device `/dev/sda'.
Try ``grub-setup --help'' for more information.

```

I assume I need to make it "sudo grub-install /dev/sda  --device-map=/boot/grub/device.map", but do I need the device.map on sda or sdb?
I guess I need the one on sdb for sdb, but I'm not sure about the one on sda.

For the record, the device.map on sda contains "(hd0) /dev/sda" and that on sdb contains "(hd0) /dev/sdb". Well, I guess that was to be expected though.

Did that change the original problem:

> The 'Windows Vista SP3', my new Windows 7 install, however gives me this.

Code:

error: invalid signature

Press any key to continue...

Pressing the key brings me back to the grub.

And does this:

```
menuentry "Windows Vista SP3" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 3ad5077a160a949f
	chainloader +1
}
```

Now point to sdb2, aka: (hd1,2)?

What boots and what doesn't boot? If everything boots and "sudo update-grub" doesn't return grub probe errors we don't care about mapping,etc.

**Only if we gained on booting Win 7** then I'd try something different with the mbr of sda, boot into Ubuntu and:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

```
sudo apt-get remove lilo
```

```
sudo update-grub
```

Wait for it to say "done" and watch for any grub probe errors.

Just FYI we're only using Lilo as a tool that's why we installed and then removed it. We used it to create a win mbr on sda which should be readable by grub2.

If we didn't gain on grub2 being able to boot Win 7 then it's time to move on to either Option #2 or #3. I'd prefer option #2.

I'll try to check back on this ASAP but I'll be tied up quite a bit in the near future working on homestead tax exemption stuff.

---

### Post by Tovam on 2010-01-13
Everything works for now, so I'm just going to leave it alone. No use messing with things if I'm going to wipe my old drive in a few weeks anyway.

Thanks for all the help.

---


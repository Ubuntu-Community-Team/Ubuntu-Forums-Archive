---
title: "upgrade from 11.10 to 12.04 won't boot, Grub problem"
date: 2012-06-10
forum: Installation &amp; Upgrades
---

### Post by mrc01 on 2012-06-10
Dual boot system, Win XP and Ubuntu 11 with Grub, working fine.
Update from 11.10 to 12.04 runs smooth, at end I reboot.
At boot, Grub menu won't appear, I get:
error: out of partition
grub rescue>

Tried the boot-repair disk. Single click "fix" has no effect, same problem.
Links to system info from boot-repair:
[http://paste.ubuntu.com/1033099](http://paste.ubuntu.com/1033099)
[http://paste.ubuntu.com/1033112](http://paste.ubuntu.com/1033112)
[http://paste.ubuntu.com/1033126](http://paste.ubuntu.com/1033126)

Boot-repair says /dev/sda6 (my Ubuntu boot partition) looks for core.img at 484962101 but it isn't there.

Booted to GPartEd, went to cmd prompted, tried this:
mount /dev/sda6 /sda6
grub-install --root-directory=/sda6 /dev/sda

Returns error:
The file /sda6/boot/grub/stage1 not read correctly

Went to the grub prompt, tried this:
find /boot/grub/stage1
root (hd0,5)
setup (hd0)

Returns error:
Error 6: Mismatched or corrupt version of stage1/stage2

I can see my data & files are still on the partitions, everything is there according to GPartEd. So it looks like if I can fix Grub I am good to go.

Thanks!

---

### Post by drs305 on 2012-06-10
mrc01,

Welcome to the Ubuntu Forums. The 'Stage 1' error message is from Grub legacy. Perhaps it came from some other rescue CD?

In any case, since you have Boot Repair, try the advanced option to purge/reinstall grub via chroot. Boot Repair can't do it automatically but it can walk you through the process. 

If it can't accomplish this, try using the instructions in the "Chroot" link in my signature line.

Note: An "out of disk" error generally is a BIOS/GRUB issue with the disk size, but I'm not sure about "out of partition".

---

### Post by mrc01 on 2012-06-10
SOLVED - thank you!
I got some error messages removing and reinstalling Grub from a cmd prompt after booting the BootRepair CD, yet it booted to hard disk afterwards.
Grub now works, my Ubuntu and XP partitions and data are intact.
Looks like root cause is Ubuntu 12 put in a new version of Grub (1.99-21ubuntu3.1) that conflicted with the Grub that Ubuntu 10 or 11 installed.

---

### Post by mrc01 on 2012-06-12
Same problem just happened again: system "boots" to the grub rescue prompt. This time the cause was I ran Synaptic Package Mgr to remove some old kernels. It automatically ran update-grub. Completed with no errors, but when it was done the system would not boot.

It seems my system is polluted with conflicting versions of Grub. I hope I can follow these steps to fix it again, but now I never know when it's going to happen again! Looks like the Ubuntu 12  upgrader really broke my system.

---

### Post by wilee-nilee on 2012-06-12
> **mrc01 said:**
> Same problem just happened again: system "boots" to the grub rescue prompt. This time the cause was I ran Synaptic Package Mgr to remove some old kernels. It automatically ran update-grub. Completed with no errors, but when it was done the system would not boot.

It seems my system is polluted with conflicting versions of Grub. I hope I can follow these steps to fix it again, but now I never know when it's going to happen again! Looks like the Ubuntu 12  upgrader really broke my system.

Use the boot-repair tool to make a new bootinfo summary and post the HTTP address where it is at.

---

### Post by mrc01 on 2012-06-12
I just followed the chroot procedure that worked before, but this time it didn't work... still no boot.
[http://paste.ubuntu.com/1036616](http://paste.ubuntu.com/1036616)
Should  I install Grub to /dev/sda6 instead of or in addition to /dev/sda? I picked  /dev/sda only, did not select /dev/sda6.
P.S. the above bootinfo summary looks the same as what I had the first time this problem struck.

---

### Post by wilee-nilee on 2012-06-12
I think you are fixable here, lets see what others have to say.

---

### Post by darkod on 2012-06-12
Boot with the ubuntu cd in live mode, open Gparted and remove the boot flag from /dev/sda6. You can do that by right-click, Manage Flags.
Then activate the boot flag on /dev/sda1. It should always be on the windows partition. Click the green button in Gparted to execute the changes if needed.

Restart and see if that changed anything.

From the results, you seem to have a working grub2 on the MBR which should work fine. You also have a broken grub2 installed on the partition /dev/sda6 but ubuntu can usually work despite this. I don't know if boot-repair did it or you, but you shouldn't install grub2 onto a partition. Always the MBR.

If the above boot flag change doesn't help, there are few other things to try.

---

### Post by YannBuntu on 2012-06-12
Hello
+1 to move the boot flag from sda6 to sda1

As your Ubuntu partition is [far from the start of the disk]("http://ubuntuforums.org/showthread.php?t=1998257") (>137GB), you can try the "out-of-disk  / ATA disk" option of Boot-Repair (Advanced options -> GRUB options tab). If that's not enough, you may have to create a separate /boot partition just after your Windows partition (we'll detail this procedure if you need).


@Darkod: FYI, Boot-Repair never puts GRUB in the PBR by default. This can only be done via the Advanced options ("Force GRUB" option). In practice, i've never seen any problem when the PBR contains GRUB (as long as GRUB is then installed correctly in the MBR, or a chainload is used), but i guess there is a reason why GRUB devs allow it only with --force option.

---

### Post by darkod on 2012-06-12
> **YannBuntu said:**
> 
@Darkod: FYI, Boot-Repair never puts GRUB in the PBR by default. This can only be done via the Advanced options ("Force GRUB" option). In practice, i've never seen any problem when the PBR contains GRUB (as long as GRUB is then installed correctly in the MBR, or a chainload is used), but i guess there is a reason why GRUB devs allow it only with --force option.

Thanks for the clarification. I also wasn't aware of the out of disk option.

You can completely remove and reinstall grub2 by using the chroot procedure anyway, but changing the boot flag is one step before that. If needed, we will provide the full chroot which in most cases should work.

Let us know how it goes.

---

### Post by mrc01 on 2012-06-12
> **darkod said:**
> Thanks for the clarification. I also wasn't aware of the out of disk option.

You can completely remove and reinstall grub2 by using the chroot procedure anyway, but changing the boot flag is one step before that. If needed, we will provide the full chroot which in most cases should work.

Let us know how it goes.
Thanks for the help. I tried the full chroot grub remove & install twice, did not work. Procedure ran without errors but did not fix problem. Next will try moving boot flag to sda1, then using 'out of disk' option. Will take a few days as I am on my way to Hadoop Summit in San Jose.

---

### Post by mrc01 on 2012-06-15
> **mrc01 said:**
> Next will try moving boot flag to sda1, then using 'out of disk' option. Will take a few days as I am on my way to Hadoop Summit in San Jose.
Just tried both of these, neither worked.
The first: move boot flag from sda6 to sda1: same problem, same error msg.

The second: apply 'out of disk' option in boot-repair. This caused a different message on failure to boot:
error: no device connected
error: no device connected
error: no such device: 011cedd0-51f3-4460-b5ad-574e6583392d

Now, when I go to the grub prompt and type: find /boot/grub/stage1, it hangs. "top" shows a "grub" process spinning one of the CPUs at 100%.
EDIT: also, if I type grub-install --root-directory=/mnt/temp /dev/sda, the same thing happens: "grub" process hangs and spins the CPU.

After moving the boot flag from sda1 to sda6 I re-ran the chroot procedure to remove & reinstall GRUB, but that didn't work either. Now I'm back to the original error. On boot I see a black screen with:
error: out of partition.
grub rescue>

I can still mount the partitions and see my data, but I'm starting to get worried that nothing is fixing this...

Here's my latest boot-repair info:
[http://paste.ubuntu.com/1043377](http://paste.ubuntu.com/1043377) before running chroot procedure
[http://paste.ubuntu.com/1043388](http://paste.ubuntu.com/1043388) after running chroot (current state)

---

### Post by darkod on 2012-06-16
Maybe Yann can help more, he's the author of boot-repair.

Few things meanwhile:
1. Leave the boot flag on sda1 and forget about it. Linux doesn't even use it, only windows, and it should be on the XP partition. It's not helping on sda6 at all. So just leave it on sda1 and don't waste your energy on the boot flag.
2. Don't run find /boot/grub/stage1, that is part of the procedure for grub1. You are now using grub2, so that command is wrong also. Forget about it too.

I don't know why the grub-install would hang when running, also you didn't specify what you have mounted at /mnt/temp, I guess /dev/sda6.

The results actually look OK. The UUIDs are correct, grub.cfg seems correct, grub2 on the MBR seems correct too.

It might be an issue with the "out of disk" thing but if you ran boot-repair with that option, it should have helped you. Yann would be more suitable to reply whether it helped, and why not if it didn't. Because apart from that the results look spot on.

---

### Post by drs305 on 2012-06-16
At the grub rescue prompt, type the following and see if you get the expected results noted after the # symbol:
```

ls (hd0,6)/  # vmlinuz & initrd.img
ls (hd0,6)/boot # the vmlinuz-3.2.0-24-generic-pae kernel and initrd.img-3.2.0-24-generic-pae
ls (hd0,6)/boot/grub # Lots of *.mod files
```

If you aren't seeing these, my guess is that the BIOS limitation is the culprit. The files are too deep on your system. You can try to enable large drives/LBA in your BIOS settings, update the BIOS to a newer version, or create a separate /boot partition within the first 130GB or so.

If BIOS changes don't work/aren't available, the good news is you already have a linux (swap) partition that you can change to /boot to see if a separate /boot might work. 

**If you want to try setting up a separate /boot partition:**
 
[LIST=1]
[*]Boot a LiveCD and open Gparted
[*]Unmount the sda3 swap partition (right click, swapoff)
[*]Format the swap partition as ext4
[*]Mount sda3 and sda6
[/LIST]

```

sudo mkdir /mnt/main /mnt/boot
sudo mount /dev/sda3 /mnt/boot
sudo mount /dev/sda6 /mnt/main
```

[LIST=1]
[*]Copy the **contents** of the /boot folder to the new partition.
[/LIST]

```

sudo cp -r /mnt/main/boot/* /mnt/boot/

```

[LIST=1]
[*]Check that *vmlinuz* & *initrd.img* are in /mnt/boot
[/LIST]
```
ls /mnt/boot
```
[LIST=1]
[*]Edit your real fstab: 
[/LIST]

```
gksu gedit /mnt/etc/fstab
```

[LIST=1]
[*]Place a # symbol at the start of the swap partition line
[*]Add the /boot partition:
[/LIST]

> 
/dev/sda3 /boot ext4 defaults,exec 0 1


[LIST=1]
[*]Save /mnt/etc/fstab and close the file
[*]Unmount the partitions
[/LIST]

```
sudo umount /dev/sda3 /dev/sda6
```

On rebooting, manually boot from the grub rescue prompt (Quick version):
Note Added: The quick boot did not work as the 'vmlinuz' and 'initrd.img' symlinks did not exist in (hd0,6)/

```

set prefix=(hd0,3)/grub
set root=(hd0,3)
insmod /grub/linux.mod
linux (hd0,[COLOR="DarkRed"]6[/COLOR])/vmlinuz root=/dev/sda6 ro
initrd (hd0,[COLOR="DarkRed"]6[/COLOR])/initrd.img
boot

```
OR:
On rebooting, manually boot from the grub rescue prompt (More foolproof version):
```

set prefix=(hd0,3)/grub
set root=(hd0,3)
insmod (hd0,3)/grub/linux.mod
linux (hd0,3)/vmlinuz-3.2.0-24-generic-pae root=/dev/sda6 ro
initrd (hd0,3)/initrd.img-3.2.0-24-generic-pae
boot

```


After booting into Ubuntu:
[LIST=1]
[*]Update grub
[/LIST]
```
sudo update-grub
```
[LIST=1]
[*]Change the fstab /boot entry to UUID (or LABEL):
[/LIST]
```
sudo blkid -c /dev/null
```
[LIST=1]
Use the above sda3 result for the /boot partition in fstab:
[/LIST]
```
gksu gedit /etc/fstab
```

> 
UUID=<sda3 UUID> /boot ext4 defaults,exec 0 1


[LIST]
[*]Create a new swap partition using Gparted
[*]Add the new swap entry to fstab (uncomment swap and change the UUID)
[/LIST]

---

### Post by mrc01 on 2012-06-16
> **drs305 said:**
> At the grub rescue prompt, type the following and see if you get the expected results noted after the # symbol:
```

ls (hd0,6)/  # vmlinuz & initrd.img
ls (hd0,6)/boot # the vmlinuz-3.2.0-24-generic-pae kernel and initrd.img-3.2.0-24-generic-pae
ls (hd0,6)/boot/grub # Lots of *.mod files
```

The first shows the root directory. There is no "initrd.img", but there is "initrd.img.old". Same for "vmlinuz.old".
The next two say "error: out of partition"

> **drs305 said:**
> If you aren't seeing these, my guess is that the BIOS limitation is the culprit. The files are too deep on your system. You can try to enable large drives/LBA in your BIOS settings, update the BIOS to a newer version, or create a separate /boot partition within the first 130GB or so.

Note: none of my partitions, BIOS or Grub setup has changed for the past year. Why would my BIOS suddenly change upon upgrading to Ubuntu 12? I looked around in the BIOS settings and couldn't find such a setting. It's a SATA drive set in BIOS to AHCI mode (whatever that means). I could set it for ATA mode, but it's been working fine in AHCI mode for the past year. Dell precision 380 BIOS A04 10/28/05.

At this point it looks like my next option is to set up a 'boot' partition. How could this have become necessary when this grub, bios and partition setup has been working for the past year?

---

### Post by drs305 on 2012-06-16
> **mrc01 said:**
> At this point it looks like my next option is to set up a 'boot' partition. How could this have become necessary when this grub, bios and partition setup has been working for the past year?

I can't say for sure that is the problem. I'm not good at math, but it looks like your Ubuntu partition spans the 137GB portion of the drive. If on the initial installation the /boot and /grub file contents were in the first 137GB there would not be a problem. If they were moved at some point beyond the 137GB partition the OS would suddenly fail to boot.

The reason you can see the files after booting is that it is only a GRUB/BIOS limitation. Today's OS's are designed to see large disks and all the contents. Until the system takes over though, the BIOS (and GRUB) cannot read information beyond a given point. Recent BIOS (and updates) recognize the expanding size of drives and don't have the limitation, but when the BIOS of yesteryear were designed the size of today's drives were not anticipated, or the creators didn't envision the boot information would be other than near the start of the drive.

I can't say for sure this is your problem, and I recognize there are a lot of steps. I've tried to tailor all the instructions to your situation, but it will still probably take 15-30 minutes or so to accomplish this with no guarantee of success. I'm not sure what other steps you can take, so if you are hesitant you can always wait to see if someone else posts a different solution.

---

### Post by mrc01 on 2012-06-16
> **drs305 said:**
> If on the initial installation the /boot and /grub file contents were in the first 137GB there would not be a problem. If they were moved at some point beyond the 137GB partition the OS would suddenly fail to boot.

The reason you can see the files after booting is that it is only a GRUB/BIOS limitation.
That sounds plausible. If the sda6 partition spans the 137GB threshold, any time files are copied they can move to either side of the threshold, making them visible or invisible to the BIOS. If this is the root cause, it's been working by accident over the past year as the critical files happened to be on the right side off the threshold.

I just did most of the steps you described, good result but I couldn't do them all, not quite there yet.

System now boots straight to Ubuntu 12 - no grub menu appears. From the Ubuntu 12 login screen, none of my logins work. All of them bounce me back to the login screen. I tried selecting different login shells including "recovery console" but they all bounce out. The screen flashes too quickly for me whether there is any visible error message.

Is this because my system doesn't have a swap partition? I commented it out in fstab. Should I boot to GPartEd to create one and update fstab?

Is there a cmd I can enter at the grub rescue prompt to boot to a recovery console instead of a full boot?

Latest system info: [http://paste.ubuntu.com/1044290](http://paste.ubuntu.com/1044290)

---

### Post by drs305 on 2012-06-16
> **mrc01 said:**
> That sounds plausible. If the sda6 partition spans the 137GB threshold, any time files are copied they can move to either side of the threshold, making them visible or invisible to the BIOS. If this is the root cause, it's been working by accident over the past year as the critical files happened to be on the right side off the threshold.

I just did most of the steps you described, good result but I couldn't do them all, not quite there yet.

System now boots straight to Ubuntu 12 - no grub menu appears. From the Ubuntu 12 login screen, none of my logins work. All of them bounce me back to the login screen. I tried selecting different login shells including "recovery console" but they all bounce out. The screen flashes too quickly for me whether there is any visible error message.

Is this because my system doesn't have a swap partition? I commented it out in fstab. Should I boot to GPartEd to create one and update fstab?

Is there a cmd I can enter at the grub rescue prompt to boot to a recovery console instead of a full boot?

Latest system info: [http://paste.ubuntu.com/1044290](http://paste.ubuntu.com/1044290)

I'll give you the short answer and then think on what may be happening.

To boot into recovery, add "single" to the linux line when you boot, ie.  ... *ro single*

Added: 

Swap should have nothing to do with your current issue, but you can create one and put it back in fstab. Just make sure to update the UUID. I'm not sure what is causing the login problems.

Also, to avoid confusion, while in the LiveCD you might want to rename the sda6 *boot* folder *boot-orig* so there is no confusion about which /boot folder is controlling things (sda3). The sda6 boot folder's contents are not being used for anything and are actually being "overmounted" (no such word) by sda3's boot folder on the running system.

---

### Post by mrc01 on 2012-06-16
> **drs305 said:**
> On rebooting, manually boot from the grub rescue prompt (Quick version):
```

set prefix=(hd0,3)/grub
set root=(hd0,3)
insmod /grub/linux.mod
linux (hd0,6)/vmlinuz root=/dev/sda6 ro
initrd (hd0,6)/initrd.img
boot

```
OR:
On rebooting, manually boot from the grub rescue prompt (More foolproof version):
```

set prefix=(hd0,3)/grub
set root=(hd0,3)
insmod (hd0,3)/grub/linux.mod
linux (hd0,3)/vmlinuz-3.2.0-24-generic-pae root=/dev/sda6 ro
initrd (hd0,3)/initrd.img-3.2.0-24-generic-pae
boot

```

In the quick version of grub cmds above, it returns an error if I use hd(0,6). I used hd(0,3) instead and it works. If I boot to single user mode, the system prints out a bunch of booting messages - runs fsck, no obvious errors - and then hangs - no prompt, ctrl-c does nothing.

I booted to GPartEd, made a new swap partition and updated 'fstab' to mount everything by UUID (new swap & boot). After that, it booted to the grub rescue prompt with "out of partition". Then I booted to the ubuntu repair and re-ran the chroot grub wipe & install procedure again. After that, it boots straight to Ubuntu without any grub screen and the login screen doesn't work.

Status summary: on boot, I get one of 2 things:
1) "error: out of partition" and grub rescue prompt. From here I can boot manually with the above grub rescue cmds (substituting hd(0,3). But the boot doesn't work. If to single user it hangs, if normal boot, can't log in - see 2 below.

2) no grub menu, boot straight to ubuntu 12 login screen, but logins don't work. For each login, none of the options work (Gnome, Ubuntu, Xubuntu, recovery console, etc.). They all snap back to the login screen.

It looks like I'm close, but still stuck. Appreciate your help - thanks.

Latest config into: [http://paste.ubuntu.com/1044529](http://paste.ubuntu.com/1044529)

---

### Post by mrc01 on 2012-06-16
PS: during login, right after I enter my password and hit ENTER, the screen flashes black before returning to the login prompt. It's so quick it's hard to read but I did it about 20 times in order to make out the following message that appears:
Stopping mount filesystems on boot.

My home directory is on a drive (/dev/sda7) that is mounted into /dsk2, and /home is a link to /dsk2/home. Perhaps if I copy my home directory files from sda7 to a real home directory on sda6, it might let me log even if it's not mounting the drives. But why isn't it mounting the drives?

---

### Post by drs305 on 2012-06-16
> **mrc01 said:**
> In the quick version of grub cmds above, it returns an error if I use hd(0,6). I used hd(0,3) instead and it works. 
Yeah, that makes sense. Your old boot folder just had vmlinuz.old and not the symlink vmlinuz. And we want to be using sda3 anyway. 

> 
If I boot to single user mode, the system prints out a bunch of booting messages - runs fsck, no obvious errors - and then hangs - no prompt, ctrl-c does nothing.

I booted to GPartEd, made a new swap partition and updated 'fstab' to mount everything by UUID (new swap & boot). After that, it booted to the grub rescue prompt with "out of partition". Then I booted to the ubuntu repair and re-ran the chroot grub wipe & install procedure again. After that, it boots straight to Ubuntu without any grub screen and the login screen doesn't work.
Your fstab shows that you have commented out the sda3 entry for /boot. This makes an interesting boot, as it uses the sda3 boot information initially but eventually will read the sda6 information after fstab is read. But to keep things straight, it would be better to uncomment the sda3 fstab entry so all boot and grub information comes off sda3. The "root=/dev/sda6" should stay the way it is in the linux line when you are manually booting.

> 
Status summary: on boot, I get one of 2 things:
1) "error: out of partition" and grub rescue prompt. From here I can boot manually with the above grub rescue cmds (substituting hd(0,3). But the boot doesn't work. If to single user it hangs, if normal boot, can't log in - see 2 below.

2) no grub menu, boot straight to ubuntu 12 login screen, but logins don't work. For each login, none of the options work (Gnome, Ubuntu, Xubuntu, recovery console, etc.). They all snap back to the login screen.

It looks like I'm close, but still stuck. Appreciate your help - thanks.

Latest config into: [http://paste.ubuntu.com/1044529](http://paste.ubuntu.com/1044529)

Note: There is another thread dealing with login problems after upgrading here. I have no idea if it's related:
[http://ubuntuforums.org/showthread.php?t=2004830]("http://ubuntuforums.org/showthread.php?t=2004830")

[COLOR="Red"]Added (Important):[/COLOR]
As I am composing this message I see you posted another and indicated you have your /home on sda7. That is most likely your login problem. You do not have sda7 listed as /home in your fstab and it needs to be there so try removing the symlink and directly assign it in fstab. 

Now the question becomes the folder structure of sda7. Is the root folder /home or is it your username? Normally you would have and empty /home folder in sda6 and /<username> in sda7, with the fstab /home listing for sda7.

---

### Post by YannBuntu on 2012-06-16
Hi
> **mrc01 said:**
> The second: apply 'out of disk' option in boot-repair. This caused a different message on failure to boot:
error: no device connected
error: no device connected
error: no such device: 011cedd0-51f3-4460-b5ad-574e6583392d

That means the "out-of-disk" option is not enough. If i were you, i would create a separate /boot as described here: [http://ubuntuforums.org/showthread.php?t=1998257](http://ubuntuforums.org/showthread.php?t=1998257)

---

### Post by mrc01 on 2012-06-16
Here's the short story: everything is working!

> **drs305 said:**
> Your fstab shows that you have commented out the sda3 entry for /boot.

Weird. I thought I had already uncommented it. Just booted to boot repair CD and confirmed it is indeed commented out. Then I uncommented it and rebooted - no other changes. I got the grub menu (first time in a week I've seen it), booted to Ubuntu, but still could not log in.

Then I booted again to the boot-repair CD. To make changes below...

> **drs305 said:**
> [COLOR="Red"]Added (Important):[/COLOR]
you have your /home on sda7. That is most likely your login problem. You do not have sda7 listed as /home in your fstab and it needs to be there!
I don't think this is a problem. Here's how it's set up: sda7 has a "/home" dir and is mounted to /dsk2. /home in sda6 (the root filesystem) is a link to /dsk2/home. So it works if everything is mounted. Perhaps everything is not being mounted? I tried making /home a real directory on sda6 but that didn't help.

I can log in if I hit "ctrl+alt+F1" to switch to a non-graphic terminal. While logged in I can see all drives are mounted in the right places. My home dir is there and all my files. I ran 'update-grub' and now the entire system is working.

Thanks for the help!  :D I'll write up a blog entry on this with summary and link it here in case it helps others.

---

### Post by drs305 on 2012-06-16
> **mrc01 said:**
> ...
I don't think this is a problem. Here's how it's set up: sda7 has a "/home" dir and is mounted to /dsk2. /home in sda6 (the root filesystem) is a link to /dsk2/home. So it works if everything is mounted. Perhaps everything is not being mounted? I tried making /home a real directory on sda6 but that didn't help.
Yes, as long as the symlinks are working and things mount. Seeing /dsk2 and not /home in fstab threw me a bit.

Glad you have the boot issues fixed. :-)

I'm not someone to ask for help on video issues though. A quick update (one sentence or link) on what you find out about the login issue will be appreciated.

Happy Ubuntu-ing - soon I hope.

---

### Post by mrc01 on 2012-06-16
*everything* is working - including video. :P My system is 100% operational - Grub, Linux and XP. No data loss.
I'm composing the summary details now... will post later tonight.
Here's a summary:
[http://mclements.net/Mike/mrc-blog/blog-120616.html](http://mclements.net/Mike/mrc-blog/blog-120616.html)
Thanks again for the help!

---


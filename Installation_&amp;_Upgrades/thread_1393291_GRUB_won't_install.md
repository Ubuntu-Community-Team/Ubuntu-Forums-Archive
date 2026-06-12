---
title: "GRUB won't install"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by greebothecat on 2010-01-29
Hey, I have a major problem here..
I have messed up my partitions really bad and grub refuses to install.
Here's how it looks:```

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   83  Linux
/dev/sda2              14        2432    19430617+  83  Linux
/dev/sda3            2433       60801   468848992+   5  Extended
/dev/sda5            2433        2930     4000153+  82  Linux swap / Solaris
/dev/sda6            2931       53535   406484631   83  Linux
/dev/sda7           53536       60801    58364113+   7  HPFS/NTFS
```

Initially there was only Linux (Karmic) on this hdd, on what is now sda2 to sda6, current sda2 being the boot partition. Now, I decided to install Windows XP and using GParted I created an NTFS partition at the end, sda7. But it wanted to have his loader on the first one, so (now this is probably stupid what I did) I cut 100MB from Linux root and put it as NTFS at the beginning, making it sda1, boot and letting windows install it's loader there. I figured I can just reintall grub on it later (think I have misred some tutorials). As you can probably guess, it won't.

I formatted sda1 to ext4 now (should it be something else?). What I do is run the Live CD (9.10), use terminal, then do
```
sudo -i
mkdir /media/boot
mount /dev/sda1 /media/boot
grub-install --recheck --root-directory=/media/boot /dev/sda1
```
and it goes
```
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly
```

also, when I do update-grub it says "grub-probe: error: cannot find a device for /."

tried installing grub on sda2 and flagging it as a boot and still no-go :/
I'm all out of ideas, could anybody please help me or point to the right tutorial?

---

### Post by darkod on 2010-01-29
The commands you are trying are wrong. First of all, /boot is a boot partition as the name says, not your root partition, so you can't have --root-directory=/media/boot.
Second, do not install grub2 onto a partition, /dev/sda1. It's better on MBR of a disk, like /dev/sda.

Next, you said /dev/sda2 is your ubuntu boot partition but it's too big for that. Are you sure? Or you meant to say root partition?

After what you did with Gparted I'm not sure Ubuntu would work at all, but depending whether your root partition is /dev/sda2 or /dev/sda6, and whether you have a separate /boot partition as /dev/sda2, the commands you need to run from the live desktop are:

sudo mount /dev/sda6 /mnt (if /dev/sda6 is your root and you don't have separate /boot)
sudo grub-install --root-directory=/mnt/ /dev/sda

If you have separate /boot partition and that's /dev/sda2 for example:

sudo mount /dev/sda6 /mnt
sudo mount /dev/sda2 /mnt/boot
sudo grub-install --root-directory=/mnt/ /dev/sda

---

### Post by greebothecat on 2010-01-29
Thanks for reply..I don't quite understand the mechanincs of partitions and MBR, but I think I did something that might work.. deleted the previous sda1 and moved my ubuntu root partition back to the beginning of drive, so it looks now like this:
```
Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        2432    19535008+  83  Linux
/dev/sda3            2433       60801   468848992+   5  Extended
/dev/sda5            2433        2930     4000153+  82  Linux swap / Solaris
/dev/sda6            2931       53535   406484631   83  Linux
/dev/sda7           53536       60801    58364113+   7  HPFS/NTFS
```
I followed your advice
```

sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
```
and grub said it has installed without errors.. update-grub still won't work thought, I'm going to reboot now and see what's up.

edit:
I LOVE YOU, worked like a charm!
Now I'm going to try to include windows in the loader, thanks again for help :)

---

### Post by darkod on 2010-01-29
update-grub doesn't work from the live desktop. You run the command when running your hdd ubuntu.
But be advised that maybe it won't detect XP because you installed it into logical partition (inside extended). Windows need to be on primary partition I believe.

---

### Post by meierfra. on 2010-01-29
> I formatted sda1 to ext4 now. 
The partition you formatted contained the XP boot files.
Follow these [instructions]("http://bootinfoscript.sourceforge.net/") to run the boot info script and post the RESULTS.txt.

Then I can you tell you  how to restore your boot files. After that 'update-grub" should detect XP. (Using grub to boot Windows XP from a logical partition is fairly easy. So there is no need to reinstall XP to a primary partition)

---


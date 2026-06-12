---
title: "Can no longer boot..."
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by XtremeGamer99 on 2009-04-01
Hello,

I'm running the Kubuntu 9.04 Beta. I recently downloaded and installed some linux games to play on an upcoming trip. One of that games returned an error during the installation, and now my laptop is completely screwed up.

First, it would boot normally to the login screen. However, when logging in, it would hang and not go anywhere. using top, I found that pdflush was going at CPU100%, and I wasn't able to kill it. So, I rebooted into recovery mode, and I somehow screwed something up (I think I tried to check a mounted filesystem). Anyway, now GRUB is returning an Error 17, and I'm unable to access anything...

Normally, I would just download and burn Knoppix, pop it in, and save my data. However, I have a few issues. I'm using the new ext4 filesystem for everything. I'm not sure if Knoppix would know what to do with it. Also, I opted to encrypt the home directory. How would I mount this encrypted partition? Kubuntu did it automatically upon login.

Should I just re-download a Kubuntu CD? I remember I had problems getting the graphical installer to work, so I just used the text-based Alternate CD. Will that be able to help?

I really need my data back. >_>

---

### Post by ispy on 2009-04-01
Fedora 10 can rescue data from a ext4 partition, as well as Sidux.

You may want to check those out.

I had a similar problem, only I accidentally updated to ext4 without updating Grub. Don't do that.

---

### Post by XtremeGamer99 on 2009-04-01
> **ispy said:**
> Fedora 10 can rescue data from a ext4 partition, as well as Sidux.

You may want to check those out.

I had a similar problem, only I accidentally updated to ext4 without updating Grub. Don't do that.

I was able to find my Kubuntu 9.04 Alpha installation disc...

I think my GRUB partition was ext2, and the rest was ext4. Or something. I honestly don't remember. <_<

---

### Post by ispy on 2009-04-01
I can't remember if the live CD of Jaunty can read/write ext4. I'm reasonably sure it can though. Best bet is to try it. I know Fedora works, I used that.

Sidux is pretty complicated, but it works as well.

---

### Post by XtremeGamer99 on 2009-04-01
Okay, I booted into "Rescue Mode" in the Kubuntu 9.04 Alpha (not Beta) Alternate CD.

I've gotten to the point where it asked which partition to use as the root filesystem?

the options are (/dev/...):
sda1
sda2
sda5
sda6
sda7

sda1 is my broken Windows Vista partition that I never bothered to delete. >_>

I'm trying to mount the encrypted /home directory (which is /dev/sda7). What exactly do I do? I think the otiginal root directory before I screwed everything up was /dev/sda5

EDIT: Well, I tried sda2, sda5, and sda6, both of which came up as an error: (check syslog for more info, yadayada)

sda7 comes up with these options:
Execute a shell in /dev/sda7
Execute a shell in the install environment
Choose a different root file system
Reboot the System

---

### Post by XtremeGamer99 on 2009-04-01
Well, it seems that the root partition has become corrupted. I've booted into Kubuntu via an external HDD, and I've been trying to change options around to boot into the laptop's root partition (using the external GRUB to boot into the laptops root). I'm able to successfully mount my /home directory that on my laptop while using the external drive as the root partition; however, I'm still not able to access my data since it's ecrytped (I can mount /home, just not /home/user).

How do I mount the encrypted part? (/home/user/.Private -> /home/user)

---

### Post by XtremeGamer99 on 2009-04-02
... So, Apparently, the encryption keys to decrypt /home/user/.Private directory are stored somewhere in the /var directory.

Bad news for me is that /var was included on the root partition -- the partition that I can't access, thus I can't get my keys for it anymore. I'm running fsck on /dev/sda5 (the root partition). It first said that the journal was corrupted, and I guess it rebuilt it. And now it keeps saying somehting like this over and over:

```
Restarted e2fsck from beginning...
/dev/sda5 contains a file system with error, check forced
Pass 1: Checking inodes, blocks, and sizes
Programming error? block #204 claimed for no reason in process_bad_block
Root inode is not a directory. Clear<y>? yes

Inode 5 has illegal block(s). Clear<y>? yes

Ilegal block #498 (##########) in inode. CLEARED. 
Ilegal block #499 (##########) in inode. CLEARED.
Ilegal block #500 (##########) in inode. CLEARED.
Ilegal block #501 (##########) in inode. CLEARED.
Ilegal block #502 (##########) in inode. CLEARED.
Ilegal block #503 (##########) in inode. CLEARED.
Ilegal block #504 (##########) in inode. CLEARED.
Ilegal block #505 (##########) in inode. CLEARED.
Ilegal block #506 (##########) in inode. CLEARED.
Ilegal block #507 (##########) in inode. CLEARED.
Ilegal block #508 (##########) in inode. CLEARED.
Too many illegal blocks in inode 5
Clear inode<y>? yes

```

And then it repeats. The only thing that seems to change is the Illegal block number and the long number right after that (in the parenthesis).

I'm sitting here just selecting yes. >_>

---

### Post by XtremeGamer99 on 2009-04-02
I'm still looking for a way to decrypt my home directory. I know the password, but I no longer have the keys (if that makes any sense)

---


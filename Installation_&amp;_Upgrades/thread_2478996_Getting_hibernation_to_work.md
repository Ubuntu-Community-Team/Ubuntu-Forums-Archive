---
title: "Getting hibernation to work?"
date: 2022-09-11
forum: Installation &amp; Upgrades
---

### Post by Peter_Brandon on 2022-09-11
Esp. with new laptops that won't enter a deep sleep state and expect Windows hybrid sleep or drain the battery extensively on 'sleep', it would be really handy to be able to get hibernation to work.

So I'm wondering if people have had success getting hibernation  to work?  If so, how was your system set up?  I'm guessing that  partition encryption, secure boot, swap size, kernel lockdown features,  and possibly lvm are all obstacles.  Did someone find some ways to get around these problems?  Is swap at 1-1.5 times RAM actually sufficient (hibernation has to store RAM + swap)?  Is it possible to have secureboot activated and still hibernate?

---

### Post by TheFu on 2022-09-11
I don't use hibernation due to well known security issues with it.  I use standby daily, but if the system is being moved out of a building, it is shutdown completely for security reasons.

Standby works with LUKs encryption and LVM. I'm 100% positive. That's how I use it.  I don't have sufficient swap to hibernate. I use swap partitions (actually it is an LV), not swapfiles.

Also, I don't use secureboot.  When I'm traveling to less-trustworthy parts of the world, I boot from a flash drive that is always on my body.  I ignore the /boot/ on the system.  Look up evil-maid attack for why.

---

### Post by Peter_Brandon on 2022-09-11
Thanks TheFu!  Yup, using a flash drive in insecure parts of the world makes a lot of sense--thanks for the idea.  Standby works fine for me as well, at least on my desktop.  But, as I mentioned, I have a laptop that won't go into deep sleep, so it burns almost as much battery suspended as it does while I'm using it.  Windows handles this with hybrid suspend--it suspends to idle, not deep sleep, for 10 minutes and then goes into hibernate.  And, even on my desktop, it would be nice to be able to hibernate so I can always get back to exactly where I was, even if I'm out of town for a while, and without using power that might itself be unreliable.

---

### Post by ne29914 on 2022-09-11
Getting Hibernate to work takes quite some effort.
My laptops hibernate fine, but only with a swap partition >10% larger than RAM size. I've never been able to get it to work with a swapfile.

---

### Post by Peter_Brandon on 2022-09-11
Thanks ne29914, good to hear it's possible!  Also the info on swap size is helpful.  What took effort?

---

### Post by ne29914 on 2022-09-11
> **Peter_Brandon said:**
> What took effort?
Well, first you need to create a swap partition. Let's say /dev/sda6 for this example.
Run:
```
sudo mkswap /dev/sda6
sudo swapon /dev/sda6
blkid
```
(you may get an error on the first command if /dev/sda6 is already a swap partition. It's unimportant).
Note the UUID of /dev/sda6. in this case (as an example): *123456-7890-abcd-ef12-34567890abcd*
Check that this file:
```
/etc/fstab
```
contains:
```
UUID=*123456-7890-abcd-ef12-34567890abcd* none swap defaults 0 2
```
If not, reboot and check again.

Modify/create:
```
/etc/initramfs-tools/conf.d/resume
```to contain:
```
RESUME=UUID=*123456-7890-abcd-ef12-34567890abcd*
```
Modify:
```
/etc/default/grub
```
To contain:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash resume=UUID=*123456-7890-abcd-ef12-34567890abcd*"
GRUB_RECORDFAIL_TIMEOUT=$GRUB_TIMEOUT
```
Modify/create:
```
/etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
```
To contain:
```
[Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes
[Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate;org.freedesktop.login1.handle-hibernate-key;org.freedesktop.login1;org.freedesktop.login1.hibernate-multiple-sessions;org.freedesktop.login1.hibernate-ignore-inhibit
ResultActive=yes

```

Run:
```
sudo update-grub
sudo update-initramfs -u
```

Reboot.

It should now work, lid switch, timeout, battery-level trigger etc. you'll have to set yourself.

---

### Post by Peter_Brandon on 2022-09-11
That's immensely helpful ne29914! Will have to give it a try.  One question though:  do you have encrypted partitions?  I was under the impression that if you encrypt /home, you also end up encrypting swap and that swap uses a randomly generated encryption key each time you boot.  So if you hibernate, that would likely mean that the system can't read the swap file when you restart.  Or?

---

### Post by ne29914 on 2022-09-12
I can't say, I don't use encryption. But as swap is on a separate partition, I don't see how /home could influence it. But I could be wrong.

---

### Post by Peter_Brandon on 2022-09-12
Thanks for the info!  My mistake--I meant if you encrypt root (typically with home in it), the default for swap is to be encrypted as well.  If someone thinks root / home aren't safe, the swap isn't either.

---

### Post by ne29914 on 2022-09-12
I never set up a machine like that. I always have separate partitions for /, /home and swap.
In that case, encrypting root makes no sense, the OS is not secret.
If you're operating with just /, this whole discussion is pointless.

EDIT: this is what I mean:
```
macro@macro6910p:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda      8:0    0 465,8G  0 disk 
&#9500;&#9472;sda1   8:1    0  29,3G  0 part /
&#9500;&#9472;sda2   8:2    0   5,9G  0 part [SWAP]
&#9492;&#9472;sda3   8:3    0 430,6G  0 part /home
sr0     11:0    1  1024M  0 rom
```

---

### Post by Peter_Brandon on 2022-09-12
Because I'd like to have root and swap encrypted, I followed the instructions here:  [https://nileshgr.com/2021/01/26/hibernate-support-on-ubuntu-20-04-encrypted-swap-and-encrypted-root-filesystem/](https://nileshgr.com/2021/01/26/hibernate-support-on-ubuntu-20-04-encrypted-swap-and-encrypted-root-filesystem/) .  I was able to get hibernation working on my laptop, so far w/o problems, though I haven't tried fully loading my system and seeing what happens.  Documentation suggests that there are some kernel parameters that might need to be set to be able to take full advantage of available swap space:  [https://www.kernel.org/doc/html/v5.10/admin-guide/pm/sleep-states.html](https://www.kernel.org/doc/html/v5.10/admin-guide/pm/sleep-states.html)

---

### Post by ne29914 on 2022-09-12
When you say "root" do you mean / or /root or the user "root"? Please be precise.
Encrypting /home makes sense, and probably also swap. But again, if you haven't created a /home partition it's moot.
Your links are a bit TL&DR to me, sorry I can't help you further. You apparently have special needs that are outside my knowledge.

Good Luck.

---

### Post by Peter_Brandon on 2022-09-13
You did help me sort out my thinking and clarify what's possible ne29914.  I was hoping there was something simpler than that web page I used if I wanted to keep encryption, but evidently not.  Also helpful to know what worked for others in terms of swap partition size.

By 'root' I mean / .  You are right that the OS isn't secret, so maybe not something for everyone to encrypt.  Depends on the level of security you want.  An unecrypted / folder allows an outside party to easily modify or install software on your system.

---

### Post by C.S.Cameron on 2022-09-13
This worked for me with 18.04 and 20.04 on an encrypted flash drive.
[https://askubuntu.com/questions/1086309/how-to-make-bios-uefi-flash-drive-with-full-disk-encryption](https://askubuntu.com/questions/1086309/how-to-make-bios-uefi-flash-drive-with-full-disk-encryption)

---

### Post by Peter_Brandon on 2022-09-21
ne29914 :  You may be right that what I'm attempting to do is overly cautious.  But, let me point out that if you do not encrypt your / directory, it's easy for a third party to install whatever software they want directly onto your system, including software that will capture and copy or communicate what is in your home directory.  A lot of people these days do encrypt their systems and not a few keep / and /home in separate partitions for obvious reasons.

I was able to successfully get my encrypted, multi-partition system to hibernate using the following, for anyone interested.  Note that I did not use lvm for my partitions, so that may alter the needed implementation.  Inspiration for what I did comes from:
[https://gist.github.com/HacKanCuBa/b8565369de9620ba1eb24b75ee836857](https://gist.github.com/HacKanCuBa/b8565369de9620ba1eb24b75ee836857)
[https://unix.stackexchange.com/questions/392284/using-a-single-passphrase-to-unlock-multiple-encrypted-disks-at-boot](https://unix.stackexchange.com/questions/392284/using-a-single-passphrase-to-unlock-multiple-encrypted-disks-at-boot)
I had previously used the following source to set up hibernation on my laptop, but the method did not carry over to my desktop (which refused to boot).  I suspect the relevant difference was that the laptop had my system in a single root partition while my desktop had / /home /boot all in separate partitions:  [https://nileshgr.com/2021/01/26/hibernate-support-on-ubuntu-20-04-encrypted-swap-and-encrypted-root-filesystem/](https://nileshgr.com/2021/01/26/hibernate-support-on-ubuntu-20-04-encrypted-swap-and-encrypted-root-filesystem/)

The following is easiest to implement if you become root (sudo su):
0) Warning:  If anything goes wrong, you'll need to unwind everything here.  So keep copies of the original versions of any files you change and be prepared to use a USB live drive with a linux system, cryptsetup to open your encrypted root partition, and the chroot command to 'become' the system on your computer so you switch back to the original version of the files and update initramfs.  chroot instructions are here:  [URL="https://forums.bunsenlabs.org/viewtopic.php?pid=55737#p55737"]https://forums.bunsenlabs.org/viewtopic.php?pid=55737#p55737
[/URL]
1) Create a swap partition large enough to contain all of your RAM and then some (I think 1.25-1.5x RAM is good, with perhaps lower numbers for larger RAM, I used 1.25 times RAM on a system with 24GB RAM).
    #While installing my OS, I set up my system with an unformatted partition large enough for the swap (the system started with no swap partition).
    #You may be able to use gparted or similar to put together a large enough unformatted partition for the swap space.  Remove any line in /etc/fstab referring to a pre-existing swap file or partition.

2) Edit or create /etc/initramfs-tools/conf.d/resume to contain the line:
    ```
RESUME=/dev/mapper/cryptoswap
```

3) Add the following line to your /etc/fstab:
     ```
/dev/mapper/cryptoswap swap swap defaults 0 0
```

4) Set up your swap using the following (my swap partition is on /dev/sda6--find your swap device name using lsblk and use that instead).  Give it the same password you use for hard disk decryption (that is, the password you use when starting your system; the one for / )
 ```

cryptsetup luksFormat /dev/sda6
cryptsetup open /dev/sda6 cryptoswap
mkswap /dev/mapper/cryptoswap

```

Note:  I believe the above should work.  What I actually did, because I wasted a lot of time with an approach that didn't work, is a bit different than the above.  It involved the following (this involves creating a random 512byte key, placing it on / and then using luksAddKey to give the swap partition a human-workable passphrase; but the 512 byte key should not be necessary):
 ```

(DO NOT USE)
dd if=/dev/urandom of=/.swap-key bs=1 count=512
cryptsetup luksFormat -d /.swap-key /dev/nvme0n1p3
cryptsetup luksAddKey -d /.swap-key /dev/nvme0n1p3
cryptsetup open -d /.swap-key /dev/nvme0n1p3 cryptswap
mkswap /dev/mapper/cryptswap

```

5) Edit your /etc/crypttab so it looks more like the following.  Basically, my crypttab already started with entries for root.fsm and 1.home.fsm.  However, after the uuid in each entry, I added 'crypt_disks'.  Together with the later parameter keyscript=decrypt_keyctl, this tells your system to use one passphrase to open all encrypted partitions labeled with 'crypt_disks'.  And, in the last component, I made sure there was a sub-phrase of 'initramfs,keyscript=decrypt_keyctl'.  Finally, I used blkid to look up the uuid on my system for cryptoswap (you'll have a different uuid of course--use that) and used it to create the cryptoswap line in the following.  Also make sure you have the keyutils package installed on your system--it has the decrypt_keyctl script.
 ```

root.fsm /dev/disk/by-uuid/51ca2671-9d41-10f7-af25-de8abaf3d85d crypt_disks luks,initramfs,keyscript=decrypt_keyctl,discard
1.home.fsm /dev/disk/by-uuid/7a5738a0-e79c-492b-a1cf-637fea8a5ce2 crypt_disks luks,initramfs,keyscript=decrypt_keyctl,discard
cryptoswap /dev/disk/by-uuid/e0e2123a-fd60-48f2-bbac-933f12225c50 crypt_disks luks,initramfs,keyscript=decrypt_keyctl,discard

```

6) Update initramfs:
 ```

sudo update-initramfs -u    

```

7) Reboot your system.

While this setup has worked so far for me (including hibernating multiple GBs of RAM), I wonder about some of the points made in [https://www.kernel.org/doc/html/v5.10/admin-guide/pm/sleep-states.html](https://www.kernel.org/doc/html/v5.10/admin-guide/pm/sleep-states.html) that seem to imply that unless a given system parameter is altered, the full swap partition will not be used for hibernation.

---


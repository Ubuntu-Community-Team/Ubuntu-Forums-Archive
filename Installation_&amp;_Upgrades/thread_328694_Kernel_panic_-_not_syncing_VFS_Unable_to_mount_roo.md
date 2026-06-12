---
title: "Kernel panic - not syncing VFS: Unable to mount root fs on unknown-block(0,0)"
date: 2006-12-31
forum: Installation &amp; Upgrades
---

### Post by amadain on 2006-12-31
I am using an Apple Dual 2 GHz Power Mac G5 with 2GB RAM.

I recently upgraded from edgy to feisty using apt-get update and apt-get dist-upgrade.

This went remarkably smoothly, out of 768 MB of updates there was only one conflict to be resolved.

The kernel was updated from 2.6.17.x to 2.6.20.x (the original 2.6.17.x kernel is still available).

After the dist-upgrade, I issued a ybin -v, to make sure that yaboot was configured correctly.

On reboot, I get the 'Kernel panic - not syncing VFS: Unable to mount root fs on unknown-block(0,0)' message.

If I reboot, and use the 'old' 2.6.17.x kernel I dropped into an 'ok >' prompt.

I have booted using a Rescue CD, I can chroot into the file system. The files all seem to be there, and the symbolic links are correct.

Could it be that the support of the SATA is no longer in the 2.6.20.x kernel?
Why would the previous kernel image drop me into the 'ok >' prompt?
Could it be an initrd-tools issue or even a udev issue?

Any and all pointers greatfully appreciated.

---

### Post by amadain on 2006-12-31
To give further information, I have again booted from a Rescue CD, and did the following
[LIST]
[*]mounted the root file system
[*]mounted /usr, /var and /home
[*]mounted /proc, /sys
[*]chroot'ed into the new environment
[*]did a update-initramfs -c -k 2.6.20-2-powerpc64-smp
[/LIST]

and had the same results - 2.6.20-2-powerpc64-smp continues to fail.

I will repeat the same procedure for 2.6.17.x and see if I can make the old kernel work.

I have also compared the configs from both kernels and can't see an obvious difference between them regarding the SATA config.

---

### Post by amadain on 2007-01-01
OK, then, the story continues.

Using the Rescue CD, I chroot'ed into my feisty installation. The previous 'update-initramfs -c -k 2.6.20.x' command succeeded successfully but still did not fix my problem.

However, the 'update-initramfs -c -k 2.6.17.x' fails as udev has been updated and will only support kernels later than 2.6.19 -- so my 2.6.17.x kernel is hosed.

I thought that all this could be a problem with initrd-tools, so I connected the network, and issued an 'apt-get install initrd-tools' -- surprisingly, these were not already installed, as a result I now have version 1.84 (I think).

A subsequent update-initramfs -c -k 2.6.20.x' command again succeeded successfully and again did not fix my problem.

I will now read up on how to initrd-tools to create a new initrd image. [EDIT] - I just read that from 2.6.14 yaird is used to create inited images.

---

### Post by amadain on 2007-01-01
Well, that didn't work.

I installed yaird and issued the command 'yaird -o /boot/initrd.img 2.6.20.2-powerpc64-smp'. Again, as before the command completed sucessfully -- but on reboot I got the following message 'Unable to handle kernel paging requst for data at address 0xc.....'.

I can also see that modules sata_svw, libata, scsi_mod, generic and evdev are loaded.

Rather that just issuing a ybin after the yaird command, I will not issue a update-initramfs and a ybin to see what happens.

---

### Post by justinchudgar on 2007-01-04
I am having the exact same issue, on an x86 system. The 2.6.17-10-generic kernel that had been working now panics with the VFS not syncing message; and, all 2.6.19 and 2.6.20 kernels through 2.6.20-3-generic hang "loading files needed to boot". I see some message about udev and an "abnormal exit", but, since the root filesystem is not mounted, there are no logs.

---

### Post by amadain on 2007-01-13
I rebooted using my rescue CD, chroot'ed into my feisty environment and did a

apt-get update
apt-get upgrade

solved the problem!

I am now up and running on Feisty!! Yippee!! Hurray!!

I would have liked to solved the problem myself though - at least like that I would have learned something.

Can complain though.

---

### Post by dorsey on 2007-01-29
Hate to be performing thread necromancy here, just wanted to let anyone else who stumbled across this know:

I had the same issue, it turned out to be due to my initramfs being FUBAR.

Just boot to single-user mode using a live CD and chroot to your Ubuntu installation.

Then run:

```
update-initramfs -u
```

and all will be well.

---

### Post by nbayiha on 2007-02-03
how to chroot into my ubuntu installation with the live cd (if Ubuntu was already installed of course )?

---

### Post by ygarl on 2007-02-27
I have the same problem, but my Mint Linux is working peachy as well.
I'm au fait with fstab etc, so I can mount the other partition from Mint if needed, but the info on chroot I have found is more than a little mysterious to me!

How - exactly - would I chroot and then apt-get update etc. 
p.s. I understand apt-get... it chroot which makes the hairs on my neck stand up on end!

---

### Post by etu on 2007-03-02
I just upgraded to Feisty and none of the menu items did boot (yes, I had dependency problems in installation and there is plenty of conflicts in the system).

After trying plenty of tricks (including replacing UUID with /dev/hda1 both in GRUB and fstab)
I found out that *all* the initrd-files are wrong.

The system booted when I changed initrd to /boot/initrd.img-...dpkg-bak. Luckily the installation had left them behind.

---

### Post by etu on 2007-03-02
Cleaned-up version with some more info:

I just upgraded to Feisty, I had the usual amount of dependency problems in installation but I rebooted the system without solving them all.

So, I got the famous 'Kernel panic - not syncing VFS: Unable to mount root fs on
unknown-block(0,0)'. This applied to all the kernel versions I had in the sytem.

After trying plenty of tricks (including replacing UUID with /dev/hda1 both in GRUB and
fstab) I found out that *all* the initrd-files are wrong. They are all of size 0.

The system booted when I changed initrd to /boot/initrd.img-...dpkg-bak. Luckily the installation had left them behind.

So, in the boot menu, select edit (e) and change initrd to add .dpkg-bak in the end. Then
the system boots.

I think that some kernel package (don't know which) was installed but not configured.
The situation likely solves when I resolve all the conflicts and get all the
packages configured.

This is not very nice behaviour of the system. In the very likely situation that you have
dependency conflicts it makes the system unbootable...

---

### Post by quick_dudley on 2007-03-28
> **nbayiha said:**
> how to chroot into my ubuntu installation with the live cd (if Ubuntu was already installed of course )?

firstly, hit alt-F1 to go to background terminal
then:
```

sudo init 1
mkdir /target
mount -t ext3 /dev/<your installation partition> /target
chroot /target
init 5

```

---

### Post by amadain on 2007-03-29
My rescue CD is a Debian Etch PPC CD.

Upon booting on the CD, I choose the rescue64 option. This brings me to the usual Debian keyboard and language settings.

After the filesystems and network have been recognised I break out to a shell prompt and do
1. mount /dev/sdb4 /mnt
2. mount /proc /mnt/proc -o bind
3. mount /sys /mnt/sys -o bind
4. mount /dev/sdb5 /mnt/home 
5. mount /dev/sdb6 /mnt/var
6. mount /dev/sdb7 /mnt/usr
7. chroot /mnt
8. . /etc/profile
9. bash
10. apt-get update
11. apt-get upgrade

Like this I can update my installation from the rescue CD, install or remove packages etc. The only thing I can do is use vi to edit files - wrong terminal type :-(

I hope this helps someone recover from an akward situation.

---

### Post by GLehnhoff on 2007-03-31
The whole Saturday gone, and only because I used the Upgrade-Manager for upgrating my 6.10 Version to 7-point-something.

The upgrade hang. I have done a restart and that was it: Kernel Panik.

**Thanks to Etu who descriped the solution.**

Cheers from sunny Germany - gl

---

### Post by firehead on 2007-04-04
Seriously, i love you guys (in the most platonic way pssible ;-) )!!!

i already saw a whole week of work on my master thesis lost and gone (i know, i should backup more often...) when my notebook suddenly crashed while updating and refused to boot anything afterwards...
but thanks to you guys and the ubuntu-community as such, it's up and running again like a charm!!

just THANK YOU!!!

---

### Post by syruppie on 2007-04-06
> **etu said:**
> Cleaned-up version with some more info:

I just upgraded to Feisty, I had the usual amount of dependency problems in installation but I rebooted the system without solving them all.

So, I got the famous 'Kernel panic - not syncing VFS: Unable to mount root fs on
unknown-block(0,0)'. This applied to all the kernel versions I had in the sytem.

After trying plenty of tricks (including replacing UUID with /dev/hda1 both in GRUB and
fstab) I found out that *all* the initrd-files are wrong. They are all of size 0.

The system booted when I changed initrd to /boot/initrd.img-...dpkg-bak. Luckily the installation had left them behind.

So, in the boot menu, select edit (e) and change initrd to add .dpkg-bak in the end. Then
the system boots.

I think that some kernel package (don't know which) was installed but not configured.
The situation likely solves when I resolve all the conflicts and get all the
packages configured.

This is not very nice behaviour of the system. In the very likely situation that you have
dependency conflicts it makes the system unbootable...

Hi,

so I upgraded to feisty via gksu sh /cdrom/cdromupgrade from the alternative install cd.  I ran into the same problem.  (ie. Kernel panic - not syncing VFS on boot)

I am trying to follow this thread.. but being the linux noob that I am.. there are stuff i can't follow.

1. how did you "replacing UUID with /dev/hda1" ?
2. how did you "changed initrd to /boot/initrd.img-...dpkg-bak"?
3. how did you do this "So, in the boot menu, select edit (e) and change initrd to add .dpkg-bak in the end. Then the system boots." ?

help!

---

### Post by HereInOz on 2007-04-07
I was lucky enough to get a previously installed kernel to boot, just by selecting it in the grub boot menu, then ran sudo apt-get dist-upgrade which told me to run sudo dpkg --configure -a  which I did.

I then ran sudo apt-get dist-upgrade again, and all is well.

---


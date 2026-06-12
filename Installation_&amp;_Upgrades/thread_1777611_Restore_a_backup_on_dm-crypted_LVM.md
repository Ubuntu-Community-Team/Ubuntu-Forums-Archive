---
title: "Restore a backup on dm-crypted LVM"
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by vangop on 2011-06-07
Hi!
I have an encrypted volume, which contains LVM volume group with volumes.
I have unencrypted /boot and the rest is on that encrypted lvm.
I have a backup I want to revert to, but that backup has a different kernel, and I don't know how to update the /boot since I have suspicions that the system won't boot if I just restore / .
I have little experience with luks and LVM, so can you plz help me?
I think I need to run update-initramfs and grub-install at some point..

---

### Post by vangop on 2011-06-08
I think the procedure is the same as if I had a nonencrypted / and a separate /boon partition. And I wanted to restore a / backup - what would I have to do to the /boot then?

---

### Post by Herman on 2011-06-11
I don't think you'll need to do anything special to /boot, just restore your / and then boot and get updates for your operating system as soon as convenient.

I don't think you'll have trouble booting an older operating system with  a newer kernel, but if you do, all you need to do is scroll down your  kernels list in your GRUB Menu at boot time and choose an older kernel.

The initrd.img file that comes with each kernel seems to be most important for booting your encrypted file system. I seem to vaguely remember running some kind of experiment a long time ago that involved deleting the initrd.img for some reason or other, I can't remember now what I was trying to prove. I think I tried replacing it with a copy of another one with the same number but from a different installation to see if it could still decrypt the file system and boot. I couldn't. I can remember chrooting into the encrypted file system to run mkinitrd to make a new initrd.img specific to the encrypted file system to fix it and make the system bootable again. But you won't have that problem.

---

### Post by vangop on 2011-06-11
Thanks for the info, just a final question before I start restoring - I always delete older kernels, just keep latest, so in the backup there will be just kernel X, while /boot is trying to reference kernel Y
The question is:
having ```
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root f80e9aba-3905-4cc4-9826-c1d5f2e3294e
	linux	/vmlinuz-2.6.38-8-generic root=/dev/mapper/vg1-root ro   nosplash nomodeset
	initrd	/initrd.img-2.6.38-8-generic
}

```
in grub.cfg will I be able to boot a system with only older installed(kernel 2.6.36 for example)?

---

### Post by Herman on 2011-06-11
Check your /boot partition and see if there are some files in there with names like initrd.img* and vmlinuz*. The ones called vmlinuz-somenumber are your Linux kernels and the ones called initrd-somenumber will be the matching initial ramdisks that help the kernel get started reading the file system to start booting the operating system. You'll need at least one of each and ideally they should be a matching pair.

There are also some symlinks in the / partition called vmlinuz, vmlinuz.old and initrd.img and initrd.img new, those are not your kernel and initrd.img files, but only symlinks to the real files, (or 'shortcuts' in some people's terminology). 

You haven't mentioned what software or method you used for the backup and I didn't ask, but as long as your backup is good  and the restore process works okay I don't think you have anything to worry about.
Just in case it would be a good idea to have a separate (ordinary) backup of your files, if you don't have one already you should probably make one before restoring your encrypted operating system.

---

### Post by vangop on 2011-06-12
This is /boot
```
drwxr-xr-x  4 root root     1024 2011-06-01 21:28 ./
drwxr-xr-x 22 root root     4096 2011-05-04 14:33 ../
-rw-r--r--  1 root root   730039 2011-04-11 07:24 abi-2.6.38-8-generic
-rw-r--r--  1 root root   130313 2011-04-11 07:24 config-2.6.38-8-generic
drwxr-xr-x  3 root root     8192 2011-06-11 19:09 grub/
-rw-r--r--  1 root root 20034182 2011-06-01 21:28 initrd.img-2.6.38-8-generic
drwx------  2 root root    12288 2010-12-09 17:47 lost+found/
-rw-r--r--  1 root root   160988 2010-10-22 15:08 memtest86+.bin
-rw-r--r--  1 root root   163168 2010-10-22 15:08 memtest86+_multiboot.bin
-rw-------  1 root root  2654256 2011-04-11 07:24 System.map-2.6.38-8-generic
-rw-------  1 root root     1368 2011-04-11 07:26 vmcoreinfo-2.6.38-8-generic
-rw-------  1 root root  4523936 2011-04-11 07:24 vmlinuz-2.6.38-8-generic
```

I was using fsarchiver savefs for backup. Not sure if it's the best way, just seems simple..
I worry that $ sudo dpkg -L linux-image-2.6.38-8-generic lists a whole lot of files/modules that come with kernel, and since I don't have this version installed in /, I'm not sure if the system would boot.. I will backup the /boot now along with current / and then will try to restore. If it fails I hope I can still revert to current backup.

---

### Post by vangop on 2011-06-13
So, just like expected. The OS booted, but drops to terminal.
i cant dpkg-reconf the old kernel since /boot aint has it.
Cant upgrade since cant connect to inet due to missing module.
Plz advise )

---

### Post by Herman on 2011-06-13
What kind of terminal, a busybox prompt?

It's quite common for an operating system that has just been restored from a whole partition backup to need a file system check before it will be bootable. I'm just guessing that might be what you need to do, and anyway it's probably the proper thing to try first.
The file system needs to be clean before we can mount it, and if this doesn't fix it we may need to mount it and chroot into it.

You'll need a Ubuntu Live CD or even better, an auxilliary Ubuntu installation in a USB flash memory stick.

[B]How to run e2fsck on an encrypted LUKS volume
[/B]**1.** This command is to make sure the required software is installed in the operating system which you are using to perform the operation.
Only needed once in a USB or hard-disk installed Ubuntu, but if you have a Live CD you'll need to do this every time.
```
sudo apt-get install lvm2 cryptsetup
```**2.** Use the next command, (below) to probe required module.
You only need to do these two steps if your operating system doesn't have the lvm2 cryptsetup program installed yet. Once it's installed it will still be there ready to use again next time except if you're in a CD, which will forget the changes on reboot. ```
sudo modprobe dm-crypt
```**3**. Look in your 'Places', 'Removable Media' Menu for the iten called something like 'X GB Encrytped' and click on it, you will be asked for the LUKS encryption passphrase.
Ignore the pop-up which will appear to tell you it can't mount the file system, (just close it). 

**4**. Run the following command, it should give you the LV name (name of the logical volume), and a list of other details, pay attention to the LV name,
```
sudo lvdisplay
```for example, the LV Name for one of mine is '[COLOR=Sienna]**/dev/silver-usb/root**[/COLOR]' We will be looking for a name something like that but not identical to that later on to copy and paste into a later command.
[B]
5[/B]. Run 'sudo blkid',
```
sudo blkid
```example output,
> /dev/sda1: UUID="97f5afde-c174-4c1d-8814-a0b495059d3f" TYPE="ext4" 
/dev/sdb1: LABEL="DATA_III" UUID="abd128aa-414d-405b-bd87-ee62ad4f065c" TYPE="ext4" 
/dev/sdc1: LABEL="DATA_1000GB" UUID="fc157c58-069e-4d1b-9613-e4843067f785" TYPE="ext4" 
/dev/sdc2: LABEL="OCZ_SAVER" UUID="eb783d62-e1eb-4f3c-8931-84211444206c" TYPE="ext4" 
/dev/sdc3: LABEL="OCZ_SAVER_II" UUID="cb4e08c2-01b9-4ce6-b6d6-213bd52f8332" TYPE="ext4" 
/dev/sdd1: LABEL="WEBSITE" UUID="a678a230-d764-46f5-b9f3-55be5c1fd207" TYPE="reiserfs" 
/dev/sde1: UUID="728f2eac-d0df-4150-9333-55140167a7c8" TYPE="ext2" 
[COLOR=Black]**/dev/sde5**[/COLOR]: UUID="dd028577-5c83-47da-8bd2-92d5c0599b68" TYPE="[COLOR=Black]**crypto_LUKS**[/COLOR]" 
/dev/mapper/udisks-luks-uuid-dd028577-5c83-47da-8bd2-92d5c0599b68-uid1000: UUID="IFQK7o-arP8-LfLv-10F0-AwUW-q35U-1GeQSm" TYPE="LVM2_member" 
[COLOR=Red]**/dev/mapper/silver--usb-root**[/COLOR]: UUID="80cfa8ca-08ac-4585-bc5f-fdb1f5170da8" TYPE="ext4" 
/dev/mapper/silver--usb-swap_1: UUID="7ffbb2ea-58bc-4951-a46f-643cdabeed22" TYPE="swap" 
In the above command output, the words '[COLOR=Red]**/dev/mapper/silver--usb-root**[/COLOR]' are the ones to copy and use in the command for the file system check, (below).

**6.** Run your file system check,
```
sudo e2fsck -C0 -p -f -v [COLOR=Red]**/dev/mapper/silver--usb-root**[/COLOR]
``` >  232061 inodes used (9.97%)
    1122 non-contiguous files (0.5%)
     438 non-contiguous directories (0.2%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 195733/167
 3241711 blocks used (34.83%)
       0 bad blocks
       1 large file

  164516 regular files
   21012 directories
      57 character device files
      26 block device files
       0 fifos
     429 links
   46436 symbolic links (36063 fast symbolic links)
       5 sockets
--------
  232481 files**7.** I recommend running the resize command as well, as often a restored file system isn't the right size to fill the partition,```
sudo resize2fs -p /dev/mapper/silver--usb-root

``` > resize2fs 1.41.14 (22-Dec-2010)
The filesystem is already 9306112 blocks long.  Nothing to do!**8.** Reboot and try to boot your encrypted operating system again. Hopefully it should boot up now.

---

### Post by vangop on 2011-06-13
Thanks for the reply.
I checked the FS and it was clean. The problem was that all the modules linked to the /boot/new_kernel were not found in the FS. And since I don't know any way to regenerate /boot/vmlinuz /boot/initrd from the kernel that IS installed in /, I was trying to install/reinstall a kernel. This didn't work since I couldn't even get the packages - no inet, unable to use usb flash/cdrom (modules not loaded).
Had to boot from flash and copy the packages to the fs, then reboot into the system and install.
That worked finally :)
Wish there was a simpler way to regenerate the files on /boot from the kernel on /. 
dpkg-reconfigure didn't work for this..

---

### Post by Herman on 2011-06-13
Okay, I'm glad you got it fixed. In all of my operating systems the kernels are in /boot, yours must be different or I'm not understanding properly what you're trying to say. I have symlinks to the kernel and initrd in / but no kernel or initrd. The main thing is you got it fixed anyway. "All's well the ends well". :D

---


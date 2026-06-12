---
title: "Unable to boot since upgrading to kernel 26 - kernel panic"
date: 2023-09-19
forum: Installation &amp; Upgrades
---

### Post by rlgribble on 2023-09-19
I did a brand new install of Ubutu 23.04 on this computer and it was working find - until kernel 6.2.0-26-generic came out (same problem with all later kernels, but kernel 25 still works great).  Since then whenever I boot I get the following (see section begining with DMAR).  Looking at all the information, I'm wondering if somehow the first kernel update (to kernel 26) figured that obviously /dev/sda would be the boot device (after all, a comes before b), especially since it's the SATA 0.0 and that seems to be where the system is looking for the root fs.  However, for all that I have been using Unix/Linux for the last, well, let's stick with "a long time" and not be specific, I've never really researched the boot sequence and so that could be completely wrong.

Any advice on how to fix this would be very much appreciated.

```
DMAR: DRHD: handling fault status reg 2
DMAR: [INTR-REMAP] Request device [f0:1f.0] fault index 0x0 [fault reason 0x25] Blocked a compatibility format interrupt request
x86/cpu: SGX disabled by BIOS.
/dev/root: Can't open blockdev
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
CPU: 0 PID: 1 Comm: swapper/0 Not tainted 6.2.0-32-generic #32-Ubuntu
                                      OR  6.2.0-31-generic #31-Ubuntu
                                      OR  6.2.0-26-generic #26-Ubuntu
Hardware name: Dell Inc. Inspiron 7472/06KVJV, BIOS 1.11.0 03/18/2022
Call Trace:
 <TASK>
 dump_stack_lvl+0x48/0x70
 dump_stack+0x10/0x20
 panic+0x37b/0x3c0
 mount_block_root+0x2c9/0x2d0
 mount_root+0x83/0xb0
 prepare_namespace+0xf5/0x200
 kernel_init_freeable+0x1e5/0x220
 ? __pfx_kernel_init+0x10/0x10
 kernel_init_0x1b/0x200
 ? __pfx_kernel_init+0x10/0x10
 ret_from_fork+0x29/0x50
 </TASK>
Kernel Offset: 0x2a00000 from 0xffffffff81000000 (relocation range: 0xffffffff80000000-0xffffffffbfffffff)
---[ end Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0) ]---
```

Disk configuration info:
Two drives - an SDD (1.28 GiB) for boot, and a 1 TB HDD (for data) (at least that's what I would like it to be)

From the BIOS Configuration:
    ```
SATA 0.0 ST1000LM035-1RK172     => Terabyte HDD, apparently /dev/sda
    SATA 0.2 LITON CV8-8E128-11    => 128 GiB SDD, apparently /dev/sdb
```

From gparted:
```
/dev/sda1, 930.46
Partition    File system     Mount Point     Size         Used             Unused      Flags
---------    ---- ------     ----- -----     ----         ----             ------      -----
/dev/sda2    fat32                             1.05 GiB                                boot, esp
    /dev/sda1    ext4            /home           930.46 GiB   178.40 GiB       752.06 GiB
    Unallocated                                    1.71 MiB

/dev/sdb2, 118.19 GiB
Partition    File system     Mount Point     Size         Used             Unused      Flags
---------    ---- ------     ----- -----     ----         ----             ------      -----
/dev/sdb1    fat 32                            1.05 GiB   11.59 MiB          1.04 GiB  boot, esp
    /dev/sdb2    ext4            /,/var/snap...  118.19 GiB   24.02 GiB         94.17 GiB
    unallocated                                    1.34 MiB
```

---

### Post by MAFoElffen on 2023-09-19
Could you, while booted from that earlier kernel, please run the [UbuntuForums 'system-info' Script]("https://github.com/UbuntuForums/system-info") and post the URL where the report uploads to?

DMAR is Direct Memory Access remapping. DMAR error usually are related to kernel, BIOS, APCI, and/or graphics drivers. I would like to see what the hardware info is and what drivers are loaded for it.

---

### Post by rlgribble on 2023-09-19
Certainly:  [https://paste.ubuntu.com/p/yzDYsbf6fj/](https://paste.ubuntu.com/p/yzDYsbf6fj/)

I have tried various versions of the NVIDIA drivers (that's a popular recommendation) without success (at least with respect to this problem - they have fixed other issues).  Currently using 535.86.05.


Thanks for the help,

Richard.

---

### Post by MAFoElffen on 2023-09-19
Your BIOS version is up to date...

Could you please do this:
```

sudo dmesg | grep -i -e IOMMU -e 'DMAR' -e 'adding to'

```
But when you go to post the output to a post, please use "Adv Reply" to use the Advanced Editor, with the expanded toolbar. Select the "#" Icon and paste the output between the inserted CODE Tags. This is important, as commands and raw output is only supposed to be post within CODE Tags.

It's a Forum Policy...

Then go back to your first post, select "Edit Post" > "Advanced Editor"... Select your output with your mouse to highlight it. Then Select the "#" Icon to wrap the highlighted output with Code Tags. The save. That should keep you out of trouble with the Moderators.

---

### Post by rlgribble on 2023-09-20
Ran the command - no output.  dmesg returns quite a bit (as I'm sure was expected), but grep doesn't find anything.

Thanks for the advice on the tags - I'll remember that in the future.

---

### Post by MAFoElffen on 2023-09-20
(Statement) It doesn't get that error with the booted kernel does it... But you posted records of those errors(???), they should be in the logs...

Boot to the Grub2 Menu, and press the <E> key. while o the latest kernel menu item. <arrow-down> to the line that starts with the word "linux'. <Arrow-Right> until the words "quiet splash". Delete the word "quiet" after the word "splash", add "iommu=off". press the keys <Cntrl><X> to boot.

See if it boots. Watch the boot messages during boot for errors.

---

### Post by rlgribble on 2023-09-20
Good morning!

I didn't think I knew how to get to the grub menu - turns out I just didn't know what it was.

So, went in as requested and deleted the word "splash" (which was before the word "quiet" - I don't think that matters, but just in case...

I also looked at the 'linux' line in the file for the one that works.  Here are the differences (the 'echo' and 'initrd' lines are not in the 33 version):

```
linux /boot/vmlinuz-6.2.0-33-generic root=/dev/scb2 ro quiet splash $vt.handoff

linux /boot/vmlinuz-6.2.0-25-generic root=UUID=[[:digit:]]{8}-[[:xdigit:]]{4}-[[:digit:]]{4}-[[:xdigit:]]{4}-[[:xdigit:]]{12} ro quiet splash $vt_handoff
echo 'Loading initial ramdisk... '
initrd /boot/initrd.img-6.2.0-25-generic
```

I didn't get the entire output while booting (it scrolls amazingly fast), but here's the last screen of it (I typed this in by hand from a picture so there may be typos in it):
```
...
zswap: loaded using pool izo/zbud
ACPI: battery: Slot [BAT0] (battery present)
Key type .fscrypt registered
Key type fscrypt-provisioning registered
Key type encrypted registered
AppArmor: AppArmor sha1 policy hashing enabled
integrity: Loading X.509 certificate: UEFI:db
integrity: Loaded X.509 cert 'Dell Inc. UEFI DB: <string of hex>'
integrity: Loading X.509 certificate: UEFI:db
integrity: Loaded X.509 cert 'Microsoft Corporation UEFI CA 2011: <string of hex>'
integrity: Loading X.509 certificate: UEFI:db
integrity: Loaded X.509 cert 'Microsoft Windows Production PCA 2011: <string of hex>'
integrity: Revoking X.509 certificate: UEFI:dbx
blacklist: Revoked X.509 cert 'Microsoft Windows PCA 2010: <string of hex>'
integrity: Loading X.509 certificate: UEFI: MokListRT (MOKvar table)
integrity: Loaded X.509 cert 'Canonical Ltd. Master Certificate Authority: <string of hex>'
integrity: Loading X.509 certificate: UEFI: MokListRT (MOKvar table)
integrity: Loaded X.509 cert 'ubuntu Secure Boot Module Signature key: <string of hex>'
integrity: Loading X.509 certificate: UEFI: MokListRT (MOKvar table)
integrity: Loaded X.509 cert 'ubuntu Secure Boot Module Signature key: <string of hex>' (different from the one two lines ago)
ima: No TPM chip found, activating TPM-bypass!
Loading compiled-in module X-509 certificates
Loaded X.509 cert 'Build time autogenerated kernel key: <string of hex>'
ima: Alloated hash algorithm: sha1
evm: Initialising EVM extended attributes:
audit: type=1807 audit(1695219869.527:2): action=measure func=KEXEC_KERNEL_CHECK res=1
evm: security.selinux
evm: security.SMACK64
audit: type=1807 audit(1695219869.527:3): action=measure func=MODULE_CHECK res=1
evm: security.SMACK64EXEC
evm: security.SMACK64TRANSMUTE
evm: security.SMACK64MMAP
evm: security.apparmor
evm: security.ima
evm: security.capability
evm: HMAC attrs: 0x1
PM:   Magic number: [[:digit:]]:[[:digit:]]{3}:[[:digit:]]{3}
RAS: Correctable Errors collector initialized.
Lockdown: swapper/0: hibernation is restricted; see man kernel_lockdown.7
md: Waiting for all devices to be available before autodetect
md: If you don't use raid, use raid=noautodetect
md: Autodetecting RAID arrays
md: autorun ...
md: ... autorun DONE.
/dev/root: Can't open blockdev
VFS: Cannot open root device "sb2" or unknown-block(0,0): error -6
Please append a correct "root=" boot option; here are the available partitions: 
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
CPU 4: PID: 1 Comm: swapper/0 Not tainted 6.2.0-33-generic #31-Ubuntu
Hardware name: Dell Inc Inspiron 7472/06KVJV, BIOS 1.11.0 03/18/2022
Call Trace:
 <TASK>
 dump_stack_lvl+0x48/0x70
 dump_stack+0x10/0x20
 panic+0x37b/0x3c0
 mount_block_root+0x2c9/0x2d0
 mount_root+0x83/0xb0
 prepare_namespace+0xf5/0x200
 kernel_init_freeable+0x1e5/0x220
 ? __pfx_kernel_init+0x10/0x10
 kernel_init_0x1b/0x200
 ? __pfx_kernel_init+0x10/0x10
 ret_from_fork+0x29/0x50
 </TASK>
Kernel Offset: 0x2a00000 from 0xffffffff81000000 (relocation range: 0xffffffff80000000-0xffffffffbfffffff)
---[ end Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0) ]---
```

It seems strange to me that there are Microsoft Windows certificates in there at all - this is not a dual-boot computer and, while Windows came with it, I would have thought the Ubuntu install would have wiped it out.

---

### Post by MAFoElffen on 2023-09-20
The installer leaves the Windows EFI files and installs it's own. That way if the user has Windows on it, it doesn't mess it up. (Unlike the Windows installer...)

This is what is really says???
> **rlgribble said:**
> 
I also looked at the 'linux' line in the file  for the one that works.  Here are the differences (the 'echo' and  'initrd' lines are not in the 33 version):
```

linux /boot/vmlinuz-6.2.0-33-generic root=[COLOR=#ff0000]/dev/**scb2** [/COLOR]ro quiet splash $vt.handoff

linux /boot/vmlinuz-6.2.0-25-generic root=UUID=[COLOR=#ff0000][[:digit:]]{8}-[[:xdigit:]]{4}-[[:digit:]]{4}-[[:xdigit:]]{4}-[[:xdigit:]]{12}[/COLOR] ro quiet splash $vt_handoff
echo 'Loading initial ramdisk... '
initrd /boot/initrd.img-6.2.0-25-generic
```

First off "root=/dev/scb2 is invalid for identifying a storage device's partition... And that is not a valid UUID on the line following that.

On lines #512-513 of your system-info report, it says:
```

The Linux Kernel Command Line use to boot was: 
BOOT_IMAGE=/boot/vmlinuz-6.2.0-25-generic root=UUID=79433039-c6d0-4545-bf07-76227e4b6984 ro quiet splash

```
On line #191, that UUID matches up with /dev/sdb2
```

|_sdb2       0 8abff0ab-3d6a-2c46-96ff-c7f3156d4442 79433039-c6d0-4545-bf07-76227e4b6984

```
Further down in your output, it said
```

VFS: Cannot open root device "sb2" or unknown-block(0,0): error -6

```
Which is also not /dev/sdb2... I can see in Line #181 that /dev/sdb2 is your root partition for your installation. 

Can you confirm that by looking at /boot/grub.cfg? 

That is a temporary file that is generated by grub, during the installation, and later on when the user updates grub... From what you posted, that seems to have invalid references...

---

### Post by rlgribble on 2023-09-20
My apologies - the "scb2" should be "sdb2," as should the "sdb2"; my apologies for the typo (I really did try to proofread it).  The UUID number you cite is the one in the file - I just didn't want to type the whole thing in.  So I think those are probably OK.

I find five "linux" entries in grub.cfg:
```
118:	linux	/boot/vmlinuz-6.2.0-33-generic root=/dev/sdb2 ro  quiet splash $vt_handoff
187:		linux	/boot/vmlinuz-6.2.0-33-generic root=/dev/sdb2 ro  quiet splash $vt_handoff
203:		linux	/boot/vmlinuz-6.2.0-33-generic root=/dev/sdb2 ro recovery nomodeset dis_ucode_ldr 
220:		linux	/boot/vmlinuz-6.2.0-25-generic root=UUID=79433039-c6d0-4545-bf07-76227e4b6984 ro  quiet splash $vt_handoff
238:		linux	/boot/vmlinuz-6.2.0-25-generic root=UUID=79433039-c6d0-4545-bf07-76227e4b6984 ro recovery nomodeset dis_ucode_ldr 
```

Is that what you were looking for?

These seem to correspond with the options I have on the grub menu when I select "Advanced options for ubuntu"

---

### Post by MAFoElffen on 2023-09-20
> **rlgribble said:**
> I find five "linux" entries in grub.cfg:
```
118:    linux    /boot/vmlinuz-6.2.0-33-generic root=/dev/sdb2 ro  quiet splash $vt_handoff
187:        linux    /boot/vmlinuz-6.2.0-33-generic root=/dev/sdb2 ro  quiet splash $vt_handoff
203:        linux    /boot/vmlinuz-6.2.0-33-generic root=/dev/sdb2 ro recovery nomodeset dis_ucode_ldr 
220:        linux    /boot/vmlinuz-6.2.0-25-generic root=UUID=79433039-c6d0-4545-bf07-76227e4b6984 ro  quiet splash $vt_handoff
238:        linux    /boot/vmlinuz-6.2.0-25-generic root=UUID=79433039-c6d0-4545-bf07-76227e4b6984 ro recovery nomodeset dis_ucode_ldr 
```

Is that what you were looking for?

Yes. It is strange that the options for Kernel 6.2.0-25 have root=UUID= options, and boot. And the options for 6.2.0-33 have root=/dev/sdb2 and do not work. Using root=/dev/XXX is discouraged, just like it is in /etc/fstab files, as those can change on boots, so instead, it is recommended that we use UUID's.

I'm wondering... You can boot from Kernel 6.2.0-25 and do
```

sudo update-grub

```
Which will update that file. Then check it again, ad see it the 'root=' references are still the same, or if changed to UUID's for 6.2.0-33. If it does, win. If not, no foal.

---

### Post by rlgribble on 2023-09-20
I think we're going with the "no foul" option...

```
169:	linux	/boot/vmlinuz-6.2.0-33-generic root=/dev/sdb2 ro  quiet splash $vt_handoff
187:		linux	/boot/vmlinuz-6.2.0-33-generic root=/dev/sdb2 ro  quiet splash $vt_handoff
203:		linux	/boot/vmlinuz-6.2.0-33-generic root=/dev/sdb2 ro recovery nomodeset dis_ucode_ldr 
220:		linux	/boot/vmlinuz-6.2.0-25-generic root=UUID=79433039-c6d0-4545-bf07-76227e4b6984 ro  quiet splash $vt_handoff
238:		linux	/boot/vmlinuz-6.2.0-25-generic root=UUID=79433039-c6d0-4545-bf07-76227e4b6984 ro recovery nomodeset dis_ucode_ldr 
```

Is it possible to add another option to the grub menu?  If so, would it be useful to copy the 33 entry and change to the UUID instead of /dev/sdb2?  (And is there a way to comment out lines when editing from the grub menu?)

Another question - it appears that /dev/sdb1 is the boot partition; gparted shows mounting to /boot/efi and using the "boot" and "esp" flags.  Then again, the UUID in the files and output would appear to be associated with sdb2 (based on output from 'ls -l /dev/disk/by-uuid') so maybe not.

BTW, thanks for your time.  This has been bothering me for a while now and I'm glad to have someone helping to fix it.

---

### Post by ubfan1 on 2023-09-20
You can copy your boot paragraph to the bottom of /etc/grub/40_custom and change the root= to the UUID. then run sudo update-grub again to update the /boot/grub/grub.cfg file with the additional boot choice.  Another debug approach is to add a set -vx to the top of the 10_linux to see how that line with the odd root= gets built.

---

### Post by MAFoElffen on 2023-09-20
+1 -- On copying the first menu section from grub.cfg to 40_custom, and making this line match to this:
```

linux    /boot/vmlinuz-6.2.0-33-generic root=UUID=79433039-c6d0-4545-bf07-76227e4b6984 ro  quiet splash $vt_handoff

```
Curious to see how that goes...

Either way (if that lets it boot on that kernel, or not), I would report it to launchpad, filed against package  'grub-pc' as a bug. It should not do this.

---

### Post by rlgribble on 2023-09-27
Sorry it's taken me so long - I had some other commitments.

I *think* I did it right - my entry is the one that begins "Ubuntu, test Linux 6.2.0-33..."  (see snippet from grub.cfg file):

```
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-79433039-c6d0-4545-bf07-76227e4b6984' {
	menuentry 'Ubuntu, with Linux 6.2.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-6.2.0-33-generic-advanced-79433039-c6d0-4545-bf07-76227e4b6984' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  79433039-c6d0-4545-bf07-76227e4b6984
		else
		  search --no-floppy --fs-uuid --set=root 79433039-c6d0-4545-bf07-76227e4b6984
		fi
		echo	'Loading Linux 6.2.0-33-generic ...'
		linux	/boot/vmlinuz-6.2.0-33-generic root=/dev/sdb2 ro  quiet splash $vt_handoff
	}
	menuentry 'Ubuntu, test Linux 6.2.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-6.2.0-33-generic-advanced-79433039-c6d0-4545-bf07-76227e4b6984' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  79433039-c6d0-4545-bf07-76227e4b6984
		else
		  search --no-floppy --fs-uuid --set=root 79433039-c6d0-4545-bf07-76227e4b6984
		fi
		echo	'Loading Linux 6.2.0-33-generic ...'
		linux	/boot/vmlinuz-6.2.0-33-generic root=UUID=79433039-c6d0-4545-bf07-76227e4b6984 ro  quiet splash $vt_handoff
	}
	menuentry 'Ubuntu, with Linux 6.2.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-6.2.0-33-generic-recovery-79433039-c6d0-4545-bf07-76227e4b6984' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  79433039-c6d0-4545-bf07-76227e4b6984
		else
		  search --no-floppy --fs-uuid --set=root 79433039-c6d0-4545-bf07-76227e4b6984
		fi
		echo	'Loading Linux 6.2.0-33-generic ...'
		linux	/boot/vmlinuz-6.2.0-33-generic root=/dev/sdb2 ro recovery nomodeset dis_ucode_ldr 
	}
```

What I did was to copy the last line from the -25 kernel and chang it to -33.  Same kernel panic as before.

---

### Post by rlgribble on 2023-10-04
Just updated the kernel to v. 34; same problem.  Anyone have any ideas?

---

### Post by ubfan1 on 2023-10-04
My virtual machine 23.04 does have the "initrd" line that you are missing.  Try adding that: initrd /boot/initrd.img-6.0.2-33-generic)

---

### Post by rlgribble on 2023-10-07
Thanks for the suggestion.  My grub.cfg file now contains:
	```
	echo	'Loading Linux 6.2.0-34-generic ...'
		linux	/boot/vmlinuz-6.2.0-34-generic root=/dev/sdb2 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-6.2.0-34-generic
```

 and I get the error:  ```
error: file'/boot/initrd.img-6.2.0-34-generic' not found.
```

The idea that there is a ramdisk at all reminded me that I have two drives in this computer (it's old, but runs Linux better than a new one I bought):  The boot drive is an SSD, /dev/sdb and the "data" drive 9s a regular HDD, /dev/sda.  I don't know if that makes a difference or not, but thought I would add the information.

---

### Post by MAFoElffen on 2023-10-07
Here is mine:
```

mafoelffen@Mikes-ThinkPad-T520:~$ ls -lah /boot
total 425M
drwxr-xr-x  4 root root   23 Oct  2 00:39 .
drwxr-xr-x 25 root root   32 Jul 25 15:36 ..
-rw-r--r--  1 root root 256K Sep  5 06:31 config-5.15.0-84-generic
-rw-r--r--  1 root root 270K Aug 18 02:38 config-6.2.0-32-generic
-rw-r--r--  1 root root 270K Sep  7 00:11 config-6.2.0-33-generic
drwx------  5 root root 4.0K Dec 31  1969 efi
drwx------  5 root root 4.0K Oct  2 00:40 grub
lrwxrwxrwx  1 root root   28 Sep 23 00:54 initrd.img -> initrd.img-5.15.0-84-generic
-rw-r--r--  1 root root 119M Sep 23 00:55 initrd.img-5.15.0-84-generic
-rw-r--r--  1 root root 131M Sep 17 18:45 initrd.img-6.2.0-32-generic
-rw-r--r--  1 root root 131M Oct  2 00:39 initrd.img-6.2.0-33-generic
lrwxrwxrwx  1 root root   27 Oct  2 00:38 initrd.img.old -> initrd.img-6.2.0-33-generic
-rw-r--r--  1 root root 179K Feb  6  2022 memtest86+.bin
-rw-r--r--  1 root root 181K Feb  6  2022 memtest86+.elf
-rw-r--r--  1 root root 181K Feb  6  2022 memtest86+_multiboot.bin
-rw-------  1 root root 6.0M Sep  5 06:31 System.map-5.15.0-84-generic
-rw-------  1 root root 7.6M Aug 18 02:38 System.map-6.2.0-32-generic
-rw-------  1 root root 7.7M Sep  7 00:11 System.map-6.2.0-33-generic
lrwxrwxrwx  1 root root   25 Sep 23 00:54 vmlinuz -> vmlinuz-5.15.0-84-generic
-rw-------  1 root root  12M Sep  5 09:57 vmlinuz-5.15.0-84-generic
-rw-------  1 root root  14M Aug 18 02:40 vmlinuz-6.2.0-32-generic
-rw-------  1 root root  14M Sep  7 01:18 vmlinuz-6.2.0-33-generic
lrwxrwxrwx  1 root root   24 Sep 23 00:54 vmlinuz.old -> vmlinuz-6.2.0-33-generic

```
It looks like the intramfs images are not being built on yours. That process should be automatic when you get a new kernel update(?)

Let's see the output of this
```

sudo update-initramfs -c -k all

```
If that gets an error then lets also see
```

apt list initramfs-tools --installed

```

---

### Post by rlgribble on 2023-10-12
```
sudo update-initramfs -c -k all
```

Gives no output at all.

```
apt list initramfs-tools --installed
```

Gives the following:

```
WARNING:  apt does not have a stable CLI interface.  Use with caution in scripts.


Listing...
W: Unable to read /etc/apt/sources.list - open (13: Permission denied)
```

A listing of /etc/apt/sources.list shows:
```
-rw-r----- 1 root adm 58 Sep 19 16:34 /etc/apt/sources.list
```

Using sudo to run the command returns the same thing (minus the warning about the permissions on the file).

---

### Post by ubfan1 on 2023-10-12
Permission/group ownership problem on that file, and who knows how many others.  Mine is 
-rw-rw-r-- 1 root root 2817 Oct 19  2022 /etc/apt/sources.list

---

### Post by rlgribble on 2023-10-12
Interesting - that's the only file with group "adm" in that directory.  Fixed group and set permissions to 660.

Changed that; file contents are very simple:
```
# deb [check-date=no] file:///cdrom lunar main restricted
```

---

### Post by MAFoElffen on 2023-10-12
Wow....
```

sudo chown root:root /etc/apt/sources.list
sudo chmod 664 /etc/apt/sources.list

```
Then try again.

---

### Post by rlgribble on 2023-10-13
update-initramfs -c -k all gives no output

apt initramfs-tools --installed gives the following (other than the CLI warning):
```
initramfs-tools/lunar-updates,now 0.142ubuntu2.2 all [installed,automatic]
```

---

### Post by MAFoElffen on 2023-10-13
The update-initramfs command should have produce some kind of output, even if that putput was an error on not running.

Let's do this to see what is going on there...
```

sudo update-initramfs -c -k all -v 2>1 > $HOME/Documents/intramfs-log.txt

```
Attach that text file as an attachment to a post.

---

### Post by rlgribble on 2023-10-15
Ran the command:

```
<hostname>:~->sudo update-initramfs -c -k all -v 2>1 > intramfs-log.txt
[sudo] password for <user>: 
<hostname>:~->cat intramfs-log.txt 
<hostname>:~->ll intramfs-log.txt 
-rw------- 1 0 Oct 15 10:17 intramfs-log.txt
```

(I've aliased "ll" to "ls -lF -o -g")

Uploading the file failed with a question about whether or not it was too large.  Maybe the system doesn't like empty files?

---

### Post by MAFoElffen on 2023-10-15
So it is empty? No output at all?

Hmmmm.... What is you reinstall that
```

sudo apt update
sudo apt install --reinstall live-tools initramfs-tools
sudo apt update-intramfs -c -k all

```

---

### Post by rlgribble on 2023-10-16
Well, this might be the problem.  It seems there is a conflict in how initramfs-tools is set up.
```
<hostname>:~->sudo apt install --reinstall live-tools initramfs-tools
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gnome-browser-connector libnvidia-egl-wayland1
Use 'sudo apt autoremove' to remove them.
Suggested packages:
  debian-installer-launcher
The following NEW packages will be installed:
  live-tools
0 upgraded, 1 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 35.4 kB of archives.
After this operation, 108 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu lunar-updates/main amd64 initramfs-tools all 0.142ubuntu2.2 [9080 B]
Get:2 http://us.archive.ubuntu.com/ubuntu lunar/universe amd64 live-tools all 1:20190831.1 [26.3 kB]
Fetched 35.4 kB in 15s (2315 B/s)    
(Reading database ... 216267 files and directories currently installed.)
Preparing to unpack .../initramfs-tools_0.142ubuntu2.2_all.deb ...
Unpacking initramfs-tools (0.142ubuntu2.2) over (0.142ubuntu2.2) ...
Selecting previously unselected package live-tools.
Preparing to unpack .../live-tools_1%3a20190831.1_all.deb ...
dpkg-divert: error: 'diversion of /usr/sbin/update-initramfs to /usr/sbin/update
-initramfs.orig.initramfs-tools by live-tools' clashes with 'local diversion of 
/usr/sbin/update-initramfs to /usr/sbin/update-initramfs.curtin-disabled'
dpkg: error processing archive /var/cache/apt/archives/live-tools_1%3a20190831.1
_all.deb (--unpack):
 new live-tools package pre-installation script subprocess returned error exit s
tatus 2
Errors were encountered while processing:
 /var/cache/apt/archives/live-tools_1%3a20190831.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
<hostname>:~->sudo apt update-initramfs -c -k all
E: Option -c requires an argument.
```

---

### Post by MAFoElffen on 2023-10-16
Hmmm...When I saw provided by 'live-tools', I went back in my history, and that was from the man page for update-initramfs for xenial, where that packge depends on initramfs-tools... 

For jammy, in that release version of the man page, 'the provided by:' changed to straight from package initramfs-tools, without live-tools... So you can remove that package, as you do not need that... But doing that did uncover the error that is affecting you:
```

dpkg: error processing archive /var/cache/apt/archives/live-tools_1%3a20190831.1
_all.deb (--unpack):
 new live-tools package pre-installation script subprocess returned error exit s
tatus 2
Errors were encountered while processing:
 /var/cache/apt/archives/live-tools_1%3a20190831.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
<hostname>:~->sudo apt update-initramfs -c -k all
E: Option -c requires an argument.

```
RE: [Ubuntu Man Page-- update-initramfs (jammy/22.04)]("https://manpages.ubuntu.com/manpages/jammy/man8/update-initramfs.8.html")
```

       -k  version
              Set  the  specific  kernel  version  for whom the initramfs will be generated.  For
              example the output of uname -r for your currently running kernel.  This argument is
              optional for update. The default is the latest kernel version.

              The  use  of  "all"  for  the version string specifies that update-initramfs should
              operate on all installed kernel versions (with -c),  or  on  all  installed  kernel
              versions that already have an initramfs (with -d or -u).

       -c     This mode creates a new initramfs.

```
From the error, that said "-c" needs and thinks it is missing an argument... but you can see by the Doc's that "-k all" is the valid argument for that.

The initramfs-tools package is confirmed as being broken. That confirms why the images where not being generated on your system...

But... dpkg depends on it a utility inside the package to be working to reinstall it??? That doesn't make any logical sense. That would be a lose-lose goose chase.

Please try:
```

sudo apt remove --purge live-tools
sudo apt install --reinstall initramfs-tools 

```
Maybe that error is just the case for installing live-tools, and why that depends on initramfs-tools... Crossing fingers for you.

---

### Post by rlgribble on 2023-10-16
Got rid of live-tools
Reinstalled initramfs-tools
Ran sudo initramfs-tools -c -k 6.2.0-34-generic (which worked - apparently it's the "all" option that doesn't); no output
Rebooted - same problem

---

### Post by #&amp;thj^% on 2023-10-16
Dang this one can be a real deal breaker so if your interested and have good back-ups in place, may I suggest something like:
1st is.
```
 sudo apt autoremove
```
you've already cleaned so if that don't work then: (ONE Line at a time)
```
cd ~
mkdir initramfs
cd initramfs
sudo cp -a /boot .
cd boot
sudo update-initramfs -ut -b .
sudo cp -a * /boot
sudo apt-get autoremove
```
That will either work or blow your system up. (Choose wisely)

---

### Post by rlgribble on 2023-10-16
Oh that's encouraging - reminds me of the EOD motto:  "Initial success, or total failure."

Fingers crossed...

---

### Post by rlgribble on 2023-10-16
Oh that's encouraging - reminds me of the EOD motto:  "Initial success, or total failure."

Fingers crossed...

---

### Post by #&amp;thj^% on 2023-10-16
> **rlgribble said:**
> Oh that's encouraging - reminds me of the EOD motto:  "Initial success, or total failure."

Fingers crossed...
:lolflag:
Mine are as well....Good Luck!

---

### Post by rlgribble on 2023-10-16
OK, I don't know how the double post happened - but that had no effect on the system.

---

### Post by MAFoElffen on 2023-10-16
LOL... And I had just posted (somewhere else) one of my old sayings:
*"Don't worry... I saw this work in a cartoon once."*

---

### Post by #&amp;thj^% on 2023-10-16
> **MAFoElffen said:**
> LOL... And I had just posted (somewhere else) one of my old sayings:
*"Don't worry... I saw this work in a cartoon once."*

If you remember a couple of months back on my zfs system it worked a treat...but I am pretty animated. :popcorn:

---

### Post by MAFoElffen on 2023-10-16
LOL! I was going to go on, but will save it for laters... :wink:

---

### Post by rlgribble on 2023-10-16
Meanwhile back at the ranch...

I'm guessing the consensus is that kernel 34 doesn't have a ram disk and we're trying to create one, correct?  Any other suggestions on how-to?

---

### Post by MAFoElffen on 2023-10-16
Well you need a working 'update-intramfs' utility to do that.

This started out 3 weeks ago as a new fresh installation 23.04 that worked until you got an update.

*** I think, since we cannot get a core kernel utility to work, even after reinstalling it, it time to pull it off life support,do a backup of your data, reinstall fresh, and restore your data.

---

### Post by rlgribble on 2023-10-16
Sigh.  Well, must needs and all that.

---


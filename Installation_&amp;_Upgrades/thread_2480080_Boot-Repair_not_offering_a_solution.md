---
title: "Boot-Repair not offering a solution"
date: 2022-10-18
forum: Installation &amp; Upgrades
---

### Post by bishoptf on 2022-10-18
I have a pretty simple VM, ubuntu server which is pretty minimal but we had a power outage and its not booting. I do back up the VM's and I should be able to restore the VM but I've never had it where boot-repair ISO doesnt work. Here is the output, I do not see what the main issue is as to why its not offering a solution but thought I would post and see what others thought:
```

boot-repair-4ppa200                                              [20221018_1301]

============================== Boot Info Summary ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 


================================ 0 OS detected =================================


================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: SVGA II Adapter from VMware
Live-session OS is Ubuntu 64-bit (Boot-Repair-Disk 64bit 20200604, bionic, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 6.00 from Phoenix Technologies LTD
This live-session is in Legacy/BIOS/CSM mode (not in EFI mode).



============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda	: notGPT,	no-BIOSboot,	has-noESP, 	not-usb,	not-mmc, no-os,	no-wind,	2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far

Partitions info (2/3): _________________________________________________________

sda1	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot

Partitions info (3/3): _________________________________________________________

sda1	: maybesepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 70 GiB, 75161927680 bytes, 146800640 sectors
Disk identifier: 0x31684276
      Boot     Start       End   Sectors Size Id Type
sda1  *         2048 142606335 142604288  68G 83 Linux
sda2       142606336 146800639   4194304   2G 82 Linux swap / Solaris
Disk zram0: 1.9 GiB, 2063790080 bytes, 503855 sectors

parted -lm (filtered): _________________________________________________________

sda:75.2GB:scsi:512:512:msdos:VMware Virtual disk:;
1:1049kB:73.0GB:73.0GB:::boot;
2:73.0GB:75.2GB:2147MB:linux-swap(v1)::;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                  PARTLABEL
sda                                                                                                              
&#9500;&#9472;sda1                                               31684276-01                                                 
&#9492;&#9472;sda2 swap     2d5bcded-2d36-48e1-b27a-c3c5606fc853 31684276-02                                                 

Mount points (filtered): _______________________________________________________

             Avail Use% Mounted on

Mount options (filtered): ______________________________________________________


======================== Unknown MBRs/Boot Sectors/etc =========================

Unknown BootLoader on sda1

00000000  03 00 06 00 0c 00 01 02  2e 00 00 00 02 00 00 00  |................|
00000010  0c 00 02 02 2e 2e 00 00  9e 06 14 00 14 00 09 02  |................|
00000020  56 4d 77 61 72 65 44 6e  44 4f 70 55 9f 06 14 00  |VMwareDnDOpU....|
00000030  14 00 09 02 2e 58 31 31  2d 75 6e 69 78 6f 32 33  |.....X11-unixo23|
00000040  a0 06 14 00 14 00 09 02  2e 49 43 45 2d 75 6e 69  |.........ICE-uni|
00000050  78 4a 43 66 a1 06 14 00  14 00 09 02 2e 58 49 4d  |xJCf.........XIM|
00000060  2d 75 6e 69 78 78 74 61  a2 06 14 00 14 00 0a 02  |-unixxta........|
00000070  2e 66 6f 6e 74 2d 75 6e  69 78 70 2e a3 06 14 00  |.font-unixp.....|
00000080  14 00 0a 02 2e 54 65 73  74 2d 75 6e 69 78 2d 69  |.....Test-unix-i|
00000090  a4 06 14 00 58 00 50 02  73 79 73 74 65 6d 64 2d  |....X.P.systemd-|
000000a0  70 72 69 76 61 74 65 2d  63 62 65 34 62 31 30 38  |private-cbe4b108|
000000b0  39 31 66 35 34 38 66 65  38 30 64 33 37 38 35 39  |91f548fe80d37859|
000000c0  31 36 37 39 64 36 32 30  2d 73 79 73 74 65 6d 64  |1679d620-systemd|
000000d0  2d 72 65 73 6f 6c 76 65  64 2e 73 65 72 76 69 63  |-resolved.servic|
000000e0  65 2d 50 4c 6c 78 59 69  a8 06 14 00 54 00 4c 02  |e-PLlxYi....T.L.|
000000f0  73 79 73 74 65 6d 64 2d  70 72 69 76 61 74 65 2d  |systemd-private-|
00000100  63 62 65 34 62 31 30 38  39 31 66 35 34 38 66 65  |cbe4b10891f548fe|
00000110  38 30 64 33 37 38 35 39  31 36 37 39 64 36 32 30  |80d378591679d620|
00000120  2d 4d 6f 64 65 6d 4d 61  6e 61 67 65 72 2e 73 65  |-ModemManager.se|
00000130  72 76 69 63 65 2d 70 6d  79 76 55 69 ac 06 14 00  |rvice-pmyvUi....|
00000140  58 00 4e 02 73 79 73 74  65 6d 64 2d 70 72 69 76  |X.N.systemd-priv|
00000150  61 74 65 2d 63 62 65 34  62 31 30 38 39 31 66 35  |ate-cbe4b10891f5|
00000160  34 38 66 65 38 30 64 33  37 38 35 39 31 36 37 39  |48fe80d378591679|
00000170  64 36 32 30 2d 73 79 73  74 65 6d 64 2d 6c 6f 67  |d620-systemd-log|
00000180  69 6e 64 2e 73 65 72 76  69 63 65 2d 41 58 55 46  |ind.service-AXUF|
00000190  7a 69 71 4b bd 06 14 00  24 00 1a 02 2e 75 6e 69  |ziqK....$....uni|
000001a0  66 69 2d 32 35 33 30 31  35 35 30 34 33 36 34 34  |fi-2530155043644|
000001b0  36 33 32 33 36 34 56 66  9e 01 06 00 38 00 0c 01  |632364Vf....8...|
000001c0  31 30 37 31 2e 6a 73 76  63 5f 75 70 12 02 06 00  |1071.jsvc_up....|
000001d0  24 00 0a 01 49 58 5f 79  42 53 54 59 72 76 62 64  |$...IX_yBSTYrvbd|
000001e0  34 61 73 73 61 67 65 2e  6b 66 6e 62 4e 39 6a 73  |4assage.kfnbN9js|
000001f0  b4 06 14 00 38 00 19 02  76 6d 77 61 72 65 2d 72  |....8...vmware-r|
00000200




Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would not act on the boot.

```

---

### Post by TheFu on 2022-10-18
For a few years now, boot-repair hasn't been able to repair many types of issues.  Count yourself as lucky.

About a year ago, the boot-repair team started an update cycle and has been working to handle more and more situations, but they will never handle them all, since we can customize our setups massively.  I don't know if they considered handling virtual machine boot issues or not.

The boot-info report looks very odd to me, but I haven't used anything from VMware in about 12 yrs.

The information that the boot-repair tool gathers is extremely useful. We've counted on that data for a long time to help people resolve booting issues.  

The Ubuntu Forums System Information tool gathers similar, but much more information.  [https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info) . A group of long-time forum contributors/moderators has been working on that tool for over a year with MAFoElffen doing 99.9% of the coding. It is a good tool trying not to be ubuntu specific.

Boot-repair is a separate project from Ubuntu.  If you like, you can open a bug through Landscape and it should get to the boot-repair team.

I don't have any recommendations to get it booting. Sorry.

---

### Post by tea for one on 2022-10-18
0 (zero) OS detected.
It looks like the power outage did irreparable damage.
As you have a backup, now is a perfect time to test it.

---

### Post by bishoptf on 2022-10-18
> **tea for one said:**
> 0 (zero) OS detected.
It looks like the power outage did irreparable damage.
As you have a backup, now is a perfect time to test it.

Yeah that is the odd one, the UPS when it starts to run low, connects to the vCenter and shuts down the VM's gracefully before pulling the power, that is how it's supposed to work but maybe they didnt all shut down before power was pulled. All the other vm's, some linux and some windows were all fine, and this is a minimal Ubuntu server install so there really is not much to it, serves one purpose.  Restoring the VM now and will see if it boots, I am thinking that it has been corrupt for some time and I have not booted for sometime so we will see. I know when I booted into the ISO that I could mount the OS partition and see all the data, its just the boot that appears to be messed up...I guess we will see.

---

### Post by TheFu on 2022-10-18
Does the Linux system not use a journeled file system, say ext4?  That should have prevented any use issue with correction being an fsck run.  If you really have data corruption issues, look to using ZFS.

---

### Post by bishoptf on 2022-10-18
Looks like the restore before the power outage booted just fine, yea its a ubuntu derivitive, Linux mint and its just using the standard install, ext4 blah blah blah...not sure why it cratered. Going to create a new minimal ubuntu server install and get it working with that, should be more streamlined than what it is now and will have to ensure that my shutdown stuff with my UPS is working, I upgraded vCenter a couple weeks ago and maybe it broke something..

Thanks for the suggestions folks, case closed.

---

### Post by TheFu on 2022-10-18
Let's be clear.  Linux Mint is NOT ubuntu. There are some very clear differences, especially related to file systems and the GUI which could be important.

Second, when you say "server", we assume "not a desktop install".  There are also differences between what an "Ubuntu Server" install and running does as compared to any desktop flavor.  There's nothing wrong with loading a desktop flavor and using it as a server, but when posting for help, please say the flavor installed, not how you use it, so we don't make assumptions that are wrong and waste time.  For booting, please always say whether BIOS or UEFI is expected too.  If you said Linux Mint, I know enough about it to know that the way it boots can be different from any Ubuntu.  A number of guys in my LUG use Mint for their desktops.  I'm considering switching myself to avoid some things that Canonical is pushing that I'd rather not have.

Third, anytime there is virtualization involved which could be critical to the problem, please post in the Virtualization sub-forum.  The ways that VMs are setup and configured still matters and is different from how real hardware works, usually for much better results, but still different.  Last time I checked, VMware made 6 different hypervisors, each is a little different.  We tend to see more VMware Player here than ESXi + vSphere, so clearly saying which is used, and perhaps the version used, would be helpful. We stopped using ESXi in my company around 2011. Switched to straight KVM/Qemu with libvirt on Ubuntu Servers. We've been extremely happy with the decision to switch, since ESXi is very picky about hardware and refused to load on 5 of our 6 physical systems.  Plus there was the cost/payment they wanted and that nearly every "feature" was a $1000 addon. With KVM/Libvirt, those things are all free, F/LOSS, and usually more flexible with higher performance.  But whatever. We all have different needs, so different solutions are fine.

Lastly, when a thread is solved, please use the "Thread Tools" button/link at the top to mark it SOLVED. This toggles a bit in the DB so others can search it, saving time overall.

Reloading an OS shouldn't really fix anything.  With a broken boot, I'd start by doing a grub-install and update-grub from a booted ISO of the same release as the installed OS, just with a chroot to use the already installed OS storage.  That's always fixed anything except if I was using encrypted storage. Then things get more complex with the cryptab, but still manually workable.

If you are using Mint, why not use timeshift to backup the OS?  Then restoring from that point should be pretty easy.  It is easier if you use btrfs, BTW, since BTRFS supports proper volume manager snapshots before doing a backup.  Setting this up is part of the Linux Mint initial setup wizard.

---


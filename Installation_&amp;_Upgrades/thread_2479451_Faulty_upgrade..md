---
title: "Faulty upgrade."
date: 2022-09-24
forum: Installation &amp; Upgrades
---

### Post by mag-linares on 2022-09-24
Hello.I had Ubuntu 18.04 and decided to go to 20.04. But after the whole update process (which took a long time) the screen to enter my username and password appeared and, despite entering it correctly, the system returned me to the screen password, thus starting in a loop.With no other choice, I rebooted the system. Since then, every time I boot I get the Ubuntu loading screen as normal, but after a few seconds the computer hangs with just a black screen.

[https://i.gyazo.com/70f9b297c29f75bfc50f7728d571420b.gif](https://i.gyazo.com/70f9b297c29f75bfc50f7728d571420b.gif)

---

### Post by Bashing-om on 2022-09-24
mag-linares; Hello

I too had a similar experience - I have sufficient experience however to manually take matters further.

Let's take the easier approach here to get us a working terminal.

Boot to the ubuntu grub boot menu >> advanced options >> latest recovery kernel,
Here select 1st "networking" l and then the "root" shell.
Now in this shell what results with the terminal commands:
```

apt update
apt upgrade
dpkg --configure -a

```

Here in this root shell "SUdo DO" is not required as you are operating as "root". SOOOO be sure to be careful what you do.

we see what the package manager has to say and what it will fix for us.\; and maybe where we go from here

[INDENT]there is a process
[/INDENT]

---

### Post by mag-linares on 2022-09-25
Hi, friend. First of all thanks for your answer. Unfortunately for me, I have to say that this serie of steps has not been able to get this Ubuntu system back up. This is the sequence of the commands.

apt update
[https://i.gyazo.com/874712a5889d991e82ed040db8dd1f29.png](https://i.gyazo.com/874712a5889d991e82ed040db8dd1f29.png)

apt upgrade
[https://i.gyazo.com/54517e3b5cbb169190edf9b8c778201c.png](https://i.gyazo.com/54517e3b5cbb169190edf9b8c778201c.png)

dpkg --configure -a
(it returns to the initial recovery menu)

resume option --> system frozen again.[/FONT]

[https://i.gyazo.com/1e2c39a6747541b6c8f4db24f789cd55.gif](https://i.gyazo.com/1e2c39a6747541b6c8f4db24f789cd55.gif)

(The only difference has been that previously the frozen screen was black, and now burgundy.)

rebooting system --> frozen again. :icon_frown:

---

### Post by TheFu on 2022-09-25
Yesterday, I finally moved an 18.04 system to 20.04.  Because the 18.04 system had been upgraded since at least 12.04, I decided it was time for a fresh install.  Because I had a new NVMe SSD to install the OS into, it was a low risk effort, plus I have backup religion, so the system - enough to restore it as it was around 2am - could be restored, should the original HDD with the OS have any issues.

I spent entirely too much time in the installer, as I wanted my storage setup to be fairly specific and was having issues with the computer BIOS booting from the flash drive consistently.  The system was legacy booted the last year (new hardware about a year ago) instead of UEFI.  But in the BIOS, it really wanted me to pick the UEFI boot choice to go with the SSD installation, so after wasting 30 minutes, I did.  Also learned that the 50MB partition I'd previously setup for EFI use, wasn't marked as partition type 1/EFI, so the installer wouldn't let me pick it for EFI use.  The 600MB /boot/ partition was easy to pick, but only if I allowed it to be formatted too. It was already formatted, but whatever. Expected these to be overwritten completely.  I use LVM for everything else.  Was a little pissed that the installer created a swapfile in / even after I'd specifically pointed the installer at my swap logical volume.  Sigh.  So many issues with the 20.04 installer. So many issues.  And don't get me started on the static IP screen.  Some grayed out hints for the correct format and filling in the next field with a good guess based on the prior field would be nice.  Why should we have to completely type in the same subnet 4 times for a simple setup.

During install, we just want enough networking setup so we can get in with ssh later and fix stuff, if needed. If there's only 1 NIC and 1 IP planned, this isn't exactly hard.

Sigh.

With the switch from spinning HDD to NVMe SSD, I expected everything to feel a bit faster. It doesn't.  Sorta wonder what all the hoopla is about using SSDs.  The OS was already caching things well, so it isn't like the SSD makes much difference in performance, except for things with large DBs stored specifically on the SSD.  

Here's the resulting storage layout, if anyone is interested:
```

nvme0n1                        465.8G disk                        
&#9500;&#9472;nvme0n1p1                       50M part vfat        EFI        /boot/efi
&#9500;&#9472;nvme0n1p2                      600M part ext4                   /boot
&#9492;&#9472;nvme0n1p3                      465G part LVM2_member            
  &#9500;&#9472;vg00-swap                    4.1G lvm  swap                   [SWAP]
  &#9500;&#9472;vg00-root--00                 35G lvm  ext4                   /
  &#9500;&#9472;vg00-var                      35G lvm  ext4                   /var
  &#9500;&#9472;vg00-home                     25G lvm  ext4        home       /home

Filesystem                                  Type  Size  Used Avail Use% Mounted on
/dev/nvme0n1p1                              vfat   50M  5.2M   45M  11% /boot/efi
/dev/nvme0n1p2                              ext4  574M  140M  392M  27% /boot
/dev/mapper/vg00-root--00                   ext4   35G  8.4G   24G  26% /
/dev/mapper/vg00-home                       ext4   25G  9.6G   14G  42% /home
/dev/mapper/vg00-var                        ext4   35G   32G  658M  99% /var

```
That's the core system. There is about 40TB of storage connected to the box.  /var is used mostly by a virtual machine for nextcloud.

---

### Post by oldfred on 2022-09-25
@mag-linares 
Do you have proprietary video like nVidia?
 Upgrade process should be uninstall nVidia driver, upgrade, and then reinstall nVidia driver.
You may then need nomodeset, recovery mode or even chroot to get into system to install driver.

@TheFu
Do you have latest UEFI firmware? And latest NVMe firmware?
Shows firmware version & compare to vendor's site.
sudo apt install nvme-cli
sudo nvme list
or
udisksctl status

Do either of these apply, latest firmware, kernel & drivers help mitigate issues.
AMD Ryzen 9 3950X Retbleed settings - greater impact on servers as secuity more important
[https://www.phoronix.com/review/amd-3950x-retbleed](https://www.phoronix.com/review/amd-3950x-retbleed)
VMware: ESXi VM Performance Tanks Up To 70% Due To Intel Retbleed Mitigation
[https://www.phoronix.com/news/VMware-Linux-5.19-ESXi-Retbleed](https://www.phoronix.com/news/VMware-Linux-5.19-ESXi-Retbleed)

I used M.2 SSD in 2016 build as NVMe was very expensive. Wanted larger drive, so ecently installed NVMe drive.
Change from HDD to SSD was huge in 2016, change from SSD to NVMe was noticeable, but not huge like change to SSD.
And it more was booting as that is loading everything into RAM. Once apps are in RAM, I tend to use mostly the same, so barely can tell that I have SSD, but do now have more RAM to cache apps, than I used to years ago. And booting required some settings & tuning.

---

### Post by TheFu on 2022-09-25
My NVMe is on the latest firmware. I tried to upgrade it last year, but could never get Samsung's upgrade tool working. No MS-Windows on that system, so I was using the FreeDOS version, but it wouldn't boot from USB storage, I vaguely recall. It just didn't seem important. Surprising that it was already on the latest version, since I had the drive unopened for over 6 months before putting it into the system and over another 6 months before using it at all - even for testing.

Booting is faster, but since there is so much other storage connected to the same system and it is a server, the boot speed really doesn't matter. It isn't like it gets rebooted more than once every few weeks.

---

### Post by mag-linares on 2022-09-25
I don't use Nvidia on that Ubuntu system.
Where can I shoot then?

---

### Post by oldfred on 2022-09-25
What brand/model system?

While you may be starting to boot, this will show entire configuration, so we can see if something is misconfigured.
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Bashing-om on 2022-09-25
mag-linares; Ouch !!

dpkg will not run - 333 packages in trouble -- we do have a problem :(

Let's try this from that recovery console:
```

apt -f install

```

If this fails - all I know to do next is to attempt to set a Full Change Root into the install from the live environment ( Or an alternate 'buntu install).
If we are able to Change Root - we can have a shot to fix the install.

-enough will and time >> there is a way --

---

### Post by mag-linares on 2022-09-26
[SIZE=4][FONT=lucida sans unicode]apt -f install doesn't work either. It [COLOR=#000000][SIZE=3]Gives the same error as apt upgrade.

This is my entire configuration:[/SIZE]

[/COLOR][/FONT][/SIZE]```
[COLOR=#111111][FONT=Ubuntu][SIZE=2][FONT=lucida sans unicode]Paste from boot-info 26 September 2022 13:54 +0000[/FONT][/SIZE]

[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]boot-info-4ppa200                                              [COLOR=#666666][[/COLOR]20220926_1354[COLOR=#666666]][/COLOR]

[COLOR=#666666]==============================[/COLOR] Boot Info [COLOR=#B8860B]Summary[/COLOR] [COLOR=#666666]===============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v2.00[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda and looks at sector [COLOR=#666666]1[/COLOR] of 
    the same hard drive [COLOR=#AA22FF]**for**[/COLOR] core.img. core.img is at this location and looks 
    [COLOR=#AA22FF]**for**[/COLOR] [COLOR=#666666]([/COLOR],msdos1[COLOR=#666666])[/COLOR]/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu [COLOR=#666666]20[/COLOR].04.5 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img


[COLOR=#666666]================================[/COLOR] [COLOR=#666666]1[/COLOR] OS [COLOR=#B8860B]detected[/COLOR] [COLOR=#666666]=================================[/COLOR]

OS#1:   Ubuntu [COLOR=#666666]20[/COLOR].04.5 LTS on [COLOR=#B8860B]sda1[/COLOR]

[COLOR=#666666]================================[/COLOR] Host/Hardware [COLOR=#666666]=================================[/COLOR]

CPU architecture: [COLOR=#666666]64[/COLOR]-bit
Video: SVGA II Adapter from VMware
Live-session OS is Ubuntu [COLOR=#666666]64[/COLOR]-bit [COLOR=#666666]([/COLOR]Boot-Repair-Disk 64bit [COLOR=#666666]20200604[/COLOR], bionic, x86_64[COLOR=#666666])[/COLOR]

[COLOR=#666666]=====================================[/COLOR] [COLOR=#B8860B]UEFI[/COLOR] [COLOR=#666666]=====================================[/COLOR]

BIOS/UEFI firmware: VirtualBox from innotek GmbH
This live-session is in Legacy/BIOS/CSM mode [COLOR=#666666]([/COLOR]not in EFI mode[COLOR=#666666])[/COLOR].



[COLOR=#666666]=============================[/COLOR] Drive/Partition [COLOR=#B8860B]Info[/COLOR] [COLOR=#666666]=============================[/COLOR]

Disks info: ____________________________________________________________________

sda    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    no-wind,    [COLOR=#666666]2048[/COLOR] sectors * [COLOR=#666666]512[/COLOR] bytes

Partitions info [COLOR=#666666]([/COLOR][COLOR=#666666]1[/COLOR]/3[COLOR=#666666])[/COLOR]: _________________________________________________________

sda1    : is-os,    [COLOR=#666666]64[/COLOR], apt-get,    grub-pc ,    grub2,    grub-install,    grubenv-ok,    update-grub,    not-far

Partitions info [COLOR=#666666]([/COLOR][COLOR=#666666]2[/COLOR]/3[COLOR=#666666])[/COLOR]: _________________________________________________________

sda1    : isnotESP,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info [COLOR=#666666]([/COLOR][COLOR=#666666]3[/COLOR]/3[COLOR=#666666])[/COLOR]: _________________________________________________________

sda1    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda

fdisk -l [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: ___________________________________________________________

Disk sda: [COLOR=#666666]44[/COLOR] GiB, [COLOR=#666666]47185920000[/COLOR] bytes, [COLOR=#666666]92160000[/COLOR] sectors
Disk identifier: 0x00001c1a
      Boot Start      End  Sectors Size Id Type
sda1  *     [COLOR=#666666]2048[/COLOR] [COLOR=#666666]92159999[/COLOR] [COLOR=#666666]92157952[/COLOR]  44G [COLOR=#666666]83[/COLOR] Linux
Disk zram0: [COLOR=#666666]496[/COLOR].5 MiB, [COLOR=#666666]520605696[/COLOR] bytes, [COLOR=#666666]127101[/COLOR] sectors
Disk zram1: [COLOR=#666666]496[/COLOR].5 MiB, [COLOR=#666666]520605696[/COLOR] bytes, [COLOR=#666666]127101[/COLOR] sectors

parted -lm [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: _________________________________________________________

sda:47.2GB:scsi:512:512:msdos:ATA VBOX HARDDISK:;
[COLOR=#666666]1[/COLOR]:1049kB:47.2GB:47.2GB:ext4::boot;

blkid [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                  PARTLABEL
sda                                                                                                              
&#9492;&#9472;sda1 ext4     2437b2d3-8597-41ed-84ce-f435e9247ac0 00001c1a-01                                                 

Mount points [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: _______________________________________________________

             Avail Use% Mounted on
/dev/sda1    [COLOR=#666666]15[/COLOR].1G  [COLOR=#666666]60[/COLOR]% /mnt/boot-sav/sda1

Mount options [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]: ______________________________________________________

/dev/sda1   ext4            rw,relatime

[COLOR=#666666]======================[/COLOR] sda1/boot/grub/grub.cfg [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]======================[/COLOR]

Ubuntu   2437b2d3-8597-41ed-84ce-f435e9247ac0
Ubuntu, with Linux [COLOR=#666666]4[/COLOR].15.0-193-generic   2437b2d3-8597-41ed-84ce-f435e9247ac0
Ubuntu, with Linux [COLOR=#666666]4[/COLOR].4.0-210-generic   2437b2d3-8597-41ed-84ce-f435e9247ac0
Ubuntu, with Linux [COLOR=#666666]3[/COLOR].13.0-35-generic   2437b2d3-8597-41ed-84ce-f435e9247ac0
Ubuntu, with Linux [COLOR=#666666]3[/COLOR].13.0-33-generic   2437b2d3-8597-41ed-84ce-f435e9247ac0
[COLOR=#008800]*### END /etc/grub.d/30_os-prober ###*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/30_uefi-firmware ###*[/COLOR]

[COLOR=#666666]==========================[/COLOR] sda1/etc/fstab [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]===========================[/COLOR]

[COLOR=#008800]*# <file system> <mount point>   <type>  <options>       <dump>  <pass>*[/COLOR]
[COLOR=#008800]*# / was on /dev/sda1 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2437b2d3-8597-41ed-84ce-f435e9247ac0 /               ext4    [COLOR=#B8860B]errors[/COLOR][COLOR=#666666]=[/COLOR]remount-ro [COLOR=#666666]0[/COLOR]       [COLOR=#666666]1[/COLOR]
[COLOR=#008800]*# swap was on /dev/sda5 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]8d954caa-da46-4b66-a5fe-c1cc47af3ad7 none            swap    sw              [COLOR=#666666]0[/COLOR]       [COLOR=#B8860B]0[/COLOR]

[COLOR=#666666]=======================[/COLOR] sda1/etc/default/grub [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]=======================[/COLOR]

[COLOR=#B8860B]GRUB_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#666666]0[/COLOR]
[COLOR=#B8860B]GRUB_TIMEOUT_STYLE[/COLOR][COLOR=#666666]=[/COLOR]hidden
[COLOR=#B8860B]GRUB_TIMEOUT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#666666]10[/COLOR]
[COLOR=#B8860B]GRUB_DISTRIBUTOR[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]`[/COLOR]lsb_release -i -s [COLOR=#666666]2[/COLOR]> /dev/null [COLOR=#666666]||[/COLOR] [COLOR=#AA22FF]echo[/COLOR] Debian[COLOR=#BB4444]`[/COLOR]
[COLOR=#B8860B]GRUB_CMDLINE_LINUX_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"quiet splash"[/COLOR]
[COLOR=#B8860B]GRUB_CMDLINE_LINUX[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]""[/COLOR]

[COLOR=#666666]====================[/COLOR] sda1: Location of files loaded by [COLOR=#B8860B]Grub[/COLOR] [COLOR=#666666]====================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]
  [COLOR=#666666]26[/COLOR].144771576 [COLOR=#666666]=[/COLOR] [COLOR=#666666]28[/COLOR].072734720   boot/grub/grub.cfg                             [COLOR=#666666]1[/COLOR]
  [COLOR=#666666]27[/COLOR].374816895 [COLOR=#666666]=[/COLOR] [COLOR=#666666]29[/COLOR].393485824   boot/grub/i386-pc/core.img                     [COLOR=#666666]1[/COLOR]
   [COLOR=#666666]1[/COLOR].955593109 [COLOR=#666666]=[/COLOR] [COLOR=#666666]2[/COLOR].099802112    boot/vmlinuz-3.13.0-33-generic                 [COLOR=#666666]1[/COLOR]
  [COLOR=#666666]11[/COLOR].607944489 [COLOR=#666666]=[/COLOR] [COLOR=#666666]12[/COLOR].463935488   boot/vmlinuz-3.13.0-35-generic                 [COLOR=#666666]2[/COLOR]
  [COLOR=#666666]32[/COLOR].188549042 [COLOR=#666666]=[/COLOR] [COLOR=#666666]34[/COLOR].562191360   boot/vmlinuz-4.15.0-193-generic                [COLOR=#666666]1[/COLOR]
   [COLOR=#666666]3[/COLOR].240398407 [COLOR=#666666]=[/COLOR] [COLOR=#666666]3[/COLOR].479351296    boot/vmlinuz-4.4.0-210-generic                 [COLOR=#666666]1[/COLOR]
  [COLOR=#666666]32[/COLOR].188549042 [COLOR=#666666]=[/COLOR] [COLOR=#666666]34[/COLOR].562191360   vmlinuz                                        [COLOR=#666666]1[/COLOR]
   [COLOR=#666666]3[/COLOR].240398407 [COLOR=#666666]=[/COLOR] [COLOR=#666666]3[/COLOR].479351296    vmlinuz.old                                    [COLOR=#666666]1[/COLOR]
  [COLOR=#666666]35[/COLOR].573261261 [COLOR=#666666]=[/COLOR] [COLOR=#666666]38[/COLOR].196498432   boot/initrd.img-3.13.0-33-generic              [COLOR=#666666]1[/COLOR]
  [COLOR=#666666]35[/COLOR].542022705 [COLOR=#666666]=[/COLOR] [COLOR=#666666]38[/COLOR].162956288   boot/initrd.img-3.13.0-35-generic              [COLOR=#666666]2[/COLOR]
   [COLOR=#666666]4[/COLOR].704097748 [COLOR=#666666]=[/COLOR] [COLOR=#666666]5[/COLOR].050986496    boot/initrd.img-4.15.0-193-generic             [COLOR=#666666]2[/COLOR]
   [COLOR=#666666]4[/COLOR].665035248 [COLOR=#666666]=[/COLOR] [COLOR=#666666]5[/COLOR].009043456    boot/initrd.img-4.4.0-210-generic              [COLOR=#666666]2[/COLOR]
   [COLOR=#666666]4[/COLOR].704097748 [COLOR=#666666]=[/COLOR] [COLOR=#666666]5[/COLOR].050986496    initrd.img                                     [COLOR=#666666]2[/COLOR]
   [COLOR=#666666]4[/COLOR].665035248 [COLOR=#666666]=[/COLOR] [COLOR=#666666]5[/COLOR].009043456    initrd.img.old                                 [COLOR=#B8860B]2[/COLOR]

[COLOR=#666666]=====================[/COLOR] sda1: ls -l /etc/grub.d/ [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR] [COLOR=#666666]======================[/COLOR]

-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root [COLOR=#666666]18224[/COLOR] Jan [COLOR=#666666]11[/COLOR]  [COLOR=#666666]2022[/COLOR] 10_linux
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root [COLOR=#666666]42359[/COLOR] Jan [COLOR=#666666]11[/COLOR]  [COLOR=#666666]2022[/COLOR] 10_linux_zfs
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root [COLOR=#666666]12894[/COLOR] Jan [COLOR=#666666]11[/COLOR]  [COLOR=#666666]2022[/COLOR] 20_linux_xen
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root [COLOR=#666666]12059[/COLOR] Feb [COLOR=#666666]24[/COLOR]  [COLOR=#666666]2021[/COLOR] 30_os-prober
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root  [COLOR=#666666]1424[/COLOR] Jan [COLOR=#666666]11[/COLOR]  [COLOR=#666666]2022[/COLOR] 30_uefi-firmware
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root   [COLOR=#666666]700[/COLOR] Feb [COLOR=#666666]21[/COLOR]  [COLOR=#666666]2022[/COLOR] 35_fwupd.dpkg-new
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root   [COLOR=#666666]214[/COLOR] May [COLOR=#666666]15[/COLOR]  [COLOR=#666666]2014[/COLOR] 40_custom
-rwxr-xr-x [COLOR=#666666]1[/COLOR] root root   [COLOR=#666666]216[/COLOR] May [COLOR=#666666]15[/COLOR]  [COLOR=#666666]2014[/COLOR] [COLOR=#B8860B]41_custom[/COLOR]

[COLOR=#666666]======================[/COLOR] sda1/etc/grub.d/35_fwupd.dpkg-new [COLOR=#666666]=======================[/COLOR]

[COLOR=#008800]*#! /bin/sh*[/COLOR]
[COLOR=#008800]*# SPDX-License-Identifier: LGPL-2.1+*[/COLOR]
[COLOR=#AA22FF]set[/COLOR] -e
[COLOR=#666666][[/COLOR] -d [COLOR=#BB6688]**${**[/COLOR][COLOR=#B8860B]pkgdatadir[/COLOR]:?[COLOR=#BB6688]**}**[/COLOR] [COLOR=#666666]][/COLOR]
[COLOR=#008800]*# shellcheck source=/dev/null*[/COLOR]
. [COLOR=#BB4444]"[/COLOR][COLOR=#B8860B]$pkgdatadir[/COLOR][COLOR=#BB4444]/grub-mkconfig_lib"[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -f /var/lib/fwupd/uefi_capsule.conf [COLOR=#666666]][/COLOR] [COLOR=#666666]&&[/COLOR]
   ls /sys/firmware/efi/efivars/fwupd-*-0abba7dc-e516-4167-bbf5-4d9d1c739416 [COLOR=#666666]1[/COLOR]>/dev/null [COLOR=#666666]2[/COLOR]>&[COLOR=#666666]1[/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
      . /var/lib/fwupd/uefi_capsule.conf
      [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"[/COLOR][COLOR=#BB6688]**${**[/COLOR][COLOR=#B8860B]EFI_PATH[/COLOR][COLOR=#BB6688]**}**[/COLOR][COLOR=#BB4444]"[/COLOR] ![COLOR=#666666]=[/COLOR] [COLOR=#BB4444]""[/COLOR] [COLOR=#666666]][/COLOR] [COLOR=#666666]&&[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"[/COLOR][COLOR=#BB6688]**${**[/COLOR][COLOR=#B8860B]ESP[/COLOR][COLOR=#BB6688]**}**[/COLOR][COLOR=#BB4444]"[/COLOR] ![COLOR=#666666]=[/COLOR] [COLOR=#BB4444]""[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
      [COLOR=#AA22FF]echo[/COLOR] [COLOR=#BB4444]"Adding Linux Firmware Updater entry"[/COLOR] >&[COLOR=#666666]2[/COLOR]
cat [COLOR=#BB4444]<< EOF[/COLOR]
[COLOR=#BB4444]menuentry 'Linux Firmware Updater' \$menuentry_id_option 'fwupd' {[/COLOR]
[COLOR=#BB4444]EOF[/COLOR]
      [COLOR=#BB6688]**${**[/COLOR][COLOR=#B8860B]grub_probe[/COLOR]:?[COLOR=#BB6688]**}**[/COLOR]
      prepare_grub_to_access_device [COLOR=#BB4444]'`${grub_probe} --target=device \${ESP}` | sed -e "s/^/\t/"'[/COLOR]
cat [COLOR=#BB4444]<< EOF[/COLOR]
[COLOR=#BB4444]    chainloader ${EFI_PATH}[/COLOR]
[COLOR=#BB4444]}[/COLOR]
[COLOR=#BB4444]EOF[/COLOR]
      [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub2 of
sda1 into the MBR of sda.
Grub-efi would not be selected by default because no ESP detected.
Additional repair would be performed: unhide-bootmenu-10s

[/FONT][/COLOR]
```

---

### Post by TheFu on 2022-09-26
```
Ubuntu, with Linux 4.15.0-193-generic 2437b2d3-8597-41ed-84ce-f435e9247ac0
Ubuntu, with Linux 4.4.0-210-generic 2437b2d3-8597-41ed-84ce-f435e9247ac0
Ubuntu, with Linux 3.13.0-35-generic 2437b2d3-8597-41ed-84ce-f435e9247ac0
Ubuntu, with Linux 3.13.0-33-generic 2437b2d3-8597-41ed-84ce-f435e9247ac0
```
says to me that you've upgraded this install 3 times BEFORE this attempt.  That means there's is a bunch of cruft and it is time for a fresh install.

20.04 <-- 18.04 <-- 16.04 <-- 14.04

Does that make sense?  Are basically in the same situation that I was a few days ago as outlined above.  It is time for a fresh install.

Ensure you backup everything you cannot lose before starting.  Most of the time, that is /etc/, /home/ and a list of packages from 'apt-mark showmanual'  With just those few areas, saved off, a fresh OS install really isn't that big of a deal.  After the fresh install, put everything from the backups of /home/ back and only return very specific files from /etc/  ... probably better to do a careful merge of the 10 files you've changed, if anything.  Then just feed the list of manually installed packages from the apt-mark command back into APT to install the applications you had installed. A few won't be available anymore. They've been deprecated and removed, but that's probably less than 5 of 200 packages. Not a big deal and APT will cause errors.

With the file containing the showmanual output (  use "apt-mark.manual" ), run:
```
sudo apt-mark manual $(cat apt-mark.manual)
sudo apt-get -u dselect-upgrade
sudo apt-get -f install
```
to manually install all those packages. Easy peasy.  If any packages cause errors, remove them from the list.

---

### Post by oldfred on 2022-09-26
Use code tags for longer text, but better to follow Boot-Repair's suggestion of posting just the link to the pastebin side.
Often report is too long to post in forum.
How to use Code tags, # in Forum's advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

Looks like older system with BIOS/MBR.
UEFI has been the standard since Microsoft required vendors to install in UEFI/gpt mode with release of Windows 8 in 2012.

You show several older kernels, so system has been updated several times. 
I tend to prefer new clean install & restore from backups to house clean old cruft like the very old kernels you still have.
Do you have good backups?

I would try Boot-Repair's advanced mode.
Choose total reinstall of grub and install newest kernel. That resets of lot of things.
Advanced mode screens:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by tea for one on 2022-09-26
I noticed these lines in your boot-repair report?
```
BIOS/UEFI firmware: VirtualBox from innotek GmbH
sda:47.2GB:scsi:512:512:msdos:ATA VBOX HARDDISK:;
```
Is your Ubuntu system installed as a Virtual Machine?

---

### Post by mag-linares on 2022-09-28
Sure enough, my Ubuntu system is mounted on a virtual machine. As from the beginning of this problem I am receiving suggestions of a clean installation, or a new installation, I have decided to resort to a backup image that I had on an external hard drive, and I have overwritten the image that had been corrupted after a couple of of updates. So I'm back to where I started from before the upgrade, with Ubuntu 16.04 LTS.


My question now is how should I update my system so that this disaster does not happen again?

---

### Post by TheFu on 2022-09-28
> **mag-linares said:**
> My question now is how should I update my system so that this disaster does not happen again?

1a) Make a list of all the manually installed packages.  I'd use 'apt-mark showmanual' and redirect the output to a file.

1b) Read the release notes for the LTS install you want and for the DE of the LTS install you want. Note any important information for your specific situation.  Samba changes, apache changes, GPU issues, file systems which have been added or are marked as 'experimental',  stuff like that.

2) Do a fresh install of the LTS release you want.

3) Restore the data, personal and server, for the stuff you want to run in the new install.  I'd also restore your HOME completely, but expect a few compatibility issues with some program settings that will require wiping and starting over.  I've had to do that with Firefox. Something was incompatible between the 16.04 and 20.04 settings.

4) Selectively restore the settings and config files of the server programs you want to run. Expect that there are major changes, since any project that is still viable has made huge changes since 2016.

5) Take that list of manually installed packages, feed it into apt for the 'to be installed' action, then tell APT to install those packages.  Because the old settings are there and the data is where it was before, the installer will see these and assume it is an upgrade for just those packages.  This works well, but when their are config files that have "new" versions, the installation should offer to keep, overwrite, merge, or let you manually take a look to see what's different.  For configs I know I've modified, I always want the last option - manually view the changes.  For programs I didn't know had a config file, I accept the new file.

If you have good backups and have properly separated the OS from the data, this process should take less than 45 minutes total to complete for 90+% of the stuff you want in the new system.  

I just went through this last Saturday.  I think only 1 thing is left to get working, but nearly everything, even a complex media center, was installed and working within that 45min initial effort.

Since you have a VM, you can easily have 10 attempts to get this optimized with zero risk.  VMs completely rock.  BTW, you might consider switching from vbox to a more capable, faster, more flexible hypervisor.  kvm-qemu + libvirt + virt-manager easily replace vbox and provide enterprise capabilities without the ugly license agreement tied to vbox.  Since kvm-qemu is part of the Linux kernel, it is that stable and that well tested. Only 1 hypervisor kernel driver can be loaded at a time, so whatever you choose, one one at a time really can be installed, unless you are comfortable adding and removing kernel modules from active to inactive on a running system.

---

### Post by mag-linares on 2022-09-28
First of all, I thank you from the bottom of my heart for your detailed response. But honestly, I find it disproportionate, demoralizing and disheartening that it is necessary to do all that (and more with my limited level of knowledge) for something as simple as updating the operating system. I think I'll stick with version 16.04 LTS forever, which is enough for the simple tasks I do.


Heartfelt thanks to all. [COLOR=#4D5156][FONT=arial]&#10084;&#65039; [/FONT][/COLOR]

---

### Post by tea for one on 2022-09-28
> **mag-linares said:**
> I think I'll stick with version 16.04 LTS forever, which is enough for the simple tasks I do.
Ubuntu 16.04 reached End of Life in April 2021.
Please use a supported version.

---

### Post by TheFu on 2022-09-28
> **mag-linares said:**
> First of all, I thank you from the bottom of my heart for your detailed response. But honestly, I find it disproportionate, demoralizing and disheartening that it is necessary to do all that (and more with my limited level of knowledge) for something as simple as updating the operating system. I think I'll stick with version 16.04 LTS forever, which is enough for the simple tasks I do.


Heartfelt thanks to all. [COLOR=#4D5156][FONT=arial]&#10084;&#65039; [/FONT][/COLOR]

Most people don't migrate their own OSes. They buy a new computer with the OS pre-installed.  After all, are you running Win2000 on the same computer you run Win10 on?  No.  That's the same amount of major OS changes as going from 16.04 to 22.04. Linux just does major OS releases faster and on a predicted schedule.

If you are one of those users, System76 and Dell sell Ubuntu pre-installed. Nothing wrong with choosing to let other people handle your OS migrations.  Most of the world does that.  You can also get help from a local LUG - Linux Users Group.

But please don't run 16.04.  There are remote root takeover attacks in the wild and have been for years. It isn't safe.  You can pay for ESM support for 16.04 for a few more years, but the end is coming.  ubuntu.com/esm/

---


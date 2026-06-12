---
title: "Crashed Grub2. Can't boot Mint 17 on /dev/sdb"
date: 2015-01-11
forum: Installation &amp; Upgrades
---

### Post by michaelcole on 2015-01-11
Hi, I just got a new laptop from System76.  
 - boots System76's Ubuntu on /dev/sda
 - has 2nd drive bay (/dev/sdb), so I added the HD from my old laptop (important data)  
 - /dev/sdb is Mint 17 with an encrypted disk.  
 - I can open Mint (/dev/sdb) using my password in System76's Ubuntu (booted from /dev/sda)

I was able to boot both Linux's using the BIOS.  I got greedy and tried to configure a boot menu with Grub2.  That was a mistake.

Now I can't boot /dev/sdb from Grub2 or the BIOS

```
error: no such device: f83asdfasd-asdfsadfasdf-asdf-sadf-sa-dfsda-fsda-fas-fdasd-f
Entering rescue mode...
grub rescue> ls
(hd0)
grub rescue>
```

I think it might have been because I ran this command (booted /dev/sda): `sudo grub-install /dev/sdb`

I don't know what's wrong, so I'm not sure how to fix it.  I've followed some tutorials and rescue disks with no luck.

At this point, I don't want to use Grub2 for managing my boot menu - the BIOS is fine for my needs.

How do I fix /dev/sdb to boot?  How do I undo the `sudo grub-install /dev/sdb`?

Thanks!

Mike

---

### Post by MAFoElffen on 2015-01-11
Do you actually have two physical drives installed or one? Because grub see's one. 

Next observation is the command you used to install grub...
```

sudo grub-install /dev/sdb

```
That would assume a second physical HDD exists. Thinking you said "Laptop"... Very few laptops have a void big enough to add a second physical drive to it. 

Please post the results of 
```

fdisk -l
sudo blkid

```

---

### Post by grahammechanical on 2015-01-11
Lets us go over the steps you took and what you should have done but maybe did not do.

I) Machine arrives from System 76 with Ubuntu installed on sda.
2) Connected a second hard drive sdb.
3) Should have loaded Ubuntu on sda and run

```
sudo update-grub
sudo grub-install /dev/sda
```

Then Grub 2 installed in the MBR of sda would have detected (maybe) Linux Mint on sdb and provided a boot option.

4) Should have loaded into Linux Mint on sdb and run

```
sudo update-grub
sudo grub-install /dev/sdb
```

I have never used Linux Mint. I do not give support to Linux Mint. So, I do not know if those commands work in Linux Mint. They work in Ubuntu but they are actually scripts that call certain Grub utilities. So, I do not know if Linux Mint has the same scripts for doing this as Ubuntu does.

By running update-grub /dev/sdb from Ubuntu you installed the Ubuntu Grub 2 into the MBR of sdb and it looks to a Grub configuration file in /boot/grub/ on sda but that configuration file does not know about Linux Mint because update-grub was not run from Ubuntu on sda.

I suggest that you load into Ubuntu and run

```
sudo update-grub
sudo grub-install /dev/sda
```

and see if Linux Mint is detected and if you can load into Linux Mint from the Grub that looks to Ubuntu on sda for its configurations files.

Regards.

---

### Post by michaelcole on 2015-01-11
Hi, thanks for your help!

Here's the two commands.  It physically has a 100G minidrive module (like a memory chip module), along with a hard drive bay (250G Linux Mint).

```

michael@mclaptop:~$ fdisk -l

Disk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 72F494C3-0E3E-4CCD-A3D6-D47C5D9F9831

Device         Start       End   Sectors   Size Type
/dev/sda1       2048      4095      2048     1M BIOS boot
/dev/sda2       4096 226050047 226045952 107.8G Linux filesystem
/dev/sda3  226050048 234438655   8388608     4G Linux swap

Disk /dev/sdb: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00029e01

Device     Boot  Start       End   Sectors   Size Id Type
/dev/sdb1  *      2048    499711    497664   243M 83 Linux
/dev/sdb2       501758 488396799 487895042 232.7G  5 Extended
/dev/sdb5       501760 488396799 487895040 232.7G 83 Linux

michael@mclaptop:~$ sudo blkid
[sudo] password for michael: 
/dev/sda2: LABEL="Ubuntu" UUID="f83cf82d-bee8-4d01-9fb0-41eb5d4d77ce" TYPE="ext4" PARTLABEL="primary" PARTUUID="6fa980df-e4c3-4cc3-8d10-38bd1645afa5" 
/dev/sdb1: UUID="892df353-6b24-45de-98c4-1e88bf7191d9" TYPE="ext2" PARTUUID="00029e01-01" 
/dev/sdb5: UUID="161f09db-631c-46e2-a964-8ef387e15f73" TYPE="crypto_LUKS" PARTUUID="00029e01-05" 
/dev/sda1: PARTLABEL="primary" PARTUUID="50d07e57-3853-4b73-b08b-ac57daf6f723" 
/dev/sda3: PARTLABEL="primary" PARTUUID="49fd7782-4d82-414b-a92c-9a901bdceb37" 
michael@mclaptop:~$ 

```

---

### Post by michaelcole on 2015-01-11
Hi, @grahammechanical

Ok, thanks for this.  I think I understand now.  I overwrote Mint's grub-install with info from Ubuntu's.  So now Mint can't boot.  Yeah, a statement of the problem :-)

I think I understand the solution is to:
  1) Configure Ubuntu to boot Mint
  2) `sudo update-grub /dev/sdb` from the booted Mint install.

Here's the output from: `sudo update-grub`

```

michael@mclaptop:~$ sudo update-grub
[sudo] password for michael: 
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.16.0-28-generic
Found initrd image: /boot/initrd.img-3.16.0-28-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
  No volume groups found
done
michael@mclaptop:~$ sudo grub-install /dev/sda
Installing for i386-pc platform.
Installation finished. No error reported.
michael@mclaptop:~$ 

```

It didn't autodetect the install on /dev/sdb.

I made a grub2 install profile(?), which shows in the menu.

```

michael@mclaptop:~$ cat /etc/grub.d/42_linux_work 
#!/bin/sh -e
echo "Linux Mint"
cat << EOF
menuentry "Linux Mint" {
set root=(hd1,1)
chainloader +1
}
EOF

```

When I try that boot option, I get (from memory):

```

error: invalid signature...

Press any key to continue

```

I tried some other grub script versions with a `linux` command but got errors that it was an invalid command.  Any suggestions on what to put in grub to get sdb to boot?  Mint is basically a customized Ubuntu 14.04.

I have access to data on both drives and can see the /etc/grub.d

I just don't know what to put in the Ubuntu grub scripts.

---

### Post by michaelcole on 2015-01-11
This log from boot repair might be handy: [http://paste.ubuntu.com/9715931/](http://paste.ubuntu.com/9715931/)

---

### Post by fantab on 2015-01-11
If you have installed grub on /dev/sdb then set your BIOS to boot from /dev/sdb first...
Check the /etc/fstab file in LinuxMint and confirm that your UUID for /dev/sdb1 (the partition on which you have linuxmint) matches the one from 'blkid' command:
```
/dev/sdb1: UUID="**892df353-6b24-45de-98c4-1e88bf7191d9**" [s]TYPE="ext2" PARTUUID="00029e01-01"[/s] 
```

The UUIDs will change if the HDD is moved around.

...and by the way, my 40_custom menu entry for LMDE looks like:

```
menuentry "Debian - LMDE (sda4)" {
    set root=(hd0,msdos4)
    search --fs-uuid --set=root --hint-bios=hd0,msdos4 7915c7b7-7e77-428b-8677-2275bb4725fd
    linux /vmlinuz root=UUID=7915c7b7-7e77-428b-8677-2275bb4725fd ro
    initrd /initrd.img
}
```

...and for Ubuntu it looks like:

```
menuentry 'Ubuntu 14.04 (sdb2)' {
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root=(hd1,msdos2)
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos2 --hint-efi=hd1,msdos2 --hint-baremetal=ahci1,msdos2  94797b8a-610f-4c6c-87c8-be93a4b0eedb
    linux /vmlinuz root=UUID=94797b8a-610f-4c6c-87c8-be93a4b0eedb ro  quiet splash $vt_handoff
    initrd /initrd.img
```

You can also try Boot-Repair tool to fix the boot issue; 'create a bootinfo summary' with boot repair and post the url link to the file here, if you still have issues.

---

### Post by fantab on 2015-01-11
You have 'encrypted' /dev/sdb... I don't know how to go about with encrypted disks.

Perhaps, reinstalling LinuxMint is a good idea. Data Backup is recommended.

---

### Post by michaelcole on 2015-01-11
Hey, thanks for the help everybody.  I really appreciate it.  This topic and this post helped:
[http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)

I had to 

1) Mount the first partition of the encrypted disk sdb (this happened in the gui so no command to copy).  It was about 255 MB
2) Do a command like this:
`sudo grub-install --boot-directory=/media/michael/130948103841034801384103841304 /dev/sdb`

After that, it worked.  This let's me choose which disk to boot in the BIOS which is just fine.

Thanks again!

---

### Post by MAFoElffen on 2015-01-11
all-- FanTab caught it...

Mint is a Ubuntu derivative. Same Grub2. Does not chain load. should be the same load image... as us.

What I see is installing grub, but has anyone done an updaye grub yet?

If from the Grub menu, if you press <esc>, then <C> to drop down to a Grub CLI
```

GRUB> ls (hd1,1)
# or 
GRUB> (hd1    [COLOR=#ff0000]# <Tab> key to try an autocomplete[/COLOR]

```
Because, like I said in my post "Grub does not see the second physical HDD"... right?

If it does not see the second drive, maybe it's not seeing it from the UEFI BIOS(?)

(looking at there own support site on adding second drives to their hardware if there is something special on those...)

---


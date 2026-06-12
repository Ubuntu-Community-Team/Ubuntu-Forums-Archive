---
title: "Install Hangs on PowerPC 710"
date: 2015-02-10
forum: Installation &amp; Upgrades
---

### Post by forteounce on 2015-02-10
Help appreciated installing on IBM powerPC 710 via serial connection. 
Both 14.04.1 and 13.04 images hang after the device tree configuration:


************************************
If in doubt, just press Enter, and if that
doesn't work, type 'install video=ofonly'.
************************************
Welcome to yaboot version 1.3.16
Enter "help" to get some basic usage information
boot: expert
Please wait, loading kernel...
   Elf32 kernel loaded...
Loading ramdisk...
ramdisk loaded at 01900000, size: 6327 Kbytes
OF stdout device is: /vdevice/vty@30000000
Preparing to boot Linux version 3.8.0-9-powerpc-smp (buildd@sagari) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #15-Ubuntu SMP Thu Apr 18 00:15:00 UTC 2013 (Ubuntu 3.8.0-9.15-powerpc-smp 3.8.8)
Detected machine type: 00000500
command line: ro ramdisk_size=8192 file=/cdrom/preseed/ubuntu-server.seed priority=low --
memory layout at init:
  memory_limit : 00000000 (16 MB aligned)
  alloc_bottom : 01f2e000
  alloc_top    : 08000000
  alloc_top_hi : 08000000
  rmo_top      : 08000000
  ram_top      : 08000000
instantiating rtas at 0x06e90000... done
boot cpu hw idx 0
starting cpu hw idx 2... done
starting cpu hw idx 4... done
starting cpu hw idx 6... done
copying OF device tree...
Building dt strings...
Building dt structure...
Device tree strings 0x0372f000 -> 0x0373082b
Device tree struct  0x03731000 -> 0x03756000

---

### Post by tgalati4 on 2015-02-11
That server has a PowerPC7+.  It's possible that the kernel you have does not support the PowerPC7+ processor.

Did you try installing using:

install video=ofonly

as suggested?  It's also possible that there is a graphics issue such that you are not getting any error messages because the video output has no place to go.  Is there a VGA terminal on the back of the server?  If so, find an old VGA terminal and plug it in.

The documentation states that Linux for Power(tm) is supported, but I'm not familiar with what kernel that is, but I'm going to guess it's IBM's flavor of Linux.

---

### Post by forteounce on 2015-02-11
Thanks for the kind reply. 
I've tried "[COLOR=#000000]install video=ofonly" option with similar results.

There's no VGA port - just sc1/2 HMC1/2.

I'm trying to use the "power 5" image from here:
Is there a different release for "powerPC7+"? If so I have not been able to locate it.


[/COLOR]http://cdimage.ubuntu.com/releases/trusty/release
[COLOR=#000000]
[/COLOR][IMG]http://cdimage.ubuntu.com/cdicons/iso.png[/IMG] [ubuntu-14.04-server-powerpc.iso]("http://cdimage.ubuntu.com/releases/trusty/release/ubuntu-14.04-server-powerpc.iso")              16-Apr-2014 21:17  654M  Server install image for Mac (PowerPC) and IBM-PPC (POWER5) computers (standard download)[COLOR=#000000]
[/COLOR]

---

### Post by tgalati4 on 2015-02-11
I'm sure you can find the differences between a ppc5 and ppc7+ on the web.  If you have a PowerMac G5 then the image you have will probably load OK.  It would probably load OK on an older IBM server using the ppc5 (Power5) CPU.  

Or, inquire with IBM directly what other linux-based OS's will run on it.  What OS was running on the server originally?

---

### Post by tgalati4 on 2015-02-22
I spoke to an IBM server representative at SCaLE13x and he said that PowerPC7 servers are "Big-Endian" and will only support "Big-Endian" operating systems such as Red Hat, Fedora, or SUSE.  You can get Debian/Ubuntu to load, but you have to flash the server with special firmware to boot a "Little-Endian" OS such as Debian/Ubuntu.

---

### Post by forteounce on 2015-02-23
> **tgalati4 said:**
> I spoke to an IBM server representative at SCaLE13x and he said that PowerPC7 servers are "Big-Endian" and will only support "Big-Endian" operating systems such as Red Hat, Fedora, or SUSE.  You can get Debian/Ubuntu to load, but you have to flash the server with special firmware to boot a "Little-Endian" OS such as Debian/Ubuntu.

Thanks for the info! :D

---


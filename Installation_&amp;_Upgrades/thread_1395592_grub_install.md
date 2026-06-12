---
title: "grub install"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by Alabamian on 2010-02-01
This is the situation on my hard drive ...

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9025    72493281    7  HPFS/NTFS
/dev/sda3            9026       19457    83795040    5  Extended
/dev/sda5   *        9026       18934    79594011   83  Linux
/dev/sda6           18935       19457     4200966   82  Linux swap / Solaris

Used to be, this was a dual boot system, chainloaded from the NTFS logical partition.  Recently, I got a new hard drive and installed Vista separately on it (with this drive unplugged).  So now Vista works fine.

The trouble is, in this whole upgrade process, I managed to goof up the MBR on sda1.  Now, I don't really care about that.  I just want sda1 to stay a 72 gig ntfs data volume.  Trouble is, I can't get grub (1 or 2, don't really care) onto sda5.  This is Ubuntu 9.10.

I tried this ...

ubuntu@ubuntu:~$ sudo grub-install /dev/sda5
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.


Hmm?  So I tried this to try and explain things ...

ubuntu@ubuntu:~$ sudo grub-probe --help
Usage: grub-probe [OPTION]... [PATH|DEVICE]

Probe device information for a given path (or device, if the -d option is given).

  -d, --device              given argument is a system device, not a path
  -m, --device-map=FILE     use FILE as the device map [default=/boot/grub/device.map]
  -t, --target=(fs|fs_uuid|drive|device|partmap|abstraction)
                            print filesystem module, GRUB drive, system device, partition map module or abstraction module [default=fs]
  -h, --help                display this message and exit
  -V, --version             print version information and exit
  -v, --verbose             print verbose messages

Report bugs to <bug-grub@gnu.org>.

Uh, well, it's definitely more information, just not anything useful to me.  I'm hoping it will be to someone else reading this.  All I want to do is have grub install on sda5 so that it boots.  Then, I figure I'll plug in my Vista drive and figure out how to chainload Vista (on sdb?) from sda.  I'm not nearly experienced enough in Linux, but trying to get the hang of it.  I thought having the two OS's on different volumes might make things easier (planning on upgrading to Win7 someday).

Thanks ahead of time,

Alabamian

---

### Post by darkod on 2010-02-01
Your grub-install didn't work because when doing it from the live desktop you need to have your root partition mounted first. Otherwise it has no clue where it is.
Another thing. Since you have two hdds right now, no need to force grub2 onto a partition (which it doesn't like) and chainload. Why not simply install grub2 onto the MBR of /dev/sda, the way it's supposed to work?

To install it on the MBR of /dev/sda:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

To force it on /dev/sda5 I think you need to use -f so it would be:

sudo mount /dev/sda5 /mnt
sudo grub-install -f --root-directory=/mnt /dev/sda5

If you install on the MBR of /dev/sda which I would recommend, you can simply put sda as first hdd in boot options and it will boot grub. Once you boot in ubuntu you might need to run
sudo update-grub

to find the vista disk and add vista to the boot menu because it wasn't there when ubuntu was installed.

---

### Post by Alabamian on 2010-02-03
Darko,

Thanks, but this didn't work.  I got this ...

ubuntu@ubuntu:~$ sudo grub-install -f --root-directory=/mnt /dev/sda5
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly

Upon rebooting, I still get a message that the NTLDR is bad or missing, unless I use sdb1, then Vista boots fine, but that makes sense.

Any other advice is appreciated.

---

### Post by Alabamian on 2010-02-09
Wow, the response has been underwhelming.  Hmm.  I was really enjoying Ubuntu.  Certainly the question I ask can't be all that hard to fix.  Folks, how does one get rid of chainloading from Windows and boot directly from Ubuntu, with Ubuntu having being the boot volume and the ntfs partition just being a data partition?  If this is complicated and impossible, so be it, but I find that hard to believe.  My Vista boot on sdb1 has NO problem seeing the old ntfs partition and can use it as a data volume.  I imagine if I were to get an ext3 driver for it, it would see Ubuntu, too.

---

### Post by darkod on 2010-02-09
> **Alabamian said:**
> Wow, the response has been overwhelming.  Hmm.  I was really enjoying Ubuntu.  Certainly the question I ask can't be all that hard to fix.  Folks, how does one get rid of chainloading from Windows and boot directly from Ubuntu, with Ubuntu having being the boot volume and the ntfs partition just being a data partition?  If this is complicated and impossible, so be it, but I find that hard to believe.  My Vista boot on sdb1 has NO problem seeing the old ntfs partition and can use it as a data volume.  I imagine if I were to get an ext3 driver for it, it would see Ubuntu, too.

I don't really use chainloaded grub so I can't help much. But instead of troubling yourself with chainloading, if you want to install it properly on the MBR of /dev/sda, just boot with the 9.10 cd, Try Ubuntu option, and in terminal:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

That will put grub2 to the MBR of /dev/sda and you can boot it anytime if you have sda set as first option in BIOS. sdb will still keep the windows bootloader on it.

Initially in the grub boot menu you won't see vista because it wasn't there when ubuntu was installed, but once you boot ubuntu just do in terminal:

sudo update-grub

and it should detect your vista on sdb1. From there on you can always boot ubuntu or vista from the grub menu.

---

### Post by Alabamian on 2010-02-11
darko,

Thanks for the response!  I can't try it now, but will try it later when I'm home tonight (or tomorrow night since I've got music plans for this evening).  I guess I was too specific with the sda5 business above, instead of just telling 'grub-install' to fix the boot sector for grub wherever it resides on good ole sda.  That makes sense, and the errors I got by being over specific make sense, too.

Muchas gracias,

Alabamian

---

### Post by Alabamian on 2010-02-12
Darko,

Thanks!  This worked like a champ.  Now I boot correctly to the grub2 menu and can select Ubuntu (which boots fine) or Vista, which also runs fine.

Thanks again.

---


---
title: "[SOLVED] Upgrade, no unable to boot from hdd"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by xfred on 2008-07-24
Hi

I've just updated my mb and processor and added yet another hard-drive.  I can boot just fine from the live cd, but I can't seem to complete a successful installation.  It seems to install, but upon reboot after the process has (allegedly) completed it just sits there after completing usual startup tests.  It's got me baffled :confused:, and because it doesn't even get as far as grub I don't even have any logs to go by.

Here's my setup:

MB: Gigabyte EP35C-DS3R
Processor: Intel core 2 Due E4600
RAM: 4gb
VGA: Asus N6600
Hard-drives: 320gb (PATA master) + 320gb (PATA slave) + 250gb (SATA) + 1TB (SATA) + 320GB (SATA) + 500GB (SATA)

The 500gb is the new one that I'm (attempting) to do the clean installation onto.

Any thoughts?

---

### Post by Pumalite on 2008-07-24
Post:
sudo fdisk -lu

---

### Post by xfred on 2008-07-24
EDIT: ok, I fixed the boot flags, so updated output is:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000bd1f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   488392064   244196001   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953520064   976760001   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00094b9b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   625137344   312568641   83  Linux

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0003aa35

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   958566419   479283178+  83  Linux
/dev/sdd2       958566420   976768064     9100822+   5  Extended
/dev/sdd5       958566483   976768064     9100791   82  Linux swap / Solaris

Disk /dev/sde: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0003e1f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63   605393459   302696698+  83  Linux
/dev/sde2       605393460   625137344     9871942+   5  Extended
/dev/sde5       605393523   625137344     9871911   82  Linux swap / Solaris

Disk /dev/sdf: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ed7f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              63   488392064   244196001   83  Linux
```

(ps: I'm trying to install 8.04)

---

### Post by Pumalite on 2008-07-24
Memory? Graphics? What iso are you using?

---

### Post by xfred on 2008-07-24
As per first post my specs are:

RAM: 4gb
VGA (graphics): Asus N6600

I'm not sure what you mean by iso?, but if that means dvd player then:
cheap liteon sata dvd writer

EDIT: if you mean which cd image then I can't give you the exact number (it's on a computer at work), but I downloaded it yesterday.

---

### Post by xfred on 2008-07-24
- Ubuntu 8.04 LTS Desktop Edition - Supported to 2011
- Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)

---

### Post by Pumalite on 2008-07-24
I think your processor allows 64 bit. Try 64 bit version. It makes better use of memory.
Make sure you burn the iso as 'image' and not as 'data'
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by xfred on 2008-07-25
(sorry for the delay... travelling from home to work)

I'll give the 64bit version a go, but I'm not sure how that would help with this problem.  As noted above, the CD itself boots fine, finds hardware perfectly (well except the digital monitor, but I suspect that's just a xorg problem which I think I can figure out myself), and the installation process gives every impression of working as well (ls of the drive looks like I'd expect a *nix install to look).  It's just that, after this, when I try to boot the newly installed version, nothing happens.  Not even grub: it just stalls.

My only thought when riding to work was that maybe I should try and see how it goes with just the 500gb hard-drive plugged in.  Not sure how that would help either really, but at least it might narrow the search a little.

---

### Post by xfred on 2008-08-31
OK, I finally got time today to sit down and sort out the problem.  So just in case anyone out there experiences the same problem here is a solution that worked for me:

- unplug all hard-drives except the one you're installing the os on.
- install the os off the cd.
- plug the hard-drives back in one at a time.
- if plugging in a particular hdd stops the system booting then try plugging it into a different socket, shuffling sata plugs, etc.
- By a process of trial and error you will with luck find an ordering that works.

I have no idea why the above was necessary for my system (probably some hopelessly obscure hardware blip that will never occur anywhere ever again), but if by chance you run into the problem I hope it is of some assistance.

Now if I could just work out why they seem to be named in an apparently arbitrary order (sdc last boot, sde this one, next one - guess I'll have to wait and see)...

---


---
title: "installing Ubuntu on an old PC"
date: 2015-07-24
forum: Installation &amp; Upgrades
---

### Post by coverup1128 on 2015-07-24
I have an old PC (2010) dualbooting Mandriva 2009 (the main OS) and Ubuntu 9 (either 9.04 or 9.10). There is no Windows on it, and the GRUB is installed in MBR if I recall correctly. I would like to give this PC the second life, and install Ubuntu 14.04 LTS. Unfortunately, I cannot boot 14.04 or 12.04 on it, only 10.10. I did not try booting any other versions of Ubuntu but I suspect being unable to boot the last two LTS releases has something to do with the age of that PC.

Anybody here have experienced a similar problem? I have in the past installed 14.04 on a laptop which was even older than the PC in question with no problems. Any suggestions?

---

### Post by kansasnoob on 2015-07-25
Let's look at some specific hardware info. Booting any version of Ubuntu that will run copy-n-paste the output of these commands:

```
cat /proc/cpuinfo | head -10
```

```
lspci | grep VGA
```

```
free -m
```

---

### Post by ajgreeny on 2015-07-25
With a machine of that age I suspect you will do much better with either Xubuntu or Lubuntu, which both need fewer resources than Ubuntu with the unity desktop.

Even though I have a powerful machine I have been running Xubuntu for a few years now as I much prefer its standard panel style desktop.  It will do everything that Ubuntu will do, the desktop you choose does not make any difference to what applications are available, and it is extremely configurable to make it look and behave as you want.

It is, however, going to be helpful to have the information from those commands that kansasnoob asks for, which might even run on Mandriva if that is still installed.  Please paste back here in code tags; see my signature for a "How-to" if you need.

---

### Post by coverup1128 on 2015-07-25
Thanks  kansasnoob and ajgreeny. Xubuntu or lubuntu should be fine, I prefer the old style gnome legacy interface anyway. The PC is Lenovo M58 tower. Here the output of the cpuinfo, lspci and free commands, as requested (obtained from mandriva, though I don't think this makes any difference except for free -m maybe): 
```
$ cat /proc/cpuinfo | head -10
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E7300  @ 2.66GHz
stepping	: 6
cpu MHz		: 2667.000
cache size	: 3072 KB
physical id	: 0
siblings	: 2
$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9500 GT (rev a1)
$ free -m
             total       used       free     shared    buffers     cached
Mem:          3421       2477        944          0        435        809
-/+ buffers/cache:       1231       2189
Swap:         9703          2       9700

```
When I am trying to boot from a CD any Linux newer than 10.10, I get an error "No operating system found".

---

### Post by kansasnoob on 2015-07-26
I think that hardware should be capable of running any member of the Ubuntu family - once installed I think you'll want to open the Additional Drivers UI and install nvidia-current (probably nvidia 304* series) - but I'd think that hardware would boot the Trusty live DVD/USB just fine.

I notice you mentioned CD - are you using a CD to burn this? Ubuntu itself now requires a DVD due to size. Maybe Lubuntu is still CD size.

Would it be possible to create a live USB using unetbootin?

I just suspect that there is an issue with the live media.

---

### Post by coverup1128 on 2015-07-26
I meant DVD of course. The problem is I cannot boot that PC off 14.04 or 12.04 DVDs, they produce "No Operating system found" error. I am certain there is no issue with the media - When I pop the same DVDs into a laptop's DVD drive, they boot just fine.

---

### Post by sudodus on 2015-07-26
There could be a problem with the DVD drive, that it is damaged. Can you boot your old Mandriva 2009 (the main OS) and Ubuntu 9 (either 9.04 or 9.10) live from a CD/DVD disk on that drive?

Or there could be a lack of compatibility with [hybrid iso files](https://help.ubuntu.com/community/mkusb) (not very likely but possible). In that case you might be able to create a USB boot drive (pendrive alias USB stick) and boot from USB instead of CD/DVD.

See this link [Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

If the computer cannot boot from USB, you can try ***Plop*** (a CD with Plop) and chainload to the USB drive.

It is also possible that you have issues with the drivers for graphics and wifi, but it should not produce the error you are describing "No Operating system found".

---

### Post by kurt18947 on 2015-07-26
I'm not certain how relevant this is to coverup1128's problem but I see similar behavior when booting live USBs on one desktop. The problem desktop uses a 2008ish Gigabyte AMD board with Award modular BIOS. If I format a USB stick with Gparted then create a live *buntu USB stick, the USB will not boot on this one machine. I get a 'no operating system found' message.  I then try the same stick on other machines - Thinkpads, HP netbook, newer Asrock based desktop - and they all boot fine. It's just this one machine.  If I format the USB drive with Windows, I can then create a *buntu live stick and it boots fine on the problem machine.  There's something different in the way that Windows and Gparted create a FAT32 partition that this one BIOS notices and doesn't like. 

I've never had a problem booting a live DVD. Maybe try a different brand DVD or burning with a different DVD drive? Or use different burning software? I know DVDs don't use a FAT32 file system but I wonder if there's something similar going on with your DVD creation because you're getting a similar error message.

---


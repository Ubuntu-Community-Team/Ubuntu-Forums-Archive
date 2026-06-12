---
title: "Booting Ubuntu 13.10 on Asus N550JV"
date: 2013-10-28
forum: Installation &amp; Upgrades
---

### Post by paralis on 2013-10-28
I have trouble to boot a fresh install of Ubuntu 13.10 so I come here in the hope someone will be able to help me :p

I got recently a brand new laptop Asus N550JV to replace my old Acer 5920G.
The official page for the laptop at Asus.com : [http://www.asus.com/us/Notebooks_Ultrabooks/N550JV/](http://www.asus.com/us/Notebooks_Ultrabooks/N550JV/)

Specs :

[FONT=verdana]- Processor Intel i7 4700HQ Haswell 4th Gen
- 16 Gb DDR3
- 15'6 screen HD IPS 1920x1080
- Optimus technology Intel HD 4600/Nvidia GT 750M 4 Gb
- [COLOR=#333333]1TB HDD 5400 RPM
[/COLOR]- [/FONT][COLOR=#333333][FONT=Arial][FONT=verdana]Windows 8 Preinstalled (upgraded to 8.1 recently)[/FONT]

[FONT=verdana]UEFI Bios, Aptio type, (204 version originally upgraded to 207, last available version)

Now, I downloaded the 64 bits desktop 13.10 ISO and made a live USB using Universal USB Installer (also tried Unetbootin btw), tried to boot the USB stick but it was not possible.
Secure Boot does not allow it (or something else).
Disabling Secure Boot, I was able to boot the USB stick and proceed. Installation went smoothly.
I forgot to mention I had previously resized the second windows partition (named 'Data') to free 200 Gb for Linux.
Since I wanted to keep things simple, I only created a swap partition of 16 Gb and a root partition (/) with the rest of the space.
I chose to install Grub on that partition (I mean the root partition) becauseI dind't want to mess with the Windows loader and all that new (at least for me) UEFI thing.
Once back in Windows, I used EasyBCD 2.2 to add Ubuntu to the Windows loader (which I find quite elegant and way more watchable than Grub but that's juste me :p).

Then I noticed something strange. At the first run of EasyBCD, there was already an 'ubuntu' entry. I did not touch that one and added mine (Type: Grub2, Name: Ubuntu 13.10, Disk: Autolocate). Rebooted and here was my new entry Ubuntu 13.10 (but the weird 'ubuntu' entry I didn't add was nowhere to be seen). Trying to boot it, I got the, I believe, 'infamous' error message :
[/FONT]
> 
(...)
\NST\AutoNeoGrub0.mbr
0xc000007b
(...)[/FONT][/COLOR][COLOR=#333333][FONT=Arial]
[FONT=verdana]
I must say sometimes there is also like 3 lines on the top left corner but it's displayed to briefly and I can't read them.

When trying to boot Linux, Secure Boot is disabled, Fast Boot is disabled, Fast Startup (in W8) is disabled. All that doesn't seem to help much.
For EasyBCD, I also modified the entry to point it to the exact partition (not using the autolocate, just in case): no luck...
Remade several times my live USB, downloading new 64 bits ISO, using Unetbootin instead of USB Universal Installer: no luck.
Reinstalled several times: no change.
Tried to install from a 'try session' : same result.

Also tried to enable CSM (or CMS don't remember the exact term, the legacy stuff), doesn't help either.

Now, I do know Ubuntu 13.10 is, as far as I can tell, perfectly (well maybe not that perfectly lol) installed, my problem is I just can't boot/run it.

I read tons of articles here and there on installing Ubuntu on UEFI computers with preinstalled W8 but so far I'm getting nowhere.

So any suggestion gladly accepted.

Thank you for your patience ;-)

Eric

P.S. Forgot to mention another thing. About that stealth 'ubuntu' entry not showing and which popped up right at the first run of EasyBCD, I found its trace when pressing Esc at start to pick up the device to boot. It's listed there (as non UEFI partition clearly). Trying to boot that way doesn't work either but no error message just black screen and auto reboot.

[Adding this after further reading:]

From that link [/FONT][/FONT][/COLOR][FONT=verdana][https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI), I believe I may have a clue.
I remember seing during partitionning when installing an EFI partition already existing (from the preinstalled Windows 8 obviously).

I read on the mentionned page that:

[/FONT]> [COLOR=#333333][FONT=Ubuntu]if you use the manual partitioning ("Something else"), the difference is that you will have to set the /boot/efi mount point to the EFI partition[/FONT][/COLOR]

They don't say how.

Also says on the very same page:

> [COLOR=#333333][FONT=inherit]If your disk already contains an EFI partition (eg if your computer had Windows8 preinstalled), it can be used for Ubuntu too. Do not format it. It is strongly recommended to have only 1 EFI partition per disk.[/FONT][/COLOR]


Hum...

When creating an EFI partition(which is not my case since I've got already one), it is said:

> [COLOR=#333333][FONT=inherit]Mount point:[/FONT][/COLOR][COLOR=#333333][FONT=inherit] /boot/efi (remark: no need to set this mount point when using the manual partitioning, the Ubuntu installer will detect it automatically)[/FONT][/COLOR]

Right...

Found this [http://askubuntu.com/questions/315297/installing-13-04-on-an-efi-partition-share-with-windows-8](http://askubuntu.com/questions/315297/installing-13-04-on-an-efi-partition-share-with-windows-8), very interesting because it says:

> [I][FONT=arial][COLOR=#333333]Note that you don't install Linux onto the ESP in any meaningful sense. You should create Linux partitions in the normal way on your GPT disk -- say, for swap, [/COLOR]/[COLOR=#333333], and [/COLOR]/home[COLOR=#333333]. In the Ubuntu installer, you then mark the ESP as being the "EFI boot partition." Alternatively, the various automated partitioning options do this automatically.
[/COLOR][COLOR=#333333]Whatever you do, [/COLOR]do not[COLOR=#333333] create a new filesystem on the ESP, and [/COLOR]do not[COLOR=#333333] remove the "boot flag" from the ESP or set a "boot flag" on any other partition.[/COLOR][/FONT][/I]

Note that ESP means here the EFI partition.

Anyway still investigating.

[COLOR=#333333][FONT=verdana][Added on 10/31:]

Booting my live usb ubuntu, I ran Boot-repair to 'fix' well that 'thing' since it's supposed to fix grub and uefi troubles. All went nicely until I got the following message:

> (...) Locked-ESP detected

So after googling that error, I found out that there is indeed a known bug with such message. The bug is described here [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829) and probably else where.

According to the people talking about that stuff on those pages, it's either a real locked up EFI partition (ESP) which prevents Ubuntu installation to write the files where it should OR, somehow, the files are corrupted (maybe for the same reason). Apparently, most people don't think the ESP is screwed but rather only the ubuntu file needed to boot in EFI mode.

Creating a second EFI partition with the bootflag doesn't seem to fix it (haven't tried).

Anyway, for info: [/FONT][/COLOR][http://paste.ubuntu.com/6332633/](http://paste.ubuntu.com/6332633/)

And the quest goes on...

Editing this, three weeks later or so : I'm stuck and a lil bit fed up struggling with that issue. Can't run Ubuntu on my laptop because of some UEFI weirdness... Sadly, I doubt I'm the only one. Maybe Ubuntu will fix that, one never knows...

---

### Post by Punk Fetish on 2013-11-30
Awful news, I just bought the same computer and I'm having all the problems you describe.

I'll let you know if i find something that can be done. Please let me know if you were able to fix this too.

Good luck

---

### Post by Punk Fetish on 2013-11-30
Hey I was able to get the Asus N550JV notebook to dobleboot OK following this guide:

[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

Good luck!

---

### Post by motifman on 2013-12-12
Hi, I just got this laptop too and have got it dual-booting OK now too. Punk Fetish's link was great, [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) helped too.

I burnt a Ubuntu DVD from windows, disabled secure boot and fast boot in the BIOS and the DVD install worked OK. The BIOS is a bit strange, it doesn't let you set DVD as a boot priority unless there is a DVD in when you boot. Possibly if you're having trouble with a USB install, a DVD might be worth trying?

I still have to try and get sound working, [http://askubuntu.com/a/371567](http://askubuntu.com/a/371567) says you can upgrade to a 3.12 kernel to fix it.

---

### Post by paralis on 2013-12-17
Thank you guys, investigating your links ;-)

---

### Post by oldfred on 2013-12-18
Not sure it applies to your brand or not, but seems to be an Intel issue.
Some of the new Haswell systems are having issues installing in UEFI mode with the Intel          NIC (Integrated Network Interface Controller) turned on. But turning it off means the hard wired Ethernet connection does not work. Wireless still does.

---

### Post by paralis on 2013-12-18
Would it be possible to turn it off, install and then turn it back on or at least has this been tried on some other brands?

---

### Post by oldfred on 2013-12-18
I saw one user say he could not turn it on. But when he installed in BIOS mode it worked. Do not know if a UEFI/BIOS update will eventually fix it or if it is a Ubuntu/grub issue. Often Linux has to work around systems that work only with Windows.

The disadvantage of BIOS mode is that you cannot dual boot from grub menu but only from UEFI menu or one time boot key may also work. And depending on system you may have to turn UEFI on/off or BIOS/CSM on/off. It seems a lot of the newer ones know if booting a BIOS system it works or if booting a UEFI system it works. But you cannot have secure boot on as that is UEFI only.

---

### Post by Lîtus on 2013-12-26
Hi!

I was trying to install Ubuntu in my brand new Asus N550JV (same as in the original post of this thread) but I'm not having success. I did everything stated in the links:

[LIST=1]
[*]I resized Win8 partitions in order to have free unassigned space for Ubuntu.
[*]At BIOS menu, I disabled **Secure boot** and **Fast boot**.
[*]I disabled **Fast startup** in Windows 8.1 (yes, I've upgraded it).
[*]I started Ubuntu from a LiveDVD. Starting it from a LiveUSB has been absolutely impossible; I tried CSM mode (i.e. Legacy BIOS mode) and UEFI mode, but my USB drive did never show up. Following **motifman** suggestions I was able to boot it from a DVD (you have to start the BIOS menu with the actual LiveDVD inside the BD unit, else it won't let you choose it as a boot option)
[*]At the beginning, the installer showed a message saying that there was no other OS installed. I kindda expected it and chose manually manage partitions. 
[*]I set the already existing EFI partition (it comes along with Windows8 pre-installations) as Ubuntu's EFI partition. I did not manually set the mount point during installation because Ubuntu detected the partition automatically, however, I've checked and it is correctly mounted on **/boot/efi**. 
[*]When the installing process finished, I rebooted and yes, Grub showed both Windows **AND** Ubuntu. If I choose to boot with Windows, everything goes well.
[/LIST]

However, when I try to boot Ubuntu, I get stuck in the purple screen. I can certainly start recovery mode but didn't try anything further than checking partitions and unsuccessfully running startx. Does anyone know how to solve this? I didn't read anything similar in the linked pages or in previous posts...

Thanks!!

---

### Post by oldfred on 2013-12-26
If it is Optimus you have both Intel & nVidia. Do you have control over which it uses to boot or is it automatic?

With nVidia you use nomodeset. But Intel needs different settings.
       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[URL="https://help.ubuntu.com/community/BootOptions"]https://help.ubuntu.com/community/BootOptions

      [/URL]
 Some other Intel boot options Each line is one that may work
acpi_osi=Linux  acpi_backlight=vendor
 i915.i915_enable_rc6=1

    
Even though this is on Dell, the comment is on i915 Intel.
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
> Running in legacy BIOS mode or in UEFI mode both work, but for now  you'll need to enable "Legacy Option ROM" in the BIOS if you're running  in UEFI mode because of the display's backlight. This is because of an  issue with the Intel i915 driver that currently affects several systems  from many vendors. If you don't enable this BIOS option, the backlight  will be stuck at the lowest setting in Linux.


---

### Post by Lîtus on 2013-12-26
Thanks oldfred! GPU drivers were the exact the problem. I managed to boot with -nomodeset and once logged in I installed Bumblebee and Nvidia drivers following [these]("http://askubuntu.com/questions/348614/bumblebee-on-ubuntu-13-04-with-geforce-750m-and-driver-319") instructions. 
```
sudo apt-get install bumblebee primus primus-libs-ia32:i386 linux-headers-generic
sudo apt-get install bumblebee-nvidia nvidia-319 nvidia-settings-319
```

Also, upgrading Linux kernel version enabled audio playback, which wasn't working at the beginning. Apart from that, during Ubuntu splash screen I'm still seeing some sort of Bluetooth driver message (error I think), and the screen brightness control is not working (I have it at 100%).

---

### Post by lokz2 on 2014-01-25
I have Asus N550JV With Nvidia GT 750M (4GB) and after installing, when I try to run firefox with optirun I get this in terminal:


~$ optirun firefox


(process:2861): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed


What is wrong?

---

### Post by erikas3 on 2014-12-11
Guys I am not using Ubuntu, because I am fan of something very very basic - Arch Linux. Here, started by some people and for now I am alone who edits this wiki page: [https://wiki.archlinux.org/index.php/ASUS_N550JV](https://wiki.archlinux.org/index.php/ASUS_N550JV)

You guys can take some useful information, because I have done a lot of research there and posted almost everything. :) this laptop basically works now 10/10! :)

---

### Post by coffeecat on 2014-12-11
Old thread about a now obsolete version of Ubuntu.

Closed

---


---
title: "Adding another distro to GRUB2?"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by zak89 on 2010-07-02
I've been using Ubuntu Lucid as my main OS lately, and it's working well. However, I'm an long-time openSUSE user, and I'd like to try out the latest openSUSE 11.3 RC. I've been busy with work recently but it seems to have slowed a bit and I'd like to install 11.3RC2 on my spare partition (over an unused Linux Mint install). However, I need to be able to access my Ubuntu install at least until I have openSUSE set up to my liking, which probably won't be till after 11.3 release (yes, I'll have to go through this again, but hey, I don't actually mind). The problem of course is that Ubuntu uses GRUB2, so it won't be recognized by openSUSE's legacy Grub.

So, I'm guessing my best course of action would be to install openSUSE and customise the bootloader installation so that Ubuntu's GRUB2 stays in the MBR, then try to add openSUSE to Ubuntu's GRUB2 menu. Does anyone know if this is would work? Specifically, has anyone dealt with this issue before? I've never worked with GRUB2 so I'm a bit in the dark here.

---

### Post by lechien73 on 2010-07-02
Yes that should work. If memory serves, openSUSE still uses Grub Legacy rather than Grub 2, so at the installation stage, do not install SUSE's boot loader.

When you have installed SUSE, boot into Lucid, open a terminal window and type:

```
sudo apt-get install libdebian-installer4
sudo os-prober
sudo  update-grub

```
openSUSE should now appear in your Grub2 list of installed operating systems.

---

### Post by zak89 on 2010-07-02
Thanks, that worked perfectly.

---

### Post by rsrini on 2010-08-07
Hi,

I had tried suse 11.3 on top of ubuntu 10.4 with grub2. While installing suse 11.3 i selected the option of don't install any boot loader. Booted ubuntu and added entries in /etc/grub.d/40_custom file. Did update-grub.  But suse 11.3 not booting properly. It gives lot of failed messages while booting and gives login prompt. But not allowing to login. I tried so many times reinstalling suse 11.3 again. I don't want suse to mess up my grub2. Any help is appreciated.
R.Srinivasan.

---

### Post by 23dornot23d on 2010-08-07
When I installed SUSE 11,3 
I put its boot loader on the same partition that I installed it to

Then just boot your Ubuntu up if thats what controls Grub2

and do a  

update-grub

---

### Post by rsrini on 2010-08-07
Hi,

Thanks for the help. It works. I had kept the /boot for suse 11.3 as inside /root-suse. Added entries in 40_custom file. 

But i have other gdm problem with suse 11.3 - failed to start gdm.

---

### Post by 23dornot23d on 2010-08-07
When I have problems with gdm ...... 

I install kdm and it usually gets me up and running ......

do you have error messages ..... or screenshots ...

I will try to help sort it if you want .... actually you should see the boot messages 
while it is trying to go into gdm ,,,, I photograph them and post them when things
are not right.

Can you get to the console ..... ok ... and log in in safe mode

What graphics card do you use .... is it Nvidia ? if so which one

[some of the problems I had are here with OS's I try out and a explanation of how I fixed them]("https://sites.google.com/site/23dornot23d/trying-these-operating-systems")

---

### Post by rsrini on 2010-08-08
I tried suse 11.3 with KDE too. The same problem. Ubuntu 10.04 working fine. Fedora 13 working fine. XP also working fine. Only i am struggling with Suse 11.3. The only thing i may be doing wrong is selecting "don't install any boot loader option" while installation. I will try that too now. I hope i will get back my ubuntu. 

I could not able to find the error messages. The video in mother board chipset ATI radeon HD 4200. I tried to installing the latest 10.7 catalyst SW from ATI site. KDM log file

(i.e., not from libraries and external programs/scripts it uses) go to the
daemon.* syslog facility; check your syslog configuration to find out to which
file(s) it is logged. PAM logs messages related to authentication to authpriv.*.
********************************************************************************


X.Org X Server 1.8.0
Release Date: 2010-04-02
X Protocol Version 11, Revision 0
Build Operating System: openSUSE SUSE LINUX
Current Operating System: Linux hnkhs 2.6.34-12-desktop #1 SMP PREEMPT 2010-06-29 02:39:08 +0200 x86_64
Kernel command line: root=/dev/sda5    resume=/dev/disk/by-id/ata-ST3500418AS_9VMFJGVE-part3 splash=silent quiet showopts vga=0x31a
Build Date: 05 July 2010  09:27:36PM
 
Current version of pixman: 0.18.0
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Aug  8 15:10:36 2010
(==) Using config directory: "/etc/X11/xorg.conf.d"
(EE) Failed to load module "fglrx" (module does not exist, 0)
(EE) FATAL: RadeonHD presently does not work with kernel modesetting (KMS).
Please disable KMS in your kernel.
(II) [KMS] Kernel modesetting enabled.
(EE) No input driver/identifier specified (ignoring)
(EE) No input driver/identifier specified (ignoring)
QFont::fromString: Invalid description 'Serif,20,5,0,50,0'
QFont::fromString: Invalid description 'Sans Serif,10,5,0,50,0'
QFont::fromString: Invalid description 'Sans Serif,10,5,0,75,0'

---

### Post by 23dornot23d on 2010-08-08
It looks like the problem lies with setting the graphics up ..... but I have no experience with ATI radeon HD 4200

and there are not that many articles to do with SUSE and success with this yet

Its not the installation of the boot  .... changing the boot will not resolve this .

The errors seem to be with the graphics card and modesetting ......

---

### Post by rsrini on 2010-08-09
Finally i could be able to boot all 4 os (XP, ubuntu 10.04, suse 11.3, Fedora13). We have to install the boot loader (grub 0.97) from suse and also inside the /root-suse boot location. I had a separate boot partition. If we give the separate boot partition to suse as /boot then after reinstalling the grub2 from ubuntu the same problem occurs. So what i did was, while installing suse 11.3 i did not gave any boot partition and asked to install grub 0.97 as boot loader inside its own root partition. With ubuntu live CD i reinstalled the grub2 with proper entries in /etc/fstab and /etc/grub.d/40_custom. Now i am able to see grub2 menu and it boots both suse and ubuntu along with other oss. But i don't know how to update grub2 after editing the 40_custom file from live cd. I can do it once i login to ubuntu. I am using full custom boot menu entries in grub2. I love ubuntu and grub2. It is very good to debug. Every body (suse/fedora) has to move to grub2 soon. Thanks for all your good support. Moral support is more important than the actual technical info. We have a feeling that somebody is there to listen us.

R.Srinivasan.
Bangalore - India

---

### Post by rsrini on 2010-08-09
It broke again the suse. Same problem. I will post if i have success

---

### Post by oldfred on 2010-08-09
From Ubuntu's grub there are a couple of ways. Most linux's have a link in root to the most current kernel. ( not sure about suse)

Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest boatable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

If you have installed old grub to the root partition you can chainload to it and the second menu will be the updated version of that install.

This is my entry to another install of old grub. Adjust drive and partitions to the partitions where you have installed grub to the boot sector.

menuentry "Chainload Other Systems Grub Menu on sdc1" {
set root=(hd2,1)
chainloader +1
}

If you do not boot from sda, the drive number may not be what you would normally think. First drive to boot is hd0 and then they will be in order after that. When I boot sdc it is hd0, and then my sda is hd1.

---

### Post by zarthon on 2010-08-09
You could boot to Ubuntu and go back to #2 in the thread and try os prober to set up SUSE instead of using a custom grub2 entry. It is unclear to me that you have tried this and it succeeded for zak89  who started this thread. Anyway I will assume you've tried it and it did not work. 

My understanding is that when booting with grub .97 packaged with suse gdm works but when booting from grub2 gdm fails.  At this point are you dropped down to a shell prompt in suse? 

First the two operating systems should have different partitions mapped to /boot. This could be accomplished by just mapping a drive to root (/) and not having a separate /boot mount for one of the operating systems. This means the Ubuntu and suse root lines in the grub2 configuration will be set to different partitions. A separate /boot will prevent trying to boot suse with an Ubuntu kernel and prevent /boot/grub directories being mixed together.

If you get a suse prompt use it to figure out what is going on. At this point grub or gurb2 should be unloaded. The effect the boot loader should have on a running system is simply through the kernel and initrd parameters. You can safely remove "quite" and "splash" so that you can follow the boot sequence on screen as it occurs. I'd also try booting without the vga=0x31a argument. This only effects the splash screen and the command prompts before X is loaded.

The following log files may help you figure out what is happening:
/var/log/Xorg*
/var/log/boot.log
/var/log/messages

I'd first compare your boot menu entries for each grub. Make sure that the kernel and initrd lines in your 40_custom have the same kernel and initrd. Note any differences in kernel arguments. Make sure they are what you intend. Name the SUSE entry something distinctive so you are certain you are booting from your custom entry and not one created by the os prober.

Before booting highlight the custom suse entry and press e to edit the boot lines to double check that the kernel parameters and initrd file match what you intend. 

You might try to use the "vesa" driver which does not require a kernel module by changing your /etc/X11/xorg.config file. 
In the ***Device section*** change the driver line to 
```
Driver "vesa"
```

If this succeeds something is going on with the driver. Prehaps the kernel helper module is not loading.
 
You might try installing grub2 in the mbr and chain loading grub installed in the suse partition.

---

### Post by 23dornot23d on 2010-08-10
A problem that does stop the boot up is the graphics being detected correctly ...... and the errors that you posted seem to confirm that.

If grub2 gets you to the right place and starts the boot process as seems to be the case here - it has pretty much done its job.

____________________________________________________________

I do not chainload to SUSE and I do not use a Custom loader for it  ...... and it boots just fine for me from LINUX MINT's GRUB2.

So What I do use different is the **Grub2 Boot loader from Mint **9
( The reason being - I have no real success with the **Ubuntu Grub2 loader** - no idea why its different !!! - but this is another option you could try if you believe its the bootloader and not the graphics at fault ...... as mentioned using VESA should let you know)

These are my two entries for SUSE 11.3

```

menuentry "openSUSE 11.3 (on /dev/sdc3)" {
    insmod ext2
    set root='(hd2,3)'
    search --no-floppy --fs-uuid --set 638f03de-52c1-49b0-ab7b-782d124d1c8f
    linux /boot/vmlinuz-2.6.34-12-default root=/dev/disk/by-id/usb-Seagate_Desktop_2GHJXRXN-0:0-part3 resume=/dev/disk/by-id/ata-ST9250827AS_5RG76V48-part9 splash=silent quiet showopts vga=0x314
    initrd /boot/initrd-2.6.34-12-default
}
menuentry "Failsafe -- openSUSE 11.3 (on /dev/sdc3)" {
    insmod ext2
    set root='(hd2,3)'
    search --no-floppy --fs-uuid --set 638f03de-52c1-49b0-ab7b-782d124d1c8f
    linux /boot/vmlinuz-2.6.34-12-default root=/dev/disk/by-id/usb-Seagate_Desktop_2GHJXRXN-0:0-part3 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x314
    initrd /boot/initrd-2.6.34-12-default

```Both work ......  

My *SUSE 11.3 is on an external USB drive ...... but I cannot see that making any difference to it booting or not.

The above is just for info ,,,, to see if you can spot anything that may be different in the boot commands.

Here is the way UBUNTU GRUB tries to set up the same OS 
All shown in red ..... as it does not work at all for me ........ I just get an error saying it cannot find the drive or partition id
but why ...... it cannot use the uuid I do not know as its the same as the other entry that works ..... 
( it seems it has no idea which drive to look at -[COLOR=Red](hd0,msdos3)[/COLOR]  )

I may be reading something wrong here - so forgive me if this does not seem to be the case .........

( I have found on my system that the USBs can swap positions depending on a COLD or WARM boot - 
I nearly always COLD boot now .... but if I do warm boot it finds my other boot loader on the USB drive )
reason they swap I believe is due to the slow identification of a USB drive from a cold start. 

My definition of Cold Boot .....  To power down the computer and letting the hard drives spin down.
My definition of Warm Boot ...... To do a restart from a previous OS ...... with my hard drives are still powered up.

 

```


[COLOR=Red]menuentry "openSUSE 11.3 (on /dev/sda3)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 638f03de-52c1-49b0-ab7b-782d124d1c8f
    linux /boot/vmlinuz-2.6.34-12-default root=/dev/disk/by-id/usb-Seagate_Desktop_2GHJXRXN-0:0-part3 resume=/dev/disk/by-id/ata-ST9250827AS_5RG76V48-part9 splash=silent quiet showopts vga=0x314
    initrd /boot/initrd-2.6.34-12-default
}
menuentry "Failsafe -- openSUSE 11.3 (on /dev/sda3)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 638f03de-52c1-49b0-ab7b-782d124d1c8f
    linux /boot/vmlinuz-2.6.34-12-default root=/dev/disk/by-id/usb-Seagate_Desktop_2GHJXRXN-0:0-part3 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x314
    initrd /boot/initrd-2.6.34-12-default
}
[/COLOR]

```

---

### Post by rsrini on 2010-08-11
Today i had tried again and installed suse 11.3 with all the drivers (and os) update etc. I had installed the ATI driver from their repository using Yast. It was booting fine with Grub 0.97. I was able to login and no issues with video. The ATI catalyst sw is up. I am able to configure the display. I had restarted the system two times and was able to use suse without any graphics or display issues. Since grub1 cannot able to understand the ubuntu grub2 i was not able to boot ubuntu. Only suse 11.3 was working fine.

I have a separate boot partition which has ubuntu and fedora image files. For the above suse 11.3 installation i had not given that common boot partition. It puts the image files and grub loader (stage 1.5 etc) inside suse's root directory (/root-suse/boot). In the suse file manager i could see the common boot partition as a unmounted drive, because i had not included it in the fstab entry. There are no confusion between ubuntu boot files and suse boot files and between grub1 and grub2.

I booted with ubuntu live cd and did the grub install to put the grub2. Then i was able to boot ubuntu as usual and fedora too. I had updated the 40_custom entries to point the correct suse / partition (image files) and it is booting with lot of failed error messages. Finally comes to login prompt. If i login either as user or root both it gives "error in service module" and struck there. I am not even able to get the prompt. The same type of error messages and behaviour in all my 10 to 12 installation attempts.

I feel grub 2 is doing its job of loading the kernal and intird images. But the suse may be expecting some thing more since it has grub1. The issue with gdm or video drivers are ruled out now.

I have the following options. I need a live cd of suse. (The current suse 11.3 installation cd gives only rescue prompt with very limited commands. They have removed lot of repair options which was there with 11.1 and 11.2. I have both the old dvds. I tried some time back with 11.2 cd in repair mode. It did not work.) With that live cd i have to install grub0.97 again and see if suse boots again with that. Second option is to  install grub2 in suse from the suse rescue prompt. I don't know will it be possible.

I think the chain loader option from grub2 to grub1 should work. I will try that also. But finally i don't want two chain loaders. I want to have a single boot menu to boot all os. I did already this with grub1. One more pc still working with 5 os - XP, ubuntu 9.04, suse 11.1, mandriva spring, fedora 11. All are booting from single grub 0.97 boot menu.

Once i am confident with grub2 in this new pc (AMD phenom II 550 BE, Asus M4A785T-M motherboard, 2GB DDR3 1333MHz) then only i want to update the other pc with grub2 and os upgrade.

This new pc is for a village school. I am suggesting them to learn and use only ubuntu. Just for my learning purpose i am keeping three linux os in that. Also they can boot and see some times if it is there. I am planning to use this pc with 10 different client pcs with only monitor keyboard etc for the school children. Looking for to buy n-computing like devices. Preference will be for AMD based (like Geode) processor. Still not finalised. 

I want to be part of spreading linux in India. Currently no time - working in Analog Devices bangalore. I need to make a good ununtu installation dvd without the need for internet connection. I will need your help in future when i get some free time.

---

### Post by 23dornot23d on 2010-08-11
Hi .... I wish you every success in getting this working and the school computer to boot
from one Menu ..... so onward .....

> 
I booted with ubuntu live cd and did the grub install to put the grub2.  Then i was able to boot ubuntu as usual and fedora too. I had updated  the 40_custom entries to point the correct suse / partition (image  files) and it is booting with lot of failed error messages. Finally  comes to login prompt. If i login either as user or root both it gives  "error in service module" and struck there. I am not even able to get  the prompt. The same type of error messages and behaviour in all my 10  to 12 installation attempts.
Can you explain what the failed error messages are prior to the  "error in service module"

_____________________________________________________________________

so 11.3 boots from 0.97 Grub and I presume that is worked from 1.5 as that is what it comes with.
(Which proves to me that there is nothing wrong with your hardware or the graphics drivers)

> 
It was booting fine with Grub 0.97. I was able to login and no issues  with video. The ATI catalyst sw is up. I am able to configure the  display.
Grub2 has dome its job to get the kernel and intrd running.

> 
I feel grub 2 is doing its job of loading the kernal and intird images.  But the suse may be expecting some thing more since it has grub1.
Which is true otherwise the error messages would not appear .... it would stop before here ....... what we do need are the error messages.
I take [photos here if that is the only way]("http://i37.tinypic.com/2vtxnuv.jpg") to see the info on the screen at boot - 
all my systems run from [ONE MENU ]("http://i33.tinypic.com/kd67eu.jpg").... (I will purge my old versions one day)

( There are quite a few tasks go on in the background as GRUB2 loads up ...... 
a lot of parallel processes are taking place ..... to do with detecting things like hard drives and graphics etc .... )

What is interesting is that the GRUB2 boot loader is running the kernel .... 
( So it is pointing to the correct place and booting SUSE 11.3 - [COLOR=Blue]this was my main problem on my system this did not work[/COLOR] )

___________________________________________________________________

What might be going wrong is what happens behind the scenes as GRUB2 is working.

[My initial search for what I think is the problem]("http://www.google.com/custom?hl=en&client=pub-5386907765195439&cof=FORID%3A13%3BAH%3Aleft%3BS%3Ahttp%3A%2F%2Fwww.linuxmint.com%3BCX%3AGoogle%3BL%3Ahttp%3A%2F%2Fwww.linuxmint.com%2Fimg%2Fcse.png%3BLH%3A100%3BLP%3A1%3BVLC%3A%23663399%3BDIV%3A%23336699%3B&adkw=AELymgVh3wuBmH_pE4ZN82p8Mru9FdU63BtIQr_PXZjqdZMCTvwbZWI6qEElsqKMH6vhV7elIU_BfwTVQJwzlIUv1q-QmJ3ksOJ4X5Tofy_EHWwPwmSleRo&channel=5656732914&q=error+in+service+module+pam+plymouth&btnG=Search&cx=002683415331144861350%3Atsq8didf9x0")
___________________________________________________________________

Although you get errors in SUSE 11.3 ......can you log in using safe mode and get a console up.

[COLOR=Blue]
Another thing to look at are the SUSE boot log files .......
[/COLOR]

---

### Post by rsrini on 2010-08-11
The boot messages from file

klogd 1.4.1, log source = ksyslog started.
<5>[    0.000000] Linux version 2.6.34-12-desktop (geeko@buildhost) (gcc version 4.5.0 20100604 [gcc-4_5-branch revision 160292] (SUSE Linux) ) #1 SMP PREEMPT 2010-06-29 02:39:08 +0200
<6>[    0.000000] Command line: root=/dev/disk/by-id/ata-ST3500418AS_9VMFJGVE-part7 resume=/dev/disk/by-id/ata-ST3500418AS_9VMFJGVE-part3 splash=silent quiet vga=0x31a
<6>[    0.000000] BIOS-provided physical RAM map:
<6>[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
<6>[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
<6>[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
<6>[    0.000000]  BIOS-e820: 0000000000100000 - 000000006fe70000 (usable)
<6>[    0.000000]  BIOS-e820: 000000006fe70000 - 000000006fe88000 (ACPI data)
<6>[    0.000000]  BIOS-e820: 000000006fe88000 - 000000006fed0000 (ACPI NVS)
<6>[    0.000000]  BIOS-e820: 000000006fed0000 - 000000006ff00000 (reserved)
<6>[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
<6>[    0.000000] NX (Execute Disable) protection: active
<6>[    0.000000] DMI present.
<5>[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
<7>[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
<7>[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
<7>[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
<6>[    0.000000] No AGP bridge found
<6>[    0.000000] last_pfn = 0x6fe70 max_arch_pfn = 0x400000000
<7>[    0.000000] MTRR default type: uncachable
<7>[    0.000000] MTRR fixed ranges enabled:
<7>[    0.000000]   00000-9FFFF write-back
<7>[    0.000000]   A0000-EFFFF uncachable
<7>[    0.000000]   F0000-FFFFF write-protect
<7>[    0.000000] MTRR variable ranges enabled:
<7>[    0.000000]   0 base 000000000000 mask FFFFC0000000 write-back
<7>[    0.000000]   1 base 000040000000 mask FFFFE0000000 write-back
<7>[    0.000000]   2 base 000060000000 mask FFFFF0000000 write-back
<7>[    0.000000]   3 disabled
<7>[    0.000000]   4 disabled
<7>[    0.000000]   5 disabled
<7>[    0.000000]   6 disabled
<7>[    0.000000]   7 disabled
<6>[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
<6>[    0.000000] Scanning 0 areas for low memory corruption
<6>[    0.000000] modified physical RAM map:
<6>[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
<6>[    0.000000]  modified: 0000000000010000 - 000000000009ec00 (usable)
<6>[    0.000000]  modified: 000000000009ec00 - 00000000000a0000 (reserved)
<6>[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
<6>[    0.000000]  modified: 0000000000100000 - 000000006fe70000 (usable)
<6>[    0.000000]  modified: 000000006fe70000 - 000000006fe88000 (ACPI data)
<6>[    0.000000]  modified: 000000006fe88000 - 000000006fed0000 (ACPI NVS)
<6>[    0.000000]  modified: 000000006fed0000 - 000000006ff00000 (reserved)
<6>[    0.000000]  modified: 00000000ff700000 - 0000000100000000 (reserved)
<7>[    0.000000] initial memory mapped : 0 - 20000000
<6>[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
<6>[    0.000000] Using GB pages for direct mapping
<6>[    0.000000] init_memory_mapping: 0000000000000000-000000006fe70000
<7>[    0.000000]  0000000000 - 0040000000 page 1G
<7>[    0.000000]  0040000000 - 006fe00000 page 2M
<7>[    0.000000]  006fe00000 - 006fe70000 page 4k
<7>[    0.000000] kernel direct mapping tables up to 6fe70000 @ 16000-19000
<6>[    0.000000] RAMDISK: 3753a000 - 37ff0000
<4>[    0.000000] ACPI: RSDP 00000000000fb3e0 00024 (v02 ACPIAM)
<4>[    0.000000] ACPI: XSDT 000000006fe70100 0005C (v01 061810 XSDT1634 20100618 MSFT 00000097)
<4>[    0.000000] ACPI: FACP 000000006fe70290 000F4 (v03 061810 FACP1634 20100618 MSFT 00000097)
<4>[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0000000000000000/1 (20100121/tbfadt-557)
<4>[    0.000000] ACPI: DSDT 000000006fe70450 0E706 (v01  A1423 A1423001 00000001 INTL 20060113)
<4>[    0.000000] ACPI: FACS 000000006fe88000 00040
<4>[    0.000000] ACPI: APIC 000000006fe70390 0007C (v01 061810 APIC1634 20100618 MSFT 00000097)
<4>[    0.000000] ACPI: MCFG 000000006fe70410 0003C (v01 061810 OEMMCFG  20100618 MSFT 00000097)
<4>[    0.000000] ACPI: OEMB 000000006fe88040 00072 (v01 061810 OEMB1634 20100618 MSFT 00000097)
<4>[    0.000000] ACPI: SRAT 000000006fe7f450 000A0 (v01 AMD    FAM_F_10 00000002 AMD  00000001)
<4>[    0.000000] ACPI: HPET 000000006fe7f4f0 00038 (v01 061810 OEMHPET  20100618 MSFT 00000097)
<4>[    0.000000] ACPI: SSDT 000000006fe7f530 00458 (v01 A M I  POWERNOW 00000001 AMD  00000001)
<7>[    0.000000] ACPI: Local APIC address 0xfee00000
<6>[    0.000000] SRAT: PXM 0 -> APIC 0x00 -> Node 0
<6>[    0.000000] SRAT: PXM 0 -> APIC 0x01 -> Node 0
<6>[    0.000000] SRAT: Node 0 PXM 0 0-a0000
<6>[    0.000000] SRAT: Node 0 PXM 0 100000-80000000
<7>[    0.000000] NUMA: Allocated memnodemap from 18000 - 19040
<7>[    0.000000] NUMA: Using 20 for the hash shift.
<6>[    0.000000] Initmem setup node 0 0000000000000000-000000006fe70000
<6>[    0.000000]   NODE_DATA [0000000001d96340 - 0000000001daa33f]
<7>[    0.000000]  [ffffea0000000000-ffffea00019fffff] PMD -> [ffff880002600000-ffff880003ffffff] on node 0
<4>[    0.000000] Zone PFN ranges:
<4>[    0.000000]   DMA      0x00000010 -> 0x00001000
<4>[    0.000000]   DMA32    0x00001000 -> 0x00100000
<4>[    0.000000]   Normal   empty
<4>[    0.000000] Movable zone start PFN for each node
<4>[    0.000000] early_node_map[2] active PFN ranges
<4>[    0.000000]     0: 0x00000010 -> 0x0000009e
<4>[    0.000000]     0: 0x00000100 -> 0x0006fe70
<7>[    0.000000] On node 0 totalpages: 458238
<7>[    0.000000]   DMA zone: 56 pages used for memmap
<7>[    0.000000]   DMA zone: 0 pages reserved
<7>[    0.000000]   DMA zone: 3926 pages, LIFO batch:0
<7>[    0.000000]   DMA32 zone: 6211 pages used for memmap
<7>[    0.000000]   DMA32 zone: 448045 pages, LIFO batch:31
<6>[    0.000000] ACPI: PM-Timer IO Port: 0x808
<7>[    0.000000] ACPI: Local APIC address 0xfee00000
<6>[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
<6>[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
<6>[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
<6>[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
<6>[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
<6>[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
<6>[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
<6>[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
<6>[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
<6>[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
<7>[    0.000000] ACPI: IRQ0 used by override.
<7>[    0.000000] ACPI: IRQ2 used by override.
<7>[    0.000000] ACPI: IRQ9 used by override.
<6>[    0.000000] Using ACPI (MADT) for SMP configuration information
<6>[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
<6>[    0.000000] SMP: Allowing 6 CPUs, 4 hotplug CPUs
<7>[    0.000000] nr_irqs_gsi: 24
<7>[    0.000000] early_res array is doubled to 64 at [191a0 - 1999f]
<6>[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
<6>[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
<6>[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
<6>[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
<6>[    0.000000] Allocating PCI resources starting at 6ff00000 (gap: 6ff00000:8f800000)
<6>[    0.000000] Booting paravirtualized kernel on bare hardware
<6>[    0.000000] setup_percpu: NR_CPUS:512 nr_cpumask_bits:512 nr_cpu_ids:6 nr_node_ids:1
<6>[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff880001e00000 s84136 r8192 d22360 u262144
<6>[    0.000000] pcpu-alloc: s84136 r8192 d22360 u262144 alloc=1*2097152
<6>[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 - - 
<4>[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 451971
<4>[    0.000000] Policy zone: DMA32
<5>[    0.000000] Kernel command line: root=/dev/disk/by-id/ata-ST3500418AS_9VMFJGVE-part7 resume=/dev/disk/by-id/ata-ST3500418AS_9VMFJGVE-part3 splash=silent quiet vga=0x31a
<6>[    0.000000] bootsplash: silent mode.
<6>[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
<6>[    0.000000] Checking aperture...
<6>[    0.000000] No AGP bridge found
<6>[    0.000000] Node 0: aperture @ d012000000 size 32 MB
<6>[    0.000000] Aperture beyond 4GB. Ignoring.
<6>[    0.000000] Subtract (50 early reservations)
<6>[    0.000000]   #1 [0001000000 - 0001d95fb8]   TEXT DATA BSS
<6>[    0.000000]   #2 [003753a000 - 0037ff0000]         RAMDISK
<6>[    0.000000]   #3 [0001d96000 - 0001d9633c]             BRK
<6>[    0.000000]   #4 [00000ff790 - 0000100000]   BIOS reserved
<6>[    0.000000]   #5 [00000ff780 - 00000ff790]    MP-table mpf
<6>[    0.000000]   #6 [000009ec00 - 00000f0910]   BIOS reserved
<6>[    0.000000]   #7 [00000f0a6c - 00000ff780]   BIOS reserved
<6>[    0.000000]   #8 [00000f0910 - 00000f0a6c]    MP-table mpc
<6>[    0.000000]   #9 [0000010000 - 0000012000]      TRAMPOLINE
<6>[    0.000000]   #10 [0000012000 - 0000016000]     ACPI WAKEUP
<6>[    0.000000]   #11 [0000016000 - 0000018000]         PGTABLE
<6>[    0.000000]   #12 [0000018000 - 0000019040]      MEMNODEMAP
<6>[    0.000000]   #13 [0001d96340 - 0001daa340]       NODE_DATA
<6>[    0.000000]   #14 [0001daa340 - 0001dab340]         BOOTMEM
<6>[    0.000000]   #15 [0000019040 - 0000019190]         BOOTMEM
<6>[    0.000000]   #16 [00025ac000 - 00025ad000]         BOOTMEM
<6>[    0.000000]   #17 [00025ad000 - 00025ae000]         BOOTMEM
<6>[    0.000000]   #18 [0002600000 - 0004000000]        MEMMAP 0
<6>[    0.000000]   #19 [0001dab340 - 0001dc3340]         BOOTMEM
<6>[    0.000000]   #20 [0001dc3340 - 0001ddb340]         BOOTMEM
<6>[    0.000000]   #21 [0001ddc000 - 0001ddd000]         BOOTMEM
<6>[    0.000000]   #22 [0001ddb340 - 0001ddb381]         BOOTMEM
<6>[    0.000000]   #23 [0001ddb3c0 - 0001ddb403]         BOOTMEM
<6>[    0.000000]   #24 [0001ddb440 - 0001ddb638]         BOOTMEM
<6>[    0.000000]   #25 [0001ddb640 - 0001ddb6a8]         BOOTMEM
<6>[    0.000000]   #26 [0001ddb6c0 - 0001ddb728]         BOOTMEM
<6>[    0.000000]   #27 [0001ddb740 - 0001ddb7a8]         BOOTMEM
<6>[    0.000000]   #28 [0001ddb7c0 - 0001ddb828]         BOOTMEM
<6>[    0.000000]   #29 [0001ddb840 - 0001ddb8a8]         BOOTMEM
<6>[    0.000000]   #30 [0001ddb8c0 - 0001ddb928]         BOOTMEM
<6>[    0.000000]   #31 [0001ddb940 - 0001ddb9a8]         BOOTMEM
<6>[    0.000000]   #32 [0001ddb9c0 - 0001ddba28]         BOOTMEM
<6>[    0.000000]   #33 [0001d95fc0 - 0001d95fe0]         BOOTMEM
<6>[    0.000000]   #34 [0001ddba40 - 0001ddbac8]         BOOTMEM
<6>[    0.000000]   #35 [0001ddbb00 - 0001ddbb88]         BOOTMEM
<6>[    0.000000]   #36 [0001e00000 - 0001e1c000]         BOOTMEM
<6>[    0.000000]   #37 [0001e40000 - 0001e5c000]         BOOTMEM
<6>[    0.000000]   #38 [0001e80000 - 0001e9c000]         BOOTMEM
<6>[    0.000000]   #39 [0001ec0000 - 0001edc000]         BOOTMEM
<6>[    0.000000]   #40 [0001f00000 - 0001f1c000]         BOOTMEM
<6>[    0.000000]   #41 [0001f40000 - 0001f5c000]         BOOTMEM
<6>[    0.000000]   #42 [0001ddbbc0 - 0001ddbbc8]         BOOTMEM
<6>[    0.000000]   #43 [0001ddbc00 - 0001ddbc08]         BOOTMEM
<6>[    0.000000]   #44 [0001ddbc40 - 0001ddbc58]         BOOTMEM
<6>[    0.000000]   #45 [0001ddbc80 - 0001ddbcb0]         BOOTMEM
<6>[    0.000000]   #46 [0001ddbcc0 - 0001ddbde0]         BOOTMEM
<6>[    0.000000]   #47 [0001ddbe00 - 0001ddbe48]         BOOTMEM
<6>[    0.000000]   #48 [0001ddbe80 - 0001ddbec8]         BOOTMEM
<6>[    0.000000]   #49 [0001ddd000 - 0001de5000]         BOOTMEM
<6>[    0.000000] Memory: 1780412k/1833408k available (4775k kernel code, 456k absent, 52540k reserved, 6607k data, 896k init)
<6>[    0.000000] Hierarchical RCU implementation.
<6>[    0.000000] NR_IRQS:33024 nr_irqs:456
<6>[    0.000000] Extended CMOS year: 2000
<4>[    0.000000] Console: colour dummy device 80x25
<6>[    0.000000] console [tty0] enabled
<7>[    0.000000] hpet clockevent registered
<4>[    0.000000] Fast TSC calibration using PIT
<4>[    0.000000] Detected 3213.953 MHz processor.
<6>[    0.002004] Calibrating delay loop (skipped), value calculated using timer frequency.. 6427.89 BogoMIPS (lpj=3213949)
<4>[    0.002074] kdb version 4.4 by Keith Owens, Scott Lurndal. Copyright SGI, All Rights Reserved
<6>[    0.003015] Security Framework initialized
<6>[    0.003029] AppArmor: AppArmor initialized
<6>[    0.003134] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
<6>[    0.003798] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
<4>[    0.004131] Mount-cache hash table entries: 256
<7>[    0.004228] tseg: 0000000000
<6>[    0.004235] CPU: Physical Processor ID: 0
<6>[    0.004236] CPU: Processor Core ID: 0
<6>[    0.004238] mce: CPU supports 6 MCE banks
<6>[    0.004245] Performance Events: AMD PMU driver.
<6>[    0.004248] ... version:                0
<6>[    0.004249] ... bit width:              48
<6>[    0.004249] ... generic registers:      4
<6>[    0.004250] ... value mask:             0000ffffffffffff
<6>[    0.004251] ... max period:             00007fffffffffff
<6>[    0.004252] ... fixed-purpose events:   0
<6>[    0.004253] ... event mask:             000000000000000f
<6>[    0.004305] Unpacking initramfs...
<6>[    0.144055] Freeing initrd memory: 10968k freed
<6>[    0.147291] ACPI: Core revision 20100121
<6>[    0.167048] Setting APIC routing to flat
<6>[    0.167341] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
<6>[    0.178026] CPU0: AMD Phenom(tm) II X2 555 Processor stepping 03
<6>[    0.184030] Booting Node   0, Processors  #1
<6>[    0.256016] Brought up 2 CPUs
<6>[    0.256016] Total of 2 processors activated (12856.52 BogoMIPS).
<6>[    0.258050] devtmpfs: initialized
<6>[    0.259161] regulator: core version 0.5
<6>[    0.259161] regulator: dummy: 
<4>[    0.259161] Time: 22:29:59  Date: 08/10/10
<6>[    0.259161] NET: Registered protocol family 16
<7>[    0.259165] node 0 link 0: io port [1000, ffffff]
<6>[    0.259167] TOM: 0000000080000000 aka 2048M
<7>[    0.259168] Fam 10h mmconf [e0000000, efffffff]
<7>[    0.259170] node 0 link 0: mmio [a0000, bffff]
<7>[    0.259172] node 0 link 0: mmio [80000000, cfffffff]
<7>[    0.259173] node 0 link 0: mmio [d0000000, efffffff] ==> [d0000000, dfffffff]
<7>[    0.259176] node 0 link 0: mmio [f0000000, fe8fffff]
<7>[    0.259177] node 0 link 0: mmio [fe900000, feafffff]
<7>[    0.259179] node 0 link 0: mmio [feb00000, ffefffff]
<7>[    0.259180] bus: [00, 07] on node 0 link 0
<7>[    0.259182] bus: 00 index 0 [io  0x0000-0xffff]
<7>[    0.259183] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
<7>[    0.259185] bus: 00 index 2 [mem 0x80000000-0xdfffffff]
<7>[    0.259186] bus: 00 index 3 [mem 0xf0000000-0xfcffffffff]
<6>[    0.259191] ACPI: bus type pci registered
<6>[    0.259231] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
<6>[    0.259233] PCI: not using MMCONFIG
<6>[    0.259234] PCI: Using configuration type 1 for base access
<6>[    0.259235] PCI: Using configuration type 1 for extended access
<4>[    0.261078] bio: create slab <bio-0> at 0
<7>[    0.264158] ACPI: EC: Look up EC in DSDT
<4>[    0.266615] ACPI: Executed 3 blocks of module-level executable AML code
<6>[    0.283752] ACPI: Interpreter enabled
<6>[    0.283756] ACPI: (supports S0 S1 S3 S4 S5)
<6>[    0.283778] ACPI: Using IOAPIC for interrupt routing
<6>[    0.283828] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
<6>[    0.286814] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
<6>[    0.307685] ACPI: No dock devices found.
<6>[    0.307688] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
<6>[    0.307836] ACPI: PCI Root Bridge [PCI0] (0000:00)
<6>[    0.308139] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
<6>[    0.308141] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
<6>[    0.308142] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
<6>[    0.308144] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
<6>[    0.308145] pci_root PNP0A03:00: host bridge window [mem 0x6ff00000-0xdfffffff]
<6>[    0.308147] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
<7>[    0.308232] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
<7>[    0.308234] pci 0000:00:0a.0: PME# disabled
<7>[    0.308271] pci 0000:00:11.0: reg 10: [io  0xc000-0xc007]
<7>[    0.308276] pci 0000:00:11.0: reg 14: [io  0xb000-0xb003]
<7>[    0.308282] pci 0000:00:11.0: reg 18: [io  0xa000-0xa007]
<7>[    0.308287] pci 0000:00:11.0: reg 1c: [io  0x9000-0x9003]
<7>[    0.308293] pci 0000:00:11.0: reg 20: [io  0x8000-0x800f]
<7>[    0.308298] pci 0000:00:11.0: reg 24: [mem 0xfe8ffc00-0xfe8fffff]
<6>[    0.308313] pci 0000:00:11.0: set SATA to AHCI mode
<7>[    0.308352] pci 0000:00:12.0: reg 10: [mem 0xfe8fe000-0xfe8fefff]
<7>[    0.308399] pci 0000:00:12.1: reg 10: [mem 0xfe8fd000-0xfe8fdfff]
<7>[    0.308456] pci 0000:00:12.2: reg 10: [mem 0xfe8ff800-0xfe8ff8ff]
<7>[    0.308502] pci 0000:00:12.2: supports D1 D2
<7>[    0.308503] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
<7>[    0.308506] pci 0000:00:12.2: PME# disabled
<7>[    0.308533] pci 0000:00:13.0: reg 10: [mem 0xfe8fc000-0xfe8fcfff]
<7>[    0.308579] pci 0000:00:13.1: reg 10: [mem 0xfe8fb000-0xfe8fbfff]
<7>[    0.308636] pci 0000:00:13.2: reg 10: [mem 0xfe8ff400-0xfe8ff4ff]
<7>[    0.308682] pci 0000:00:13.2: supports D1 D2
<7>[    0.308683] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
<7>[    0.308686] pci 0000:00:13.2: PME# disabled
<7>[    0.308781] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
<7>[    0.308786] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
<7>[    0.308791] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
<7>[    0.308796] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
<7>[    0.308802] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
<7>[    0.308855] pci 0000:00:14.2: reg 10: [mem 0xfe8f4000-0xfe8f7fff 64bit]
<7>[    0.308893] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
<7>[    0.308896] pci 0000:00:14.2: PME# disabled
<7>[    0.308992] pci 0000:00:14.5: reg 10: [mem 0xfe8fa000-0xfe8fafff]
<7>[    0.309110] pci 0000:01:05.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
<7>[    0.309113] pci 0000:01:05.0: reg 14: [io  0xd000-0xd0ff]
<7>[    0.309115] pci 0000:01:05.0: reg 18: [mem 0xfeaf0000-0xfeafffff]
<7>[    0.309120] pci 0000:01:05.0: reg 24: [mem 0xfe900000-0xfe9fffff]
<7>[    0.309129] pci 0000:01:05.0: supports D1 D2
<7>[    0.309140] pci 0000:01:05.1: reg 10: [mem 0xfeae8000-0xfeaebfff]
<7>[    0.309155] pci 0000:01:05.1: supports D1 D2
<6>[    0.309188] pci 0000:00:01.0: PCI bridge to [bus 01-01]
<7>[    0.309190] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
<7>[    0.309192] pci 0000:00:01.0:   bridge window [mem 0xfe900000-0xfeafffff]
<7>[    0.309195] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
<7>[    0.309231] pci 0000:02:00.0: reg 10: [io  0xe800-0xe8ff]
<7>[    0.309244] pci 0000:02:00.0: reg 18: [mem 0xfdfff000-0xfdffffff 64bit pref]
<7>[    0.309253] pci 0000:02:00.0: reg 20: [mem 0xfdff8000-0xfdffbfff 64bit pref]
<7>[    0.309259] pci 0000:02:00.0: reg 30: [mem 0xfebf0000-0xfebfffff pref]
<7>[    0.309284] pci 0000:02:00.0: supports D1 D2
<7>[    0.309286] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
<7>[    0.309289] pci 0000:02:00.0: PME# disabled
<6>[    0.311015] pci 0000:00:0a.0: PCI bridge to [bus 02-02]
<7>[    0.311019] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
<7>[    0.311021] pci 0000:00:0a.0:   bridge window [mem 0xfeb00000-0xfebfffff]
<7>[    0.311024] pci 0000:00:0a.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
<6>[    0.311083] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
<7>[    0.311086] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
<7>[    0.311090] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
<7>[    0.311093] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
<7>[    0.311095] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
<7>[    0.311097] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
<7>[    0.311098] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
<7>[    0.311100] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
<7>[    0.311102] pci 0000:00:14.4:   bridge window [mem 0x6ff00000-0xdfffffff] (subtractive decode)
<7>[    0.311103] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
<7>[    0.311118] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
<7>[    0.311303] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
<7>[    0.311374] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
<7>[    0.311441] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
<6>[    0.317567] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 *10 11 12 14 15)
<6>[    0.317670] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 *11 12 14 15)
<6>[    0.317770] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
<6>[    0.317870] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 12 14 15)
<6>[    0.317974] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
<6>[    0.318077] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
<6>[    0.318178] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 *11 12 14 15)
<6>[    0.318280] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
<6>[    0.318373] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
<6>[    0.318375] vgaarb: loaded
<6>[    0.318392] usbcore: registered new interface driver usbfs
<6>[    0.318401] usbcore: registered new interface driver hub
<6>[    0.318411] usbcore: registered new device driver usb
<6>[    0.318411] PCI: Using ACPI for IRQ routing
<7>[    0.318411] PCI: pci_cache_line_size set to 64 bytes
<7>[    0.318411] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
<7>[    0.318411] reserve RAM buffer: 000000006fe70000 - 000000006fffffff 
<6>[    0.318411] NetLabel: Initializing
<6>[    0.318411] NetLabel:  domain hash size = 128
<6>[    0.318411] NetLabel:  protocols = UNLABELED CIPSOv4
<6>[    0.318411] NetLabel:  unlabeled traffic allowed by default
<6>[    0.318411] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
<6>[    0.318411] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
<6>[    0.320016] Switching to clocksource tsc
<6>[    0.322854] AppArmor: AppArmor Filesystem Enabled
<6>[    0.322862] pnp: PnP ACPI init
<6>[    0.322869] ACPI: bus type pnp registered
<6>[    0.327408] pnp: PnP ACPI: found 15 devices
<6>[    0.327409] ACPI: ACPI bus type pnp unregistered
<6>[    0.327416] system 00:01: [mem 0x70000000-0x7fffffff] has been reserved
<6>[    0.327421] system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
<6>[    0.327422] system 00:0a: [mem 0xfee00000-0xfee00fff] has been reserved
<6>[    0.327426] system 00:0b: [io  0x04d0-0x04d1] has been reserved
<6>[    0.327427] system 00:0b: [io  0x040b] has been reserved
<6>[    0.327429] system 00:0b: [io  0x04d6] has been reserved
<6>[    0.327431] system 00:0b: [io  0x0c00-0x0c01] has been reserved
<6>[    0.327432] system 00:0b: [io  0x0c14] has been reserved
<6>[    0.327434] system 00:0b: [io  0x0c50-0x0c51] has been reserved
<6>[    0.327435] system 00:0b: [io  0x0c52] has been reserved
<6>[    0.327437] system 00:0b: [io  0x0c6c] has been reserved
<6>[    0.327438] system 00:0b: [io  0x0c6f] has been reserved
<6>[    0.327440] system 00:0b: [io  0x0cd0-0x0cd1] has been reserved
<6>[    0.327441] system 00:0b: [io  0x0cd2-0x0cd3] has been reserved
<6>[    0.327443] system 00:0b: [io  0x0cd4-0x0cd5] has been reserved
<6>[    0.327444] system 00:0b: [io  0x0cd6-0x0cd7] has been reserved
<6>[    0.327446] system 00:0b: [io  0x0cd8-0x0cdf] has been reserved
<6>[    0.327447] system 00:0b: [io  0x0b00-0x0b3f] has been reserved
<6>[    0.327449] system 00:0b: [io  0x0800-0x089f] has been reserved
<6>[    0.327450] system 00:0b: [io  0x0b00-0x0b0f] has been reserved
<6>[    0.327452] system 00:0b: [io  0x0b20-0x0b3f] has been reserved
<6>[    0.327454] system 00:0b: [io  0x0900-0x090f] has been reserved
<6>[    0.327455] system 00:0b: [io  0x0910-0x091f] has been reserved
<6>[    0.327457] system 00:0b: [io  0xfe00-0xfefe] has been reserved
<6>[    0.327459] system 00:0b: [mem 0xffb80000-0xffbfffff] has been reserved
<6>[    0.327461] system 00:0b: [mem 0xfec10000-0xfec1001f] has been reserved
<6>[    0.327462] system 00:0b: [mem 0xfed40000-0xfed44fff] has been reserved
<6>[    0.327466] system 00:0c: [io  0x0230-0x023f] has been reserved
<6>[    0.327467] system 00:0c: [io  0x0290-0x029f] has been reserved
<6>[    0.327469] system 00:0c: [io  0x0300-0x030f] has been reserved
<6>[    0.327470] system 00:0c: [io  0x0a30-0x0a3f] has been reserved
<6>[    0.327473] system 00:0d: [mem 0xe0000000-0xefffffff] has been reserved
<6>[    0.327479] system 00:0e: [mem 0x00000000-0x0009ffff] could not be reserved
<6>[    0.327481] system 00:0e: [mem 0x000c0000-0x000cffff] has been reserved
<6>[    0.327482] system 00:0e: [mem 0x000e0000-0x000fffff] could not be reserved
<6>[    0.327484] system 00:0e: [mem 0x00100000-0x6fefffff] could not be reserved
<6>[    0.327486] system 00:0e: [mem 0xfec00000-0xffffffff] could not be reserved
<6>[    0.333544] pci 0000:00:01.0: PCI bridge to [bus 01-01]
<6>[    0.333547] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
<6>[    0.333549] pci 0000:00:01.0:   bridge window [mem 0xfe900000-0xfeafffff]
<6>[    0.333551] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
<6>[    0.333554] pci 0000:00:0a.0: PCI bridge to [bus 02-02]
<6>[    0.333556] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
<6>[    0.333558] pci 0000:00:0a.0:   bridge window [mem 0xfeb00000-0xfebfffff]
<6>[    0.333560] pci 0000:00:0a.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
<6>[    0.333562] pci 0000:00:14.4: PCI bridge to [bus 03-03]
<6>[    0.333563] pci 0000:00:14.4:   bridge window [io  disabled]
<6>[    0.333567] pci 0000:00:14.4:   bridge window [mem disabled]
<6>[    0.333570] pci 0000:00:14.4:   bridge window [mem pref disabled]
<7>[    0.333582]   alloc irq_desc for 18 on node 0
<7>[    0.333583]   alloc kstat_irqs on node 0
<6>[    0.333587] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
<7>[    0.333589] pci 0000:00:0a.0: setting latency timer to 64
<7>[    0.333595] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
<7>[    0.333596] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
<7>[    0.333597] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
<7>[    0.333599] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
<7>[    0.333600] pci_bus 0000:00: resource 8 [mem 0x6ff00000-0xdfffffff]
<7>[    0.333601] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
<7>[    0.333603] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
<7>[    0.333604] pci_bus 0000:01: resource 1 [mem 0xfe900000-0xfeafffff]
<7>[    0.333605] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
<7>[    0.333607] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
<7>[    0.333608] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
<7>[    0.333610] pci_bus 0000:02: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
<7>[    0.333611] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
<7>[    0.333612] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
<7>[    0.333613] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
<7>[    0.333615] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
<7>[    0.333616] pci_bus 0000:03: resource 8 [mem 0x6ff00000-0xdfffffff]
<7>[    0.333617] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfebfffff]
<6>[    0.333663] NET: Registered protocol family 2
<6>[    0.333736] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
<6>[    0.334156] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
<6>[    0.335160] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
<6>[    0.335456] TCP: Hash tables configured (established 262144 bind 65536)
<6>[    0.335457] TCP reno registered
<6>[    0.335463] UDP hash table entries: 1024 (order: 3, 32768 bytes)
<6>[    0.335477] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
<6>[    0.335581] NET: Registered protocol family 1
<4>[    0.335590] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
<7>[    1.066088] pci 0000:01:05.0: Boot video device
<7>[    1.066093] PCI: CLS 64 bytes, default 64
<6>[    1.066398] Scanning for low memory corruption every 60 seconds
<6>[    1.066487] audit: initializing netlink socket (disabled)
<5>[    1.066494] type=2000 audit(1281479399.065:1): initialized
<6>[    1.074597] HugeTLB registered 2 MB page size, pre-allocated 0 pages
<5>[    1.076136] VFS: Disk quotas dquot_6.5.2
<4>[    1.076158] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
<6>[    1.076253] msgmni has been set to 874
<6>[    1.078106] alg: No test for stdrng (krng)
<6>[    1.078132] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
<6>[    1.078134] io scheduler noop registered
<6>[    1.078136] io scheduler deadline registered
<6>[    1.078147] io scheduler cfq registered (default)
<7>[    1.079082] pcieport 0000:00:0a.0: setting latency timer to 64
<7>[    1.079101]   alloc irq_desc for 24 on node 0
<7>[    1.079102]   alloc kstat_irqs on node 0
<7>[    1.079108] pcieport 0000:00:0a.0: irq 24 for MSI/MSI-X
<6>[    1.079170] pcieport 0000:00:0a.0: Requesting control of PCIe PME from ACPI BIOS
<6>[    1.079177] pcieport 0000:00:0a.0: Failed to receive control of PCIe PME service: no _OSC support
<4>[    1.079180] pcie_pme: probe of 0000:00:0a.0:pcie01 failed with error -13
<4>[    1.079196] pci-stub: invalid id string ""
<6>[    1.079555] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90010980000, using 5120k, total 16384k
<6>[    1.079557] vesafb: mode is 1280x1024x16, linelength=2560, pages=5
<6>[    1.079558] vesafb: scrolling: redraw
<6>[    1.079560] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
<6>[    1.079709] bootsplash 3.1.6-2004/03/31: looking for picture...
<6>[    1.079711] bootsplash: silentjpeg size 189087 bytes
<6>[    1.093260] bootsplash: ...found (1280x1024, 95355 bytes, v3).
<4>[    1.203043] Console: switching to colour frame buffer device 156x60
<6>[    1.313071] fb0: VESA VGA frame buffer device
<6>[    1.313889] Non-volatile memory driver v1.3
<6>[    1.313891] Linux agpgart interface v0.103
<6>[    1.313894] Serial: 8250/16550 driver, 8 ports, IRQ sharing disabled
<6>[    1.313993] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
<6>[    1.314260] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
<6>[    1.314340] Fixed MDIO Bus: probed
<6>[    1.314344] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
<7>[    1.314388]   alloc irq_desc for 17 on node 0
<7>[    1.314390]   alloc kstat_irqs on node 0
<6>[    1.314396] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
<6>[    1.314412] ehci_hcd 0000:00:12.2: EHCI Host Controller
<6>[    1.314429] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
<6>[    1.314455] ehci_hcd 0000:00:12.2: debug port 1
<6>[    1.314473] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe8ff800
<6>[    1.320006] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
<6>[    1.320031] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
<6>[    1.320033] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
<6>[    1.320034] usb usb1: Product: EHCI Host Controller
<6>[    1.320035] usb usb1: Manufacturer: Linux 2.6.34-12-desktop ehci_hcd
<6>[    1.320036] usb usb1: SerialNumber: 0000:00:12.2
<6>[    1.320097] hub 1-0:1.0: USB hub found
<6>[    1.320100] hub 1-0:1.0: 6 ports detected
<7>[    1.321110]   alloc irq_desc for 19 on node 0
<7>[    1.321112]   alloc kstat_irqs on node 0
<6>[    1.321116] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
<6>[    1.321129] ehci_hcd 0000:00:13.2: EHCI Host Controller
<6>[    1.321139] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
<6>[    1.321164] ehci_hcd 0000:00:13.2: debug port 1
<6>[    1.321181] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe8ff400
<6>[    1.327006] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
<6>[    1.327019] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
<6>[    1.327020] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
<6>[    1.327021] usb usb2: Product: EHCI Host Controller
<6>[    1.327023] usb usb2: Manufacturer: Linux 2.6.34-12-desktop ehci_hcd
<6>[    1.327024] usb usb2: SerialNumber: 0000:00:13.2
<6>[    1.327077] hub 2-0:1.0: USB hub found
<6>[    1.327080] hub 2-0:1.0: 6 ports detected
<6>[    1.327140] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
<7>[    1.328107]   alloc irq_desc for 16 on node 0
<7>[    1.328109]   alloc kstat_irqs on node 0
<6>[    1.328113] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
<6>[    1.328125] ohci_hcd 0000:00:12.0: OHCI Host Controller
<6>[    1.328132] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
<6>[    1.328153] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe8fe000
<6>[    1.383039] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
<6>[    1.383041] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
<6>[    1.383043] usb usb3: Product: OHCI Host Controller
<6>[    1.383044] usb usb3: Manufacturer: Linux 2.6.34-12-desktop ohci_hcd
<6>[    1.383045] usb usb3: SerialNumber: 0000:00:12.0
<6>[    1.383102] hub 3-0:1.0: USB hub found
<6>[    1.383107] hub 3-0:1.0: 3 ports detected
<6>[    1.384113] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
<6>[    1.384125] ohci_hcd 0000:00:12.1: OHCI Host Controller
<6>[    1.384134] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
<6>[    1.384148] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe8fd000
<6>[    1.439040] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
<6>[    1.439042] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
<6>[    1.439044] usb usb4: Product: OHCI Host Controller
<6>[    1.439045] usb usb4: Manufacturer: Linux 2.6.34-12-desktop ohci_hcd
<6>[    1.439046] usb usb4: SerialNumber: 0000:00:12.1
<6>[    1.439104] hub 4-0:1.0: USB hub found
<6>[    1.439108] hub 4-0:1.0: 3 ports detected
<6>[    1.440120] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
<6>[    1.440133] ohci_hcd 0000:00:13.0: OHCI Host Controller
<6>[    1.440141] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
<6>[    1.440162] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe8fc000
<6>[    1.495052] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
<6>[    1.495054] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
<6>[    1.495055] usb usb5: Product: OHCI Host Controller
<6>[    1.495056] usb usb5: Manufacturer: Linux 2.6.34-12-desktop ohci_hcd
<6>[    1.495057] usb usb5: SerialNumber: 0000:00:13.0
<6>[    1.495116] hub 5-0:1.0: USB hub found
<6>[    1.495121] hub 5-0:1.0: 3 ports detected
<6>[    1.496125] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
<6>[    1.496138] ohci_hcd 0000:00:13.1: OHCI Host Controller
<6>[    1.496146] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
<6>[    1.496160] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe8fb000
<6>[    1.551056] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
<6>[    1.551058] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
<6>[    1.551059] usb usb6: Product: OHCI Host Controller
<6>[    1.551060] usb usb6: Manufacturer: Linux 2.6.34-12-desktop ohci_hcd
<6>[    1.551061] usb usb6: SerialNumber: 0000:00:13.1
<6>[    1.551119] hub 6-0:1.0: USB hub found
<6>[    1.551124] hub 6-0:1.0: 3 ports detected
<6>[    1.552131] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
<6>[    1.552145] ohci_hcd 0000:00:14.5: OHCI Host Controller
<6>[    1.552152] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
<6>[    1.552167] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe8fa000
<6>[    1.607061] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
<6>[    1.607063] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
<6>[    1.607065] usb usb7: Product: OHCI Host Controller
<6>[    1.607066] usb usb7: Manufacturer: Linux 2.6.34-12-desktop ohci_hcd
<6>[    1.607067] usb usb7: SerialNumber: 0000:00:14.5
<6>[    1.607126] hub 7-0:1.0: USB hub found
<6>[    1.607131] hub 7-0:1.0: 2 ports detected
<6>[    1.607181] uhci_hcd: USB Universal Host Controller Interface driver
<6>[    1.607229] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
<4>[    1.607230] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
<6>[    1.607342] serio: i8042 KBD port at 0x60,0x64 irq 1
<6>[    1.607382] mice: PS/2 mouse device common for all mice
<6>[    1.607438] rtc_cmos 00:03: RTC can wake from S4
<6>[    1.607462] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
<6>[    1.607484] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
<6>[    1.607491] cpuidle: using governor ladder
<6>[    1.607493] cpuidle: using governor menu
<6>[    1.607638] usbcore: registered new interface driver hiddev
<6>[    1.607645] usbcore: registered new interface driver usbhid
<6>[    1.607646] usbhid: USB HID core driver
<6>[    1.654072] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0
<6>[    1.658701] TCP cubic registered
<6>[    1.658739] NET: Registered protocol family 10
<6>[    1.658988] lo: Disabled Privacy Extensions
<6>[    1.659134] lib80211: common routines for IEEE802.11 drivers
<7>[    1.659135] lib80211_crypt: registered algorithm 'NULL'
<7>[    1.659189] PM: Checking image partition /dev/disk/by-id/ata-ST3500418AS_9VMFJGVE-part3
<7>[    1.659191] PM: Resume from disk failed.
<4>[    1.659199] registered taskstats version 1
<4>[    1.659362]   Magic number: 6:25:502
<6>[    1.659411] rtc_cmos 00:03: setting system clock to 2010-08-10 22:30:00 UTC (1281479400)
<6>[    1.659471] Freeing unused kernel memory: 896k freed
<6>[    1.659720] Write protecting the kernel read-only data: 10240k
<6>[    1.659841] Freeing unused kernel memory: 1352k freed
<6>[    1.660309] Freeing unused kernel memory: 636k freed
<5>[    1.685133] SCSI subsystem initialized
<7>[    1.695115] libata version 3.00 loaded.
<6>[    1.695961] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
<7>[    1.695982] pata_atiixp 0000:00:14.1: setting latency timer to 64
<6>[    1.696035] scsi0 : pata_atiixp
<6>[    1.696086] scsi1 : pata_atiixp
<6>[    1.697164] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
<6>[    1.697165] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
<6>[    1.726025] usb 4-3: new low speed USB device using ohci_hcd and address 2
<7>[    1.885017] ahci 0000:00:11.0: version 3.0
<7>[    1.885028]   alloc irq_desc for 22 on node 0
<7>[    1.885030]   alloc kstat_irqs on node 0
<6>[    1.885034] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
<6>[    1.885130] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
<6>[    1.885132] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
<6>[    1.885313] scsi2 : ahci
<6>[    1.885355] scsi3 : ahci
<6>[    1.885384] scsi4 : ahci
<6>[    1.885413] scsi5 : ahci
<6>[    1.885499] ata3: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffd00 irq 22
<6>[    1.885501] ata4: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffd80 irq 22
<6>[    1.885504] ata5: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffe00 irq 22
<6>[    1.885506] ata6: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffe80 irq 22
<6>[    1.893110] usb 4-3: New USB device found, idVendor=046d, idProduct=c05b
<6>[    1.893112] usb 4-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
<6>[    1.893114] usb 4-3: Product: USB Optical Mouse
<6>[    1.893115] usb 4-3: Manufacturer: Logitech
<6>[    1.900224] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/input/input1
<6>[    1.900269] generic-usb 0003:046D:C05B.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:12.1-3/input0
<6>[    2.190075] ata4: SATA link down (SStatus 0 SControl 300)
<6>[    2.190078] ata6: SATA link down (SStatus 0 SControl 300)
<6>[    2.343046] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
<6>[    2.343066] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
<6>[    2.344105] ata3.00: ATA-8: ST3500418AS, CC38, max UDMA/133
<6>[    2.344108] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
<6>[    2.345306] ata3.00: configured for UDMA/133
<6>[    2.346045] ata5.00: ATAPI: HL-DT-ST DVDRAM GH22NS40, NL01, max UDMA/100
<6>[    2.349878] ata5.00: configured for UDMA/100
<5>[    2.356072] scsi 2:0:0:0: Direct-Access     ATA      ST3500418AS      CC38 PQ: 0 ANSI: 5
<5>[    2.369360] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS40  NL01 PQ: 0 ANSI: 5
<6>[    2.381061] udev: starting version 157
<6>[    2.447949] [drm] Initialized drm 1.1.0 20060810
<5>[    2.450165] sd 2:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
<5>[    2.450191] sd 2:0:0:0: [sda] Write Protect is off
<7>[    2.450193] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
<5>[    2.450205] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
<6>[    2.450301]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 sda9 sda10 sda11 sda12 sda13 >
<5>[    2.589423] sd 2:0:0:0: [sda] Attached SCSI disk
<6>[    2.604476] [drm] radeon defaulting to kernel modesetting.
<6>[    2.604478] [drm] radeon kernel modesetting enabled.
<6>[    2.604545] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
<7>[    2.604548] radeon 0000:01:05.0: setting latency timer to 64
<6>[    2.605747] [drm] initializing kernel modesetting (RS880 0x1002:0x9710).
<6>[    2.605803] [drm] register mmio base: 0xFEAF0000
<6>[    2.605804] [drm] register mmio size: 65536
<6>[    2.606358] ATOM BIOS: 113
<6>[    2.606370] [drm] Clocks initialized !
<6>[    2.606372] [drm] 3 Power State(s)
<6>[    2.606373] [drm] State 0 Default (default)
<6>[    2.606373] [drm]     1 Clock Mode(s)
<6>[    2.606374] [drm]         0 engine: 300000
<6>[    2.606375] [drm] State 1 Performance 
<6>[    2.606376] [drm]     1 Clock Mode(s)
<6>[    2.606377] [drm]         0 engine: 200000
<6>[    2.606378] [drm] State 2 Default 
<6>[    2.606379] [drm]     1 Clock Mode(s)
<6>[    2.606379] [drm]         0 engine: 500000
<6>[    2.606382] [drm] radeon: power management initialized
<6>[    2.606388] radeon 0000:01:05.0: VRAM: 256M 0xC0000000 - 0xCFFFFFFF (256M used)
<6>[    2.606390] radeon 0000:01:05.0: GTT: 512M 0xA0000000 - 0xBFFFFFFF
<6>[    2.607722] [drm] Detected VRAM RAM=256M, BAR=256M
<6>[    2.607725] [drm] RAM width 32bits DDR
<6>[    2.607776] [TTM] Zone  kernel: Available graphics memory: 897132 kiB.
<6>[    2.607787] [drm] radeon: 256M of VRAM memory ready
<6>[    2.607788] [drm] radeon: 512M of GTT memory ready.
<6>[    2.607816] [drm] radeon: irq initialized.
<6>[    2.607818] [drm] GART: num cpu pages 131072, num gpu pages 131072
<6>[    2.608340] [drm] Loading RS780 Microcode
<6>[    2.608342] platform radeon_cp.0: firmware: requesting radeon/RS780_pfp.bin
<6>[    2.609229] platform radeon_cp.0: firmware: requesting radeon/RS780_me.bin
<6>[    2.610035] platform radeon_cp.0: firmware: requesting radeon/R600_rlc.bin
<6>[    2.645950] [drm] ring test succeeded in 1 usecs
<6>[    2.646014] [drm] radeon: ib pool ready.
<6>[    2.646056] [drm] ib test succeeded in 0 usecs
<6>[    2.646058] [drm] Enabling audio support
<6>[    2.646077] [drm] Unknown TV standard; defaulting to NTSC
<6>[    2.646138] [drm] Radeon Display Connectors
<6>[    2.646139] [drm] Connector 0:
<6>[    2.646140] [drm]   VGA
<6>[    2.646141] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
<6>[    2.646142] [drm]   Encoders:
<6>[    2.646143] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
<6>[    2.646144] [drm] Connector 1:
<6>[    2.646145] [drm]   DVI-D
<6>[    2.646145] [drm]   HPD1
<6>[    2.646147] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
<6>[    2.646148] [drm]   Encoders:
<6>[    2.646148] [drm]     DFP3: INTERNAL_KLDSCP_LVTMA
<6>[    2.782545] [drm] fb mappable at 0xD0141000
<6>[    2.782547] [drm] vram apper at 0xD0000000
<6>[    2.782548] [drm] size 5760000
<6>[    2.782549] [drm] fb depth is 24
<6>[    2.782550] [drm]    pitch is 6400
<3>[    2.782553] fb: conflicting fb hw usage radeondrmfb vs VESA VGA - removing generic driver
<4>[    2.782567] Console: switching to colour dummy device 80x25
<4>[    2.782876] Console: switching to colour frame buffer device 200x56
<6>[    2.797739] bootsplash: scaling image from 1280x1024 to 1600x900
<6>[    2.856476] bootsplash: scaling image from 1280x1024 to 1600x900
<6>[    2.907840] bootsplash: scaling image from 1280x1024 to 1600x900
<6>[    2.967292] bootsplash: scaling image from 1280x1024 to 1600x900
<6>[    3.001081] fb0: radeondrmfb frame buffer device
<6>[    3.001083] registered panic notifier
<6>[    3.001092] [drm] Initialized radeon 2.3.0 20080528 for 0000:01:05.0 on minor 0
<7>[    3.714116] PM: Marking nosave pages: 000000000009e000 - 0000000000100000
<7>[    3.714119] PM: Basic memory bitmaps created
<7>[    3.725911] PM: Basic memory bitmaps freed
<6>[    3.781527] PM: Starting manual resume from disk
<7>[    3.781529] PM: Resume from partition 8:3
<7>[    3.781530] PM: Checking hibernation image.
<7>[    3.781687] PM: Error -22 checking image file
<7>[    3.781688] PM: Resume from disk failed.
<6>[    3.902661] EXT4-fs (sda7): mounted filesystem with ordered data mode
<7>[    4.903476] preloadtrace: systemtap: 1.1/0.147, base: ffffffffa030a000, memory: 37data/40text/25ctx/13net/443alloc kb, probes: 44
<6>[    5.708937] udev: starting version 157
<6>[    5.730184] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
<6>[    5.745114] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
<6>[    5.767555] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
<6>[    5.767585] ACPI: Power Button [PWRB]
<6>[    5.767616] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
<6>[    5.767631] ACPI: Power Button [PWRF]
<6>[    5.807317] ACPI: WMI: Mapper loaded
<6>[    5.807940] input: PC Speaker as /devices/platform/pcspkr/input/input4
<6>[    5.820781] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
<6>[    5.820799] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
<7>[    5.820845] r8169 0000:02:00.0: setting latency timer to 64
<7>[    5.821089]   alloc irq_desc for 25 on node 0
<7>[    5.821091]   alloc kstat_irqs on node 0
<7>[    5.821101] r8169 0000:02:00.0: irq 25 for MSI/MSI-X
<6>[    5.821403] r8169 0000:02:00.0: eth0: RTL8168d/8111d at 0xffffc90013e80000, e0:cb:4e:7f:d3:64, XID 083000c0 IRQ 25
<6>[    5.824884] IT8712 SuperIO detected.
<6>[    5.830087] EDAC MC: Ver: 2.1.0 Jul  5 2010
<4>[    5.834270] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SOR1 [io  0x0b00-0x0b0f 64bit pref window]
<6>[    5.834273] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
<6>[    5.834416] parport_pc 00:06: reported by Plug and Play ACPI
<6>[    5.834466] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
<5>[    5.838930] sd 2:0:0:0: Attached scsi generic sg0 type 0
<5>[    5.838949] scsi 4:0:0:0: Attached scsi generic sg1 type 5
<6>[    5.846842] EDAC amd64_edac:  Ver: 3.3.0 Jul  5 2010
<5>[    5.850131] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
<5>[    5.850137] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
<5>[    5.850138]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
<5>[    5.850139]  (Note that use of the override may cause unknown side effects.)
<4>[    5.850151] amd64_edac: probe of 0000:00:18.2 failed with error -22
<4>[    5.871109] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
<6>[    5.871111] Uniform CD-ROM driver Revision: 3.20
<7>[    5.871170] sr 4:0:0:0: Attached scsi CD-ROM sr0
<6>[    5.871471] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
<7>[    5.934759] ALSA hda_codec.c:4358: autoconfig: line_outs=4 (0x1c/0x19/0x22/0x23/0x0)
<7>[    5.934763] ALSA hda_codec.c:4362:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
<7>[    5.934765] ALSA hda_codec.c:4366:    hp_outs=1 (0x1d/0x0/0x0/0x0/0x0)
<7>[    5.934767] ALSA hda_codec.c:4367:    mono: mono_out=0x0
<7>[    5.934768] ALSA hda_codec.c:4370:    dig-out=0x20/0x21
<7>[    5.934770] ALSA hda_codec.c:4378:    inputs: mic=0x1a, fmic=0x1e, line=0x1b, fline=0x0, cd=0x0, aux=0x0
<6>[    5.940029] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
<7>[    5.940053] HDA Intel 0000:01:05.1: setting latency timer to 64
<6>[    5.945752] ppdev: user-space parallel port driver
<6>[    7.177993] Adding 1879600k swap on /dev/sda3.  Priority:-1 extents:1 across:1879600k 
<6>[    7.959642] device-mapper: uevent: version 1.0.3
<6>[    7.959732] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
<6>[    9.250548] loop: module loaded
<6>[    9.525933] EXT4-fs (sda8): mounted filesystem with ordered data mode
<6>[    9.682674] EXT4-fs (sda11): mounted filesystem with ordered data mode
<6>[    9.727200] EXT4-fs (sda12): mounted filesystem with ordered data mode
<6>[    9.804646] EXT4-fs (sda13): mounted filesystem with ordered data mode
<6>[    9.866532] EXT4-fs (sda6): mounted filesystem with ordered data mode
<6>[    9.930715] EXT4-fs (sda5): mounted filesystem with ordered data mode
<6>[    9.951826] fuse init (API version 7.13)
Kernel logging (ksyslog) stopped.
Kernel log daemon terminating.

Boot logging started on /dev/char/../tty7(/dev/console) at Tue Aug 10 22:33:37 2010
Master Resource Control: previous runlevel: 5, switching to runlevel: 6
<notice -- Aug 10 22:33:37.201607000> service atieventsd start<notice -- Aug 10 22:33:37.201914000> service cron start<notice -- Aug 10 22:33:37.202081000> service smartd start<notice -- Aug 10 22:33:37.202239000> service cups start<notice -- Aug 10 22:33:37.202399000> service mcelog start<notice -- Aug 10 22:33:37.202556000> service nscd start<notice -- Aug 10 22:33:37.202723000> service SuSEfirewall2_setup start<notice -- Aug 10 22:33:37.202886000> service alsasound startStopping atieventsddone
<notice -- Aug 10 22:33:37.223124000> service atieventsd done<notice -- Aug 10 22:33:37.223205000> service xdm start<notice -- Aug 10 22:33:37.261010000> service SuSEfirewall2_setup doneShutting down the Firewall skipped
<notice -- Aug 10 22:33:37.261095000> service avahi-daemon start<notice -- Aug 10 22:33:37.263071000> killproc: kill(3879,15)
<notice -- Aug 10 22:33:37.265168000> killproc: kill(3871,15)
<notice -- Aug 10 22:33:37.265752000> killproc: kill(3910,15)
<notice -- Aug 10 22:33:37.268667000> service alsasound done<notice -- Aug 10 22:33:37.268712000> service irq_balancer start<notice -- Aug 10 22:33:37.270485000> killproc: kill(4211,15)
<notice -- Aug 10 22:33:37.271461000> killproc: kill(4204,15)
<notice -- Aug 10 22:33:37.314357000> killproc: kill(3887,15)
<notice -- Aug 10 22:33:37.323661000> killproc: kill(1470,15)
<notice -- Aug 10 22:33:37.323782000> service cups doneShutting down cupsddone
<notice -- Aug 10 22:33:37.323864000> service network-remotefs start<notice -- Aug 10 22:33:37.326739000> service mcelog doneShutting down mcelog... done
<notice -- Aug 10 22:33:37.333874000> service splash startShutting down smartd done
<notice -- Aug 10 22:33:37.334065000> service smartd done<notice -- Aug 10 22:33:37.334105000> service auditd start<notice -- Aug 10 22:33:37.335980000> service cron doneShutting down CRON daemondone
<notice -- Aug 10 22:33:37.336017000> service postfix start<notice -- Aug 10 22:33:37.346396000> service nscd doneShutting down Name Service Cache Daemondone
<notice -- Aug 10 22:33:37.346449000> service splash_early start<notice -- Aug 10 22:33:37.365218000> service splash done<notice -- Aug 10 22:33:37.365280000> service bluez-coldplug start<notice -- Aug 10 22:33:37.375190000> killproc: kill(4170,15)
<notice -- Aug 10 22:33:37.375377000> killproc: kill(3690,15)
<notice -- Aug 10 22:33:37.380866000> service irq_balancer doneShutting down irqbalance done
<notice -- Aug 10 22:33:37.380945000> service fbset start<notice -- Aug 10 22:33:37.382822000> service avahi-daemon doneShutting down Avahi daemon done
<notice -- Aug 10 22:33:37.382870000> service dbus start<notice -- Aug 10 22:33:37.403639000> service splash_early done<notice -- Aug 10 22:33:37.403689000> service haldaemon startdone
<notice -- Aug 10 22:33:37.416178000> service bluez-coldplug done<notice -- Aug 10 22:33:37.416216000> service random start<notice -- Aug 10 22:33:37.441420000> service postfix doneShutting down mail service (Postfix)done
<notice -- Aug 10 22:33:37.441520000> service stoppreload start<notice -- Aug 10 22:33:37.448469000> service fbset done<notice -- Aug 10 22:33:37.448512000> service xinetd startShutting down auditd done
<notice -- Aug 10 22:33:37.458305000> service auditd done<notice -- Aug 10 22:33:37.464381000> service stoppreload donedone
<notice -- Aug 10 22:33:37.480970000> service random doneSaving random seeddone
<notice -- Aug 10 22:33:37.481042000> killproc: kill(1378,15)
<notice -- Aug 10 22:33:37.495974000> killproc: kill(1376,15)
<notice -- Aug 10 22:33:37.547855000> killproc: kill(1340,15)
Shutting down (remotefs) network interfaces:
<notice -- Aug 10 22:33:37.563580000> service network-remotefs done<notice -- Aug 10 22:33:37.564414000> service haldaemon doneShutting down HAL daemondone
<notice -- Aug 10 22:33:37.609621000> service dbus doneShutting down D-Bus daemondone
Shutting down service gdmdone
<notice -- Aug 10 22:33:38.42081000> service xdm done<notice -- Aug 10 22:33:38.46643000> service kbd start<notice -- Aug 10 22:33:38.46852000> service earlyxdm start<notice -- Aug 10 22:33:38.46997000> service acpid start<notice -- Aug 10 22:33:38.47135000> service xinetd doneShutting down xinetd: (waiting for all children to terminate) done
<notice -- Aug 10 22:33:38.60006000> killproc: kill(1336,15)
<notice -- Aug 10 22:33:38.69010000> service kbd done/etc/init.d/kbd stopdone
<notice -- Aug 10 22:33:38.69099000> service cifs start<notice -- Aug 10 22:33:38.69229000> service nfs startShutting down service gdmdone
<notice -- Aug 10 22:33:38.72575000> service earlyxdm done<notice -- Aug 10 22:33:38.85541000> service cifs doneUmount CIFS File Systems done
Shutting down NFS client services:done
<notice -- Aug 10 22:33:38.117907000> service nfs done<notice -- Aug 10 22:33:38.118179000> service rpcbind start<notice -- Aug 10 22:33:38.121976000> service acpid doneShutting down acpid done
<notice -- Aug 10 22:33:38.130362000> killproc: kill(3689,15)
Shutting down rpcbind done
<notice -- Aug 10 22:33:38.192074000> service rpcbind done<notice -- Aug 10 22:33:38.192263000> service syslog startShutting down syslog services
<notice -- Aug 10 22:33:38.214421000> killproc: kill(3648,15)
done
<notice -- Aug 10 22:33:38.278032000> service syslog done<notice -- Aug 10 22:33:38.278117000> service earlysyslog start<notice -- Aug 10 22:33:38.278467000> service network start<notice -- Aug 10 22:33:38.302641000> service earlysyslog doneShutting down (localfs) network interfaces:
    eth0      device: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    eth0     
done
<notice -- Aug 10 22:33:40.267943000> service network doneShutting down service (localfs) network  .  .  .  .  .  .  .  .  .done
<notice -- Aug 10 22:33:40.268036000> service SuSEfirewall2_init start<notice -- Aug 10 22:33:40.276477000> service SuSEfirewall2_init done<notice -- Aug 10 22:33:40.277171000> killproc: kill(7880,31)
<notice -- Aug 10 22:33:40.295420000> reboot start
Running /etc/init.d/halt.local
done

---

### Post by rsrini on 2010-08-11
The chain loader +1 command from grub2 worked. It showed the grub1 graphics window. Then i selected the suse 11.3 from the grub1 window. It booted suse properly. 

Pressed e in the suse menu entry and removed --search line, linux line, intird lines and added only chainloader +1. set root = '(hd0,7)' was there before chain loader +1. 

Now i have to find how to add the entries for booting directly the suse 11.3 images from grub2 instead of chain loading. One good step today. Sending this message from suse 11.3 (first time) after lot of struggle.

---

### Post by 23dornot23d on 2010-08-11
Great work .... not sure about the chainloading to get it to auto load .... maybe Oldfred or someone else can help you out here .... 
*thinking about it - can't you set the wait to zero in Grub 1.5  and have SUSE as the first option"
Glad you have it working now though ..... why it did not work from GRUB2 is still a mystery.

---

### Post by oldefoxx on 2010-08-11
Let me jump in here to see if I can help a bit.  But to do that, I have to try and explain something that happens, not only between different distros,
but different installs of Ubuntu alone, even if all the same version.  Some like this feature and may have asked for it, but it is a cronic troublemaker.

The troublesome spot is user accounts.  These are not just specific programs if installed that way, but data, and more corruptive, user-specific configuration settings.  They are fine for one distro and one version only, and could even become corruptive with a single configuration update change, because changes in settings from one release to the next vary, even if intended to duplicate those used previously, because they are not standardized in any uniform way.  Or like with grub, someone is in the process of revising and improving on what already exists.  Now grub is not a part of individual account settings, but someone might decide in the future to make it so, so that some users have these boot options and others a different set.  And since Legacy grub does not work with Grub2 (naturally), and Grub2 can't cope with Legacy grub (isn't that rich?), we are caught in a messy tangle.

For Ubuntu at least, and likely universally, user accounts fall under one  very specific folder named /home.  So same-named accounts under different installs actually end up being the same account here.  Some like that a whole lot, since they can then have all their stuff with them whichever distro they log into.  But say on your last install you used all the same account data, but mistakenly did a capslock as you pressed the "A" key.  If this is the first letter of the password, both it and the verification password will be the same, to it passes a check.  But you don't know this, and when you try to log in later using lower case, it fails and you don't know why.  So you try to log in on the same named account on another install, and what do you suppose the chances are that you inadvertenty put the password there to upper case as well?  A simple error, but it cost you access to all your accounts, since they are really all the same to start with.  You might work something out, but it is time wasted.

There is another reason you should not want the same account everywhere.  Why do we bother with backups in the first place?  Yet here you are, going the other way, consolidating everything in one place, meaning one significant error and it is all gone.

Sorry to make this so long, but it was first important to frame out the nature of the problem.  Now there are ways to get around all this, as I laborously worked out and explained in other threads, but here is a new one that came to me, so I haven't tried it yet, but it could work,

First, map out in your head on paper the exact arrangement of partitions you want and use gparted or another tool to set them up that way.  Don't mess with any you want to stay intact as they are.  

Second, remove any boot flags and mark them all as hidden except where you want to put the next install, and oh yes, the small one for a swap.  You may have an 8 GB monster on hand, but if installing 32-bit OS, I would stick to a maximum of about 3 GB for the swap.  You can only use 2 GB of RAM when doing 32-bit, and they only recommend about 1.5 times as much for the swap.  Your other 6 GB of RAM?  Probably money down the drain unless you can use them as spares or go to 64-bit for some reason

So now you can use several install approaches, but since only one partition shows up outside swap, the root and all subfolders should go there.  Unless you inhibit the creation of a boot process, it wiii appear there as well, meaning /boot/grub should be evident,  If you did add the boot process (default choice), you might test to see if it works.  There are issues with drive and partition order, partition designatons, what can boot and what doesn't that likely have to be sorted out, so it is uncertain at this point, and will be made more uncertain going forward.  But fret not, it should work out well towards the end.

This should be the pivot step:  Get gparted up again, hide this partition, unhide the next one to install to, and go through the process again with a different distro or whatever.  Never let more than one install partition and the swap to be evident at a time.  This way the only choice for the installer is to put everything on that one partition, including its own /home and user accounts.  Now if you want to pause the install process and get some updates in as you proceed, even add more packages, no big deal. It's your machine and your call.

Okay, you have just finished the last install.  What now?  Well, unhide all those hidden partitions with gparted, decide which is boot and flag it, and on reboot see if it flies.  If not, don't panic.  Try each of the others as well in the same manner.  I am rather certain that at least one will launch as it should. perhaps more than one.  Fine.  Now to attend to them all.

Here you can go to grub direct, whichever version you want, and have it install and locate all the installs on its own.  Or if there is a spot of trouble with one, you can look at its own grub script file likely in some place like /boot/grub/menu,lst on the partition in question.  Now I can't go much further because it all varies by PC and what you want on it.  But the hurdle of snatching access to each other's user accounts has been met.

Now far as I know, /home is the only folder and contents that the installer will respect and leave intact on a partition if you do not specify there needs to be a reformat as well.  This may also be true with other distros, but I can't say with any certainty.  But where true, it can be used to another advantage, to house packages, images, common downloads, and virtual drive images (.VDI).  These can then be treated as shared or common among the users, and will like the user accounts, have more persistence on that partition while also reducing the number of copies needed to meet user needs.  Here might be a typical folder add-on layout:

/home/VDIs
/home/ISOs
/home/DEBs
/home/SAVs
/home/ZIPs

Now something like /home/DEBs is somewhat questionable.  I mean, once a package is installed, what is the point of holding onto the shipping carton?  An argument might be to just download it once, put it in one spot, then when needed for an install on a different partition, you know pretty much where to find it, just cutting across partitions to get to it
and by spreading some debs among several partitions like this. no one partition gives up too much disk space for this purpose.  I mean, be creative.  You can always change things around later.

I hope this proves useful.  I've yet to find an OS that does it all and gets it all right, and while Ubuntu has it pretty good thus far, it seems a go forward somewhere calls for at least one "go back" elsewhere.  Maybe someday they will get it completely right, but what would any of us have to look forward to then?  But not to panic, I see no sign that we are close to that taking place any time in the near , or possibly the distant future,  As I've noted elsewhere, linux is locked rather strongly to the past in some respects, and I just wonder if that is its best course.  It's not going backwards, but how is it then considered going forward?

---

### Post by 23dornot23d on 2010-08-11
You may have it worked out there, that is probably why mine works ok and the one being set up does not ......

I always keep the same userid and username and set all of my accounts exactly the same .....
I have no issues swapping between systems .......  or booting up into them from GRUB2 even for SUSE

You seem to be saying its a good idea ...... to have different users and ids .... my experience on my system
that is set up only for me, may be different as it suits my way of working between desktops and OS's
 
I found that with using the same user accounts all my information is available to me from one OS to the
next .... (I would be surprised if this was as easy to do with different accounts and ids/passwords)
 
I am quite happy with the way the set up works too and have 3 OS's sharing the same /home.
and at least 12 more OS's now using there own /homes .....

I have never had a problem with passwords either .....   but as you say messing up the ones that share 
the same /home all on the  same drive too ....... could probably lead to some problems 
(I have noticed a few odd things with settings but there but have never crashed or had any real visible problems).
I will watch what I do in the shared home more closely now though ....

---

### Post by zarthon on 2010-08-12
> **23dornot23d said:**
> You may have it worked out there, that is probably why mine works ok and the one being set up does not ......

I always keep the same userid and username and set all of my accounts exactly the same .....I have no issues swapping between systems .......  or booting up into them from GRUB2 even for SUSE

23dornot23d, My experience is similar to yours. I have had only rare and application specific problems with sharing user accounts between different Linux installations. Where such an issue would start is after logging in. Even at that point it's rare because most programs now properly save settings for incompatible versions in separate folders.

I agree that user settings can cause problems that are difficult to troubleshoot but they are not boot or X11 problems. They always start after login.

A good trick for trouble shooting any such problems is to ```
#cp -a /home/jondoe/.* /home/johndoe/settingsbackup
## then reboot
#sudo shutdown -r now
```


> 
You seem to be saying its a good idea ...... to have different users and ids .... .... passwords etc. etc. 

If these should not match then someone sure had better rethink NIS!

This could have been a mess experienced but unresolved, and so feared and avoided, If usernames and Ids just kinda match but actually don't exactly file ownership breaks down and havoc ensues. Make sure early on when adding a new distro-version to the system that the new user id's match the existing linux distros and the /home partition. Since different distros start user id's at different numbers you must check and hack /etc/passwd to make the shared /home mount work properly. You can append the non-daemon users from the old distro onto the /etc/passwd of the new one.  


It is suboptimal that user settings are stored in hidden files in each user's home folder. User data and user settings should be stored in different places that could be easily managed as separate mount points.  

I have another trick to keep my data with me wherever I go. I separate out large parts of my own data from /home/jondoe/. I have separate lvm volumes that I mount at points below my user folder for documents pictures video and music.  I paste these mounts to the end of /etc/fstab/ after creating my user and the mount point directories.  This way I can choose to have an install with separate settings  and still retain a good chunk of my data. I have found this is better than juggling settings files in and out of my user home folder.

IMNHO distribution installers should be asking if you have existing users and partitions that you want to use with the new installation and handle this in a self-adaptive fashion.

---

### Post by 23dornot23d on 2010-08-12
> 
You seem to be saying its a good idea ...... to have different users and  ids .... my experience on my system
that is set up only for me, may be different as it suits my way of  working between desktops and OS's
You have to take these two lines together ..... the context I meant this in ....

Was about easily sharing information across OS's and Desktops for one USER ..... it sounds odd now when I re-read it .... ( first thing in the morning ) obviously there should be no problem with having multiple users ..... the way I meant this to come out - was that to make it easier for me I do not use multiple id's.
I do not have to go around and make changes to my file system to make the files and directories RW ..... they are already set up for me ...... but if I had multiple users and accounts that would not be easily achieved .... which is the way it should be - otherwise each user could go into another users account and overwrite that users data with there own. *I hope this is clearer ..... 


Saying this then blows my theory out of the water ....
> 
I agree that user settings can cause problems that are difficult to  troubleshoot but they are not boot or X11 problems. They always start  after login.
Because he should not have experienced a userid or account problem before logging into the Desktop.

My thought here now is that he may have had the same userid .... therefore having the same named ******/home ......... but maybe having a different password or other settings ,,,, that are causing a problem as he tries to go into it ..... 

I don't know ...... this is my best guess work here ...... 


**So we really need to know from rsrini if the user was set up the same across the different systems giving in effect the same /home directory ..... (so that we can make any sense of this)** and was this a shared /home between one or more systems ..... also were there any differences in the way he assigned the user files within this /home

But even here I am not sure that we are looking at the right thing .... why would it boot ok from GRUB 1.5 .......... and yet not boot ok from GRUB2.


What you have said gives me more confidence that the user being the same across the different OS's is alright to have - 
if their individual user information is stored in different places for each OS ..... that is brilliant especially for same user names.
should mean I can have separate desktops for each user that use the same /home area.


But at least SUSE 11.3 works from GRUB 1.5 .... and if the auto boot  into the system from GRUB1.5 can be made to work then I guess the OP  ...... has a solution to this problem
(I guess the account and Userids are not a issue in this scenario either as it works ok)

---

### Post by zarthon on 2010-08-12
> **23dornot23d said:**
> You have to take these two lines together 
What you have said gives me more confidence that the user being the same across the different OS's is alright to have - 
........
But even here I am not sure that we are looking at the right thing .... why would it boot ok from GRUB 1.5 .......... and yet not boot ok from GRUB2.



Those were the messages I was trying to convey, but I was primarily agreeing with you.

[SIZE="3"][INDENT]**For Rsrini** to eliminate the possiblity that it's a problem with user settings just backup the user settings with cp, and make sure that uids used in the filesystems match. Oh! And also, while passwords can differ across OS's for each OS it's /etc/passwd and /etc/shadow pair must match. man "shadow" and "pwconv" for more info.

/var/log/boot.log and "tail -n 150 /var/log/messages > /tmp/messages.post" would be useful as attachments for further trouble shooting.
You might use an external drive for booting up a bunch of OS's like i think 23dornot23d was talking about and keep the setup for the school simple?

[/INDENT][/SIZE]
[B]
A warning about Grub-install![/B] It only updates the grub2 stage 1 in the mbr or partition boot area **however it does nothing for the corresponding modules in /boot/grub! ** The grub2 that shipped with Ubuntu 9.10 is not compatible with the one from 10.04, and the one from MINT might be different from each of them. I don't think this is the problem because you would fail to the "grub rescue" prompt. ( That would also happen if /boot/grub had the stage 1.5 for grub (v1) and no grub2 modules. ) 

The conservative measure when upgrading a /boot mount in place is to back up /boot/grub before the upgrade to /boot/grub910 or /boot/grubmint.  If it fails you will get a "grub rescue" prompt. If you can find the right module files either from a backup or another partition,
```
## For GRUB2 RESCUE prompt
#set prefix=<where the modules matching the loaded stage1 are>
#set root=<where the kernel and intit rd are>
#insmod normal
#normal

```
[SIZE="1"]* There is a second step to get running after insmod normal to get up and running.I believe the command is **normal** but it could be something like **loadnormal**.[/SIZE]

Use ls and ls / to find the right place for the modules. If after the **normal*** rescue command a menu comes up and it's the one you want you are good to go otherwise drop to healed grub2 prompt to boot manually.

I am not sure, but I think the menu ( grub.cfg ) used is from the $root/grub/grub.cfg and not $prefix/grub.cfg so it should match the setup in the partition you choose as root. Does anyone listening know this? 


If you ever get into a mismatched uid or gid situation you can repair it using a one line script designed around the **find** command. (that is one line per uid that needs to be adjusted)

Aside comments
[LIST]
[*]23dornot23d, I talk like there are multiple users on the system i referring to. The the other users are non-primary guest users. They are either logging in for file sharing or are borrowing my workstation mainly to get on-line so are a secondary concern to me than *my user*..lol. Its always good to consider if there were many others how would the setup be different? 
[*]23dornot23d,rsrini, What is attractive about the new SUSE?
[*]rsrini, If you start a new thread about this DVD you want to make please link back to this thread. I'd like to follow that topic too.
[/LIST]

---

### Post by 23dornot23d on 2010-08-12
> 23dornot23d,rsrini, What is attractive about the new SUSE?I would love to be able to give you a run down on SUSE 11.3 ....... but my main reason for loading it up was to see how it had progressed from the last version I had tried a long time ago.
* In all honesty I prefer Debian based Distros ..... and the only benefit I have found so far is the Make Human application ...... which loads from the package manager.
( One disadvantage was not being able to get Cairo-Dock to work in SUSE 11.3 probably missing some plugins .... I will sort it )

Most of the things that I do are to do with Photography ..... 2D editing and 3D .....

The OS is of no real concern as long as its quick - stable and runs the software I want ....
and saves my files ok ...... 

I do like lots of desktops though ,,,,  I have them all set out as I want them and its nice to open up Firefox and its got all the relevant info on the first set of tabs I open up ...... and it is a reminder where I left off ...... 
( Its good fun too ..... sometimes I get to a desktop and can quickly get up to speed from exactly where I left off .... some OS's do - do some task's a little better than others
Also running Blender 2.53 files separate from the 2.49b ones .......   
Similar with Gimp 2.6 and 2.7 ...... although on one system I do have both of these running [Gimp 2.7 in a opt directory] as there are no compatibility problems.)

---

### Post by rsrini on 2010-08-16
Due to time constraints i did the work around for now. Used the Suse 11.3 grub1 as a chain loader from ubuntu 10.04 grub2. Made the grub1 waiting time as 0. I am getting a text screen immediately after grub2 menu start chain loading grub1. But it works. I definitely want to upgrade suse 11.3 with grub2 - not now.

I am sending the pc to the school now - updated with lot of education SW in ubuntu 10.04. I hope they enjoy the stuffs. I have to add 5 more thin clients to it next month. 

I am going to buy one more similar PC for me now. In that i want to keep at least three (ubuntu, suse and fedora). Thanks for your help. I may need some more help. 

Some people like suse. Somebody likes ubuntu. That is personal choice. I don't have any like to particular os. Only learning.

---


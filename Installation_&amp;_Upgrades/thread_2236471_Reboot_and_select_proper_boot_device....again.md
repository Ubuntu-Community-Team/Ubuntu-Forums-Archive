---
title: "Reboot and select proper boot device....again"
date: 2014-07-27
forum: Installation &amp; Upgrades
---

### Post by Autra_Tipton on 2014-07-27
First things first: I'm running a Toshiba Satellite e55-a5114

That said, I'm new as all hell to Linux in general, but trying to figure it out because it seems like a damn good idea and it's interesting to me. 

Also, I'm stuck.

My HDD died on me a few days ago, and instead of dealing with the irritating people on geek squad, I've got a new hard drive in my comp, and I've been trying to install ubuntu all day. No matter what I do, I'm getting "reboot and select proper boot device or insert boot media in selected boot device and press a key"

I've installed about 12 times so far, hit f12 like a crazy man to make sure I'm booting off my HD and not the usb after install, I've run common sense setups, I've gone with installs that follow instructions from youtube...none of it actually lets me run ubuntu in any way that isn't straight off the stick.

What info do I need to give you guys/gals to help figure out what I'm doing wrong and fix this? It's driving me insane that I can't figure it out on my own with reading or watching videos, but here I am.

Thanks in advance!

---

### Post by sotiris2 on 2014-07-27
Check [this](http://ubuntuforums.org/showthread.php?t=1821980&p=11136267#post11136267) post to see how you can install a tool ,using the usb stick's **Try Ubuntu** option, that will create a comprehensive report of your system. It will give you a link to that report, post that link here.

To open a terminal you can use Ctrl+Alt+t.

---

### Post by Autra_Tipton on 2014-07-27
So when I go to follow those instrustions, I get:

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

Then I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package boot-repair

Where should I take this next, since it won't let me go any further than that? Apparently I can't install boot-repair at all

---

### Post by Bucky Ball on 2014-07-27
Welcome. You are booting from a USB stick and getting to a desktop fine when you 'Try Ubuntu'? You could open gparted, take a screenshot and post it here.

If the installer is working as it should, when you get to the partitioning section of the install, could you choose 'Something Else' and tell us if it sees a drive in there?

You give the impression the install is getting to the end then you are rebooting. Take the USB stick out after the install and when the machine reboots, what error are you getting? 

Is this a brand new hard drive and do you know how it was formatted previously? Again, boot from the LiveUSB, Try Ubuntu, launch Gparted, delete anything that's there partition-wise, if there is anything, and create one large partition or partition the drive the way you are going to want to install, for instance (example only):

/ =20Gb
/home = Large as you like
/swap = 2Gb

Back to desktop, install icon, during install choose 'Something else' and install to those partitions using those mountpoints (/, /home, /swap or whatever you decide) and those sizes. 

Hope that helps and let us know how it goes. ;)

Please let us know what release and flavour you are trying to install. 12.04 LTS and 14.04 LTS are the currently supported releases.

---

### Post by Autra_Tipton on 2014-07-27
>  Welcome. You are booting from a USB stick and getting to a desktop fine  when you 'Try Ubuntu'? You could open gparted, take a screenshot and  post it here.

Correct. Here's a screenshot: [http://i.imgur.com/eK3SOhC.png](http://i.imgur.com/eK3SOhC.png)

> If the installer is working as it should, when you get to the  partitioning section of the install, could you choose 'Something Else'  and tell us if it sees a drive in there?

Here's a screenshot of what I currently have at that point in an install: [http://i.imgur.com/secl3n4.png](http://i.imgur.com/secl3n4.png) (Fair warning, this is the last effort I made last night and I had been drinking a little at this point because I was so irritated.)

> You give the impression the install is getting to the end then you are  rebooting. Take the USB stick out after the install and when the machine  reboots, what error are you getting?

Yeah, that's what's driving me crazy. The install runs and apparently works just fine, then I click the prompt to reboot, and get the remove media/close disk drive promp. After I do that and hit enter, I get "Reboot and select proper boot device or insert boot media in selected boot device and press a key"

Also, once I get to this point, I have to manually reboot my machine with the USB inserted, because pressing a key, even with the USB in place, just gives me a repeat of the same message.

I've made sure that I'm booting from the HDD before the USB, so that's not an issue.

> Is this a brand new hard drive and do you know how it was formatted  previously? Again, boot from the LiveUSB, Try Ubuntu, launch Gparted,  delete anything that's there partition-wise, if there is anything, and  create one large partition or partition the drive the way you are going  to want to install, for instance (example only):

/ =20Gb
/home = Large as you like
/swap = 2Gb

No, it's not new. It's a replacement that I grabbed from my brother. I'll give this a shot after I finish this post and I'll let you know.

Oh, and I'm running 14.04 LTS

Thanks so much for taking the time to respond

---

### Post by Bucky Ball on 2014-07-27
The screen shot you show shows Ubuntu installed in EFI, no Windows or anything else. FAT would be the EFI partition, sda2 the / partition with Ubuntu, and /swap self explanatory. Have you another drive in there or is this what you want? I'm figuring that's it, and if so, you have Ubuntu on there, for sure. 

The error message you give in the first post, is that when booting with USB out I presume? I reckon try Boot Repair. That might work. You can install in a Live boot if you have ethernet or download ISO/burn disk/USB and boot it.

Get and use Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

### Post by Autra_Tipton on 2014-07-27
Welp, with the link you posted, I finally got Boot Repair to install, so progress. 

[http://paste.ubuntu.com/7877685/](http://paste.ubuntu.com/7877685/)

There's what I got from running it in case I need it, and I'm off to attempt to reboot.

---

### Post by Autra_Tipton on 2014-07-27
Still have the same issue on reboot.

Thoughts?

---

### Post by Bucky Ball on 2014-07-28
Did you run the recommended repair with Boot Repair (and a recent version of Boot Repair)? Well done with that, BTW. ;)

---

### Post by Autra_Tipton on 2014-07-28
Yeah, that's what I've done so far.

Thanks. Haha

---

### Post by Autra_Tipton on 2014-08-01
So I've been talking to my brother about this, and he's stumped as well.

We even went as far as to get a new SSD to put in, and I'm still having the same issue with the new hardware.

Any thoughts?

Edit: I just did a generic install, and after running boot repair, this is what I got: [http://i.imgur.com/MTXvYzZ.png](http://i.imgur.com/MTXvYzZ.png)

Here's the link it listed: [http://paste.ubuntu.com/7928791/](http://paste.ubuntu.com/7928791/)

---

### Post by yancek on 2014-08-01
Your boot repair output again shows you are using GPT partitioning in uefi mode.  sda1 is your efi boot partition where I would expect to see some boot files.  There are none but I don't use uefi so I'll just point you to the site below which explains using uefi.  If you haven't seen that site, some of the info might help. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by ubfan1 on 2014-08-01
Yup, your boot files are missing.  Definitely read the link above about UEFI.  Now I expect to see missing boot files when installing to external media, since the installer really wants to put them onto the hard disk, but in your case you are already installing to the hard disk.  I guess you could run the grub-install from the usb and install to the hard disk's efi, or maybe just copy the files you need from the / partition to the following on the EFI partition:
/EFI/Boot/BOOTX64.efi   (you could grab this one off the install media, it's set up for secure boot, so it's a copy of shimx64.efi)
/EFI/Boot/grubx64.efi     The signed version, again from the install media.  
/EFI/ubuntu/grub.cfg    copy from /boot/grub/grub.cfg    This is the full file which would need to be recopied after each kernel update which changes the /boot/grub/grub.cfg file.  The installer is better and just leaves a 3 line file which pulls in the maintained file with the configfile .... command.
That should give you a working fallback boot.  Now the nvram in your machine should point to /EFI/ubuntu/shimx64.efi (for a secure boot) with the
grubx64.efi (signed version)
The /  install has copies of all the shim and grubx64.efi files tucked away for doing the installs, but you can just copy them yourself (Their locations are like /usr/lib/grub/x86_64-efi-signed/grubx64.efi.signed  and /usr/lib/shim/shim.efi.signed)  When copied, change the names to shimx64.efi and grubx64.efi.

---

### Post by oldfred on 2014-08-01
Pastebin does not really look different.
Grub says it installed correctly and ubuntu is shown in UEFI boot options.

 Reinstall the GRUB of sda2 into the MBR of sda
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

    BootOrder: 0000,0003,0002,0004
Boot0002* UEFI: IP4 Realtek PCIe GBE Family Controller
Boot0003* UEFI: IP6 Realtek PCIe GBE Family Controller
Boot0004* UEFI:  Patriot Memory PMAP
Boot0000* ubuntu.

I thought Toshiba's worked, but Sony & HP have modified UEFI to only boot Windows.
Do you have secure boot off in UEFI, but UEFI on?

Because you do not now have Windows, does not mean you cannot create a /efi/Microsoft/Boot folder with the Windows efi file that is really grub or shim.


 [http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
**Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Backup entire efi partition before making changes.
**A:** Manually rename files either  efi\Microsoft\Boot\bootmgfw.efi and/or /EFI/BOOT/BOOTX64.EFI to be grub or shim
**a1**: Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.
**a2:**(this is the same as what Boot-Repair does in B:. 
Rename /efi/Microsoft/Boot/bootmgfw.efi and copy grub or shim into /efi/Microsoft/Boot and name it bootmfgw.efi  Then boot Windows entry to boot to grub menu. You have to manually add a grub menu entry to boot renamed Windows efi file. Grub2's os-prober entry boots bootmfgw.efi entry which is now just grub, so it will not work.

   Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   **B:**Boot_Repair renames Windows bootmgfw.efi. But cannot boot Windows from UEFI only from grub menu  with bkpbootmgr.efi entry
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair of bootmfgw.efi will need to be redone after a Windows update as it will restore Windows files.

   **C: **Edit Windows BCD, one Alternative to Boot-Repairs rename to make shim have Windows name.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   **D:** If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

   **E:** Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)
Now has a ppa to make it easy to install:
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)

      
     From live installer mount the efi partition on hard drive:
    mount /dev/sda1 /mnt
    cd /mnt/efi

       us ls to see if created correctly
    ls -l
    mkdir Microsoft
    mkdir Microsoft/Boot
    cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Microsoft/Boot/bootmfgw.efi

Other Toshiba models, UEFI may be similar or other issues also:
  [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)
Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)
How to install Ubuntu 13 dual boot with Windows 8 Ubuntu Studio
[http://ubuntuforums.org/showthread.php?t=2186838](http://ubuntuforums.org/showthread.php?t=2186838)
Used jockey to install correct video driver
[http://ubuntuforums.org/showthread.php?t=2188572](http://ubuntuforums.org/showthread.php?t=2188572)
Toshiba laptop C850 Windows 7 with upgrade to 8 version -  sudodus
[http://ubuntuforums.org/showthread.php?t=1769482&p=12606025#post12606025](http://ubuntuforums.org/showthread.php?t=1769482&p=12606025#post12606025)

---


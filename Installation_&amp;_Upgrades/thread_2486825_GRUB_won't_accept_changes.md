---
title: "GRUB won't accept changes"
date: 2023-05-12
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2023-05-12
My GRUB 2.06 font is tiny, so I found [this explanation]("https://blog.wxm.be/2014/08/29/increase-font-in-grub-for-high-dpi.html") of how to increase it.  After a *sudo update-grub, *nothing changed. Since I have 3 installs on 3 drives, I made sure that all three */etc/default/grub* files are identical. Still nothing changed.

relevant settings:
```
#GRUB_TERMINAL  (commented-out)
GRUB_GFXMODE=2560x1600x32,1920x1080x32,auto
GRUB_GFXPAYLOAD=keep

# For a more readable font on high dpi screens, generated with:
# sudo grub-mkfont --output=/boot/grub/fonts/DejaVuSansMono24.pf2 --size=24 /usr/share/fonts/truetype/dejavu/DejaVuSansMono.ttf 
# per <https://blog.wxm.be/2014/08/29/increase-font-in-grub-for-high-dpi.html>  
GRUB_FONT=/boot/grub/fonts/DejaVuSansMono24.pf2
```

other settings:
```
GRUB_DEFAULT="0"
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

Everything else is commented-out. 
Any tips (on where to start looking to get GRUB to accept changes) appreciated.

---

### Post by MAFoElffen on 2023-05-12
You have 3 instances of Grub... reminds me of... Well... "Me".

I have done a lot of grub theming in the past when I was bored. What I had to look for, and was causing me frustration was determining where the current Grub Menu was coming from (which OS), and how to control that change made there, made changes to the menu, without getting zapped, during an upgrade of another OS Grub Update.

For me to get around that, and to help me ID that, I used to configure each OS that used Grub with a way to ID with where it was coming from.

I see you used this: [https://unix.stackexchange.com/questions/31672/can-grub-font-size-be-customised](https://unix.stackexchange.com/questions/31672/can-grub-font-size-be-customised)

Is your PC EFI or BIOS boot?

---

### Post by ubfan1 on 2023-05-12
Nvidia can run with secure boot these days, but I think there might be a signing issue for the grub fonts.

---

### Post by watchpocket on 2023-05-12
I hadn't actually seen that stack exchange page but what's there is essentially what I did.

My computer (desktop workstation) boots via UEFI/GPT, motherboard is in my sig. I'm running UbuntuMATE 22.04 on an nvme1 drive (newly installed); UbuntuMATE 20.04 on an nvme0; and 20.04 on an SSD, all internal drives.  Secure boot is, and has always been on this box, disabled. Also, it's not just the font-change that won't go into effect, it's any change.

---

### Post by oldfred on 2023-05-13
All installs of Ubuntu, Ubuntu flavors & most many unoffical distributions based on Ubuntu use "ubuntu" as UEFI boot entry.
So only one UEFI boot entry which will point to one ESP which has a 3 line grub.cfg that is a configfile to point to full grub.cfg in your default install.
You can trace boot by checking GUID/partUUID in ESP entry & UUID of configfile in ESP. 
sudo efibootmgr -v
cat /boot/efi/EFI/ubuntu/grub.cfg
(if using default setting of 0077 of mount of fstab, you will not be able to see grub in ESP for security reasons).
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid

Note that major updates to grub will reinstall it, that then that version, becomes new default.
You then have to boot into version you want as default and reinstall grub. If fstab has correct ESP entry, you just need:
sudo grub-install

I in past tried this which did not work as something in shimx64.efi is hard coded to find grub.cfg in /EFI/ubuntu.
[FONT=monospace][COLOR=#000000]In /etc/default/grub:
#GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
[/COLOR][/FONT][FONT=monospace][COLOR=#000000]GRUB_DISTRIBUTOR=jammy
[/COLOR]
Then in UEFI I get different entries, but they do not work as mentioned above. Hoping they fix eventually. jammy-b is an install on my sdb drive.
[/FONT][FONT=monospace][COLOR=#000000]BootOrder: 0001,0018,0002,0019,001A,001B,0005,0000,002E,002F [/COLOR]
Boot0000* jammy-b       HD(1,GPT,c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1,0x800,0x100000)/File(\EFI\JAMMY-B\SHIMX64.EFI) 
Boot0001* jammy HD(1,GPT,c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1,0x800,0x100000)/File(\EFI\JAMMY\SHIMX64.EFI)
[/FONT][FONT=monospace][COLOR=#000000]Boot001A* ubuntu        HD(1,GPT,c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO[/COLOR]

Uses grub.cfg in Ubuntu folder in ESP, not jammy folder.
[/FONT]

[FONT=monospace]
[/FONT][FONT=monospace]


[/FONT]

---

### Post by watchpocket on 2023-05-13
I've gotten into a bit of a pickle & not sure how to proceed: Grub will not appear at all now when I press <SHIFT> as I'm booting up, and my main install suddenly takes a full 2 minutes to boot up to the login screen. (Much longer than it normally does.)

AFAICT this happened right after I used *sudo efibootmgr -b 0001 -B*  and *sudo efibootmgr -c -L "20.04_SSD"* to re-name (a) my first other boot entry (to "20.04-SSD" instead of "ubuntu"); and (b) I used the same commands to re-name (to "22.04") my 2nd other boot entry. ( I didn't rename the entry for the system I was logged in on (which was 20.04 on nvme0, my current main system). I'm not sure that would even work.

When I *FIRST* re-booted after making this change, I *WAS* able to use the <SHIFT> key to bring up the Grub menu.  And, in fact, for the first time, the Grub font *WAS* the larger 24-point fontsize that I'd been trying to make happen.

But with every re-boot since then, I can't get Grub to appear, and the login takes inordinately long.

 Also, when I brought up *sudo efibootmgr -v*, all 3 boot entries had reverted back to the same name of "ubuntu", instead of 2 of them having the new names I gave them.  Also the numbers got changed from 0000, 0001 and 0002, to 0001,0002,0003.

And in the newly installed 22.04 fstab, the umask is set to 0077. The better setting might be 0007? I'm murky on that. (In my other fstabs, there are no umask, dmask, or fmask entries.)  

My question is [I]**how can I get the Grub menu back,** and how can I get my install to boot at its normal faster time?
[/I] 
```
--> lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid

NAME        FSTYPE   SIZE FSUSED LABEL       PARTLABEL                  MOUNTPOINT UUID                                 PARTUUID
sda                894.3G                                                                                               
&#9500;&#9472;sda1      vfat   550.3M        SSD_ESP     SSD_EFI-system-partition              6DE5-0FF8                            684141f2-20c3-41be-b2c4-7058d9488896
&#9492;&#9472;sda2      ext4   893.7G        20.04_SSD   UbuntuMATE-20.04_SSD                  21697ef7-83e3-4414-a859-91841f61dce8 7cc6f822-eb23-4829-9039-6d09e6e0ca55
sdb                894.3G                                                                                               
&#9492;&#9472;sdb1      ext4   894.3G        WeirdBeard  WeirdBeard_data                       70e15e24-a75c-4115-9c83-29cb585676f6 5ab70820-78e7-466e-9c0f-101054d5df9b
nvme0n1            931.5G                                                                                               
&#9500;&#9472;nvme0n1p1 vfat     402M  11.3M NVME0_ESP   nvme0_EFI-system-partition /boot/efi  2BD2-4199                            337ce8d2-65a0-4051-8c12-55cc22666e7e
&#9492;&#9472;nvme0n1p2 ext4   931.1G  56.6G 20.04-nvme0 UbuntuMATE-20.04           /          07041e0f-1cde-4caf-9b1d-86851e9601ed 0657b873-53c2-4a40-9e60-3b26c891fd1b
nvme1n1            931.5G                                                                                               
&#9500;&#9472;nvme1n1p1 vfat   402.5M        NVME1_ESP   nvme1_EFI-system-partition            E23B-29C2                            90af4214-eca8-4265-8e5f-9c2e3301bba9
&#9492;&#9472;nvme1n1p2 ext4   931.1G        22.04_NVMe1 UbuntuMATE-22.04_nvme1                3bcf9a37-e310-4945-87a8-dac0932a16cb 77706804-715d-4276-9824-a184ed00df4f
```

```
--> sudo efibootmgr -v
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0001,0002,0003
Boot0001* ubuntu    HD(1,GPT,337ce8d2-65a0-4051-8c12-55cc22666e7e,0x4000,0xc9000)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO
Boot0002* ubuntu    HD(1,GPT,90af4214-eca8-4265-8e5f-9c2e3301bba9,0x4000,0xc939a)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO
Boot0003* ubuntu    HD(1,GPT,684141f2-20c3-41be-b2c4-7058d9488896,0x4000,0x113229)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO
```

  ```
--> vim //etc/default/grub
  1 # If you change this file, run 'sudo update-grub' afterwards to update /boot/grub/grub.cfg.
  2 # For full documentation of the options in this file, see:
  3 #   info -f grub -n 'Simple configuration'
  4  
  5 GRUB_DEFAULT="0"
  6 GRUB_TIMEOUT_STYLE="hidden"
  7 GRUB_TIMEOUT="0"
  8 GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
  9 # GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
 10 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nvidia-drm.modeset=1"
 11 GRUB_CMDLINE_LINUX=""
 12  
 13 # Uncomment to enable BadRAM filtering, modify to suit your needs
 14 # This works with Linux (no patch required) and with any kernel that obtains
 15 # the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
 16 #GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
 17  
 18 # Uncomment to disable graphical terminal (grub-pc only)
 19 #GRUB_TERMINAL=console
 20  
 21 # The resolution used on graphical terminal.
 22 # Note that you can use only modes which your graphic card supports via VBE.
 23 # You can see them in real GRUB with the command `vbeinfo' or 'videoinfo'.
 24 GRUB_GFXMODE="2560x1600x32,1920x1080x32,auto"
 25  
 26 # For a more readable font on high dpi screens, generated with:
 27 # sudo grub-mkfont --output=/boot/grub/fonts/DejaVuSansMono24.pf2 --size=24 /usr/share/fonts/truetype/dejavu/DejaVuSansMono.ttf
 28 # per <https://blog.wxm.be/2014/08/29/increase-font-in-grub-for-high-dpi.html>
 29 GRUB_FONT="/boot/grub/fonts/DejaVuSansMono24.pf2"
 30                                                                                                                                                                                        
 31 # This tells the bootloader the graphics mode before the standard graphics driver is loaded
 32 # into memory. The value keep tells GRUB to use the same parameters as defined during the
 33 # initial startup sequence:
 34 GRUB_GFXPAYLOAD="keep"
 35  
 36 # Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
 37 #GRUB_DISABLE_LINUX_UUID=true
 38  
 39 # Uncomment to disable generation of recovery mode menu entries
 40 #GRUB_DISABLE_RECOVERY="true"
 41  
 42 # Uncomment to get a beep at grub start
 43 #GRUB_INIT_TUNE="480 440 1"

```

---

### Post by MAFoElffen on 2023-05-13
Change the highlighted items:
```

# If you change this file, run 'sudo update-grub' afterwards to update /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'
  
GRUB_DEFAULT="0"
GRUB_TIMEOUT_STYLE="[COLOR=#ff0000]menu[/COLOR]"
GRUB_TIMEOUT="[COLOR=#ff0000]5[/COLOR]"
[COLOR=#ff0000]GRUB_RECORDFAIL_TIMEOUT=5[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
# GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nvidia-drm.modeset=1"
GRUB_CMDLINE_LINUX=""
 
# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
 
# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console
 
# The resolution used on graphical terminal.
# Note that you can use only modes which your graphic card supports via VBE.
# You can see them in real GRUB with the command `vbeinfo' or 'videoinfo'.
GRUB_GFXMODE="2560x1600x32,1920x1080x32,auto"
 
# For a more readable font on high dpi screens, generated with:
# sudo grub-mkfont --output=/boot/grub/fonts/DejaVuSansMono24.pf2 --size=24 /usr/share/fonts/truetype/dejavu/DejaVuSansMono.ttf
# per <https://blog.wxm.be/2014/08/29/increase-font-in-grub-for-high-dpi.html>
GRUB_FONT="/boot/grub/fonts/DejaVuSansMono24.pf2"
                                                                                                                                                                                       
# This tells the bootloader the graphics mode before the standard graphics driver is loaded
# into memory. The value keep tells GRUB to use the same parameters as defined during the
# initial startup sequence:
GRUB_GFXPAYLOAD="keep"
 
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true
 
# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"
  
# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by watchpocket on 2023-05-13
Thank you! 

This got grub to appear.  

I'm going to run boot-repair now, and report back.

---

### Post by watchpocket on 2023-05-13
Grub appears fine, but my main system is uncharacteristically slow to load.  I ran boot-repair from within my main system, [here is boot-repair's report.]("https://paste.ubuntu.com/p/GgJqqw3vRy/")

Any suggestions how to fix the slowloading appreciated.

---

### Post by ubfan1 on 2023-05-13
Take a look at the output of systemd-analyze blame

---

### Post by watchpocket on 2023-05-13
Just did, but don't know what I'm supposed to find there.  Searched on "boot" and saw that one of the items in the long list of items is 
"74ms secureboot-db.service"

I hope that doesn't mean secureboot is active.  I know that I've always had it off in the UEFI settings.

Searched on "grub" & found "269ms grub-common.service" and "20ms grub-initrd-fallback.service"

Waiting now for boot-repair disk iso to download so I can run it from a flash drive.

---

### Post by oldfred on 2023-05-13
The Boot-Repair ISO typically is older.
Better to use Ubuntu live installer and add the ppa. Since you always should have live installer in case you need to make repairs, adding ppa for Boot-Repair is relatively easy.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by watchpocket on 2023-05-14
Boot info report [is here]("https://paste.ubuntu.com/p/CRdRYK3vHH/").  I ran this from the Jammy live installer, with the ppa Jammy boot-repair version 4ppa2056, dated 2023-02-09.  

I opened boot-repair and went right to the creation of the report, I didn't run the auto-fix or any repair sequence. 
And I always use the newer PPA boot-repair app on all my installs.

Just to recap: main issue I'm looking at currently is very slow booting of my main system, which is UbuntuMATE 20.04 on nvme0.
I'd like to get it back to its normal short-boot time.

My other 2 installs (nvme1, containing 22.04; and sda, containing a backup 20.04) both boot in normal fairly-quick time.

I see in the report that  [I]"No boot loader is installed in the MBR of /dev/nvme1n1." 
[/I] I think that's where I'd like the main bootloader/grub to be as I will soon be using jammy as my main system, and jammy is on nvme1.

I'd also like to make sure that after I re-set grub to appear only when I press <shift> as I'm booting up, that that actually happens. 

(Right now I have grub set to appear immediately for several seconds.  Before I set it that way, it would not appear after holding <shift>.)   

The grub that I see when I boot is version 2.06.

Thanks for any insights.

---

### Post by #&amp;thj^% on 2023-05-14
Do you really need this in grub>>>"nvidia-drm.modeset=1"
Are you running custom kernels?
```
apt policy nvidia-driver-530
nvidia-driver-530:
  Installed: 530.41.03-0ubuntu0.22.04.2
  Candidate: 530.41.03-0ubuntu0.22.04.2
  Version table:
 *** 530.41.03-0ubuntu0.22.04.2 100
        100 /var/lib/dpkg/status

```
My Grub_Line:
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

---

### Post by watchpocket on 2023-05-14
I just deleted *"nvidia-drm.modeset=1"* from grub.

My understanding of why I put it there was murky to begin with, which is always a bad idea, and I'm not running any custom kernels.
Thanks for the heads-up.

```
--> apt policy nvidia-driver-530
nvidia-driver-530:
  Installed: (none)
  Candidate: 530.41.03-0ubuntu0.20.04.2
  Version table:
     530.41.03-0ubuntu0.20.04.2 500
        500 [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) focal-updates/restricted amd64 Packages
        500 [http://ubuntu.mirror.constant.com](http://ubuntu.mirror.constant.com) focal-security/restricted amd64 Packages
        500 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) focal/main amd64 Packages
```

```
--> apt policy nvidia-driver-470
nvidia-driver-470:
  Installed: 470.182.03-0ubuntu0.20.04.1
  Candidate: 470.182.03-0ubuntu0.20.04.1
  Version table:
 *** 470.182.03-0ubuntu0.20.04.1 500
        500 http://ubuntu.mirror.constant.com focal-updates/restricted amd64 Packages
        500 http://ubuntu.mirror.constant.com focal-security/restricted amd64 Packages
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu focal/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by oldfred on 2023-05-14
With UEFI, you do not want grub installed to MBR for old BIOS boot.
UEFI boots from an ESP - efi system partition. Only one ESP per drive.
Ubuntu defaults to installing grub to first drive's ESP. During install you just about cannot change that. 
Grub can be installed to any ESP, best to either use one on first drive or have ESP on same drive as any other installs.
I prefer second option, but Ubuntu defaults to first option. 

You show an ESP on every drive with different GUIDs/partUUIDs. And three Ubuntu entries one using each ESP.
I change the setting in grub to have different names.

When Ubuntu first used the ESP in fstab, it used defaults. About 16.04 it changed to umask=0077  to lock down the ESP. Since FAT32 & Windows format, there is no ownership nor permissions, so a rogue app could easily write into it. So mount changed to have more security.
Boot-Repair changes that back to defaults, it makes it easier to access ESP, but it then is not as secure.  I current use defaults, but may change to the 0077 setting.

```
[FONT=monospace][COLOR=#000000]BootOrder: 0001,0018,0002,0019,001A,001B,0005,0000,002E,002F [/COLOR]
Boot0000* jammy-b       HD(1,GPT,c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1,0x800,0x100000)/File(\EFI\JAMMY-B\SHIMX64.EFI) 
Boot0001* jammy HD(1,GPT,c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1,0x800,0x100000)/File(\EFI\JAMMY\SHIMX64.EFI) 
Boot0002* lunar HD(1,GPT,c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1,0x800,0x100000)/File(\EFI\LUNAR\SHIMX64.EFI) 
Boot0005* focal_a       HD(1,GPT,e58602b1-8fc4-46d1-991f-1d6511d9cdf4,0x800,0xff1b9)/File(\EFI\FOCAL_A\SHIMX64.EFI)
[/FONT]
```

I change /etc/default/grub to use the name/label I prefer. So a simple grub-install changes name. But actual boot still is from the Ubuntu folder's grub.cfg in that ESP.
#GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_DISTRIBUTOR=jammy

---

### Post by watchpocket on 2023-05-14
> **oldfred said:**
> With UEFI, you do not want grub installed to MBR for old BIOS boot.
UEFI boots from an ESP - efi system partition. Only one ESP per drive.

So when the Boot Info Summary states at the top:

*"=> Grub2 (v1.99-2.00) is installed in the MBR of /dev/sda and looks at . . ."*

. . . is it using the term "MBR" as a holdover from the days before ESP?  I don't think I *HAVE* an MBR on any of my 3 drives.  Doesn't the summary really mean that Grub2 is installed on sda's* ESP?*  If so, it's damn confusing.

> Grub can be installed to any ESP, best to either use one on first drive or have ESP on same drive as any other installs.

My first drive is NVMe0, which has focal on it. I'd like Grub to be on the ESP of NVMe1, where I've newly installed jammy.  I'll look into the boot-repair util to see if I can use boot-repair to put it there.

> You show an ESP on every drive with different GUIDs/partUUIDs.

Is something wrong with that?

 > And three Ubuntu entries one using each ESP.

So, I take it that one Ubuntu entry should not be using three ESPs. All three Ubuntu entries should be using the Grub that's on ONE ESP. Yes?

> I change the setting in grub to have different names.

I tried to do this with efibootmgr but at the next boot my names all reverted back to "ubuntu".

I'll need to re-read & ponder your post a bit more before I take any action.

---

### Post by oldfred on 2023-05-14
Is sda not the live installer?
The live installer has both versions of grub installed. It has grub-pc for BIOS boot which is in MBR to start boot and grub-efi-amd64 for UEFI boot.
Both MBR & ESP only have parts of grub, most is in the install.

Boot-Repair defaults to first install and first drive, if it offers to reinstall grub. It often only does an update to grub which only updates menu.
But its advanced mode lets you choose an install and choose a drive.

It is Ubuntu's Ubiquity installer that only installs grub to first drive. The flavors & older versions use Ubiquity. The newest installer for servers & latest Ubuntu desktop is subiquity which some have posted fixed that issue.

If any grub you boots lets you boot into another install, and correct ESP is mounted in fstab, you can just reinstall grub from there. With UEFI boot & it can find ESP in fstab it reinstalls grub. I have used this to reinstall with new name, when I have changed distribution entry in /etc/default/grub.
sudo grub-install

---

### Post by ubfan1 on 2023-05-14
Pretty sure MBR means the first 512 bytes of the device, so a legacy, non-UEFI boot (which may not work without a supporting bios-grub on gpt drives).  Leaving it causes no problems with UEFI boots (except some confusion on the user's part maybe ;^) .
A UEFI partition usually includes a default device bootloader (.../EFI/Boot/bootx64.efi), which does not need an nvram entry (you boot the device instead of a name like "ubuntu".  The biggest problem with multiple EFI partitions is keeping the separate grub menus in sync -- old ones may contain old deleted kernels.  Don't know what boot-repair does with grub, but running grub-install from a terminal will allow you to specify exactly what you want (see the man grub pages) with the options.

---

### Post by watchpocket on 2023-05-16
I wanted to make my grub fully EFI, so I went into Synaptic and selected: 

grub-efi-amd64, 
grub-efi-amd64-bin, and 
grub-efi-amd64-signed 

for installation, heeding the note with *grub-efi-amd64* that says: *"Installing this package indicates that this version of GRUB should be the active boot loader."*

(Installing * grub-efi-amd64 *automatically removes *grub-pc* and *grub-gfxpayload-lists.)*

After installing it, I got this error: [I]
"Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting." 

S[/I]o I went in search of an updated Memtest86+ and found the new, EFI-compatible, version 6.20, at [https://www.memtest.org]("http://, at https://www.memtest.org").

This new Memtest86+ is to be used on a bootable flash drive (though also offered on that page is a *"Linux ISO w/ GRUB (64 bits)"*).
 
I installed (the non-grub) Memtest86+ on a flash drive, booted it and ran a RAM test and all was well with it.

My question is: If I install *grub-efi-amd64*,** will it now be safe for me to remove the (non-EFI-compatible) file *"20_memtest86+"* from the /etc/grub.d/ folder?** 

Or does grub require its own Memtest86+ to always be in place as part of grub? In which case I'd guess that I would instead need to install the *"Linux ISO w/ GRUB (64 bits)" *version.

Also, a perhaps dumber, though more fundamental question: Can I have just one grub for 3 OS-installs? My guess is that each separate OS-install must have its own grub, even though a single grub can, to some extent, control the booting of the other OSs.

---

### Post by watchpocket on 2023-05-16
Are you making sure to run ```
sudo update-grub
``` after making changes in /etc/default/grub? You have to do that for any change to take effect.

I would be careful with grub-customizer.  I didn't have such good luck with it back when I tried using it, and I stay away from it.

Also, you seem to have posted the wrong link. It has nothing to do with your question.

---

### Post by watchpocket on 2023-05-16
> **watchpocket said:**
> My question is: If I install *grub-efi-amd64*,** will it now be safe for me to remove the (non-EFI-compatible) file *"20_memtest86+"* from the /etc/grub.d/ folder?** 

I went ahead and did this.  I moved 20_memtest86+ into my home dir and named it OLD___20memtest86+ , then installed grub-efi-amd64, and got no warnings.

A new boot-info report is here: [https://paste.ubuntu.com/p/3dFz8W6Km8](https://paste.ubuntu.com/p/3dFz8W6Km8)

---

### Post by oldfred on 2023-05-16
You have three UEFI Ubuntu entries default is to nvme1n1p1 and then the UUID in its ESP.
With multiple installs and multiple ESPs, you will have to manage as updates may change which is default.

Always know GUID/partUUID that UEFI uses, the entries in  fstab by UUID and UUID of installs.
Boot-Repair report can help you keep track or efibootmgr, entries in ESP & entries in fstab of each install.

---

### Post by watchpocket on 2023-05-19
I'm marking this thread as solved since its various issues have been fixed, the most recent issue being that my main 20.04 system was very slow to load.

Apparently, ***OS Prober*** was (and may still be) disabled in Ubuntu 22.04, according to [this article]("https://www.omgubuntu.co.uk/2021/12/grub-doesnt-detect-windows-linux-distros-fix") from December 2021.  The workaround it suggests is to add this line to /etc/default/grub:
```
GRUB_DISABLE_OS_PROBER="false"
```
Immediately after I added that line, the slow-boot problem ended, and my boot-time was back to a much faster normal.
So either the slow-boot-on-20.04 problem was in fact due to a disabled OS prober on 22.04 (I'm running os-prober v1.79ubuntu2 there), or I just got lucky.

---


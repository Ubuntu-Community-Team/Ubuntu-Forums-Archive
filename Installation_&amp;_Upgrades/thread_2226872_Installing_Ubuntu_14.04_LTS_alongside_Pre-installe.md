---
title: "Installing Ubuntu 14.04 LTS alongside Pre-installed Windows 8.1 dual boot Problem"
date: 2014-05-29
forum: Installation &amp; Upgrades
---

### Post by Amro_Ali on 2014-05-29
Hello everyone,
Getting straight to the point, I am trying to install Ubuntu 14.04 LTS alongside a pre-installed Windows 8 (now updated to 8.1).  I am a newbie (even though I used Linux and Ubuntu for some time now, I still see myself as a newbie), so I would appreciate as much help and clarity as I can get. 
[h=1][SIZE=2]I am using a Toshiba Satellite L850-1L1 Laptop with the following specs[/SIZE][/h][h=1][SIZE=2]·         Processor Intel(R) Core(TM) i7-3630QM CPU @ 2.40 GHz[/SIZE][/h][h=1][SIZE=2]·         8 GB RAM[/SIZE][/h][h=1][SIZE=2]·         64 bit Operating System, x64-based processor[/SIZE][/h][h=1][SIZE=2]·         1 TB HDD (No SSD), GPT Partitioning scheme (GUID Partition Table)[/SIZE][/h][h=1][SIZE=2]·         System BIOS Version 6.7 / EC Version 6.00 (no idea if this bit of info will help or not)[/SIZE][/h][CENTER]
[IMG]http://tinypic.com/r/24lv236/8[/IMG]
[/CENTER]

I removed about 60 GB of the C partition that has windows. I left it as a new unallocated volume (I left it as free unpartitioned and unformatted space).  As for the Secure Boot and UEFI settings in the BIOS, I left them enabled (since I read in ask Ubuntu that it is always better to try installing with both options enabled) and shut down the laptop. Something worth mentioning, I read an article that said I should switch to CSM Mode before shutting down and then install Ubuntu; I did not do that. When I change the boot manager from UEFI to CSM Boot, it does not boot anything coz of copyright issues. Plus, Ubuntu boots in legacy mode and not UEFI Mode.

With try Ubuntu I was able to boot the live version without problems, then started installing Ubuntu and when I got to the system installation window there was no option that said “install alongside windows 8”. So I picked “something else”, made a 5.77 GB partition (read somewhere that it is supposed to be 10% the size of the main system partition) for swap area and 51.22 GB for booting the main system ( / ). After Installation GRUB menu opened and I could open Ubuntu without problems but with windows, it gave me an error and did not want to boot it. I ran boot repair and it closed with an error and gave me a pop out message saying I should turn off secure boot. After that, there was no GRUB and it boots straight to windows.

Here is the first boot repair link: paste.ubuntu.com/7517709

I then formatted the partitions again and did the whole thing again with secure boot disabled this time. Again no GRUB menu and boots straight to windows 8 (yes windows 8 on my laptop works with secure boot disabled), so I entered the live version and ran boot repair again. This time it did not tell me that I should disable secure boot, but it did not solve the problem either. Same problem, no GRUB and boots straight to windows.

Here is the first boot repair link: paste.ubuntu.com/7536732

A couple of more points:

·         I cannot change the OS boot manager in BIOS. Simply because that option does not exist
·         Boot Manager in BIOS allows me to choose between CSM and UEFI only
 
Appreciate any help to make the dual boot work.
Thanks

---

### Post by ubfan1 on 2014-05-29
Your setup looks like a standard secure boot one, which with the ubuntu first in the boot list (sudo efibootmgr-v ), should bring up the grub menu.  If that is not happening, maybe you didn't turn off the "fast boot" in the Windows power options.  That option short circuits the whole boot process and just brings in a Windows system image from disk.  You can try the efi menu (F12 ?) at power up (I wait until the vendor spash, then press it (boot speed set to normal in BIOS/UEFI Settings).  The one glitch with your machine may be that it cannot boot windows from grub with the secure boot on, but as you have noticed, everything works with it off too.  One other way into the windows boot is the /EFI/Boot/bootx64.efi .  Some boot failures (like trying to boot non-signed grubx64.efi with secure boot enabled) will silently fall back to trying bootx64.efi instead of trying the next boot loader in efibootmgr's list).  You can make bootx64.efi a copy of shim.efi, and put a copy of the signed grubx64.efi into /EFI/Boot too to fall back to the grub boot.  You are confusing modes with bootloaders -- UEFI systems allow multiple bootloaders, and you have successfully added the ubuntu shim bootloader as far as I can tell from your paste.

---

### Post by oldfred on 2014-05-29
Some just work better with secure boot off.
You should be able to boot either system with secure boot on from UEFI menu, but maybe not Windows from grub.
 
Unable to chainload Windows 8 with Secure Boot enabled  Also post #11 on using refind
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)

---

### Post by Amro_Ali on 2014-06-01
This is a repost because my original post was marked as having a solution/duplicate somewhere else and I read those solutions before and tried them countless times with no success. I followed the advice in my original post and I would like to say thank you for your help but the problem still exists.

I am using a Toshiba Satellite L850-1L1 Laptop with the following specs
· Processor Intel(R) Core(TM) i7-3630QM CPU @ 2.40 GHz
· 8 GB RAM
· 64 bit Operating System, x64-based processor
· 1 TB HDD (No SSD), GPT Partitioning scheme (GUID Partition Table)
· System BIOS Version 6.7 / EC Version 6.00 (no idea if this bit of info will help or not)

Note: in the My computer window i can see only 3 Partitions (C, E and G). There are 3 Other partitions - OEM Partition, UEFI Partition, OEM/Recovery Partiton. After Installing Ubuntu u can add a swap area partition and the ubuntu system partition. Is the max number of 4 primary partitions the problem with my system or am I in the clear on this one?

With try Ubuntu I was able to boot the live version without problems, then started installing Ubuntu and when I got to the system installation window there was no option that said &#8220;install alongside windows 8&#8221;. So I picked &#8220;something else&#8221;, made a 5.77 GB partition (read somewhere that it is supposed to be 10% the size of the main system partition) for swap area and 51.22 GB for booting the main system ( / ). After Installation GRUB menu opened and I could open Ubuntu without problems but with windows, it gave me an error and did not want to boot it. I ran boot repair and it closed with an error and gave me a pop out message saying I should turn off secure boot. After that, there was no GRUB and it boots straight to windows.

Here is the first boot repair link: paste.ubuntu.com/7517709

I then formatted the partitions twice more and did the whole thing again with secure boot disabled this time. Again no GRUB menu and boots straight to windows 8 (yes windows 8 on my laptop works with secure boot disabled), so I entered the live version and ran boot repair again. This time it did not tell me that I should disable secure boot, but it did not solve the problem either. Same problem, no GRUB and boots straight to windows.

Here is the boot repair link: paste.ubuntu.com/7536732 
Here is the boot repair link: paste.ubuntu.com/7565465

A couple of more points:
· I cannot change the OS boot manager in BIOS, i.e. I cannot choose boot priority between windows 8 & ubuntu. Simply because that option does not exist
· Boot Manager in BIOS allows me to choose between CSM and UEFI only

Plus Hibernate and fast startup are disabled. No matter what I do grub never comes up and boot repair ends with an error.

Please i need advice urgently. It has been a week now

---

### Post by Amro_Ali on 2014-06-01
it did not really work with me, though i would appreciate a little more enlightment on the copying the  signed grubx64.efi into /EFI/Boot and all of that. I am still a newbie. Sorry for the inconvenience

---

### Post by Amro_Ali on 2014-06-01
> **oldfred said:**
> Some just work better with secure boot off.
You should be able to boot either system with secure boot on from UEFI menu, but maybe not Windows from grub.
 
Unable to chainload Windows 8 with Secure Boot enabled  Also post #11 on using refind
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)



None of them worked for me :(. I have to be doing something wrong

---

### Post by coffeecat on 2014-06-01
> **Amro_Ali said:**
> This is a repost because my original post was marked as having a solution/duplicate somewhere else and I read those solutions before and tried them countless times with no success.

Threads merged. Please do not post duplicate threads about the same problem. If the first solutions do not work, simply give feedback to those helping you so that everyone can move onto other ways of solving the problem. Starting a new thread merely confuses those trying to help you and dilutes community effort.

---

### Post by oldfred on 2014-06-01
If secure boot is off, you should not need the signed copies, but it does not hurt to install them. Boot-Repair can do that.
The errors in Boot-Repair all all related to various older software it uses to parse install that does not work with new systems, but is required if you have an older system.

I think those with Toshiba systems have not had UEFI issues like the HP & Sony systems. Those only boot Windows as they modify UEFI to only read a Windows entry.

These are different Toshiba and older installs but your system may have some of the same issues?
  [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)
Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by oldfred on 2014-06-01
Are you sure you cannot make any changes in your UEFI? 
Some have hardware as one boot selection and UEFI as another boot selection, not always on same UEFI/BIOS screen. 
And if in CSM/legacy mode it will not show UEFI options.

I think returning it may be overkill, as mode Toshibas have worked. Sony & HP are usually the one's with major issues.

[http://askubuntu.com/questions/475241/after-boot-repair-laptop-boots-straight-to-windows-8-without-grub-no-solution](http://askubuntu.com/questions/475241/after-boot-repair-laptop-boots-straight-to-windows-8-without-grub-no-solution)

---

### Post by Amro_Ali on 2014-06-01
Success, before I read the answers here I found a link that said when windows 8 starts I should open the command prompt and type in &#8220;bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi&#8221;. It exited successfully and I restarted my computer and the grub menu came up with both systems and both boot normally.

---


---
title: "UEFI still boots directly into Windows 8 instead of GRUB"
date: 2013-01-05
forum: Installation &amp; Upgrades
---

### Post by benzejaa on 2013-01-05
Hey all:

I am attempting to install Ubuntu on my new laptop, which runs windows 8 preinstalled (in UEFI mode).  I would like to do this in a dual boot situation.  

Secure boot is off.  

Running the ubuntu installer seems to work, and has correctly installed Ubuntu in EFI mode.  However, my laptop still boots directly into windows 8.  Boot-repair returns no problems, but it advises me to make sure my BIOS boots to sda3/EFI/ubuntu/grubx64.efi, which I believe is probably my problem.  Unfortunately I don't know much about the layout of an EFI partition, so I don't know how to do this.

Here is the summary from boot-repair:

[http://paste.ubuntu.com/1500260/](http://paste.ubuntu.com/1500260/)

Any suggestions?  I've kind of hit a brick wall here.

---

### Post by oldfred on 2013-01-05
I am not sure why Boot-Script is giving the READ-Only errors?

But you have to go into UEFI/BIOS to change boot order. Some systems use f2 but it varies by vendor.

Microsoft posted many of the options.
       UEFI/BIOS Boot keys - about halfway down on this page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

    
One user said you can even change the name in the UEFI menu.

> Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 

    

Some UEFI seem to have settings for secure boot on & off. Others seem to just have a setting for UEFI on, which means secure boot off. And then many have setting for legacy/BIOS/AHCI boot which then is no UEFI at all. Sometimes when one setting is enabled you cannot change the others without changing the first. For example,  if secure boot is on, you cannot change to legacy boot without first turning off secure boot.

---

### Post by benzejaa on 2013-01-05
Let me start off by apologizing that this computer has the most bizzare boot setup and the most poor BIOS that I've ever seen.

My computer is [this one seen here]("http://www.bestbuy.com/site/Sony+-+VAIO+14%22+Touch-Screen+Laptop+-+8GB+Memory+-+1TB+Hard+Drive+-+Gunmetal/Vintage+Gold/6747147.p?id=1218792108092&skuId=6747147").  To start the BIOS, I have to press a dedicated button on the computer, which starts up a graphical menu with a bunch of options, such as "booting windows", "starting the windows repair utilities", and the golden one, getting into the BIOS settings.

However, the BIOS really has no useful options, it's the "Aptio Setup Utility" all I can do is turn on/off secure boot and change between UEFI and Legacy boot.

I guess this is something I should take up with Sony then?

---

### Post by oldfred on 2013-01-05
I believe Boot-Repair has a work around. It renames the Windows boot file to .bkp for backup and puts the grub efi file as the Windows file. Then it adds a chain load entry to the backup so you can boot Windows from the grub menu.

       How Boot-Repair works with UEFI systems - post 687 Dec 15, 2012
[http://ubuntuforums.org/showthread.php?t=1769482&page=69](http://ubuntuforums.org/showthread.php?t=1769482&page=69)
How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)

    
Other Sony's that have worked. May have same UEFI?
       Sony Vaio [SOLVED] dual boot ubuntu 12.10 & windows 8 problem 
[http://ubuntuforums.org/showthread.php?t=2094761](http://ubuntuforums.org/showthread.php?t=2094761)

            Sony T & Intel SRT ubuntu 12.10 & Windows 8 oem 
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)

---

### Post by benzejaa on 2013-01-05
Thanks for your help, I was going to try manually doing something like that myself, but I'll poke around in boot-repair some more to see if that can work.

Here is my chat with a sony rep.  Not exactly promising:

[http://paste.ubuntu.com/1500516/](http://paste.ubuntu.com/1500516/)

In summary, you can't dual boot because we locked down your BIOS ha ha.

I'll give the boot-options a shot and will post again if I have results.

---

### Post by benzejaa on 2013-01-05
Okay I have it working now, I'll set the thread to SOLVED.

My problem ultimately is that this computer has TWO Fat32 partitions with EFI tables on them...one for windows normal mode (sda3) and one for windows advanced system settings (sda1).  Even though I told boot-repair that my EFI partition was on sda3, I believe it still screwed around with sda1.  So my solution was to manually do the process:

1) mount the efi partition 
```
sudo mount -t vfat /dev/sda3 /mnt
```2) create backups of your windows .efi files 
```
sudo cp /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.bkp
sudo cp /mnt/EFI/Microsoft/Boot/bootmgfw.efi /mnt/EFI/Microsoft
```/Boot/Bootmgfw.efi.bkp
3) Copy the ubuntu .efi file  in it's place 
```
sudo cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Boot/bootx64.efi
sudo cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/MicrosoftBoot/bootmgfw.efi
```4)  Copy the ubuntu .efi file to the same location with a .grb extention, in case you need to use boot-repair in the future.
```
sudo cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Boot/bootx64.efi.grb
sudo cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/MicrosoftBoot/bootmgfw.efi.grb
```This will allow the computer to boot to Grub by replacing it's original destination with a new file, while keeping the old ones around as backup.  However, since boot-repair created grub around the wrong partition, the "start windows from bootmgfw.efi.bkp" entries only started the advanced system utilties, not windows itself.  To fix this, I changed the grub menu items to point to the right location.

5)  Go to /etc/grub.d/ and find the file which contains your menu entry.  Grep might be helpful for this. For me, the file is 25_custom it looks like:
```
menuentry "windows UEFI bootmgfw.efi.bkp" {
search --fs-uuid --no-floopy --set=root DE90-E7F8
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi.bkp
```6)  Back up this entry if you wish, or simply change it.
7)  Replace the line that begins with "search" to say
```
set root='(hd0,gpt3)'
```(note that I have gpt formatted disk, and hd0, gpt3 corresponds to /dev/sda3, the disk which contains my .efi files.
8) Run update-grub to update the menu
```
update-grub
```9) You win!

A great deal of this was taken from [this comment]("http://ubuntuforums.org/showpost.php?p=12379441&postcount=637") on how boot-repair works.

Thanks for the help!

---

### Post by YannBuntu on 2013-01-05
Good job!
(Boot-Repair never creates *.grb and *.bkp for the same efi file, so please delete your two .grb files, there are useless and might cause problems if you use Boot-Repair in the future.

FYI , in the Boot-Repair log, we can see many mount errors, which are why Boot-Repair failed. Apparently, you managed to mount these partitions later, so I don't know why you had these errors.)

---

### Post by benzejaa on 2013-01-06
Thanks for the update on the .grb files.  Note that the .grb files correspond to ubuntu/grubx64.efi and the .bkp files correspond to the orginal bootx64.efi and bootmgfw.efi files, so they are not the same file.

I think something is strange either about the ubuntu grub install or the partition itself...When I look into EFI/ubuntu/ there's a lot of files with weird filenames, and there's some sort of black unknown partition after sda3 when I view it in GParted, although that's been there since I got the computer.  However, I tend not to touch things that are working, so I'm just leaving it alone.

I'm actually trying a few other distros now, because ubuntu was doing funny things with my touch screen, but doing ubuntu first was a great learning experience and extremely helpful, since it currently seems to have the best resources for dealing with UEFI and windows 8.  I think I'd be toast if it wasn't for the forum advice here and the post I had previously linked, so thanks :-)

---

### Post by oldfred on 2013-01-06
Windows has a MSR partition which is unformatted space or scratch space for Windows. With MBR Windows & DRM vendors hid serial numbers and other info in the space between the MBR and the first partition, so I assume this is where Windows now puts that info.

Currently only a few systems work with secure boot.
        The State Of Linux Distributions Handling Secure Boot
[http://www.phoronix.com/scan.php?page=news_item&px=MTI2MzI](http://www.phoronix.com/scan.php?page=news_item&px=MTI2MzI)

---


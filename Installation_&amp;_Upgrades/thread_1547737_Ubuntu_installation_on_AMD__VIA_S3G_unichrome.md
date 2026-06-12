---
title: "Ubuntu installation on AMD / VIA S3G unichrome"
date: 2010-08-07
forum: Installation &amp; Upgrades
---

### Post by bsubbudu on 2010-08-07
I have a desktop with AMD Sempron 3000+, 1.2GB RAM, VIA S3G Unichrome Pro IGP, VIA SATA RAID controller based disks, PS/2 mouse and keyboard running Windows XP.
 
Wanted to move to years ago favourite (linux based systems), I downloaded Ubuntu 10.04 for i386 and am trying to install both using CD as well as USB.
 
After the Ubuntu start-up menu for installation, I select install Ubuntu option, turn off 'quiet' so that I can see what happens. The screen goes blank dark with a flashing cursor at the top.
 
In the kernel messages, the see that it has detected the processor, set the clock, assigned the PS/2 keyboard to input3 and then says:
 
[ 1.911624] isapnp: no plug and play device found
 
After this, the system hangs. Keyboard doesn't work.
 
Any thoughts?

---

### Post by S.R on 2010-08-07
Did you try the alternate install download ... [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

---

### Post by bsubbudu on 2010-08-07
Not yet. Am downloading the same.
 
In the meanwhile, wanted to try out with any other possible kernel command changes...

---

### Post by bsubbudu on 2010-08-07
ok, I tried the alternate install. NO luck.
 
after vmlinuz and initrd loading, when it tries to check the devices, it reboots. NO messages too this time. 
 
Need help!

---

### Post by bsubbudu on 2010-08-07
There's an error that flashes for a millionth of a second :( while booting that says:
unrecognized keyboard configuration in gfxboot. I cant find anything to do with keyboard in the gfxboot config file:
 
----------------------------------------------------------
[SIZE=2]foreground=0xFFFFFF
background=0x958490
screen-colour=0x270A1E
label normal=Normal
append normal=
label oem=OEM install (for manufacturers)
append oem=oem-config/enable=true
applies oem=install
label cli=Install a command-line system
replace cli=file=/cdrom/preseed/cli.seed
applies cli=install
label ltsp=Install an LTSP server
replace ltsp=file=/cdrom/preseed/ltsp.seed
applies ltsp=install
-----------------------------------------------
any guidance?
[/SIZE]

---

### Post by S.R on 2010-08-07
Try disabling USB Legacy Support in the BIOS.

---

### Post by rivenathos on 2010-08-07
This may sound odd, but it has worked in the past for me when installing to a system with Via Unichrome or Chrome9 chipsets.

Instead of burning the ISO to a CD, burn it to a DVD.  This is the exact same ISO, but using a DVD instead of a CD.

From what I gather, the SquashFS errors that can occur when using a CD are not present when using a DVD. I am not an expert, but can only verify that this method has been known to work for installing Ubuntu 9.04, 9.10, and 10.04.  Hopefully this helps.

---

### Post by bsubbudu on 2010-08-07
tried doing both, one at a time - disabling legacy USB as well as the DVD write. Same result. isapnp - no device found.
 
feeling stuck!

---

### Post by bsubbudu on 2010-08-07
Went into the text mode finally and was able to go past the isapnp - no plug and play device found error.
 
Now, it asks me to specify a root device. how do I do it in the cli. all that I see is a boot:
 
Looking for help to get past.

---

### Post by S.R on 2010-08-07
Beyond my level so I will give you a bump.

Don't know if it is feasible for you but have you thought about getting an USB wireless keyboard /mouse combo?

---

### Post by bsubbudu on 2010-08-08
This must be a very simple thing that I am missing. Need help:
 
Alternate CD install of 10.04.
 
I get the Ubuntu install menu. I choose the 'install Ubuntu' option. Switch tab and remove 'quiet --'
 
Output:
 
It scans 0 and adds 0 RAID devices
 
RAMDISk: gzip image found at block 0
usb 1-5: new high speed USB device using ehci_hcd and address 2
List of all partitions: <<<<<<nothing gets listed here>>>>>>>
No filesystem could mount root, tried: ext3 ext2 ext4 fuseblk
 
Post this, I see a kernel panic with the now famous, yet another scenario, message 'not syncing: VFS: Unable to mount root fs on unknown-block(8,1)'
 
Wondering how to get this fixed.
 
Have tried switching BIOS config from RAID to IDE and back for SATA mode. Still no luck.

---

### Post by bsubbudu on 2010-08-09
What is the scenario when it detects raid arrays but detects 0 disks?
 
Could it be a problem that Ubuntu does not work well with RAID where Windows XP is previously installed in another partition?
 
Am still hoping one of those experts will come by and answer :)

---


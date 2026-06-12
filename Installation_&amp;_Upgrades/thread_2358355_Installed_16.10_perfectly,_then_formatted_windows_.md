---
title: "Installed 16.10 perfectly, then formatted windows bootloader, now I have black screen"
date: 2017-04-12
forum: Installation &amp; Upgrades
---

### Post by neorich20022 on 2017-04-12
Hi All,

My setup was Windows7, with two internal hard disks. A 1TB and a 250GB one. 

Today I installed Ubuntu 16.10 on the 1TB disk, erasing everything else. I was surprised to get no messages about the UEFI etc, but alas it worked.

Required me to change the boot order to boot from the 1TB disk, but so far so good. 

I wanted to remove windows totally. So I downloaded gparted, and removed all the partitions of the 250GB disk and then reformatted to EXT4. 

Unfortunately with this last step, I think I took out the bootloader with it.

I now get a black screen when turning the computer on, no splash screens, the green power light goes on and the fan works, but I see nothing on screen. I confirm the monitors are working. Even if I insert a bootable USB or CD, it doesn't boot and I can't access any boot menus.

Ideally I would simply totally remove anything to do with Windows, and have 100% clean Ubuntu install, but if I need to have a windows style bootloader or something I can tolerate it. 

Unfortunately I have no idea how to fix this now, as I seen unable to interact with the computer. 

Presumably I can remove the HDD and give it a bootloader through another working PC? But not sure how.

Any advice would be appreciated.

Thanks

Joey

---

### Post by Bucky Ball on 2017-04-12
Welcome. Boot Repair is your friend. Please see the red link at the end of the first line of my signature at the bottom of this post. 

Boot Repair will give you the option to run the bootinfo script. Please run that rather than the 'Recommended Repair' for now. When it's finished it will give you a link to the output. Post the link back here, thanks.

PS: Can you get to the BIOS at boot? Is it possible this is a coincidental hardware failure? Checked cables? Tried a different monitor? Are you running a laptop and if so, it is on battery or plugged in? If the former, plug it in.

---

### Post by neorich20022 on 2017-04-12
Thanks for your reply, 

1.) Coincidental hardware failure seems extremely unlikely. I wiped the disk and then restarted and immediately it black-screened. I have checked all the cables, tried a different monitor (which I know to work) etc. 

2.) I am unable to get the BIOS. I am also unable to boot from USB or CD, so I'm not able to use boot repair on this machine.

3.) This is a desktop PC.

---

### Post by oldfred on 2017-04-12
If newer UEFI system and smaller drive was sda, then Ubuntu boot loader was in ESP on sda.
If BIOS system, did you install grub to same drive as your Ubuntu install when using Something Else? Any of the auto install options install grub to sda's MBR.

Newer systems have UEFI fast boot (different than Windows fast start up). That may prevent you from booting live installer.
You can try full cold boot or power down. Unplug system, hold power switch for 10 sec or so to drain all power, then on boot either get into UEFI and turn off fast boot or boot flash drive immediately. Better to turn off fast boot when ever reconfiguring system.
Most desktops also have instructions on jumpering pins on motherboard. That will totally reset UEFI/BIOS to defaults and you must go into UEFI and change all the setting you changed before. 

Then if you can boot live installer, run Boot-Repair.

---

### Post by neorich20022 on 2017-04-12
Hi,

The smaller drive I wiped was the sdb one. 

As for UEFI/SecureBoot, I had the legacy mode enabled and the fast boot off.

I shall look into jumping pins.

Thanks

---

### Post by efflandt on 2017-04-14
Try disconnecting power from the internal drives and booting a live/install iso. If still not BIOS splash, shut down and try one more time.

I actually cannot run 16.04 on my main desktop because it leaves something in my system in a state such that my screen does not display any text until something does graphics (blank screen all through BIOS splash and grub menu until gui login). And even after I disconnect the 16.04 drive, it is still blank during one more boot until something does graphics (either Ubuntu gui login or Win7 does graphics, depending upon default). Next boot BIOS splash and everything shows up. That does not happen with 16.04 on any other computer and does not happen running 16.10 on this computer.

I think you can then try plugging power into the drives while running. When I was trying to security-erase an SSD I had to hot disconnect/reconnect power from the SSD while running to clear up something that was preventing that. The secure erase totally clears all blocks of an SSD quickly (erasing everything) for fasted writing. After that TRIM periodically clears up blocks from deleted files.

---

### Post by neorich20022 on 2017-04-20
Hi Again,

I have now tried removing the CMOS battery and also using the jumper switch to clear the BIOS cache. Neither worked.

I got my hands on another PC of identical spec, and I can report the following.

The new PC has the same disk set up, a 1TB disk and a 250GB disk. This machine has windows installed. It boots perfectly.

If I take the large disk from the old PC with Ubuntu on it and add it into the new PC (in addition to existing disks), then new PC fails to boot, and fails to even go to POST, no beeps, nothing.

If I remove disk again, it boots to Windows perfectly. 

If I take the working windows disk and put it in old machine (without the linux disk) it still doesn't boot, or even reach POST.

Any further thoughts?

---

### Post by oldfred on 2017-04-20
What brand/model PC? Or What motherboard?
And what video card/chip?

It seems like both a UEFI/BIOS configuration and then the drive is corrupted. 
Do you have same version of UEFI/BIOS on both systems?

---

### Post by neorich20022 on 2017-04-20
It's an HP Z420. 
Video Card is an Nvidia Quadro K600.

The systems are of similar age, and things are pretty standard here, so I believe the versions on each are the same.

Is there a reason that a second system (which otherwise is fully operational) would fail to boot or even POST if a corrupt drive was used as a slave?

---

### Post by oldfred on 2017-04-20
Working install probably has the nVidia driver.

Is system UEFI or just BIOS?

Workstation systems, may need extra drivers that are not default with standard desktop installer.
[https://certification.ubuntu.com/hardware/201406-15260/](https://certification.ubuntu.com/hardware/201406-15260/)

google has a link to a now non-working page. 
Part of description mentions certain ports & UEFI issues, but link to more info does not work.

---


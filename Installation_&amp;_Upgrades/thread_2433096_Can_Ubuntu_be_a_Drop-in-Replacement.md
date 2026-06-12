---
title: "Can Ubuntu be a Drop-in-Replacement?"
date: 2019-12-13
forum: Installation &amp; Upgrades
---

### Post by rebeltaz on 2019-12-13
I got a new-to-me laptop and I'd like to transfer my old laptop to this one. I know that, back in my younger, unenlightened window$ days, you couldn't just take the hard drive out of one computer and drop it in another one and expect it to work due to hardware and driver issues.

My question is does Ubuntu suffer from this as well? Or is it able to adapt itself to the new hardware?

---

### Post by tea for one on 2019-12-13
I've taken an SSD from a 9 year old Intel Mini-ITX desktop machine and installed it in a more modern Intel NUC, lo and behold, everything worked.

However, your new laptop may have different wifi, graphics and sound devices compared to your older one?

I would simply try it - nothing ventured nothing gained.

In my experience Ubuntu is quite versatile when presented with alternative hardware.

---

### Post by rebeltaz on 2019-12-13
> **tea for one said:**
> I've taken an SSD from a 9 year old Intel Mini-ITX desktop machine and installed it in a more modern Intel NUC, lo and behold, everything worked.

However, your new laptop may have different wifi, graphics and sound devices compared to your older one?

I would simply try it - nothing ventured nothing gained.

In my experience Ubuntu is quite versatile when presented with alternative hardware.

Honestly, I am seriously hoping for a different (i.e. better) graphics adapter. I can't do anything related to rendering with my current laptop. 

If I do try this, if it doesn't work as expected, you don't think it'd do any damage to the system to where I can't put it back in my old laptop and it pick up where it left off, do you? Thank you for the vote of confidence!

---

### Post by yancek on 2019-12-13
> back in my younger, unenlightened window$ days, you couldn't just take  the hard drive out of one computer and drop it in another one and expect  it to work due to hardware and driver issues.

It would also be a problem because the windows license is specific to one computer and specific hardware.  Obviously that is not the case with Ubuntu.  You should be able to move the drive to another computer and have the new hardware detected.  I'd try the drive in the new computer and see what happens and don't make any changes if you think you might want to put it back in the old computer.  If you get ereros, you might post again with the specific error before making any change. You might try using an Ubuntu 'live' system of the same version to test.

---

### Post by tea for one on 2019-12-13
> **rebeltaz said:**
> If I do try this, if it doesn't work as expected, you don't think it'd do any damage to the system to where I can't put it back in my old laptop and it pick up where it left off, do you? Thank you for the vote of confidence!

I do not think that you would cause any damage by transferring the (Ubuntu) drive to your newer laptop.

However, it is always advisable to proceed cautiously and carefully..

As **yancek** mentioned, try it and do not make any changes until you confident that there are no trapdoors.

Is Windows OS also on your original drive? I keep forgetting about this because I last dual-booted more than 10 years ago? 

I have no idea if you can transfer a Windows drive seamlessly.

By the way, what are the models of each laptop? Similar or markedly different?

---

### Post by crip720 on 2019-12-13
With Ubuntu you should be able to just to drop in the HD.  Only problem would be If old Ubuntu does not have drivers for the new hardware yet.  14.04 won't have drivers for 2019 hardware.

---

### Post by rsteinmetz70112 on 2019-12-13
It should work, I've done it lots of times including changing motherboards in desktop cases. In most cases Ubuntu will simply load the correct drivers.

The only potential fly in the ointment is if the old laptop is old enough to be BIOS based and the new one is UEFI.

---

### Post by kurt18947 on 2019-12-13
The only thing I've heard of when swapping hard drives is to be sure there are no user added drivers. For instance, if drivers from Nvidia were installed and active and the install were inserted into a machine with AMD graphics it may not be happy. Using drivers already installed 'out of the box' shouldn't cause a problem. I did something similar this past weekend. I had a desktop power supply that decided it had lived long enough and decided to take the motherboard along for its trip the the hereafter. I bought a new Ryzen motherboard/processor, installed them and everything worked, no surprises. I know graphics drivers can be a problem, I'm not sure about others such as Broadcom Wifi drivers.

---

### Post by TheFu on 2019-12-13
I've swapped drives multiple times in multiple different machines.  In general, it works, but ... 
* NICs might not work due to the new system having an odd NIC; MAC changes cause udev to work through reassigning device names
* Any fstab entries that aren't lookups, i.e. are direct device names like /dev/sda1, can fail totally. UUIDs have been the default for 15+ yrs, so it would be manually added storage.
* Drivers, especially for GPUs that don't exist. Usually when a driver for a discrete GPU is installed, sometimes other drivers have to be blacklisted. This can end up with no GPU drivers on the new system.  Best to remove any proprietary GPU drivers and un-blacklist the GPL GPU drivers BEFORE moving the disk.
* I did have an issue moving a virtual machine server from Intel to AMD CPUs.  Some of the VMs were specifically setup to use Intel CPUs, so it wasn't any surprise on an AMD VM host when the VMs weren't happy to boot.  Fixed that in the VM settings, no other issues.
* Obviously, moving a 64-bit install into a i686 CPU won't work.

None of this is unexpected, right?

---

### Post by Tadaen_Sylvermane on 2019-12-14
For what it's worth I can attest to success here. I've moved my server ssd to 2 different machines now with totally different hardware from the first installation. Not one single problem yet. To be fair I haven't had any custom drivers or firmware to deal with, that may be an issue. The only minor "issue" i had was that my static ip didn't work as my interface name had changed on the new hardware. Easy fix, just plan for it.

---

### Post by rebeltaz on 2019-12-14
No, no window$ on drive I place to transfer. Single linux operating system.

The donor laptop is an HP Pavilion DV6. The new one is a Compaq CQ56.

I appreciate all of the responses. I'll try it this weekend and cross my fingers. Thanks guys and gals.

---

### Post by kansasnoob on 2019-12-14
Both the old and new computers must boot in the same mode - older BIOS or UEFI. Other than that it'll typically work if you first remove any and all "additional drivers".

---

### Post by kurt18947 on 2019-12-23
> **kansasnoob said:**
> Both the old and new computers must boot in the same mode - older BIOS or UEFI. Other than that it'll typically work if you first remove any and all "additional drivers".
And PPAs. I should have mentioned that one in my earlier response. You want as close to a "plain vanilla" install as you can get before trying to upgrade.

---

### Post by bunny9000 on 2019-12-25
I can see a problem - if the drive is IDE and laptop is sata. ;)

---


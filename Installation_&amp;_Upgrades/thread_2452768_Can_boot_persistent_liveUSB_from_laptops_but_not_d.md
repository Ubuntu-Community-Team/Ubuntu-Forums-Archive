---
title: "Can boot persistent liveUSB from laptops but not desktops"
date: 2020-10-28
forum: Installation &amp; Upgrades
---

### Post by ping-wu on 2020-10-28
Without getting into details, I have made a groovy persistent LiveUSB. I have tried this liveUSB on several laptops of different makes (all are AMD Ryzen laptops) without any problem. Actually it works great (except that I have to hit ctrl + c keys to stop filesystem checking during grub booting).

But yesterday I tried to boot this liveUSB on my main working machine, which is an AMD Ryzen 7 desktop with B450 mainboard, and run into kernel panic. A friend with a similar machine also couldn't boot from a similar liveUSB.

Just wondering what might have been the problem?

---

### Post by sudodus on 2020-10-28
Maybe a problem with the graphics. Did you try with recovery mode or to add the boot option nomodeset at the grub menu?

---

### Post by ping-wu on 2020-10-28
> **sudodus said:**
> Maybe a problem with the graphics. Did you try with recovery mode or to add the boot option nomodeset at the grub menu?

Tried.  Still getting kernel panic.

---

### Post by sudodus on 2020-10-28
Have you tried also booting live (live-only, not persistent)?

It is possible that the linux kernel cannot manage the hardware of that computer. But let us hope that you can change some setting in order to make things work.

I must admit, that I don't know what is the problem. Let us hope that someone else can chip in and suggest what to try next.

---

### Post by ping-wu on 2020-10-28
No problem with normal boot from the LiveUSB.  Looks like the persistent parameter caused kernel panic.

---

### Post by sudodus on 2020-10-29
Can you still boot other computers from this persistent live drive?

In that case there is a problem with this particular computer (and I don't know how to solve it).

But if also the other computers fail now, the problem is probably that the content of the partition for persistence causes the corruption. In this case you can remove all files from it and also check/repair the file system.

```

sudo e2fsck -f /dev/sdxn

```

where x is the drive letter and n is the partition number of the partition for persistence.

---

### Post by ping-wu on 2020-10-29
I have no problem booting this persistent LiveUSB from all my other computers &#65288;all three of them are Ryzen notebooks).  A persistent LiveUSB made from the same procedures had problem booting from another B450 based desktop computer.  Indeed, the reason I discovered this problem was a friend had problem booting the persistent LiveUSB from a similar B450 desktop.

BTW, I made a persistent LiveUSB for 20.04.1 and 18.04.5; both failed to boot.  But I was successful in booting a persistent LiveUSB, made from identical procedures, from 19.10.

To reiterate, I have no problem in booting the same LiveUSB with the persistent boot parameter disabled, from all my computers.  No problem in booting this persistent LiveUSB from notebooks.  No problem with 19.10.  Similar problem with 20.04.1 and 18.04.5.

I copied the EFI folders from 19.10 iso to 20.10 persistent LiveUSB, but for unknown reasons, I screwed up--system not found.

---

### Post by sudodus on 2020-10-29
You have really checked a lot of alternatives and shown where the problem occurs. I don't understand what is the problem and how to make a persistent live drive work in the problematic computer.

[HR][/HR]
Maybe you find it worthwhile to test an installed system in a USB pendrive or SSD connected via USB (installed like into an internal drive, but into a USB drive). I would be very interested in the result - if it works or not in the problematic computer.

I made a compressed image file from an installed system of Ubuntu 20.04 LTS. This system can boot both in UEFI mode and BIOS mode. You can download it (and check with md5sum) and then use mkusb to extract and flash it to the USB drive (with size at least 16 GB) in one operation.

See the following links,

[If you need not encrypt the drive, there is an easy alternative](https://ubuntuforums.org/showthread.php?t=2447539&p=13974203#post13974203)

[help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

### Post by ping-wu on 2020-10-30
This is the error message I got when booting the 20.10 persistent LiveUSB from a B450M based desktop machine:

run-init: can't execute '/sbin/init': No such file or directory
Target filesystem doesn't have requested /sbin/init.
run-init: can't execute '/sbin/init': No such file or directory
. . .

Again, no such problem when booting from laptops or when the persistent parameter was turned off.

---

### Post by sudodus on 2020-10-30
Thanks for the details. Unfortunately I still don't understand what is the problem. I can only suggest some more 'trial and error'.

Try another tool/method to create the persistent live drive

1. What tool/method have you been using? If you used **mkusb-dus**, you can try **mkusb-plug** instead and vice versa. If you intend to use mkusb-plug with Ubuntu 20.10, you should get the newest version from the unstable PPA

```

sudo add-apt-repository ppa:mkusb/unstable

```

2. You can also try '**grub-n-iso**' alias '**isoboot**' according to [this link](https://help.ubuntu.com/community/Installation/iso2usb/isoboot)

---

### Post by C.S.Cameron on 2020-10-30
If you want to bypass disk checks when booting see: [https://askubuntu.com/questions/1250119/how-to-skip-filesystem-checks-during-boot/1250141#1250141](https://askubuntu.com/questions/1250119/how-to-skip-filesystem-checks-during-boot/1250141#1250141)

If you make the Persistent USB using **mkusb** it will do the fix automatically.

I think that I recall that filling up a Persistent "writable" partition will cause kernel panic, confirm that your persistent partition is not full.

---

### Post by ping-wu on 2020-10-30
> **sudodus said:**
> Try another tool/method to create the persistent live drive

1. What tool/method have you been using? If you used **mkusb-dus**, you can try **mkusb-plug** instead and vice versa. If you intend to use mkusb-plug with Ubuntu 20.10, you should get the newest version from the unstable PPA

```

sudo add-apt-repository ppa:mkusb/unstable

```

2. You can also try '**grub-n-iso**' alias '**isoboot**' according to [this link]("https://help.ubuntu.com/community/Installation/iso2usb/isoboot")

I looked at both methods and they use the same basic tools as I use in creating my persistent LiveUSB.  Plus, my method works in all my laptops with all versions of Ubuntu including 20.10.  The only problem I am having is booting my persistent LiveUSB from a B450M based desktop.  Even with the B450M desktop, I was successful in booting from a Ubuntu 19.10 persistent LiveUSB.  Thus, this seems more likely a hardware-related problem (or more specifically a bug in the 5.8 kernel as it relates to the B450M mainboard)? 

BTW do you know anyone who has successfully booted from a B450M based desktop using a mksub-dus- or mksub-plug-generated persistent LiveUSB?

---

### Post by ping-wu on 2020-10-30
> **C.S.Cameron said:**
> If you want to bypass disk checks when booting see: [https://askubuntu.com/questions/1250119/how-to-skip-filesystem-checks-during-boot/1250141#1250141](https://askubuntu.com/questions/1250119/how-to-skip-filesystem-checks-during-boot/1250141#1250141)

If you make the Persistent USB using **mkusb** it will do the fix automatically.

I think that I recall that filling up a Persistent "writable" partition will cause kernel panic, confirm that your persistent partition is not full.

I already included fsck.mode=skip in the kernel parameter.  Sometimes I took it out to see more verbose.

---

### Post by sudodus on 2020-10-30
> **ping-wu said:**
> I looked at both methods and they use the same basic tools as I use in creating my persistent LiveUSB.  Plus, my method works in all my laptops with all versions of Ubuntu including 20.10.  The only problem I am having is booting my persistent LiveUSB from a B450M based desktop.  Even with the B450M desktop, I was successful in booting from a Ubuntu 19.10 persistent LiveUSB.  Thus, this seems more likely a hardware-related problem (or more specifically a bug in the 5.8 kernel as it relates to the B450M mainboard)? 

Yes, it seems likely a hardware-related problem.
> 
BTW do you know anyone who has successfully booted from a B450M based desktop using a mksub-dus- or mksub-plug-generated persistent LiveUSB?

Sorry, but I don't know anybody who uses a B450M based desktop. Let us hope someone with experience of that kind of computer can chip in and help you.

---

### Post by oldfred on 2020-10-30
Not sure what installer these users actually used.
Issues are common by chip, motherboard & vendor. 
So similar chip/motherboard, but different vendor may have similar issues.

Asrock B450 UEFI & Driver update to stop flickering.
[https://pcpartpicker.com/b/t4KBD3](https://pcpartpicker.com/b/t4KBD3)
Asrock B450M Steel Legend - turn UEFI Secure Boot off
[https://askubuntu.com/questions/1183093/ubuntu-corrupts-bios-on-ryzen-3000-machine](https://askubuntu.com/questions/1183093/ubuntu-corrupts-bios-on-ryzen-3000-machine)
Vega GPU is built into the CPU, then the M.2_2 socket cannot be used. 
[https://ubuntuforums.org/showthread.php?t=2424099&p=13877199#post13877199](https://ubuntuforums.org/showthread.php?t=2424099&p=13877199#post13877199)
Gigabyte B450 Ryzen needs kernel & mesa drivers
[https://ubuntuforums.org/showthread.php?t=2408247](https://ubuntuforums.org/showthread.php?t=2408247) & 
[https://ubuntuforums.org/showthread.php?t=2423649](https://ubuntuforums.org/showthread.php?t=2423649)

MSI B450 Tomahawk Max & MSI Nvidia GTX 1080 TI UEFI update & defaults
[https://ubuntuforums.org/showthread.php?t=2450961](https://ubuntuforums.org/showthread.php?t=2450961)

Asus B450-F Clock speeds
[https://ubuntuforums.org/showthread.php?t=2414502&p=13845363#post13845363](https://ubuntuforums.org/showthread.php?t=2414502&p=13845363#post13845363)

---

### Post by ping-wu on 2020-10-31
My Mainboard maker is ASRock.  I have tried all the options and to no avail.  

A new development.  I have created a casper-rw-labeled partition in the harddrive (SSD) of the B450M-based Ryzen computer (not on USB) and booted from a Ubuntu 20.10 iso image also stored in the same computer (thus, creating a sorta "persistent LiveUSB" without actually using a USB stick).   Booting was successful as if from a persistent USB.  The changes I made were also preserved.

---

### Post by sudodus on 2020-11-01
Congratulations to the solution, or should we say workaround :-)

This makes me think that the problem in this particular computer (with Asrock B450M) is caused by a timing problem or race condition, when booting persistent live from USB (for example that it tries a access [something in] the partition for persistence before it is mounted).

*Maybe* it would work with a faster USB drive (for example an SSD connected via USB or an 'extra fast' USB 3 pendrive), *maybe* the USB system itself is the problem.

I think it is worthwhile to try an installed system in USB. It might not suffer from the same timing problem or race condition. See what I suggested in [post #8](https://ubuntuforums.org/showthread.php?t=2452768&p=13996468#post13996468).

---

### Post by ping-wu on 2020-11-01
One of the USB sticks I tried was a SanDisk Extreme Pro which has a write speed of ~400MB/s; that should be fast enough. Also, I have previously installed Ubuntu 20.10 into another USB3 stick; it won't even go to the grub boot screen. EFI USB boot was not shown on the POST screen. (There was a USB boot option on the POST screen, but I think that was meant for dd-generated USB stick, it didn't work for either persistent LiveUSB or install USB). BTW, because of many considerations, I have zero interest in installed USB even if this were successful.

BTW, I tried a Ubuntu 20.04.1 daily built (b/f the official release came out) and was successful. Right now I am having problems only with the official versions of 20.04.1 and 20.10.(and only with B450M-based desktop machines.)  Ubuntu 20.10 persistent LiveUSB boots successfully with all my laptops (all three of them are Ryzen 5 and 7 based laptops,).

---


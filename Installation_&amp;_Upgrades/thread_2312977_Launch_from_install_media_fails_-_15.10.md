---
title: "Launch from install media fails - 15.10"
date: 2016-02-08
forum: Installation &amp; Upgrades
---

### Post by maraym on 2016-02-08
Hello - 

Looking to install 15.10 as dual boot with Windows 10 on a brand new Asus M32CD desktop

Prior to installing, I'm attempting to run the system from the install media

In all cases, the launch fails (after some varying amount of time) and I end up with a stream of (at least 2-3) error messages that I am unable to read because they are coming through too quickly.  Neither Ctrl-s, nor Ctrl-z are of any help in reading the messsages.

- I get the same (presumably) errors when launching from either a USB device or a DVD
- Same errors whether I boot via "General USB" or "UEFI General USB" (or "General DVD" or "UEFI General DVD") BIOS options
- The sha256 on the .iso used to create both the USB and DVD matches the sha256 on the release page
- the sha256 on the DVD matches the .iso

There are differences in how Ubuntu launches (directly, or selected from a grub menu) and how I get to view the messages (they just start streaming, or I have to Ctrl-Alt-F1) depending on whether I boot from "General USB" or "UEFI General USB" (or "General DVD" or "UEFI General DVD") 

But in all cases, we spend some amount of time launching, and end up with the same error messages

Anybody have any ideas on how to move forward?

Thanks!

Additional BIOS info:

AMI 2.17.1246

Changed the following settings:

- Launch CSM - reset from Auto to Enabled
- PK key - cleared
- Fast Boot - reset from Enabled to Disabled

After doing so, I can visually confirm the following:

- Secure Boot: Disabled
- Platform Key (PK): Disabled
- OS: Windows UEFI mode
- Fast Boot: Disabled

In all cases, I am booting via a Boot Override option (in BIOS), rather than reconfiguring my boot order

---

### Post by maraym on 2016-02-09
I've confirmed that setting the "nomodeset" kernel boot option does not solve this problem

Also confirmed that the Scroll Lock and Pause/Break buttons do not help in reading the error messages

---

### Post by grahammechanical on 2016-02-09
I cannot see any description of what you mean when you say "install media fails." The messages that you see are not necessarily error messages. They are mostly normal Linux system messages. There may be among them notification of some part of the system that failed to load. But most of the time the normal Linux system message are covered by a splash screen.

When you start to load the Ubuntu live session do you

1) get a purple screen with an icon of a human and an icon of a keyboard?
2) If you wait does the installer load to a point where you are at a kind of desktop that offers to Try Ubuntu or Install Ubuntu?
3) does the live session load but the failure comes after you click to install Ubuntu?

Regards.

---

### Post by maraym on 2016-02-09
Hi grahammechanical - thanks for the reply!

1) This happens if I use Boot Override option "General USB Flash Disk 1.0 (3824MB)"
2) This happens if I use Boot Override option "UEFI: General USB Flash Disk 1.0 (3824MB)"

I'll ignore the non-UEFI option fromm here forth, as I now understand that I must use the UEFI option in order to dual boot with Windows 10.  Nevertheless, I always end up with the same error stream

3) The process (for UEFI boot) is as follows:

- grub screen (2.02 beta 2-29)
- click "Try Ubuntu without installing
- black screen for 5 seconds
- splash screen for approximately 10 seconds (11 dot flashes)
- black screen - no further progress

At this point, if I type Ctrl-Alt-F1 (to get to a text terminal), I will see a stream of at least 2-3 repeating error messages

It occurred to me to try taking pictures of my screen.  All messages appear to begin with "XX printk messages dropped **" (where XX is a numeric count)

Some of the strings that I can pick out from these messages include:

pcieport 0000:00:1c.6: PCIe Bus error: severity=Corrected, type=Physical Layer, id=00e6 Receiver ID)
pcieport 0000:00:1c.6: [ 0] Receiver Error
device [8086:a116] error status/mask=00000001/00002000

---

### Post by oldfred on 2016-02-09
If nomodeset does not work, have you tried Intel boot parameters.
       Skylake needs this boot parameter:  i915.preliminary_hw_support=1
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support)
Xubuntu 14.04 - GRUB2 nomodeset brings wrong screen resolution - Acer TravelMate 4740 with Intel HD Graphics
[http://ubuntuforums.org/showthread.php?t=2240620](http://ubuntuforums.org/showthread.php?t=2240620)

---

### Post by maraym on 2016-02-10
Thanks, oldfred!  It is indeed a Skylake

I'll keep this as an expectation going forward, but as of now, neither nomodeset nor i915.preliminary_hw_support=1 (or both) seems to help with this problem

I should have listed this before, but this is what the system has

Intel Skylake i5-6400 2.7 GHz
8GB RAM DDR3L 1600
Toshiba DT01ACA100 1TB 7200rpm hard drive
Super Multi DVD Burner
Intel HD Graphics 530
Intel H110 chipset
Realtek 802.11ac Wi-Fi and Gigabit Ethernet and Bluetooth 4.0
HP 22cwa monitor

---

### Post by oldfred on 2016-02-10
Different model Asus needed UEFI/BIOS update
 ASUS G752 Can't see SSD NVMe Needed UEFI/BIOS update
[http://ubuntuforums.org/showthread.php?t=2307273](http://ubuntuforums.org/showthread.php?t=2307273)

Some Asus also need other boot parameters:

 ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)

---

### Post by maraym on 2016-02-10
Thanks again, oldfred!

I'll work through your links, but I'm leary of the words BIOS update after they bricked a bunch of other M32CD users a month ago 

But first, something else I just remembered

I'm using this system with an (also brand new) HP 22cwa monitor

When I first booted the system (to Windows 10) I got messages along the lines of "no input found", and then a black screen.

Apparently, the monitor ships with an install CD.  I tried booting again with that CD in the drive and I was fine (with Windows 10) from then on.

Would this also impact or need to be accommodated for with linux?

---

### Post by maraym on 2016-02-10
Woohoo!

The combination of 

i915.preliminary_hw_support=1
pci=nomsi

did the trick

---

### Post by maraym on 2016-02-10
Hopefully this will save some time for other M32CD users.  

This is what I had to do to trial Ubuntu 15.10 from a Live USB.  You must do (at least the first two of) these in order.  I will update this as necessary

Enable [Launch CSM]
    [https://www.asus.com/support/faq/1013017/](https://www.asus.com/support/faq/1013017/)

Disable [Secure Boot Control]
    [http://www.technorms.com/45538/disable-enable-secure-boot-asus-motherboard-uefi-bios-utility](http://www.technorms.com/45538/disable-enable-secure-boot-asus-motherboard-uefi-bios-utility)

Disable Fast Boot

Disable Fast Restart
    [http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html) from [http://ubuntuforums.org/showthread.php?t=2253168&p=13169524#post13169524](http://ubuntuforums.org/showthread.php?t=2253168&p=13169524#post13169524)

Type 'e' at the grub screen to set the following Kernel Boot Options
    pci=nomsi
    i915.preliminary_hw_support=1

**2016-10-21 edit**: the i915.preliminary_hw_support option is no longer needed as of Ubuntu 16.04, or any kernel >= 4.3.x.  See [https://wiki.archlinux.org/index.php/intel_graphics#Skylake_support](https://wiki.archlinux.org/index.php/intel_graphics#Skylake_support)

Select the "Try Ubuntu without installing" grub option


Huge thanks to oldfred for the help!

---

### Post by oldfred on 2016-02-10
Glad you found a combination of settings that worked, so far at least.
Keep us updated.

---

### Post by scblokhande on 2016-03-31
Thank you everyone involved for opening and solving this post. I had a hard time while installing ubuntu on my new Asus vivoPC M32CD. It kept failing for no apparent reasons. Took me 2 days to figure out the problem and find correct keywords to google. This post was a life saver.
For those who want to install Ubuntu-14.04 in Skylake systems, this solution works just fine. And if you are wondering where to put **pci=nomsi & i915.preliminary_hw_support=1** during a fresh install, I had made a bootable Ubuntu pendrive and edited this file in it: *{Bootable_USB_Drive}/boot/grub/grub.cfg* 
Unedited file looks like this:
[I]menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash ---
    initrd    /casper/initrd.lz
}[/I]

Replace with these lines:
[I]menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed pci=nomsi i915.preliminary_hw_support=1 boot=casper only-ubiquity quiet splash ---
    initrd    /casper/initrd.lz
}
[/I]Hope this will save time for someone

---

### Post by ehsan11 on 2016-05-05
I had the same problem with **Dell Inc. XPS 8900/0XJ8C4, BIOS 2.1.3 01/20/2016** and  **pci=nomsi & i915.preliminary_hw_support=1 **combination solved it for me too.

---


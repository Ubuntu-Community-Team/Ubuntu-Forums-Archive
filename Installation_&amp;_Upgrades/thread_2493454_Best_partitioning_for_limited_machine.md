---
title: "Best partitioning for limited machine"
date: 2023-12-15
forum: Installation &amp; Upgrades
---

### Post by someguy99 on 2023-12-15
I have a little, nearly ChomeOS-like machine, an IdeaPad Flex 3, which is Celeron based and has only 58GB of mmc memory.
It actually is surprisingly serviceable, and is running Windows 10, but I wish to install some variant of Ubuntu alongside.
My question is one of partitioning, specifically, since it DOES have a slot for a microSD card, what should I place on the (faster) built-in memory?
I'm thinking perhaps I should put /boot there as well as /swap at the end, while putting / on the 128GB SD card (which already has Windows user files in an NTFS part), which would include /home. Just want to minimize usage of the limited built-in memory, but use it where best for speed (e.g. swap)
Does that make sense?
I'm using UEFI, and already have grub installed, so perhaps /boot can just be on the SD card under root (?). I am using GPT, if that's relevant.
Also interested in any suggestions for making best use of the touchscreen,  perhaps a specific desktop.

Thanks a lot!

---

### Post by SeijiSensei on 2023-12-15
I'd put the root of the Linux filesystem on the internal memory device and add an ext4 partition to the microSD card that you can mount as /home.

---

### Post by someguy99 on 2023-12-15
ahh, so you think pretty much the entire filesystem (other than /home) should run on the faster memory, then. I was tying to minimize that area's usage,, but perhaps you're right.
Thanks!
Oh, for clarification of my original post, when I referred to "58 gigs of memory", that's the built-in storage (like an on board SSD, I guess) The actual working memory/RAM is 4 gigs on this machine.Just in case anybody was confused ("58 gigs--wow!!)

---

### Post by TheFu on 2023-12-15
I though you had a limited file system.  32G+ isn't limited.  Just do a standard install. Choose a light DE version.

I ran Lbuntu on a 2012 Chromebook with 2GB of RAM and 16GB total storage.  Ubuntu has drastically bloated since 2012, but even 35G is huge for a normal install. No worries.  Just don't use Gnome and everything should be fine.

The MicroSD should only hold things that don't change - basically read-only stuff like videos and music.  Not documents that you are editing all the time.
Also, as with all laptops, you'll need to have encryption AND excellent backups.  That should go without saying.

I'd wipe the NTFS parts.  You don't need it. Transfer files to other systems using a USB sneaker*net or over regular networking.

Since 2015, using GPT should be the default and expected with Linux.  Linux doesn't tie the boot method (UEFI/Legacy) with the partition table type in an arbitrary way like that other company does. Always use GPT.

---

### Post by someguy99 on 2023-12-15
Well, I AM still dual-booting Windows...

---

### Post by oldfred on 2023-12-15
If you really want a faster system, consider an external SSD.
I found an external SSD with Kubuntu which is more of a mid-weight flavor worked well with both an old 2006 BIOS only system and a new Dell with 11th gen Intel chip. 
On old laptop, I booted from grub on its own HDD. While not speedy, very functional. 
With newer system I used UEFI boot. SSD was gpt and had UEFI configuration. External SSD was almost as fast as iwhen it was my internal drive on desktop.
USB SSD to USB3 enclosure for m.2 SSD and not really that expensive now considering how good it worked.

---

### Post by TheFu on 2023-12-15
> **oldfred said:**
> If you really want a faster system, consider an external SSD.

Saw a Samsung T7 2TB SSD with USB 3.2 connector (very fast and reputable) for $90 today.  Let me see of I can find that deal again.
[https://slickdeals.net/f/17168368-samsung-edu-epp-2tb-samsung-portable-t7-touch-usb-c-3-2-external-ssd-89-99-free-shipping](https://slickdeals.net/f/17168368-samsung-edu-epp-2tb-samsung-portable-t7-touch-usb-c-3-2-external-ssd-89-99-free-shipping)
If you can stack a $25-off coupon and have a 5% cash back from your credit card, this deal becomes must greater. Obviously, YMMV depending on where you are in the world, your specific credit and cards, etc.

Many people will just load Ubuntu onto a USB3 Flash drive and keep it self-contained. That's fine for about a year, but flash storage does fail and I've gotten about 1 yr from named-brand flash storage when used in a similar fashion.  OTOH, a 120G-250G flash drive is usually $15-$30, so the price is right until you decide to wipe MS-Windows from the system.

---

### Post by tea for one on 2023-12-16
> **someguy99 said:**
> I have a little, nearly ChomeOS-like machine, an IdeaPad Flex 3, which is Celeron based and has only 58GB of mmc memory.
It actually is surprisingly serviceable, and is running Windows 10, but I wish to install some variant of Ubuntu alongside.
I have a similar Netbook (Lenovo Ideapad 11.6") and, a couple of years ago, I temporarily dual booted as an experiment.
Anyway, this was the partition info (Windows 10 S mode and Xubuntu):-
```
Model: MMC DA4064 (sd/mmc)
Disk /dev/mmcblk0: 62.5GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  274MB   273MB   fat32        EFI system partition          boot, esp
 2      274MB   290MB   16.8MB               Microsoft reserved partition  msftres
 3      290MB   39.6GB  39.3GB  ntfs         Basic data partition          msftdata
 5      39.6GB  61.5GB  21.9GB  ext4
 4      61.5GB  62.5GB  1049MB  ntfs         Basic data partition          hidden, diag
```

---

### Post by SeijiSensei on 2023-12-16
> **someguy99 said:**
> ahh, so you think pretty much the entire filesystem (other than /home) should run on the faster memory, then. I was tying to minimize that area's usage,, but perhaps you're right.
Why? Are you worried you'll "wear out" the internal memory?

I want executables and libraries to load as fast as possible, so I'd keep the root filesystem on the memory device.

---

### Post by someguy99 on 2023-12-16
Well, again, since I'm running this alongside WIndows I'm just trying to preserve the internal space since it's a bit limited.
I think you and others make sense in that the bulk of Ubuntu (or whichever) should reside on that internal space for speed's sake, so I will stick the root there, but put my /home onto the SD. Similarly, for Windows, I use the SD for docs/downloads/images/videos. Guess I'm using the built-in SD (reader) in lieu of a USB stick, which was suggested above, although for me with more of a hybrid approach.  I think I'll pass on an external SSD since I want maximum portability (although salvaging an old m2 128 gb one from an old, broken laptop and putting it into one of those tiny external cases is a future possibility...)

Listen, thank ALL of you for the valuable input and perspectives--I appreciate it!

---

### Post by oldfred on 2023-12-16
I upgraded M.2 SSD to M.2 NVMe and put SSD into adapter.
Fideco M.2 to USB3.1
[https://www.amazon.com/FIDECO-External-Enclosure-Adapter-Transfer/dp/B07XCWG15C?th=1](https://www.amazon.com/FIDECO-External-Enclosure-Adapter-Transfer/dp/B07XCWG15C?th=1)

Now almost all the M.2 to USB3 adapters are NVMe or both SATA & NVMe. Not sure you get any extra speed with NVMe to USB3 unless you nave a newer USB-C port.
I purchased a larger NVMe drive to put into another desktop and used this adapter for older smaller NVMe drive.
ORICO M.2 NVMe SSD Enclosure, USB 3.1 Gen 2 (10 Gbps) to NVMe PCI-E M.2 SSD Case Support UASP for NVMe SSD Size 2230/2242/2260/2280(up to 4TB)-M2PV 

So much pleased with speed of external SSD, I do not plan on buying any more USB flash drives. But I have many flash drives to use, anyway.
Adapters are $20 to $30 plus price of drive, if you need a new larger drive.

---


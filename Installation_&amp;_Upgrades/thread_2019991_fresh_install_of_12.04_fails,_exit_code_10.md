---
title: "fresh install of 12.04 fails, exit code 10"
date: 2012-07-07
forum: Installation &amp; Upgrades
---

### Post by jody858 on 2012-07-07
I'm attempting a fresh install of Ubuntu 12.04 on an older PC. It had Windows XP on it. I made a bootable USB drive using LiLi and the ISO I downloaded from this website. I tested the USB install at work on a Lenovo x301 and Ubuntu installed fine, so I don't think it's my USB drive. This is an older custom built PC with a VIA motherboard. I have the onboard RAID disabled in the BIOS so that should not be coming into play. It has a single 40GB WD drive attacted on IDE1.

The install fails just after I finish filling out the who are you screen. The error states, "The installer encountered an unrecoverable error." I take it to the live desktop and attempt to reinstall using the icon that is on the screen. That's when I get, "ubi-partman failed with exit code 10," again after the who are you screen.

I tried using F6 and choosing a few different options like nodmraid and nomodeset but my results are the same. I've searched this site and Google but I can't find much information what this error means in my situation. The formatting looks to be ext4, which doesn't mean much to me, but I did see several other formatting options under advanced. I'm primarily a Windows guy, so FAT32 and NTFS are the only formatting terms that mean something to me. Any advice on what to try next would be much appreciated.

---

### Post by Paddy Landau on 2012-07-08
I am suspecting you are using a low-specification PC.

Try using [Lubuntu]("http://lubuntu.net/") instead; it is tailored for low-spec computers and may help.

---

### Post by efflandt on 2012-07-08
You should be able to get more information from syslog, but not sure if you can get there from file view, although, you should be able to with Log Viewer or from a terminal with **less /var/log/syslog**

How much RAM do you have (part of which may be shared if video is integrated)?

Not sure if this could be related to an issue I had, but I have install iso on USB with persistent data.  I used that to install to a USB drive, and once that worked fine, I replaced 10.10 on my desktop hard drive with 12.04 (I have 11.10 on SSD).

But trying to install 12.04 in place of 10.04 on my laptop kept aborting trying to copy settings and files when I never even saw a screen asking if I wanted to do that. Apparently it was trying and failing to NTFS mount sda3 which is a swap partition (it was a Win7 partition on my desktop).  So I redid the iso on USB with Startup Disk Creator, and install is running much longer to the point of installing packages, so I expect it will complete (will edit this if it doesn't).

PS: The redone USB and regular install CD hung forever with no errors at about 90% of "Installing system". So now I am trying 64-bit 12.04 alternate CD (text based install).

---

### Post by jody858 on 2012-07-09
> **Paddy Landau said:**
> I am suspecting you are using a low-specification PC.

Try using [Lubuntu]("http://lubuntu.net/") instead; it is tailored for low-spec computers and may help.

It's an Athalon XP 2100 CPU, 512MB RAM, Ti4600 GPU (128MB?)...so yeah pretty slow by today's standards. It's my mom's PC that I'm trying to freshen up so she doesn't have to buy a new one. It's built from a bunch of my old parts as I upgraded through the years.

In the meantime to get it up and running I reloaded XP on it. It's funny it seems to run good on it's first boot, but once you start applying updates the slowness creeps back in.

I'm downloading lubuntu right now. I'll check it out, thanks.

---

### Post by jody858 on 2012-07-09
> **efflandt said:**
> You should be able to get more information from syslog, but not sure if you can get there from file view, although, you should be able to with Log Viewer or from a terminal with **less /var/log/syslog**

How much RAM do you have (part of which may be shared if video is integrated)?

Not sure if this could be related to an issue I had, but I have install iso on USB with persistent data.  I used that to install to a USB drive, and once that worked fine, I replaced 10.10 on my desktop hard drive with 12.04 (I have 11.10 on SSD).

But trying to install 12.04 in place of 10.04 on my laptop kept aborting trying to copy settings and files when I never even saw a screen asking if I wanted to do that. Apparently it was trying and failing to NTFS mount sda3 which is a swap partition (it was a Win7 partition on my desktop).  So I redid the iso on USB with Startup Disk Creator, and install is running much longer to the point of installing packages, so I expect it will complete (will edit this if it doesn't).

It has 512 MB of RAM and a 128 MB AGP card. Compared to my current machine it's dismal, but I figured it would be enough for ubuntu, maybe not. I went ahead and burned a CD instead of using the USB drive, but the results were the same. I was able to get to the syslog, but I couldn't make heads or tails of it with regards to why the install fails.

---

### Post by Paddy Landau on 2012-07-09
> **jody858 said:**
> 512 MB of RAM...
Too little for Ubuntu, but should be fine for Lubuntu.

If Lubuntu is still too slow, you can try an even lighter distro such as [Bodhi]("http://www.bodhilinux.com/"), which is Ubuntu-based but not part of the Ubuntu family.

---

### Post by acidophilus on 2012-12-26
Howdy, thanks for your tips. I tried installing Ubuntu and Kubuntu 12.10 on an old Asus Z9200 laptop with an AMD turion 64 mobile processor and 512 mb ram. The installer kept crashing with partman exitcode 10, even after trying several tips found on this forum. I finally nailed it by "erasing" my harddisk with an eraser tool and then unplugging the network cable (I think this is the crux of the biscuit) before running the installer. After the installer finished, i plugged the network cable back in and installed all updates. My laptop has been running smoothly ever since.

---

### Post by Paddy Landau on 2012-12-27
> **acidophilus said:**
> My laptop has been running smoothly ever since.
On just 512Mb RAM? That's good. What did you install: Ubuntu, Kubuntu, …?

---


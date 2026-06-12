---
title: "noob getting hands dirty w/ubuntu..."
date: 2005-03-06
forum: Installation &amp; Upgrades
---

### Post by MojoJojo on 2005-03-06
Hello.

I'll start by stating I'm a general noob when it comes to linux (except my smoothwall), and am having issues w/installing ubuntu via VMware.

**What I have:**

-VMware ver. 4.0.5 running Virtual Win98, win2K and WinNT on: 

* AMD Athlon Thunderbird 1.1 GHz 
* Gigabyte 7ZX-F Mobo w/VIA KT133 Chipset 
* 1.25GB PC133 SDRAM (512x2, 256x1) 
* Radeon 7000 64MB DDR Vid Card (Catalyst drivers, DirectX 9) 
* Maxtor 60GB 7200 RPM HDD w/2MB cache (Pri Master) 
* ASUS 52x24x52 CD/R-RW (Sec Master) 
* Generic 52X CD ROM(Sec Slave) 
* WinXP Pro SP2
* Linksys NC100 10/100 NIC 
* Powmax 400 Watt Power Supply 
* GoldStar 17" Monitor 
* Enlight ATX Case 
( Rounded IDE 80 conductor cables (X2) for Primary/Secondary 
Drives.)

**The issue: ** 

After burning the ISO install file (using Nero), I deleted the Virtual winNT machine and its' corresponding folders and created a new Virtual Machine for Ubuntu with 256MB RAM, 6GB HDD and setting the burner as the primary CD drive.  Everything seems to go OK on the install **UNTIL:** I get an error during the base installation stating: **"The debootstrap program exited with an error (return value 1).  Check var/log/messages or see virtual console 3 for the details".**

**What I've done:**

-re-downloaded/burned the iso image (x4, on different brands/types of media and from all three US mirrors I've found off of the site)
-verified md5 (x6)
-burned image at a slower speed (10x, 8x)
-re-created the Virtual machine w/varying configurations (including letting the virtual disk grow, and setting a pre-configured size)
-attempted a manual partitioning of the virtual HDD for the install
-attempted install straight from the ISO image itself on the HDD
-downloaded/burned live cd (returns with a memory error of some kind on boot and the ubuntu splash screen appears and hangs there)
-tried above live cd straight from the image on the HDD (same error and splash screen hang).
-tried booting install disk from another CD drive (bootstrap error again)
-searched these forums and found a few threads relating to the issue and tried all suggestions: all failed
-googled the error, leading to a few boards w/the same issue and resolutions
-I'm about to ghost one of my other machines' drives and attempt an install on it directly to see if it's the computer or the media.  I'm at a loss.

I appreciate any help in correcting this issue.

Thanks so much for your time.

MjJj

---

### Post by Juergen on 2005-03-07
> Check var/log/messages or see virtual console 3 for the details.
Did you do that? 
You can switch to console 3 with <ALT>+<F3>

---

### Post by MojoJojo on 2005-03-08
Thanks for the reply...

Here's what the messages say...

NOTE: I installed ubuntu successfully on my old Win2k server machine (ghosted it and wiped it out).  It's fantastic.

I still would like to set this up in a virtual machine, though.

Thanks for the help.

MjJj

---


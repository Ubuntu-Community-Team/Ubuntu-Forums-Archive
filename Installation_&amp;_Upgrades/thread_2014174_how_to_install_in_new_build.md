---
title: "how to install in new build"
date: 2012-07-01
forum: Installation &amp; Upgrades
---

### Post by builderbob62 on 2012-07-01
I want to try ubuntu instead of windows and want to know do i follow the basic install instructions

---

### Post by oldfred on 2012-07-01
With a new build you need to know if the motherboard is UEFI or BIOS. UEFI also has a BIOS mode. Many new systems are now UEFI.

Both Windows and Ubuntu will boot in UEFI or BIOS mode from USB or liveCD, but then your install is in that mode.

If you will never install Windows or boot in UEFI mode you then partition hard drive in gpt(GUID) not MBR(msdos).

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)
[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)

Whatever way you install, it is best to partition in advance, but you do need to know which way you will install. Most of the users in the forum are familar with the BIOS/MBR way  as that is how computers have booted since the first hard drive on a PC in the '80s.

But a few have posted success with the new UEFI install, both just Ubuntu or dual boot with Windows.

---

### Post by black veils on 2012-07-01
what is the ram, processor speed and hard drive size/arrangement?


1.  download ubuntu [here]("http://www.ubuntu.com/download/desktop")  (the top one)

2.  get your .iso image [md5sum]("https://help.ubuntu.com/community/UbuntuHashes")

3.  Verify .iso integrity:
Scroll down to **MD5SUM with "Checksums calculator"** [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

4.  put .iso image to [usb flash drive]("http://unetbootin.sourceforge.net/")  or [cd/dvd]("http://infrarecorder.org/?page_id=5") (burn as image, and use slowest burning speed)

5.  [install ubuntu]("http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml")

---

### Post by builderbob62 on 2012-07-02
> **black veils said:**
> what is the ram, processor speed and hard drive size/arrangement?


1.  download ubuntu [here]("http://www.ubuntu.com/download/desktop")  (the top one)

2.  get your .iso image [md5sum]("https://help.ubuntu.com/community/UbuntuHashes")

3.  Verify .iso integrity:
Scroll down to **MD5SUM with "Checksums calculator"** [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

4.  put .iso image to [usb flash drive]("http://unetbootin.sourceforge.net/")  or [cd/dvd]("http://infrarecorder.org/?page_id=5") (burn as image, and use slowest burning speed)

5.  [install ubuntu]("http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml")
BIOSTAR A55MH FM1 AMD A55 (Hudson D2) HDMI Micro ATX AMD Motherboard

AMD A4-3300 Llano 2.5GHz Socket FM1 65W Dual-Core Desktop APU (CPU + GPU) with DirectX 11 Graphic AMD Radeon HD 6410D AD3300OJHXBOX

G.SKILL Ripjaws Series 4GB 240-Pin DDR3 SDRAM DDR3 1333 (PC3 10666) Desktop Memory Model F3-10666CL9S-4GBRL

i have already burned the cd iso file and waiting on my DVD-RW to show up before i start.  i looked at the spec of the mother board and it said nothing about the UEFI so i assume it is the ms-dos(MBR) boot.  Do I just put this disk in I burned and then start-up the PC..

---

### Post by Cheesehead on 2012-07-02
> **builderbob62 said:**
> Do I just put this disk in I burned and then start-up the PC..

Yes. That's about it.

---

### Post by mrag on 2012-07-03
Not to sidetrack this thread, but it matched my search on 'install new  hard drive' and may help those that follow. I bought a used 80 GB HDD on  Ebay and the goal is to strictly run/test/explore Ubuntu (12.04)-no  dual boot stuff. It will go into a 2007 Dell AMD 2GB desktop.

The used HDD is NTSF and now has about 7 GB of an old Windows OS and program files on it. It appears it came from an old Dell. Any need to format and how-assume this would be done during install.

I did the checksums and just plan to take out the current HDD drive, put  this used HDD in, put in the newly burned Ubuntu cd and follow the  Ubuntu install instructions.

Just want to confirm that this would be the same instructions as already supplied in this thread. Thank you.

---

### Post by oldfred on 2012-07-03
The install screen has several choices. 

One is to totally erase drive and create a default install of / (root) & swap. Another is just to find and use unallocated space.  I recently tried that just to see what it would do. I had 40GB not used on my sdc drive and it just went out and installed to that space. I already had swap & it reused that.

The final choice is more detailed. It lets you (now) create partitions, choose which partition is / , and swap. You then can create a separate /home. For server installs or other special cases you can create all the other system folders as separate partitions, but that is not normally required and most server installs use the alternative or server versions to install.

---

### Post by mrag on 2012-07-04
I put 12.04 on cd. Got to very end of installation three times (duh?) and it reported 'installation failure.' I then burned 11.10 (Oneiric Ocelot) to cd and that install went well. Now it is asking me if I want to 'upgrade' to 12.04! I think I'll pass for now, thank you.

Once I remembered to fix the bios to boot first to cd, things could not have been easier on install. Put in a name, a password, pick your keyboard and then do I want to use my whole used HDD? That's all I was asked and a half hour later I was on Firefox using Yahoo email. Thanks for the help. Apologies for interrupting original thread.

---


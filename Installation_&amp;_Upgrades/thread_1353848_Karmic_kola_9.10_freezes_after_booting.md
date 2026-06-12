---
title: "Karmic kola 9.10 freezes after booting"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by techfolkcmr on 2009-12-13
Hello all,
                First of all I thank you for sparing a minute on my problem. I have been used to Windows and due to overwhelming response of Linux I love to learn and hence I decided to install Linux. As per my friends suggestion I installed Linux Mint 7.0 as am new to Linux and worked a couple of months on it with no problem. And after that Ubuntu Karmic Kola is released and I downloaded and installed that. Installation went off without any problem but the thing is after Login Karmic kola freezes. Even if I just move my mouse it gets hanged. I don’t know what might be the problem and hence I formatted Ubuntu and installed Linux Mint 8.0. 
                  The sad thing is it too behaves as Ubuntu Karmic Kola 9.10 but I don’t have any problems with Linux Mint 7.0. What might be the problem and I have added some more details for your help. Please Guys I want to work in Karmic Kola.
  RAM : 2 GB
  HARD Disk : 80 GB (Of Which Partitioned C: (15 GB Installed Windows 7) D: (20 GB Splitted  to two 10 GB’s and installed Karmic Kola on One 10 GB drive) E & F Drive of 20 GB each.
  Processor :          Intel(R) Pentium(R) Dual  CPU  E2140  @ 1.60GHz, 1600 Mhz, 2 Core(s), 2 Logical Processor(s)
  System Type:     X86-based PC
  PS:  I haven’t given any swap space during installation as I thought my RAM is more than sufficient. If u need more details please reply. Thanks in advance.

---

### Post by phillw on 2009-12-13
Hi and welcome,

Firstly > PS: I haven’t given any swap space during installation as I thought my RAM is more than sufficient. If u need more details please reply. Thanks in advance.

*nix's (Mint, Ubuntu et all) get a bit stressed out if there is not a swap area. 1 swap area of, in your case, 2GB, can be shared by ALL your linux installs - you just point them to it & they'll be happy bunnies. I'd certainly suggest that as a 1st step.

Regards,

Phill.

---

### Post by techfolkcmr on 2009-12-13
Thanks a lot for replying

But I didnt given the swap space for Linux Mint 7.0 or Linux JBOSS too but they worked fine . Meantime I'll give you the details what I get on pressing 'e' in the boot screen.

record fail = 1
if [-n ${have_gurbenv}]; then save_env recordfail; fi
set quiet = 1
insmod ext2
setroot =(hd0,5)
search --no floppy --fs --uuid -- set b8dfod3a -23ad-4a31-9494-402bb8095\4e7
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=b8df0d3a-23ad-4a37-9\494-402bb80954e7r0
quiet splash
initrd /boot/initrd.img-2.6.31.14-generic

I'll try this and reply and is that 2 GB Swap Space is enough or more is needed.

---

### Post by phillw on 2009-12-13
The community document on Grub2 - covering errors, getting it to rescue mode, reconfiguring etc. etc. is covered here -->  [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Hope that is of help.

regards,

Phill.

---


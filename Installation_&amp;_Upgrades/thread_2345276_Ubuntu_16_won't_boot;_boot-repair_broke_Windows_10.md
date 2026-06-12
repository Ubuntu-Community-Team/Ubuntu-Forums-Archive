---
title: "Ubuntu 16 won't boot; boot-repair broke Windows 10"
date: 2016-12-02
forum: Installation &amp; Upgrades
---

### Post by kaanta on 2016-12-02
I've been dual booting Ubuntu 16.04 and Windows 10 on my XPS15 9550 for a few months and it worked great until a few days ago. I shutdown from Ubuntu and the next time I powered up, Windows 10 booted when normally GRUB should come up. Didn't think much of it since I needed Windows anyway but when I tried booting into Ubuntu from the Boot Menu, Dell SupportAssist came up, did some check, and said there was an error. Tried again, same result. Windows 10 still worked at this point. I used a live USB to run boot-repair using the recommended settings and after that completed, neither Ubuntu nor Windows will boot. Live USB still works. I ran an extended hardware test and all the hardware is in working order.
Boot repair info: [http://paste2.org/j54zEMPv](http://paste2.org/j54zEMPv)

So far I've tried:
     Creating new boot options for both. Ubuntu as \EFI\ubuntu\shimx64.efi and Windows as \EFI\Microsoft\Boot\mgfw.efi
     
     Changing SATA to AHCI from RAID but my dual boot setup worked under RAID the entire time. Hard drive is detected in BIOS, status is "non-raid" and controller type is "AHCI"

     I tried enabling Legacy Option ROMs since some mentioned it in other forums but that didn't change anything (expected since both OS are UEFI) Secure boot has always been an still is off.

I've searched online for days and can't seem to nail down the issue. It's software related but I'm not advanced enough in linux to come up with my own solution :(

Some additional info: I can access the files on both my Ubuntu and Windows partitions when in the live USB. Computer has a 1TB HDD where everything is located and also a 30GB m.2 SSD that acts as a cache on Windows. GParted shows the SSD as /dev/sda and the HDD as /dev/sdb so I had a thought that boot repair might have used the wrong drive when repairing. The log also shows a bunch of RAID related things but again, I have no past experience with this stuff. And this most likely is completely unrelated, but my processor info on BIOS used to list the i5-6300HQ maximum clock speed as 3.2GHz (turbo boost) but it's now 2.3GHz. Not sure when this changed. BIOS version is 1.2.14 btw.

I'm at the very end of my semester and I really need my computer the next couple weeks for finals so I really hope there a savior out there.

---

### Post by oldfred on 2016-12-02
I do not understand the RAID and whether it needs to be off or not.

But UEFI grub only installs to drive seen as sda. If sda not seen, it will not update into the ESP on any other drive. 

I also have seen that Dell's seem to need to have Legacy on, but still boot in UEFI mode. Almost all systems need to have Legacy/BIOS/CSM off. 

Your UEFI boot entries are:
sudo efibootmgr -v

And it uses GUID, so you need to check that GUID (not UUID) matches UEFI boot entries.
       to see GUID/partUUID for each device, post with code tags to preserve formatting:
lsblk -o +PARTUUID /dev/sda

---

### Post by kaanta on 2016-12-02
Appreciate the quick response oldfred,
I switched to legacy and booted the UEFI Ubuntu entry and same thing happened. Didn't have enough time to look into the second half of your suggestion so I'll update in a little bit.

---

### Post by kaanta on 2016-12-02
Here's the print out of those commands:

```
ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0006
Timeout: 0 seconds
BootOrder: 0002,0000,0001,0003,0004,0006,0009,000A,000D,000E
Boot0000  Windows Boot Manager    HD(1,GPT,baf0efd5-9732-4df9-9dc2-b8402249a046,0x800,0x3b99fdf)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* USB    PciRoot(0x0)/Pci(0x14,0x0)/USB(16,0)/HD(1,GPT,17b31b70-be96-4976-b746-1ef5a87af4d7,0x800,0x3b99fdf)
Boot0002* ubuntu    HD(1,GPT,baf0efd5-9732-4df9-9dc2-b8402249a046,0x800,0xfa000)/File(\EFI\ubuntu\shimx64.efi)
Boot0003* UEFI: HGST HTS541010A7E630, Partition 1    HD(1,GPT,baf0efd5-9732-4df9-9dc2-b8402249a046,0x800,0xfa000)/File(EFI\Microsoft\Boot\bootmgfw.efi)..BO
Boot0004  Ubuntu2    PciRoot(0x0)/Pci(0x17,0x0)/Sata(2,32768,1)/HD(1,GPT,baf0efd5-9732-4df9-9dc2-b8402249a046,0x800,0xfa000)/File(\EFI\ubuntu\shimx64.efi)
Boot0006* UEFI: Samsung Flash Drive 1100, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(17,0)/HD(1,MBR,0x4294967236,0x800,0x3bbf800)..BO
Boot0009* Diskette Drive    BBS(Floppy,Diskette Drive,0x0)..BO
Boot000A* Internal HDD    BBS(HD,Internal HDD,0x0)..BO
Boot000D* CD/DVD/CD-RW Drive    BBS(CDROM,CD/DVD/CD-RW Drive,0x0)..BO
Boot000E* USB Storage Device    BBS(USB,Samsung Flash Drive 1100,0x0)..BO

ubuntu@ubuntu:~$ lsblk -o +PARTUUID /dev/sda
NAME MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT PARTUUID
sda    8:0    0 29.8G  0 disk            

ubuntu@ubuntu:~$ lsblk -o +PARTUUID /dev/sdb
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT PARTUUID
sdb      8:16   0 931.5G  0 disk            
&#9500;&#9472;sdb1   8:17   0   500M  0 part            baf0efd5-9732-4df9-9dc2-b8402249a046
&#9500;&#9472;sdb2   8:18   0   128M  0 part            fb4da4ef-9c7d-423f-a7d0-6760baa9b334
&#9500;&#9472;sdb3   8:19   0 849.2G  0 part            7f70b988-032b-4b09-9c57-100e0aed71f8
&#9500;&#9472;sdb4   8:20   0   450M  0 part            676a0f51-32e3-473f-acca-ac73b807768f
&#9500;&#9472;sdb5   8:21   0  11.3G  0 part            debbdb3f-b308-433e-a300-c18c092a39c1
&#9500;&#9472;sdb6   8:22   0     4G  0 part            7a7ee397-f7ff-4d39-986f-5482e0a5ccd0
&#9500;&#9472;sdb7   8:23   0    25G  0 part            cdf90e06-bccf-42f0-aa20-2216cec6343c
&#9492;&#9472;sdb8   8:24   0    41G  0 part            5747ed52-afb8-4d69-b868-bc7951b4060b

```

For the boot order, **Windows Boot Manager** and **UEFI: HGST HTS541010A7E630, Partition 1** both point to the same location and **ubuntu** and **Ubuntu2** both point to the same location. The extra's were created just to test if maybe the boot selection wasn't working. The samsung flash drive is what I'm booting live with right now. As you can see, the sda drive is the cache drive I was talking about. The GUID's you mentioned do in fact match up to the EFI parition. I attached the GParted view of both /dev/sda and /dev/sdb for reference.

---

### Post by oldfred on 2016-12-02
GUIDs match, but everything is saying sdb.
Is sda hidden as it is mirror of sda?

Is system set for RAID or AHCI?
I have seen conflicting info on whether Dell (and RAID systems) should be changed to AHCI, but most systems should be AHCI. Removing RAID in UEFI may then break whatever RAID you have.

       XPS 13 9350 Windows reinstall & discussion of RAID vs. AHCI
[https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/](https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241)

---


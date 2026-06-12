---
title: "Unable to get a new SSD to boot"
date: 2016-11-05
forum: Installation &amp; Upgrades
---

### Post by mayoko1852 on 2016-11-05
Hello I'm hoping someone out there can help me with an issue. I bought a new SSD for my OS drive and at first used clonezilla to clone the old drive to the new one but the new drive wouldn't boot. I then tried to repair grub with boot-repair from the live disk it acted like it worked but still wont boot.

I thought maybe it has something to do with my old install somehow, so I wiped the new SSD and did a fresh install of ubuntu server. Still no OS found error. Did a second attempt with boot repair and it still doesn't boot. Here is the log output from the 2nd boot repair attempt: [http://pastebin.com/nK6HEtnE](http://pastebin.com/nK6HEtnE) That is with just the new SSD and the Live USB stick connected to the computer.

So somehow Im really missing something or I might need to RMA this new drive :(

Other things not sure if theyre important: 
*drive is plugged into the first sata port
*the old SSD still boots and works fine
*Data can be written to and read from this new drive just fine (just wont boot)

I appreciate any help

---

### Post by FerryGnu on 2016-11-05
I suspect the issue is with Clonezilla. Yesterday I tried to clone a drive and it would not boot. I reluctantly used a wndows laptop and Macrium Reflect to clone it and it worked fine. I have used Clonezilla in the past with great results, but that was about a year back so not sure what version of CZ that was. I no longer have the LiveCD of it, but remember clearly that the cloning worked fine then.

---

### Post by oldfred on 2016-11-05
What brand/model system? Or what motherboard?

In one place in script it does not show bootfiles (at top) but later it says they are there?
Same with kernel. Not found in one place, and listed in another.

If you totally cloned drive, you cannot have both drives plugges in as you would have duplicate UUIDs.
Not sure but then duplicate GUIDs also, which would be an even bigger issue.

Post these:
sudo efibootmgr -v
       to see GUID/partUUID for each device, post with code tags to preserve formatting:
lsblk -o +PARTUUID /dev/sda
sudo blkid -c /dev/null -o list

---

### Post by mayoko1852 on 2016-11-05
> **oldfred said:**
> What brand/model system? Or what motherboard?

In one place in script it does not show bootfiles (at top) but later it says they are there?
Same with kernel. Not found in one place, and listed in another.

If you totally cloned drive, you cannot have both drives plugges in as you would have duplicate UUIDs.
Not sure but then duplicate GUIDs also, which would be an even bigger issue.

Post these:


Its a system I put together the motherboard is asus m5a97 r2

The Pastebin in my first post was after I did a fresh ubuntu server install. The Below is after I re-cloned from my old drive.

> **oldfred said:**
> sudo efibootmgr -v
```
BootCurrent: 0008
Timeout: 0 seconds
BootOrder: 0000,0008,0004,0007
Boot0000* ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0004*  Hard Drive      BBS(HD,,0x0)AMGOAMNO........o.C.r.u.c.i.a.l._.C.T.7.5.0.M.X.3.0.0.S.S.D.1....................A...........................>..Gd-.;.A..MQ..L.  . . . . . . .  .6.1.4.1.2.1.9.5.2.2.4.5......AMBOAMNOs.......Q.S.a.n.D.i.s.k....................A.......................$..Gd-.;.A..MQ..L.S.a.n.D.i.s.k......AMBO
Boot0007*  Network Card     BBS(Network,,0x0)AMGOAMNO........q.I.B.A. .G.E.  .S.l.o.t. .0.5.0.0.  .v.1.3.2.1.........................rN.D+..,.\...........B..Gd-.;.A..MQ..L.I.B.A.  .G.E. .S.l.o.t. .0.5.0.0. .v.1.3.2.1......AMBO
Boot0008* UEFI: SanDisk    PciRoot(0x0)/Pci(0x16,0x0)/USB(1,0)/HD(1,MBR,0x40,0x800,0x1dd1000)AMBO


```
> **oldfred said:**
> to see GUID/partUUID for each device, post with code tags to preserve formatting:
lsblk -o +PARTUUID /dev/sda
```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT PARTUUID
sda      8:0    0 698.7G  0 disk            
&#9500;&#9472;sda4   8:4    0 183.2G  0 part            b0472992-83d3-4d6e-8733-9ed006abf83f
&#9474; &#9500;&#9472;janeway--vg-swap_1
&#9474; &#9474; 252:1    0  15.9G  0 lvm             
&#9474; &#9492;&#9472;janeway--vg-root
&#9474;   252:0    0 167.1G  0 lvm             
&#9500;&#9472;sda2   8:2    0   244M  0 part            02ac25fd-84a3-4120-a8f2-41dd1339354c
&#9500;&#9472;sda5   8:5    0  39.7G  0 part            62424eb0-9fd2-4023-8873-f71f05f2c044
&#9500;&#9472;sda3   8:3    0  15.9G  0 part [SWAP]     b9fc05d3-e8cc-450c-a715-81d096d8a7d7
&#9492;&#9472;sda1   8:1    0   512M  0 part            84a22d71-6d40-43a7-a50f-64ab2d313310
```

```
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/loop0 squashfs         /rofs          
/dev/sda1  vfat             (not mounted)  F277-F142
/dev/sda2  ext2             (not mounted)  125087da-f822-443b-b101-e81486724a63
/dev/sda3  swap             [SWAP]         01bb4a90-c3aa-4500-8c83-75d2818efa36
/dev/sda4  LVM2_member      (in use)       fT4jrQ-BPJC-2Pgf-bMl5-uZ4y-2oeF-Y4YxAj
/dev/sda5  ext4             (not mounted)  d3f0a66a-01c0-4e81-b81e-97e952dc6871
/dev/mapper/janeway--vg-root
           ext4             (not mounted)  b4681276-3c54-4797-8925-41f3063e581d
/dev/mapper/janeway--vg-swap_1
           swap             (not mounted)  bda1b56f-b6a5-4203-b0d1-1eff9001dcb7
/dev/sdb1  vfat    MYLINUXLIVE /cdrom      407A-0194


```

Edit: here is the boot-repair report I did after the drive as cloned: [http://paste2.org/hsf4M4ma](http://paste2.org/hsf4M4ma)

Still says no boot device available :(

> **FerryGnu said:**
> I suspect the issue is with Clonezilla.  Yesterday I tried to clone a drive and it would not boot. I reluctantly  used a wndows laptop and Macrium Reflect to clone it and it worked fine.  I have used Clonezilla in the past with great results, but that was  about a year back so not sure what version of CZ that was. I no longer  have the LiveCD of it, but remember clearly that the cloning worked fine  then.

I tried Macrium Reflect with the same result  as clonezilla :(

---

### Post by oldfred on 2016-11-05
It looks like Boot-Repair did reinstall grub-efi-amd64 and now you have a new UEFI entry for ubuntu in UEFI. That was missing before.

But maybe now you are into AMD video issues?
If you press escape at UEFI/BIOS boot do you get grub menu?

---

### Post by mayoko1852 on 2016-11-05
I don't think its video issues, everything works fine on my USB drive with ubuntu on it and everything works fine with the drive I't replacing. Nothing wrong with the old drive, only replacing it because I wanted a bigger drive.

So far I've tried to install a fresh copy of ubuntu server and cloning from the old to new drive. I'm starting to think maybe I got a lemon, and need to send it back.

Thanks for your help though

---

### Post by kurt18947 on 2016-11-05
> **mayoko1852 said:**
> I don't think its video issues, everything works fine on my USB drive with ubuntu on it and everything works fine with the drive I't replacing. Nothing wrong with the old drive, only replacing it because I wanted a bigger drive.

So far I've tried to install a fresh copy of ubuntu server and cloning from the old to new drive. **I'm starting to think maybe I got a lemon, and need to send it back.**

Thanks for your help though

I'd be thinking along the same lines, I think. The only thing I might try would be to install Windows 8 or 10 to see if it installs. I'm no expert though. I can see where perhaps a cloning effort might get crossways but I'd think a fresh install should work.

---


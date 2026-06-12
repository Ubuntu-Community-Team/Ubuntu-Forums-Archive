---
title: "Triple Boot OSX, Window7,Mint-NVIDIA RAID0 - 2/3 successful"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by WhiteWidow on 2010-06-10
1st off Im am a linux semi noob. I know basics. I have successfully managed to dual boot Windows 7 and OSX. Windows 7 is on 2 WD raptors in RAID 0, OSX is on it own WD HD. Im using chameleon to boot them, that works fine. I wanted to add Ubuntu onto my RAID 0 which I have done by shrinking the windows volume and installing it on a 50gb partition. My issue is GRUB I believe. I want linux to show in chameleon but I needs to detect GRUB which I dont have configured properly. Im in mint now using a super grub disc, this is the only way I can boot it. From what I have read GRUB wont install on a RAID volume. So I tried following some tutorials but im lost. I thinbk I got it downloaded but Im stuck. Here is what I have so far:

```

control          nvidia_bhdjhebb1  nvidia_bhdjhebb5
nvidia_bhdjhebb  nvidia_bhdjhebb2  nvidia_bhdjhebb6

```

```

Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> 

```

Can anyone walk me through getting GRUB working at boot on a NVIDIA RAID0?

---

### Post by WhiteWidow on 2010-06-14
No one?

---


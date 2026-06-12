---
title: "Installing Ubuntu 10.10 over old Kubuntu (and dual-booting XP)"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by Kylotan on 2010-12-01
I have one disk which is currently partitioned as follows:

140 GB Ext3 -- with an old Kubuntu installation on it (7.04, I believe)
510 MB Swap
156 GB NTFS -- with my 32-bit Windows XP installation on it


I am looking to install Ubuntu 10.10 from a cd onto this drive, without disturbing the XP installation. I wish to completely overwrite the Kubuntu installation as there is no data there I wish to save.

I got to the advanced partition management part of the installation process on the installation cd, but it was a little *too* advanced for my liking. I wasn't exactly sure what the implications of everything was, in particular:

[LIST]
[*]Should I reformat the ext3 partition as ext4? I am not sure as to the pros and cons of either. I'm assuming mounting '/' there is fine.
[*]Is 510 MB of swap enough? I have 2GB of RAM and don't expect to use any memory intensive applications, nor use any hibernation functionality, etc.
[*]There is a dropdown list asking me about where to put the bootloader. I already have one which currently prompts me to choose between various Kubuntu kernels or Windows XP. I suspect this is located on "/dev/sda" (ie. the drive, presumably the MBR) as opposed to "/dev/sda1" (the ext3 partition) or "/dev/sda2" (the XP partition) but I am unsure where the current one is. The word 'GRUB' does appear about 380 bytes into my first physical disk however, which seems like the MBR if I'm remembering correctly. What should I choose here?
[*]Is there a need for me to explicitly mount my NTFS drive here, or is that something I can easily do later? (I gather NTFS support is pretty good these days?)
[/LIST]

---

### Post by gordintoronto on 2010-12-02
I still see complaints about ext4, so I have stuck with ext3. It's completely your choice.

If you don't run a lot of programs at the same time, the small swap file is probably OK.

I don't know about the bootloader location.

You don't have to sweat the NTFS drive at all. The "place," "computer" will show it as (some number) GB filesystem.

---

### Post by Kylotan on 2010-12-02
Thanks, I went with ext3 and installed the bootloader to sda and everything was fine. (Well, apart from it hanging at the end of installation, fatal errors with modprobe when I boot up, and the sound not working, that is ;) )

---

### Post by witeshark17 on 2010-12-02
@ [gordintoronto]("http://ubuntuforums.org/member.php?u=507940") Can you please add detail about the complaints about ext4?

---

### Post by gordintoronto on 2010-12-03
> **witeshark17 said:**
> @ [gordintoronto]("http://ubuntuforums.org/member.php?u=507940") Can you please add detail about the complaints about ext4?

Sorry, I have not kept track. 

EXT3 works for me, so I'm sticking with it.

---

### Post by witeshark17 on 2010-12-03
Thanks, from what I have read, ext4 should be fine in my case.

---


---
title: "Dual boot questions"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by Burnasty on 2009-12-02
I am attempting a dual boot.  I have searched the forums and haven't really seen the situation I am proposing.  The dual boot is Windows 7 on one hdd located on one sata port followed by ubuntu 9.10 on a separate hdd on an additional sata port.  My question is, when I install this way will grub locate the two os's and offer a choice or will one just boot?  Any help with making this simple and easy is much appreciated. 

Brian

---

### Post by impreziv on 2009-12-02
I just posted a thread about this exact situation. So far I cannot get the GRUB to boot my Windows 7. I can boot into Ubuntu when that drive is first in the boot order in the BIOS and vice versa for Windows 7. I have added Windows 7 to my menu.lst, but it wont boot when I select it in the bootloader. I'll keep my thread updated with my attempts and you can see if I manage to find anything that works.

---

### Post by oldfred on 2009-12-02
Grub2 is good about finding working Win operating systems on any drive. For some users the automatic entry has not been quite right but copy and minor edit fix it.

I like to keep at least one operating system on each drive and have that operating system in the MBR of that drive so if I make it first in BIOS it will boot. Often the normal install has  windows on the first drive and Ubuntu on the second but then to boot grub overwrites the windows boot in the first. That works but now we find a minor bug in grub2 that makes it 10-20 sec slower booting if grub is one one drive and Ubuntu is on the the second. Grub will set up windows from a second drive with mapping commands so it still thinks it is on the first drive without any issue.

Set your Ubuntu drive to be first in BIOS and install to it. Use the advanced button near the end of the install to make sure it installs grub to the correct drive. Mixed IDE and Sata drives usually have issues with drive priority but pure Sata should be ok, but sda may not be the first drive in BIOS.

---

### Post by presence1960 on 2009-12-02
> Set your Ubuntu drive to be first in BIOS and install to it.
by oldfred

Exactly what you need to do. Can't get any more simple than that. Then leave the Ubuntu disk booting first in BIOS so GRUB comes up at boot.

---

### Post by Burnasty on 2009-12-02
Thank you all very much for the help I will see how it goes.  I am eager to get back to ubuntu.  I wish I didn't need windows for the few programs I have to have.

Brian

---

### Post by CaminoSS on 2009-12-02
I had the same type problem.
Ubuntu / Vista listed in grub menu, working fine
Installed grub2 and grub was chained to grub2
After running upgrade-from-grub-legacy
I lost my Windoze selection in grub2 menu
I used Vista install to execute bootrec /fixboot then bootrec /fixmbr
which disables grub completely
I then re-installed grub from Ubuntu CD
When I run update-grub2 I get:

Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /windows/Boot
boot: No such file or directory
done.
Of course there is no /windows/Boot directory. I cannot find
in any of the grub2 files /etc/grub.d or in /etc/default/grub
any reference to /windows/Boot
I have read through the various links on grub2 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) but no mention of this
problem or where /windows/Boot is coming from.

sudo fdisk -l returns: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x58000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9982    80180383+   7  HPFS/NTFS
/dev/sda2            9983       30401   164015617+   5  Extended
/dev/sda5            9983       30285   163083816   83  Linux
/dev/sda6           30286       30401      931738+  82  Linux swap / Solaris

any ideas / thoughts would be appreciated......

---

### Post by oldfred on 2009-12-03
CaminoSS Please start you own thread so we do not mix your questions and answers the the OP - original poster. Also Presence has a link to a script that you should run and post as part of your new thread.

---

### Post by CaminoSS on 2009-12-03
Excuse my ignorance,
I apologize for confusing the original issue.

---

### Post by richlyn9 on 2009-12-03
> **Burnasty said:**
>   I wish I didn't need windows for the few programs I have to have.

Brian

dont worry eventually you'll find programs in linux for those in MS win 7

---

### Post by CongoJim on 2009-12-03
> **Burnasty said:**
> Thank you all very much for the help I will see how it goes.  I am eager to get back to ubuntu.  I wish I didn't need windows for the few programs I have to have.

Brian

Might I sugest [http://www.howtoforge.com/virtualbox_ubuntu](http://www.howtoforge.com/virtualbox_ubuntu) ?
With it you can install a copy of Windoz that you run from within Ubuntu. It even allows you to operate USB devices that have no Ubuntu support (a scanner or printer for example). No rebooting or anything beyond giving it permission to run the USB device.

---

### Post by Bartender on 2009-12-03
Looks like I'm going to have to toss half of what I thought I knew about GRUB out the window...

oldfred, are you saying that if you install Ubuntu COMPLETELY to  HDD #2 (the entire GRUB bootloader as well as the OS), then set HDD #2 first in the boot order from BIOS, that GRUB2 can find and boot Windows on HDD #1?

That's a big difference from the previous GRUB.  I mean, you could manually add Windows to GRUB but that was iffy for someone who's not somewhat familiar with the command line.

---

### Post by presence1960 on 2009-12-03
> **Bartender said:**
> Looks like I'm going to have to toss half of what I thought I knew about GRUB out the window...

oldfred, are you saying that if you install Ubuntu COMPLETELY to  HDD #2 (the entire GRUB bootloader as well as the OS), then set HDD #2 first in the boot order from BIOS, that GRUB2 can find and boot Windows on HDD #1?

That's a big difference from the previous GRUB.  I mean, you could manually add Windows to GRUB but that was iffy for someone who's not somewhat familiar with the command line.

I have karmic and GRUB 2 on sdb and windows on sdc. GRUB 2 found both OSs and I was able to boot both with no adjusting or customizing. Another enhancement I have found is that the boot order plays no role in chainloading OSs as it did in GRUB 0.97. In 0.97 the x designation in (hdx,y) and (hdx) was determined by the hard disk boot order in BIOS. In GRUB 2 you just need the disk with GRUB 2 on MBR to be first to boot in BIOS then GRUB 2 takes care of the other OSs. If you want a custom entry in GRUB 2 the numbering for disks actually follows the sda, sdb, sdc, etc order as reported by fdisk.

---

### Post by darkod on 2009-12-03
@bartender
I have single drive myself but from other people here that I've given advice about grub2, yes it can. It seems it scans everything. The way it's supposed to be anyway. :)

---

### Post by oldfred on 2009-12-03
Ok, I will admit I have been giving advice but not following it myself. My old set up for the last several years was windows on sda, current Ubuntu ( now Fiesty32) on sdb, booting from sda. I added a new drive sdc and installed Fiesty64 to test and Karmic alpha to test and chainbooted from my Fiesty install. Then a clean install of Karmic over Fiesty64 so I could migrate my settings from my 3 years of accumulated cruft in Fiesty to a clean Karmic. Karmic installed its grub2 to sdc, I am not sure why but it worked out great. Grub was slow loading (known bug) until I went back in and set sdc to be the boot drive per BIOS.  I expected all the grub.cfg and drive order stuff to be updated/changed. Absolutely no change to drive order or menus and everything still boots just fine. It looks like my drive order is in the SATA port order as plugged in to the motherboard.

I did not have much issue with old grub finding installs, I had a old, old windows drive that I wanted to copy data from and it added it to my boot menu. It just seems that grub2 is a lot better at finding systems and update-grub almost always works at finding other systems.

---


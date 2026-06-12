---
title: "Install bootloader"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by rplantz on 2010-05-10
I'm doing a fresh install of 10.04. When I get to the final commit screen, I clicked on the "Advanced" button because I want to install the bootloader on my Ubuntu partition. The only choice was to install the bootloader or not.

Question 1: When I choose to install the bootloader, do I get a chance to specify *where* to install it?

Reason I am asking: This is a laptop with Vista preinstalled without a Vista install disk. I wish to keep the Vista bootloader on my MBR so that I can get to the "hidden" Vista partition in case I ever need to reinstall Vista. I used EasyBCD to add Ubuntu 9.10 to Vista's boot choices before, now I'm replacing 9.10 with 10.0.

Question 2: I already installed 10.04, specifying that it should not install a boot loader. Now, of course, I cannot boot into it. Is there any way to simply install the bootloader (grub2) in my Ubuntu / partition without going through the whole installation process again?

--Bob

---

### Post by darkod on 2010-05-10
Grub2 doesn't like being installed on a partition but you can force it. The parameter was -f, I think.
Assuming your ubuntu root partition is /dev/sda5, you need to boot the live mode with the cd and execute:

sudo mount /dev/sda5 /mnt
sudo grub-install -f --root-directory=/mnt/ /dev/sda5

On another note:

1. When you clicked the Advanced button there should be drop down list where you can select the partition if you insists to install grub2 there.

2. The restore partition usually has boot files to kick off, and those are detected by grub2. You could access it like that from grub2 installed on the MBR. It would show for example:
Ubuntu
Vista on /dev/sda1 (your vista on partition #1)
Vista on /dev/sda4 (the restore partition #4)

---

### Post by rplantz on 2010-05-10
> **darkod said:**
> Grub2 doesn't like being installed on a partition but you can force it. The parameter was -f, I think.
Assuming your ubuntu root partition is /dev/sda5, you need to boot the live mode with the cd and execute:

sudo mount /dev/sda5 /mnt
sudo grub-install -f --root-directory=/mnt/ /dev/sda5

Thank you, darkod. I tried this without "-f" and grub-install, as you say, told me this was not a good idea and I would have to use "--force" to do it anyway.
> 
On another note:

1. When you clicked the Advanced button there should be drop down list where you can select the partition if you insists to install grub2 there.

2. The restore partition usually has boot files to kick off, and those are detected by grub2. You could access it like that from grub2 installed on the MBR. It would show for example:
Ubuntu
Vista on /dev/sda1 (your vista on partition #1)
Vista on /dev/sda4 (the restore partition #4)

Are you sure grub2 will do this? Acer has created the restore partition as a "hidden partition." When I first got this laptop, I installed Ubuntu 8.04 as dual boot with the Vista. I thought that grub would find both the Vista partition and the restore partition and all would be good. Wrong! I spent the rest of the day downloading Vista repair things, etc., etc. Being a Windows newbie, it was quite an adventure!

So I would like to be sure that grub2 would find the hidden restore partition before repeating this experience.

Another option is to use an older Ubuntu live CD to install grub instead of grub2.

BTW, I prefer grub2. I use it on my desktop machine to dual boot Ubuntu 10.04 and Windows 7.

--Bob

---

### Post by darkod on 2010-05-10
I can't say for sure, but have in mind that "hidden" is a relative term. For example, the 100MB boot partition sometimes created by win7 installer doesn't show up in win7 in Computer but ubuntu can easily see it.

Open Gparted from live mode or from your hdd ubuntu and take a look at the disk. If Gparted can see it, I don't see a reason why grub wouldn't.

Also simply run in terminal:

sudo fdisk -l

you will see it reported in the result. While windows doesn't show it unless you go into Disk Management, it will be there.

So, hidden partition is extremely relative term.

You can also run the boot info script from my signature from ubuntu live mode or hdd, and take a look in the results.txt file. It will show whether it can see that partition and whether it has boot files on it.
If you need help running the script just ask.

---

### Post by rplantz on 2010-05-10
Your script gives more info. The relevant part seems to be:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file 
                       /NST/nst_grub-5E6465A1F1E369C6FCCBE5AE4319FE7F.mbr is 
                       trying to chain load sector #186080958 on boot drive 
                       #1 BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #186080958 on boot drive #1
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,482,047    20,480,000  27 Hidden HPFS/NTFS
/dev/sda2    *     20,482,048   166,536,735   146,054,688   7 HPFS/NTFS
/dev/sda3         166,539,264   186,070,513    19,531,250   7 HPFS/NTFS
/dev/sda4         186,080,956   312,576,704   126,495,749   5 Extended
/dev/sda5         186,080,958   205,599,869    19,518,912  83 Linux
/dev/sda6         205,599,933   209,503,664     3,903,732  82 Linux swap / Solaris
/dev/sda7         209,503,728   312,576,704   103,072,977  83 Linux


```
It's pretty clear that /dev/sda1 is the restore partition. Since I'm not at home now, I'm nervous about letting grub2 take over my MBR. My previous experience with grub on 8.04 increases my nervousness.

I just thought of another option -- a WUBI install. Almost all my activity is on my desktop machine, so a WUBI install on this laptop would probably be okay for my uses.

Meanwhile, perhaps someone who has actually seen grub2 recognize the hidden restore partition my respond, which would ease my nervousness.

--Bob

---

### Post by darkod on 2010-05-10
I have definitely seen cases on this forum which could kick off the recovery partition from grub2. In fact, sometimes you have to be careful because the entries would be very similar like:
Vista on /dev/sda1
Vista on /dev/sda2

Because of the same type of boot files the recovery partition is usually detected as Vista/Win7 too. And sometimes selecting that entry instead of the OS will kick off the recovery process overwriting grub2 on your MBR before you can stop it. Of course, that's a worst case scenario and even then restoring grub2 is easy.

But I can not claim for 100% what will happen on your machine exactly.

As you can see, there are /bootmgr and /boot/bcd boot files on /dev/sda1 as expected.

But I'm interested in this part of the results:
Boot file info:     BootPart in the file 
                       /NST/nst_grub-5E6465A1F1E369C6FCCBE5AE4319FE7F.mbr is 
                       trying to chain load sector #186080958 on boot drive 
                       #1 BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #186080958 on boot drive #1

This code is in the boot sector of the /dev/sda2 partition and I assume it's part of EasyBCD otherwise there shouldn't be any code there.

If you decide to try out grub2 on the MBR, remove EasyBCD first and that should remove that code. You might even run the script again to confirm it's gone. Otherwise it can create a loop. Grub2 will jump to /dev/sda2 when Vista is selected, and this code will send it elsewhere.

And then you'll blame ubuntu. :)

---

### Post by rplantz on 2010-05-10
> **darkod said:**
> 
But I can not claim for 100% what will happen on your machine exactly.

Only taxes and death are 100%. :-)

> 
And then you'll blame ubuntu. :)

I'm sure I would blame Vista. As I mentioned above, I'm a Windows newbie. My adventures with computers started in the early 1960s, so I've worked with lots of OSs, including installing from paper tape. I was mostly a Mac user until 1999, when I mostly moved to Linux. Have been mostly on Ubuntu since about 2004. I'm still learning about Windows, so it usually gets my first blame when something goes wrong. :-)

I'm going to set this aside until I get back home. No sense in tempting the devil while I'm on the road. Thank you for your very kind help.

--Bob

---

### Post by markthecarp on 2010-05-10
Good luck rplantz! I'm an old linux hand since '99; winxp has been messing with my virtualbox playground.

I'm too old to learn the wrong way ;-)

-mark

---

### Post by rplantz on 2010-05-27
> **darkod said:**
> Grub2 doesn't like being installed on a partition but you can force it. The parameter was -f, I think.
Assuming your ubuntu root partition is /dev/sda5, you need to boot the live mode with the cd and execute:

sudo mount /dev/sda5 /mnt
sudo grub-install -f --root-directory=/mnt/ /dev/sda5

On another note:

1. When you clicked the Advanced button there should be drop down list where you can select the partition if you insists to install grub2 there.

You're right. I reinstalled Ubuntu and used the drop down menu to install grub2 in my Ubuntu partition.

Then I booted into Vista and used EasyBCD (1.7.2) to install a boot entry to Ubuntu. I had to use something like "Neogrub." I don't recall the exact procedure, but it was pretty simple.

I went this route instead of using grub2 for my main boot loader. grub2 may had detected the "hidden" partition okay, but I'm not sure that Acer's magic restore sequence would know what to do with grub2. Hopefully, I will never have to use this partition to set my laptop back to factory settings, so I'll probably never know the answer.

Thanks again for the suggestions.

---

### Post by WinRiddance on 2010-05-27
**Eventually** you'll probably do what most Ubuntu users with laptops do ... two or three or four years down the road wipe out the entire disk, install the latest hottest most awesome linux system with a bunch of eye candy, and then sell the machine on eBay or to a friend or a neighbor. I never use a laptop more than 3 years max and by then any WinOS that's already 3 years older than the latest & greatest Ubuntu is not an easy sell since the hardware isn't worth much anymore by then anyway. Just my 2 cents ...
.

---

### Post by rplantz on 2010-05-27
> **WinRiddance said:**
> **Eventually** you'll probably do what most Ubuntu users with laptops do ... two or three or four years down the road wipe out the entire disk, install the latest hottest most awesome linux system with a bunch of eye candy, and then sell the machine on eBay or to a friend or a neighbor. I never use a laptop more than 3 years max and by then any WinOS that's already 3 years older than the latest & greatest Ubuntu is not an easy sell since the hardware isn't worth much anymore by then anyway. Just my 2 cents ...
.

Well, I still have my Mac Plus, and my partner still has a Lisa! Okay, they only collect dust these years.

I don't use my laptop much. Mostly for Skype, which works better under Vista than Ubuntu. (Haven't tried it on 10.04 yet.) And it's nice when I have to wait places, like getting my car serviced. So I tend to keep it fairly "stock." 95% of my time is spent on my desktop machine, which dual boots Ubuntu and Windows 7. It changes constantly.

---


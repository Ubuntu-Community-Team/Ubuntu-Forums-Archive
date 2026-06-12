---
title: "Windows 7 + Ubuntu 8.10 Dual Boot FAIL"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by AdamShumpisxXx on 2010-03-12
I am VERY frustrated right now with Ubuntu. It makes me so angry to know that I had this working like 3 months ago before my motherboard sh*t the bed and I had to purchase a replacement. Here's my issue guys / gals...

I'm trying to dual boot Windows 7 and Ubuntu 8.04 LTS Hardy Heron. I followed the instructions here due to my need to have Windows 7 own the MBR with it's own bootloader:

 [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

Here's my partition setup:

Primary
sda1 = Windows 7 (loader)
sda2 = Windows 7 C:\
sda3 = Windows 7 X:\ (NTFS Storage Partition)
Logical
sda5 = Ubuntu /boot 512MB ext2
sda6 = Ubuntu swap 2048MB
sda7 = Ubuntu / 17GB ext3

I used EasyBCD to add the Ubuntu entry to the Windows 7 bootloader and pointed it to sda5. When I restart my computer I see the entry I made but whenever I go to choose it I get an error screen provided by the Windows 7 bootloader that my Windows partition needs to be recovered. I get two options...ESC or Continue and they both go back to the OS Choices menu. The Windows 7 option works perfectly as that is what I'm using to type out this thread. I have absolutely no access to Ubuntu. Can anyone tell me where I went wrong ](*,)?

Thanks in advance to everyone! I look forward to getting past this nonsense...

*EDIT = By the way...During the Ubuntu installation I used the advanced option to install the GRUB bootloader to the sda5 /boot partition. Thought that might help. If you need pictures of anything or any further information lemme' know!

---

### Post by tommcd on 2010-03-12
Is Windows 7 supported by EasyBCD? According to the changelog for EasyBCD, the latest version dates from 04-08-08, and does not mention Windows 7. It only mentions Vista:
[http://neosmart.net/changelog.php?id=1](http://neosmart.net/changelog.php?id=1)
The tutorial on the neosmart website also deals with Vista.

It should not be necessary to have a separate /boot partition for Ubuntu. The tutorial on the neosmart site does not mention this.

If it were me I would reinstall Ubuntu. Delete the partitions you have made. Then make just the root and swap partitions for Ubuntu on logical partitions. (Ideally you should have a separate home partition, but with just 17GB for Ubuntu, you may want to stick with just a root partition.)
Then just install Ubuntu's grub to the MBR. If you have been using Ubuntu for a while you should be able to dual boot with grub. Also, I would either install Ubutnu 9.10 (the current version), or wait for Ubuntu 10.04 LTS. Beta versions of 10.04 LTS should be available soon. The final version of 10.04 LTS will be out the end of April.

I don't know if the grub-legacy that comes with 8.04 will reliably boot Windows 7. There are lots of people dual booting Windows 7 with the grub2 that ships with Ubuntu 9.10 and 10.04.

---

### Post by AdamShumpisxXx on 2010-03-12
Thanks for the help. Here's a couple issues. I know EasyBCD is compatible with Windows 7. It's in the v1.7.2 README file (which is the version I have). That tutorial was the same one I used when I first did this...yes I have done this exact thing before and it worked BEFORE I changed out my motherboard and HDD. I don't want to use Ubuntu 9.10 because the X server is not compatible with the driver of my ATI x1950xt graphics card and I doubt Ubuntu 10.04 is going to regress it's X server just for little ol' me... Lastly I can't let Ubuntu take over the MBR. I have to let the Windows 7 bootloader control the MBR and then chainload into GRUB from the Windows 7 OS Choices menu (exactly how I had this setup originally before said incident). The reason for this is every time I let Ubuntu d*ck with the MBR I lose Windows 7 activation and have to restore the MBR before I can reactivate.

I'll try your suggestion and just set my partitions up this way:

sda5 = Ubuntu swap 2048MB
sda6 = Ubuntu / 17GB ext3

I'll let you know how that turns out in about 45 minutes. Thanks again!

---

### Post by tommcd on 2010-03-13
> **AdamShumpisxXx said:**
>  I know EasyBCD is compatible with Windows 7. It's in the v1.7.2 README file (which is the version I have). 
I had not read the details of the changelog, since, apparently, you have to login to that site to read them. I had only read the highlights on the page I linked to. It is good that you have verified compatibility with Windows 7.
> **AdamShumpisxXx said:**
> 
 I have to let the Windows 7 bootloader control the MBR and then chainload into GRUB from the Windows 7 OS Choices menu (exactly how I had this setup originally before said incident). The reason for this is every time I let Ubuntu d*ck with the MBR I lose Windows 7 activation and have to restore the MBR before I can reactivate.
Is this a homemade computer or an OEM model? If OEM, then check the motherboard's BIOS for some setting that you may be able to disable to prevent this from happening. If you built this computer yourself, then this is odd indeed. I can only assume this is a "feature" of Windows 7 if that is the case.
> **AdamShumpisxXx said:**
> 
I'll try your suggestion and just set my partitions up this way:

sda5 = Ubuntu swap 2048MB
sda6 = Ubuntu / 17GB ext3

So have you had any luck wit this setup, and without the /boot partition?

---

### Post by Mark Phelps on 2010-03-14
AFAIK, EasyBCD 1.7.2 does NOT support Win7.  You need to go to the NeoSmart Technology forums and download v2 beta bld 82. 

Also, while you're there, look around through the forums.  They have tutorials and how-to's on doing what you want to do.

---

### Post by tommcd on 2010-03-15
> **Mark Phelps said:**
> AFAIK, EasyBCD 1.7.2 does NOT support Win7.  You need to go to the NeoSmart Technology forums and download v2 beta bld 82. 

Mark,
Have you had any problems with losing the Windows 7 activation and having to restore the MBR to the control of Windows 7 in order to get Windows back, as AdamShumpisxXx reports? I have read of similar stuff like this before with Windows 7. IIRC, it was always with a manufacturer's OEM BIOS setting or something like that.

Since your sig says you use Windows 7, do you have any insight as to how to work around this?

---

### Post by Mark Phelps on 2010-03-15
> **tommcd said:**
> Mark,
Have you had any problems with losing the Windows 7 activation and having to restore the MBR to the control of Windows 7 in order to get Windows back, as AdamShumpisxXx reports? I have read of similar stuff like this before with Windows 7. IIRC, it was always with a manufacturer's OEM BIOS setting or something like that.

Since your sig says you use Windows 7, do you have any insight as to how to work around this?

As sensitive as Vista was with ANY changes messing up activation, I took the position of avoiding messing with the MBR at all costs.  On a multi-disk machine, I kept the MS Windows-created MBR on that drive and allowed Ubuntu to install GRUB-related MBRs on the other drives.  On a single-drive system, I use EasyBCD to modify the BCD to add the Ubuntu entry.

I've kept the same practices since I upgraded from Vista to Win7.

So, I don't have any experience with messing with the MBR to see if it hoses up activation, sorry.

With OEM versions, motherboard (actually, BIOS) changes, and HDD changes will most certainly hose up activation, but I would think that MBR changes would not.

Also, a recent Windows Update (if it was installed) now monitors the machine for any "piracy-related" exploits (whatever MS means by that!).  So, if the copy of Win7 has this KB installed, I wouldn't be surprised if MBR changes hose up activation.

---

### Post by oldfred on 2010-03-15
I also would review BIOS settings to see if something is not compatible. I have XP and found some settings work for Ubuntu and not XP and vice-versa.

---


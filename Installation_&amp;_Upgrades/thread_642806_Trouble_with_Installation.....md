---
title: "Trouble with Installation...."
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by wotonka on 2007-12-17
First, let me confess that I am a "newbie", and I greatly appreciate the assistance that is so generously offered via this forum:

I have a Dell Pentium 4 HT with (2) hard drives installed. The first hard drive has Windows XP.  I installed a second (slave) hard drive, and used Windows "Manage" to re-partition and format it. It now has one large (80GB) partition.  Next, I removed the Windows drive, and moved the jumper to make the second drive the "master" (and I completely removed the first Windows drive).  I tried to install Ubuntu V 7.10 on the newly formatted, remaining drive.  The installation of Ubuntu hung up indefinitely on Step 2 "Enter your time".   I realized that I downloaded the 32 bit version of Ubuntu, but think I need the 64 bit version (downloading currently from the Web).  Here are my questions:

1. I assume that using Windows to format my Linux drive is proper (formatted using NTFS ??).  
2. I assume the proper procedure will be to boot from CD (Bios setting), and install to the Hard Drive. 
3. I assume the 64 bit version is the one I want to use for a Pentium 4 HD? Right?

I can't figure out why the installation would have hung up the first time, unless one of the items mentioned above are the culprit.  Again, because I don't have experience at this, I am finding this a challenge.

Thanks very much in advance for any assistance you may offer !

---

### Post by erfahren on 2007-12-17
I'm not sure why it hung up either

but
1) Linux uses ext3 filesystem - but that isn't a big deal if it's already formatted to NTFS since the Ubuntu install will format it as needed

2) yes, boot from CD

3) no, you shouldn't necessarily need the 64-bit version, the 32-bit version will (should) work with 64-bit processors 

4) when you go to install Ubuntu on that drive are you manually making a partition for both root ( / ) and swap? - or are you using the guided install?

good walk through guide here: [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

another question: are you intending to make it dual boot with Windows and have Ubuntu on the slave drive? I must confess I don't know to much about using two drives but if you want to dual boot you'd want to install a bootloader (GRUB is the bootloader Ubuntu uses). -- and if both the drives are in when you install GRUB should pick up on the setup and configure itself accordingly.
more info about GRUB on hermanzone's site: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Recovering from MS. on 2007-12-17
> **wotonka said:**
> I have a Dell Pentium 4 HT 

3. I assume the 64 bit version is the one I want to use for a Pentium 4 HD? Right?


Um I'm a bit of a newbie to linux myself, but I also use a p4 with hyper theading....
And as far as I can tell they still run at 32bit.

As for the rest I'm sorry I cant be of more help.

---

### Post by JangMunho on 2007-12-17
1.Linux has its own file system, it support ext3, reiserfs... But no dos-fs and NTFS. They are only for Windows.
2. Yes, live system will boot from CD, and install the system on the hd.
3. Pentium 4 HT is a 32-bit CPU rather then a 64-bit one. You can't install a 64-bit OS on a 32-bit CPU, the live system even won't boot.

Try to use partition magic to make at lease a ext3 partition and a linux-swap partition on your hard drive. And then try again.
If it don't help, try to download the alternate CD. Sometimes alternate CD is more stable then the Desktop one.

---

### Post by Edho on 2007-12-17
My Desktop PC :

Master HD with Windows XP.
Slave HD with Ubu Dapper.

Just installed Dapper on the slave,, asking for installing the bootloader Grub in the MBR.

Yess...

Before booting i can choose Dapper or WinXP.

---

### Post by erfahren on 2007-12-17
> **JangMunho said:**
> 1.Linux has its own file system, it support ext3, reiserfs... But no dos-fs and NTFS. They are only for Windows.
2. Yes, live system will boot from CD, and install the system on the hd.
3. Pentium 4 HT is a 32-bit CPU rather then a 64-bit one. You can't install a 64-bit OS on a 32-bit CPU, the live system even won't boot.

Try to use partition magic to make at lease a ext3 partition and a linux-swap partition on your hard drive. And then try again.
If it don't help, try to download the alternate CD. Sometimes alternate CD is more stable then the Desktop one.
partition magic is *not* needed, and actually can cause more problems than it solves.
the Ubuntu LiveCD contains GParted (along with the partitioner used in the installer)

to launch it, go to the terminal (Apps > Accessories > Terminal) and type in:
```

sudo gparted

```

I agree with the suggestion of using the Alternate CD though (if need be). I wasn't going to mention that since the OP was already downloading that 64-bit one.

good walk-through guide with screenshots for the AlternateCD at: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by wotonka on 2007-12-17
Thanks a million to all of you who gave advice.  I will read through the comments and give it a try.  Again - much thanks !!

---


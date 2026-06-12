---
title: "Ubuntu Installation Problems"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by zorneatsham on 2007-09-03
I recently assembled a file server on which I intended to install Ubuntu. I have tried just about every image file from Ubuntu (desktop, alternate, 64-bit desktop, 64-bit alt, both server versions) and none will install. I have tried them on both CDs and DVDs (burned at low speeds). All of these were burned on my MacBook. I tried a second MacBook as well. I have tried to install both Fedora and OpenSUSE on this sever, but both failed. I even returned the DVD drive to the store for a replacement. For all of the above, the CD fails verification and/or installation fails. I have tried installing so many different OS flavors that I have lost track of the specific errors, but CD verifications generally fail.

Here's the kicker, I can install both Windows XP (pressed CD) and an old Windows Vista beta (burned DVD). Once, I had XP installed, I burned an Ubuntu image using the very drive with which I want to install Ubuntu. No dice; same error. 

Here are the specs on my server:

Athlon 64 X2 4000+
ASUS M2NPV-VM (Nvidia Geforce 6150 chipset)
Pioneer DVR-1810 DVD burner
Seagate 400GB SATA hard drive

Any ideas? Is this a problem with the server or with the images? Surely 3 different burners can't all be broken?

---

### Post by Pumalite on 2007-09-03
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by zorneatsham on 2007-09-04
I have already referred to that page. THe MD5 Sums checked out and I burned as per the instructions. There isn't a problem with the image, but how is it that burning it from 3 different computers would yeild bad disks?

---

### Post by matthewrdamon on 2007-09-08
I hope I am not thread hijacking.  I am having a very similar problem on my computer.  My specs are entirely different, however, and I have never had problems with burning/using disk images.

My computer has never gotten past the "Loading components from CD" part.  When this fails, I select the option to test the CD, which almost instentaniously fails.  I am not on my home computer right now, and I can't think of the file that it says is corrupt, I'll post it later.

First of all, my computer specs:
   Intel 586 3.0Ghz w/ hyperthreading
   nVidea graphics
   dual boot with windows xp
   brand new LG DVD/CD Burner
   1Gig of RAM

  I don't think anything else is really relevant at this point

My process for burning/testing installation media:
  1.  download the ISO
  2.  vierfy via md5 the integrity of the download
  3.  burn to CD
  4.  verify the cd using the command: md5 /dev/cdrom
  5.  attempt installation

I have tried ubuntu alternate, xubuntu alternate and ubuntu server.  They have all been verified with md5, and they all say that the media is corrupt when I attempt the installation.  

I'm running out of CDs here, I don't know what to do.

Any help would be greatly appreciated.

---

### Post by Pumalite on 2007-09-08
Maybe your burner has had it. Clean the lens or change the burner. One can have a perfect iso and then the burner produce a corrupted CD. Also try burning at 4x or even at 1x.

---

### Post by matthewrdamon on 2007-09-08
My burner is brand new, and the CD is NOT corrupted, it is a binary equal of the iso.  tested with the command: md5 /dev/cdrom  it produces the exact same output as what is listed on the ubuntu server.

---

### Post by Pumalite on 2007-09-08
They have all been verified with md5, and they all say that the media is corrupt when I attempt the installation. 

What is this then?. I don't understand you.

---

### Post by matthewrdamon on 2007-09-08
Sorry for not being clearer.  When I burn the CD, using a different computer, I verify the burned media with md5.  Then I walk across the room to the computer that I want to install ubuntu on and place the CD in the drive.  The installation media fails in this computer.  Then, just for kicks, I bring the CD back across the room to the computer that I originally burned it on, test the md5 sum again, still perfect.  

That is why I am inclined to say that it is not the CD as I can test the md5 sum on my other computer.  It is a very strange situation.

---

### Post by zorneatsham on 2007-09-08
This sounds very similar. I can't imagine it likely that 3 burners would all be bad. I will check the checksums on my "bad" discs. I'm waiting for some pressed discs from canonical. Hopefully that will be better. 

A friend suggested an issue with my hard drive, but I don't have another hard drive to spare, so I haven't been able to test this hypothesis.

---

### Post by Pumalite on 2007-09-08
Obviously the computer in which you are trying to boot the disk has a badly working burner (rom).

---

### Post by matthewrdamon on 2007-09-08
That computer is the one with the brand new burner, I have used it before.  I Installed xp with it, and I have used it for burning DVDs/CDs

---

### Post by zorneatsham on 2007-09-08
Ditto here. I installed both XP and Vista on this computer. I don't want either of those OSs on my file server, but I tried it to see if it would work.

---

### Post by Pumalite on 2007-09-08
This is worthy of Agatha Christie then.

---

### Post by devmod on 2007-09-19
same thing happening here ...

M2NPV-VM + pionner dvd rw  AMD X2 4200+ dual core...

not sure what is going on with this. I got this for a media center I need linux... 


Any updates on this?

---

### Post by andrewski on 2007-10-03
> **zorneatsham said:**
> ASUS M2NPV-VM (Nvidia Geforce 6150 chipset)
> **devmod said:**
> M2NPV-VM 

Interesting that you both have the same motherboard.

I've been working with zorneatsham on this and he mentioned that it could be a motherboard issue.

This bug sounds similar, can anyone confirm?
[https://bugs.launchpad.net/ubuntu/+bug/63313](https://bugs.launchpad.net/ubuntu/+bug/63313)

Has anyone tried BIOS updates?

---

### Post by Pete317 on 2007-10-03
I'm a bit of a newbie (to Ubuntu at any rate)

I upgraded from 6.06 to 6.10, no problems at all.
Then I checked for and downloaded updates, still OK.
Then I tried upgrading to 7.04 - it started, went a little way, and then stopped with the following error:

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

I've tried several times, even rebooting in between, but it's still the same.

My network connection is working, so I don't know what's wrong.

Please help

Cheers

---

### Post by andrewski on 2007-10-03
> **Pete317 said:**
> I'm a bit of a newbie (to Ubuntu at any rate)

I upgraded from 6.06 to 6.10, no problems at all.
Then I checked for and downloaded updates, still OK.
Then I tried upgrading to 7.04 - it started, went a little way, and then stopped with the following error:

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

I've tried several times, even rebooting in between, but it's still the same.

My network connection is working, so I don't know what's wrong.

Please help

Cheers
This is a completely different issue, can you post a new thread?

---

### Post by Pumalite on 2007-10-03
> **andrewski said:**
> Interesting that you both have the same motherboard.

I've been working with zorneatsham on this and he mentioned that it could be a motherboard issue.

This bug sounds similar, can anyone confirm?
[https://bugs.launchpad.net/ubuntu/+bug/63313](https://bugs.launchpad.net/ubuntu/+bug/63313)

Has anyone tried BIOS updates?

[http://www.linuxquestions.org/questions/showthread.php?t=499929](http://www.linuxquestions.org/questions/showthread.php?t=499929)

[http://ubuntuforums.org/archive/index.php/t-404298.html](http://ubuntuforums.org/archive/index.php/t-404298.html)

---

### Post by zorneatsham on 2007-10-20
As an update:  I switched out the DVD drive and am now able to boot into the Live CD. I was using a Pioneer DVD-RW drive. I replaced it with an Asus CD-ROM and it's booting. My troubles are not done, though. I cannot get past 5% on "Partions formatting." Sigh...

---

### Post by Pumalite on 2007-10-20
Go Manual or use the Alternate CD.

---

### Post by zorneatsham on 2007-10-20
No need. I was way too impatient. It eventually progressed past 5%. I now have a working install. Gutsy is a major improvement over my last Ubuntu experience (once I got it working!).

---


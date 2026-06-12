---
title: "What's wrong? Ubuntu or my computers?"
date: 2017-11-14
forum: Installation &amp; Upgrades
---

### Post by emtor on 2017-11-14
I've got two computers: An old Lenovo N500 running Ubuntu 17.04, and a new HP Pavilion Notebook running Win 10.
Trying to install Ubuntu Studio fails for both computers.
On the HP I've tried several 64-bit Ubuntu Studio versions which starts loading files from the DVD, shows the startup screen and then shows a long list of errors.
Then the installation halts.
My last try ended up with just showing the startup screen,- and then it halted.

On the Lenovo the 32-bit installer let's me choose from trying the software, installing or checking files.
Trying Ubuntu Studio went fine and I get a desktop and it connects to the internet, but when installing permanently it copies files and shows the slides and then crashes.

So,- what's wrong . . . Ubuntu Studio or my computers?

---

### Post by ubfan1 on 2017-11-14
1) Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
  For other releases' hashes, like lubuntu, see:
  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
2) If using a CD/DVD, did you burn the disc as slowly as possible?
  See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
3) Did you select the media check before trying to install?
 [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
4) Did you ever do a "memory check" (perhaps another live-media menu choice) on your PC?
Doing the above can save you a lot of time struggling with a bad install media or
hardware problems.

---

### Post by ian-weisser on 2017-11-14
We cannot see what you are seeing, please elaborate.

> **emtor said:**
> On the HP I've tried several 64-bit Ubuntu Studio versions which starts loading files from the DVD, shows the startup screen and then shows a long list of errors.

What kinds of errors? Please be specific - it matters.

> **emtor said:**
> Trying Ubuntu Studio went fine and I get a desktop and it connects to the internet, but when installing permanently it copies files and shows the slides and then crashes.

Please describe the crash in more detail. There are many kinds of crashes.

---

### Post by emtor on 2017-11-14
Windows 10 machine:

I'm replying to both of you:
No,-I haven't checked md5sum yet.
memory is fine.
Burnt at lowest speed.
Memory test OK.

Startscreen appears, then displayes an error message:
firmware bug cpu 0 invalid threshold interrupt offset 1 for bank 4 block 0.

(initram fs) stdin: I/O error mount: mounting /dev/loop0 on //filesystem. squashfs failed: no such device 

could not mount /dev/loop0 (cdrom/caspar/filesystem.squashhfs) on //filesystem.sqashfs

After that it just halts.

---

### Post by emtor on 2017-11-15
Update: md5sum checks out OK.
media check OK
memory OK
burned at lowest speed
legacy mode enabled

Same result,-computer boots from DVD, shows the startup screen were you can choose "try", "install" etc.
I choose try, and the ubuntustudio icon starts spinning and then the above mentioned error message appears for a second, then the icon stops spinning, the computer's fan stops and the DVD drive shuts down. After that nothing happens.
I've tried several versions of ubuntustudio with the same result.

---

### Post by ian-weisser on 2017-11-15
Is the N500 32-bit or 64-bit?

---

### Post by emtor on 2017-11-15
> **ian-weisser said:**
> Is the N500 32-bit or 64-bit?


The N500 is 32-bit, and the ubuntustudio version is 32 bit also.
On the N500 the installer behaves differently from the 64-bit installer on my win 10 machine.
On the N500 the installer loads files and eventually starts displays slides, but after a while a message pops up saying the installer has crashed.

Ubuntustudio has so far been frustrating so I had a look at Fedora and downloaded the media writer for windows . . . which crashed big time.
Seems like this is a common problem judging from googling a bit.

Next up is Mint . . . . who knows what happens then . . .

---

### Post by ian-weisser on 2017-11-15
> stdin: I/O error mount: mounting /dev/loop0 on //filesystem. squashfs failed: no such device
This is usually caused by several of the common culprits for installer crashes listed by ubufan1 in Post #2

Rule out a bad burn: Try booting the DVD to the "try" environment in a known good machine.

I have successfully installed Ubuntu on many machines over the past decade, 32-bit, 64-bit,  several Win 10 machines, and more...without any problems at all.
The installer does indeed work for the majority of users.
Most installer failures on older equipment that I have run across turned out to be bad burns or dying hardware (disks and motherboards). Your mileage may vary.

---

### Post by emtor on 2017-11-16
> **ian-weisser said:**
> This is usually caused by several of the common culprits for installer crashes listed by ubufan1 in Post #2

Rule out a bad burn: Try booting the DVD to the "try" environment in a known good machine.

I have successfully installed Ubuntu on many machines over the past decade, 32-bit, 64-bit,  several Win 10 machines, and more...without any problems at all.
The installer does indeed work for the majority of users.
Most installer failures on older equipment that I have run across turned out to be bad burns or dying hardware (disks and motherboards). Your mileage may vary.

It may be a bad burn. I downloaded a mint distro and did a checksum test and it checked out OK.
Next I burned a DVD (new win10 machine) and told the software to confirm the burn (something I did not do on all of my previous tries) and it did not check out well meaning that the DVD differs from the downloaded file. 
This may be the cause.

---


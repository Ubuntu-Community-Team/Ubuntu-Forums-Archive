---
title: "AMD A10 from 2013"
date: 2020-05-05
forum: Installation &amp; Upgrades
---

### Post by max8425752574 on 2020-05-05
Hi all,
Sorry i started asking about my installation problems in another thread but can't find it anymore.

I had an HD crash and needed to install windows XP again and that was also the moment to try Ubuntu.

I've now done with my backup and try to find a solution for my operating system problem.

That's why I downloaded Ubuntu and put it now at a usb stick. That's a sure way to crash my PC!
Booting with the DVD works but causes my monitor to switch off ... I think two times ... 

I'll report here later at the moment I try a demo from Windows 7 and later windows 10. I have also vista but don't knew if I can still activate it.

At the moment I am disappointed that booting from a stick doesn't work. Maybe that can be fixed?

---

### Post by ubfan1 on 2020-05-05
Describe your machine with hardware details and maybe we can offer reasonable suggestions for the cause of your problems.  Guessing a cause, you have Nvidia hardware and didn't use nomodeset.

---

### Post by max8425752574 on 2020-05-05
> **ubfan1 said:**
> Describe your machine with hardware details and maybe we can offer reasonable suggestions for the cause of your problems.  Guessing a cause, you have Nvidia hardware and didn't use nomodeset.

It's a CPU with graphics on chip ;) but it was my first try to boot from stick and I created it from the Ubuntu desktop (booted from DVD).

CPU: AMD S-FM2 A10-5800K APU HD7660D
MB: MSI FM2-A85XA-G65 ATX

The stick I tried to boot has 8 GB but Windows tells me now that it has only 4 KB! Windows showed me that the stick has only one file and one drawer ... This makes me believe something gone wrong creating it?

---

### Post by CelticWarrior on 2020-05-05
> **max8425752574 said:**
> It's a CPU with graphics on chip ;) but it was my first try to boot from stick and I created it from the Ubuntu desktop (booted from DVD).

CPU: AMD S-FM2 A10-5800K APU HD7660D
MB: MSI FM2-A85XA-G65 ATX

The stick I tried to boot has 8 GB but Windows tells me now that it has only 4 KB! Windows showed me that the stick has only one file and one drawer ... This makes me believe something gone wrong creating it?

That's perfectly normal.

---

### Post by ubfan1 on 2020-05-05
So it's running the installer that blacks out, probably a problem with the ISO:
1) Does your system meets the minimum requirements for your selected edition?
  See [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
  Lack of enough memory can cause boot failure of the install media. Select a
  lower requirement edition like Lubuntu or Xubutnu if necessary.
2) Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
  For other releases' hashes, like lubuntu, see:
  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
3) If using a CD/DVD, did you burn the disc as slowly as possible?
  See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
  If using USB install media, use a  tool like unetbootin or rufus. 
  Don't just copy files to the USB.  
  See [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)  
4) Did you select the media check before trying to install?  
  See [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
5) Did you ever do a "memory check" (perhaps another live-media menu choice) on your PC?

---

### Post by max8425752574 on 2020-05-06
> **ubfan1 said:**
> So it's running the installer that blacks out, probably a problem with the ISO:
3) If using a CD/DVD, did you burn the disc as slowly as possible?
  See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
  If using USB install media, use a  tool like unetbootin or rufus. 
  Don't just copy files to the USB.  
  See [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)  


At the moment I can only tell that rufus forced me to install windows XP again :/
Because it takes time to find a operating system at such an old computer I can't tell much now

I played a little with rufus and it looks a good tool. I discovered that I can choose the boot medium in the bios directly ... That's why I used another stick and now I can boot Ubuntu from stick :)

---


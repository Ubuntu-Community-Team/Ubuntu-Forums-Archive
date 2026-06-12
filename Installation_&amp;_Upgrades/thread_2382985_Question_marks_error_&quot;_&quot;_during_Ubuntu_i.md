---
title: "Question marks error &quot;??? ???&quot; during Ubuntu installation"
date: 2018-01-19
forum: Installation &amp; Upgrades
---

### Post by nvmcviana on 2018-01-19
I'm currently running Windows 10 but I want to install Ubuntu in order to have both OS in my laptop (Toshiba Satellite L50-A-1EF). I'm trying to install Ubuntu 16.04.3 LTS using a PEN drive. During the installation process, right after the window where the options to "Download updates while installing Ubuntu" and "Install third-party software" are shown (I checked on both), the installation process just stops and the error "??? ???" appears. I found a couple of threads with the same problem but I couldn't find a solution that worked for me. I'm posting here hoping that someone is able to help me solve this problem. Thank you.

---

### Post by mörgæs on 2018-01-20
Hi, welcome to the fora.

Does it work better if you boot 17.10.1?

---

### Post by grahammechanical on 2018-01-20
Did the installation process ask you about the installation type? Did it ask you is you wished to install alongside an existing OS? MIcrosoft Windows does not shutdown. It hibernates so as to give faster boot times. This makes the Windows partitions unreadable to the Ubuntu installer. So, I ask. Have you switched off Windows fast startup?

[https://uk.answers.acer.com/app/answers/detail/a_id/37059/~/windows-10%3A-enable-or-disable-fast-startup](https://uk.answers.acer.com/app/answers/detail/a_id/37059/~/windows-10%3A-enable-or-disable-fast-startup)

Regards

---

### Post by nvmcviana on 2018-01-22
The installation process didn't ask me for the installation type, I didn't get to that point unfortunately. And yes, I have switched off Windows fast startup. 
Thank you for your answer.

---

### Post by ubfan1 on 2018-01-22
1) Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
  For other releases' hashes, like lubuntu, see:
  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
2) If using a CD/DVD, did you burn the disc as slowly as possible?
  See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
   If using USB install media, use a  tool like unetbootin or rufus. 
   Don't just copy files to the USB.  
   See [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)  
3) Did you select the media check before trying to install?  
   See [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
4) Did you ever do a "memory check" (perhaps another live-media menu choice) on your PC?
Doing the above can save you a lot of time struggling with a bad install media or
hardware problems.

---

### Post by nvmcviana on 2018-01-22
Tried it, same error. Thanks anyway.

---

### Post by nvmcviana on 2018-01-23
First of all, thank you for your reply. 
I've done the md5sum check using winMd5Sum for windows and the resulting number was the one expected. I'm using a pen USB (I've already tried two different ones) and rufus (selected options: MBR partition scheme for BIOS, FAT32, 4096 bytes). I've also done a memory check and no errors were detected. 
Since I couldn't install Ubuntu [COLOR=#000000]16.04.3 [/COLOR]I tried to install Ubuntu [COLOR=#000000]17.10.1 and [/COLOR]Mint but I still got the same error "??? ???". This is very frustrating.

---


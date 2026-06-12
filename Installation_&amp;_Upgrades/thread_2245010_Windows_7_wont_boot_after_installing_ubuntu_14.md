---
title: "Windows 7 wont boot after installing ubuntu 14"
date: 2014-09-20
forum: Installation &amp; Upgrades
---

### Post by mcgrasus on 2014-09-20
[TABLE]
[TR]
[TD="class: postcell"]                I cant boot up wiindows 7 after installing ubuntu 14
boot repair's logs: [http://paste.ubuntu.com/8387936/](http://paste.ubuntu.com/8387936/)

      
[/TD]
[/TR]
[/TABLE]

Okay. I repaired it using this tutorial: [http://www.tweakhound.com/2012/11/13/how-to-fix-the-windows-bootloader/](http://www.tweakhound.com/2012/11/13/how-to-fix-the-windows-bootloader/)
But now i cant choose which os i wanna run. How to change it?

---

### Post by Mark Phelps on 2014-09-20
> But now i cant choose which os i wanna run. 

Is one of the OS's booting by default? If so, which one?

Also, what DO you see when you start up the PC.

It could be a simple matter of reinstalling GRUB to the MBR of the disk, which can be done using the info in the link: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by mcgrasus on 2014-09-20
> **Mark Phelps said:**
> Is one of the OS's booting by default? If so, which one?

Also, what DO you see when you start up the PC.

It could be a simple matter of reinstalling GRUB to the MBR of the disk, which can be done using the info in the link: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
Windows is running by default
1. Bios is running
2. windows is running 
lel

Wont i have a bug like before? ill check it later and edit the post. Thanks mate.

---

### Post by James_Brooks on 2014-09-20
Every boot issue ive ever had i just ran linux secure in live mode and chose the fix boot button on the left when it boots up, biggity bam, done.

---

### Post by mcgrasus on 2014-09-20
> **James_Brooks said:**
> Every boot issue ive ever had i just ran linux secure in live mode and chose the fix boot button on the left when it boots up, biggity bam, done.

Thanks. It worked.
How i solved the problem:
1. I used the windows 7 cd to run the repair mode
2. i chose the terminal
3. in the terminal i have typed:
bootrec.exe /FixMbr
bootrec.exe /FixBoot
bootrec.exe /ScanOs
4. I rebooted the system
5. Windows succesfully was running
6. I used the ubuntu cd and chose Try Ubuntu
7. I downloaded the Boot-Repair
8. I have chose "recommended repair"
9. Rebooted the system after it succesfully repaired boot
10. And now i have been able to chose what system i wanna use, and both of them works :]

---

### Post by James_Brooks on 2014-09-20
sounds like work to me. 

Could start at number six but use linux secure, boot, try, click "fix boot", then restart (minus a couple yes and no's)

---


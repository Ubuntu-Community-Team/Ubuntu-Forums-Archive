---
title: "Acer Inspire XC 1660G Can't install"
date: 2021-11-10
forum: Installation &amp; Upgrades
---

### Post by agemini68 on 2021-11-10
Does windows do something to the computers they come installed on so you can't install a different OS? I have burned the iso image on DVD+r and DVD - R. When I try to boot from the DVD to install, The ubuntu logo comes up but it says it can't find it. I have an Acer inspire with windows 10. I don't use 3/4 of the stuff on there and all it does us take up space. Anyone come across this problem?

---

### Post by oldfred on 2021-11-10
What model Acer Inspire?

You typically have to change UEFI settings for drives from Intel RST to AHCI.
And in Windows make sure fast start up is off.

Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)
Acer Aspire A515-54G Newer Acer -  CTRL S on the main Tab in BIOS to get the option to change SATA to AHCI
[https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected](https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected)

After install, many Acer need "trust" setting:
Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

---

### Post by agemini68 on 2021-11-10
Acer Inspire XC 1660G And all those threads just confused the hell out of me. I can boot from the hard drive or the DVD, I changed it to DVD.

---

### Post by agemini68 on 2021-11-10
What do I do here? unable to find a medium containing a live file system
                                   Attempt Interactive net boot from a URL?
                                    yes no (default yes) :

---

### Post by agemini68 on 2021-11-11
I got it, but honestly not sure which combo worked. I kept turning things off and on in the Bios until I found the right settings.

---

### Post by yancek on 2021-11-11
Glad you got it working.  I don't use Acer but from what I have read, to be able to install another OS that did not come preinstalled with the Acer, you first need to be able to access the BIOS firmware immediately upon boot.  You will need to do an online search for the appropriate key for your specific Acer model.  You need to set a Supervisor password in the BIOS firmware and select aTrust option to be able to install Ubuntu or another OS.  I'd suggest you try to find an online manual for your specific Acer model for future reference.

---

### Post by agemini68 on 2021-11-12
Supervisor and password weren't in my Bios, Acer didn't put it in mine. I did turn off windows fast start, and I do remember turning off secure boot.

---

### Post by oldfred on 2021-11-12
Since you did install, you can change to solved.

---


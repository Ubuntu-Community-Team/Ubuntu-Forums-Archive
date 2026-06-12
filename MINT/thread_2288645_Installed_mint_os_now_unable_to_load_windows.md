---
title: "Installed mint os now unable to load windows"
date: 2015-07-28
forum: MINT
---

### Post by pranish on 2015-07-28
I had windows 8.1 freshy installed and then I installed mint os later. Now the linux grub doesnt show windows os.  How to restore the windows os? Is reparing windows boot loader the solution?

---

### Post by oldfred on 2015-07-29
Moved to Mint subforum as not Ubuntu.

Did you install in UEFI boot mode? Not sure how Mint works with UEFI?
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

May be best to see details, but do not auto fix from Boot-Repair until someone has reviewed report.

        Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Boot-Repair can convert a BIOS boot install to UEFI boot.

---

### Post by pranish on 2015-07-29
okay now I have made boot recovery for windows running ```
bootrec 
``` command. Now windows os loads but Linux grub is gone and therefore I cant access mint. What to do please help

---

### Post by yancek on 2015-07-29
Post responses to the questions asked above by oldfred, particularly useful will be posting the output from the boot repair script after selecting the option to Create BootInfo Summary.  When you use it, do not try to make any repairs.

---


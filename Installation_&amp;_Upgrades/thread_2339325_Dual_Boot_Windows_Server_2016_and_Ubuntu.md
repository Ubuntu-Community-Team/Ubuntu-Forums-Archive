---
title: "Dual Boot Windows Server 2016 and Ubuntu"
date: 2016-10-07
forum: Installation &amp; Upgrades
---

### Post by devik on 2016-10-07
Hello,

I am trying to setup a dual boot system with Windows Server 2016 and Ubuntu 16.04.1

Already installed Server 2016 and reserved disk space while installing the OS

However when I run the Ubuntu setup I dont get the option to install Ubuntu alongside Windows Server

The options available are

- Erase disk and install Ubuntu

- Encrypt the new Ubuntu installation for security

- Use LVM with the new Ubuntu installation 

and 

- Something else

Any suggestions on how to solve this problem?

Many thanks

---

### Post by QIII on 2016-10-07
Hello!

The good news is that you have no problem.  "Something else" is what you want.

The bad news is that sometimes it takes a few tries to get it right -- which sometimes means some foul language while you re-install Windows.

Do you intend to use Windows Server as an actual always-available server, or do you plan to shut it down periodically and boot to Linux?

---

### Post by yancek on 2016-10-07
If you have resized (shrunk) the windows partition, you should run chkdsk from windows before trying to install Ubuntu in the unallocated, unformatted space and using the manual Something Else option.  You also need to verify whether your windows is using UEFI or MBR and install Ubuntu the same.  UEFI dual boot is explained at the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by devik on 2016-10-08
I intend to shut it down periodically and boot to Linux, need it to work on SQL server and Visual Studio.

Ill reinstall again then :) 

thanks


> **QIII said:**
> Hello!

The good news is that you have no problem.  "Something else" is what you want.

The bad news is that sometimes it takes a few tries to get it right -- which sometimes means some foul language while you re-install Windows.

Do you intend to use Windows Server as an actual always-available server, or do you plan to shut it down periodically and boot to Linux?

---

### Post by devik on 2016-10-08
I allocated some space while installing windows. Is it still necessary to run chkdsk? Ubuntu was in UEFI, not sure but I believe Windows was in UEFI too

When using something else, should I just allocated Ubuntu to the free space?

Thanks

> **yancek said:**
> If you have resized (shrunk) the windows partition, you should run chkdsk from windows before trying to install Ubuntu in the unallocated, unformatted space and using the manual Something Else option.  You also need to verify whether your windows is using UEFI or MBR and install Ubuntu the same.  UEFI dual boot is explained at the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by yancek on 2016-10-08
If you have free space which is outside any windows partitions, that is what you should use.  You need to format the partition during the install because a default windows system is not capable of doing that.  If you resized a windows partition, it is always a good idea to run chkdsk.

I would expect your windows server to be UEFI.  I don't use windows but there should be some way to verify that.  As explained at the link I posted earlier, if windows is UEFI then UBuntu must also be UEFI so you need to find that out.

---

### Post by devik on 2016-10-09
Could not install Ubuntu in the something else

So I went back and installed Win Server again and again tried to dual boot with Ubuntu....no sucess

So......went back to basics tried to create a Win Server USB forcing GPT so that it would work with UEFI, 

used Rufux, 

Windows7-USB-DVD-Download-Tool-Installer,

Command Line using diskpart with the following commands

1- list disk

2- select disk

3- clean

4- convert gpt

5- cre par pri

6- format quick fs=fat32

7- list volume

8- exit 

9- xcopy a:\* b:\ /s /e
No sucess :(

So....im still looking for ways to make it work

Meanwhile since the USB with Win Server doesnt even boot :confused:  I have installed Ubuntu on its own, while I look for solutions for my problem


Thanks for all the help provided

p.s. sorry for the cmd stuff, i know its a ubuntu forum and not a windows one, was just listing the steps

---

### Post by devik on 2016-10-09
On another note does the command

sudo apt-get install exfat-utils exfat-fuse

adds the capability to read a USB formated in ExFAT?

---


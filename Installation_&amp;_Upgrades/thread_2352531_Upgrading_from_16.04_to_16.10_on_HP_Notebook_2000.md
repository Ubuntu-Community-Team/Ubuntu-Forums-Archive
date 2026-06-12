---
title: "Upgrading from 16.04 to 16.10 on HP Notebook 2000"
date: 2017-02-13
forum: Installation &amp; Upgrades
---

### Post by Todd_Chilson on 2017-02-13
[COLOR=#111111][FONT=Ubuntu]Tried to upgrade from Ubuntu 16.04 to 16.10 on a HP Notebook 2000. The upgrade went very badly. I could login, but I received a completely black screen with a message saying internal error. I downloaded a copy of 16.10 and am trying to repair or salvage the laptop. However, when I try to install over my old version and save my data, I get a message saying there is no /boot partition. Yet there is an option to Go Back which will allow me to edit my partitions, and there I clearly see /sda1 listed as /boot and /efi. I cannot complete the install without the /boot partition being recognized. Any suggestions of what to do next?[/FONT][/COLOR]

---

### Post by ajgreeny on 2017-02-13
It can not be both /boot and /EFI; it must be one or the other, though if /EFI it must have the boot flag..

Did you choose "Something Else" at partitioning stage of your reinstallation, which is the only sensible way to proceed with what you are wanting to do?

---

### Post by Todd_Chilson on 2017-02-13
Actually before there was an option to reinstall which is what I choose. Now that I tried it again, there is no operating system detected. So in fact the "sensible" option as you put it was to choose reinstall not "something else". At this time; however, "something else" is my only option for what I am trying to do.
Now the problem when I choose the "something else" option is that there is no / directory supposedly, and I cannot create it without destroying the old partitions.
Ubuntu has always been free and more importantly Linux in general has always been more of a learning tool than anything. I am pretty upset at the loss of data. But in hindsight, Ubuntu has been stable for years now. In fact, it has been so stable for so long that I never even considered backing up before the upgrade as I have been upgrading for many many versions now. 
I fear my only real option is a wipe which is really as I said before hurt and upset me. However, I am not leaving Ubuntu. I have had a lot of good years with Ubuntu and have a feeling there will be many more to come.

---

### Post by ajgreeny on 2017-02-13
Before you start doing anything else to reinstall the OS, try to backup any of your personal files and folders on to an external disk using a live USB/DVD system.

I am sorry that you have had this problem, but do not be dismayed just yet; there may still be some or even most of your data left on disk.
From the live system run command ```
sudo parted -l
``` and show us the output.
Please use **Code-Tags** for the terminal output. See my signature below for a **How-to**

---

### Post by Todd_Chilson on 2017-02-13
Too late. And there was no way to get to a command prompt anyway. I spent two days fiddling with it before I wrote, so I was really at the point of acceptance. Thank you for trying though. I appreciate your time and input.

---


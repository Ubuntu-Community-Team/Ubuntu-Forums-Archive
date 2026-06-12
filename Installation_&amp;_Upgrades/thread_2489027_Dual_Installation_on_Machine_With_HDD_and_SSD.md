---
title: "Dual Installation on Machine With HDD and SSD"
date: 2023-07-15
forum: Installation &amp; Upgrades
---

### Post by cobras on 2023-07-15
Greetings Folks,

Just purchased a Dell Precision 7510 i7 with Windows 10 pre-installed.  I would like to install Ubuntu 22.04 alongside Windows, but I just don't know how to do this properly on this machine because it has a 256GB SSD and 1TB HDD.

I actually began the process but when it came to determining the partitions I figured I should get some education before proceeding.

Thank you for any suggestions you can offer.

---

### Post by tea for one on 2023-07-15
Two disks = two options.

Windows 10 and Ubuntu on one disk?
Windows 10 and Ubuntu on separate disks?

---

### Post by cobras on 2023-07-15
This seems to make sense, but I think there's more to it.

I may be wrong, but I think the SSD is faster, so this is where the OS should  boot from. The HDD might best be used for long term storage.  However, is 256GB enough for both Windows and Ubuntu?  Also, if mount both OSs on the SSD, will both have access to the HDD?

Besides this, when presented with the option of assigning partitions it wasn't clearr to me which part was SSD and which was HDD.

---

### Post by guiverc on 2023-07-15
What you do is up to you, and your plans for the system.

I purchased this machine earlier this year (*my old PC's PSU died thus was forced to*), its a *refurbished* machine that came with windows 11. It came with a 256GB ssd.

I wanted my machine dual-boot, my wanted OSes being Ubuntu LTS & Ubuntu *development*; I didn't care if windows 11 survived actually as I won't use it.

As I didn't care about windows 11 and it had no data; I just booted it & explore and worked out how much disk space I felt it required, added a little then decided what size I felt I could shrink the partition too. This gave me how much of the SSD space I was willing to partition for my wanted Ubuntu systems.

My considerations were

- into the future, was I going to switch to a different GNU/Linux, as whilst Ubuntu can safely re-install a desktop system into a single partition non-destructively, other GNU/Linux distros cannot.  My default is to create a separate data partition for /home (my data) to allow for this. I have no plans of switching away from Ubuntu, thus this wasn't a must for me.

- did I want a swap partition; so the space can be shared between my two intended Ubuntu OSes.. There are *pros* & *cons* with this & other considerations too (*will I hibernate, as if one is using it to hibernate the other will destroy that hibernate** if booted*).

- what size I wanted to allocate to each, my default is half each, then subtract 1 from one & give it to the other so they're not identical sizes (*another clue being size in determining which is which*).

In the end I didn't create a separate home, as I used the machine for QA-testing of a Lubuntu 23.04 install (where I let it shrink the partition creating space using the *install alongside* option & that testcase didn't allow me to set swap partition or create separate /home as it uses a basic setup. 

I'm on the Lubuntu team, which is why I used my *new* system for QA-test installs, but it'd have been the same if using Ubuntu Desktop, Xubuntu or any other *flavor*.  After I'd ensured the install was good, I then inserted the Lubuntu 22.04 *daily* ISO & did another install shrinking the new 23.04 partition to give me a third OS. Again my decision was purely following the install *QA testcase*, all of which used easy options of the installer, the result being this box now has

- Windows 11 (*booted twice; once after each install to confirm it survived after each install & ignored since*)
- Ubuntu 22.04 LTS ([I]I installed using Lubuntu media as I'm in that team, but its now a Lubuntu/Xubuntu/Ubuntu desktop install, I select at login which desktop I'll use)
- [/I]Ubuntu *mantic* (*the 23.04 wasn't yet released when I did the install; I sit this install on development so the lunar was bumped to mantic on lunar's switch to 23.04 & a released product*)

Had my installs failed, I would have started fresh, and had the following 

- ESP as required by uEFI hardware I'm using to boot
- / partition for Ubuntu LTS
- /home partition for Ubuntu LTS
- / partition for Ubuntu *development*
- /home partition for Ubuntu [I]development
- [/I]swap partition.. 

My last box included those partitions; all partitions being different sizes so I could easily *map on envelope* which was which based purely on size (*details in tools we don't use such as installers can show detail different to the tools we always use, so I don't just want partition names, but also sizes etc as another check*).

Additional note:  The windows ESP partition was I felt too small (*it was fine for a windows only install, but I wanted dual boot thus needed larger!*) so I ensured it wasn't used and a new ESP was created during first Ubuntu/Lubuntu install; the subsequent Ubuntu/Lubuntu install just re-used the ESP created by first Ubuntu install.

This box is a desktop system, I trust my *physical security* thus didn't consider *encryption* (*it complicates things*).  My last box (*what this replaced*) did have encryption, but only as I wanted more experience dealing with it, if this was a laptop however which would leave this location/address - I'd have used encryption. There are many types of encryption & this with dual boot added complexity.

FYI:  I consider Lubuntu a Ubuntu system, and other than Lubuntu using the `calamares` installer, my install would have been identical if I'd used Ubuntu Desktop media using `ubuntu-desktop-installer` OR Ubuntu Desktop media using `ubiquity` installer, likewise the same if I used Xubuntu using `ubiquity` etc.. My older primary box had the ~same setup except I did use Ubuntu Desktop media for that box (*I hadn't yet joined the Lubuntu team back then*)

Summary:  Consider the future; as that's what will dictate what's best for you. Otherwise keep it simple!

---

### Post by yancek on 2023-07-16
I have windows 10 and 2 Linux systems on a 256 GB SSD.  You should set your / (root filesystem partition) at about 30 GB for Ubuntu.  You can create a 2nd partition for your /home partition directory, either on the SSD or the HD.  The size will depend upon how much additional software you install and how much data you have.  You could create a shared ntfs filesystem partition on the HD to share data files between windows and Linux   You should use an ntfs filesysem as windows and Linux can read/write to ntfs while windows cannot access a Linux filesystem, by design of microsoft.  An SSD will show partitions similar to: /dev/nvme0n1p1  The HD will show something like /dev/sda1  The numbers at the end of each entry are the partition numbers.  You might try an online search for "Linux drive naming conventions" to get more detail.

Another thing you should do, since windows is already installed is to us the windows Disk Management tool to shrink the largest windows partition to create unallocated space for Ubuntu.  Best to do this from windows and when it is finished, you should reboot windows and run chkdsk to make certain there are no problems with the resizing of windows.  Then reboot and select the Ubuntu USB drive from the BIOS boot options and make certain you select the UEFI options if you have more than one option and begin the install.

There are many tutorials on installing Ubuntu so go online and find one you understand.  You should use the Something Else (manual) option so you can control the install.  The install alongside will probably work also.

An SSD will be much faster.  I have 2 laptops with similar hardware but one has a SATA drive and the other an SSD.  Both laptops have the same 3 operating systems and the SSD boots about 4 times faster for each of them.

---

### Post by cobras on 2023-07-16
Thanks guiverc for your detailed and thoughtful response.

---

### Post by cobras on 2023-07-16
That's what I was hoping for yancek!  Thank you.

I should have mentioned earlier that I won't be using Windows at all except for the rare exception when Ubuntu won't work (we do still live in a Windows universe), and your suggestions would allow me to configure the drives accordingly.

Unfortunately, last night I became impatient and opted for Install Alongside rather than Something Else.  It worked fine, but your method would have been better.  Next time I'll know better.

---


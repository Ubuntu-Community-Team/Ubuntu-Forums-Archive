---
title: "How to Add New Boot Option"
date: 2012-09-02
forum: Installation &amp; Upgrades
---

### Post by todd2000 on 2012-09-02
I have installed Ubuntu 12.04.1 on a Asus G75 Laptop, but I can't get it to boot. All the other Bios that I have used had a boot from hard drive option, this one does not. The Bios has the Aptio Setup Utility using UEFI and has "Boot Option Priorties". The boot options available right now are "Windows Boot Manager" and “P2: HL-DT-ST DVDRAM GT51M” listed on the Boot tab.

I go to "Add New Boot Option" to add a new EFI boot option to the boot order and hit enter. 4 items are listed:

Add boot option
Select Filesystem    [PCI(1F|2)\DevicePa...]
Path for boot option
Create

I think I need "Path for boot option". When that is selected it says Enter the path to the boot option in the format fs0:\path\filename.efi

Is this the correct selection I should make, and if so what is the path I should enter.

Any help would be appreciated as this has been driving me up the wall.

---

### Post by oldfred on 2012-09-04
When you booted the Ubuntu 6+4 bit installer, it should have given two choices, one UEFI/EFI and the other BIOS/legacy/AHCI or whatever it calls it. Which ever way you boot installer is how it installs. So if you install Ubuntu in BIOS mode and have Windows in efi mode you need to fix Ubuntu to have an efi entry. Boot repair can do that if Windows is in efi mode. If not just post link to BootInfo report.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by todd2000 on 2012-09-15
> **oldfred said:**
> When you booted the Ubuntu 6+4 bit installer,

Looks, like I will have to re-install using the 64-bit version. Why is the 32-bit version recommended on the website? Is the 64-bit version stable? I see from a web search that "desktop-amd64.iso" is compatable with intel.

---

### Post by Bashing-om on 2012-09-15
UEFI ????

see these links
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[http://ubuntuforums.org/showthread.php?t=1974392 <-Dual booting UEFI](http://ubuntuforums.org/showthread.php?t=1974392 <-Dual booting UEFI)
[INDENT][INDENT]hth in a small way <==BDQ
[/INDENT][/INDENT]

---

### Post by YannBuntu on 2012-09-16
Hello

> **todd2000 said:**
> Looks, like I will have to re-install using the 64-bit version.

Yes. Please follow the 1st paragraph of [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> **todd2000 said:**
> Why is the 32-bit version recommended on the website?

Because it is compatible with old computers (which are not compatible with Ubuntu64bit), and recent computers ([except EFI ones]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555")).
But since 2011 more and more recent computers are EFI, so we should ask Canonical to recommend Ubuntu-64bit for recent computers.

> **todd2000 said:**
> Is the 64-bit version stable?

Yes, no problem.

> **todd2000 said:**
> I see from a web search that "desktop-amd64.iso" is compatible with intel.

Indeed it is compatible with all 64bit computers, not only Intel ones.

---

### Post by todd2000 on 2012-09-18
Problem is now solved, here is a summery of steps taken.

1. First tried the sugguestion in post #2 to install and run boot-repair.  Ran the boot-repair utility which bombed. I can't remember the the actual error. 

2. Since I was running the 32-bit version I downloaded the 64-bit version as sugguested in posts #'s 2,4 and 5.

3. During the installation of the 64-bit version I never saw an option between EFI/EFI and BIOS/legacy/AHCI as sugguested in post #2.

4. After installation still had the problem in the orginal post.

5. Installed boot-repair again and this time it ran. I first ran the bootinfo summary to get a snapshot at where I was. The results are at 

[http://paste.ubuntu.com/1213644/]("http://paste.ubuntu.com/1213644/")

6. Next ran the boot-repair to fix the problem and it instructed the following:

```
sudo apt-get install -fy
sudo dpkg --configure -a
sudo apt-get purge -y --force-yes grub-common
```

gui window opened up for me to confirm changes then entered:

```
sudo apt-get install -y --force-yes grub-efi
```

7. Ran bootinfo summary again.

[http://paste.ubuntu.com/1213665/]("http://paste.ubuntu.com/1213665/")

8. Restarted, used F2 to get into "bios" and Ubunutu now shows up as an option. Set boot priorty for Ubuntu and it booted up without problems.

Thanks to everyone who replied. The help is greatly appreciated.

---

### Post by YannBuntu on 2012-09-18
Good job :)
You can mark yourself as "affected" by bug [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1050940](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1050940)

---


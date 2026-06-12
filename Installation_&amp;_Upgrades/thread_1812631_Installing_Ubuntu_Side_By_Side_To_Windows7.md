---
title: "Installing Ubuntu Side By Side To Windows7"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by jadellah177 on 2011-07-26
hii , so i'm downloading the 10.04 Version of Ubuntu 

name: ubuntu-11.04-desktop-i386.iso

-i was wondering if i can install it Side By Side To win7 and How?

-And Can i Burn The ISO Copy of 685MB to a CD-R then install it?

PS: i don't have a USB Flash drive


My Laptop Specs:

-intel core 2 duo
-3GB Ram DDR3
-250GB HDD (50gb for ubuntu and 200 for windows)
-intel graphics up to 1024mb
-16:9 1366x768 HD 1080P LCD Monitor

---

### Post by Quackers on 2011-07-26
Welcome to UF :-)
If you are downloading "ubuntu-11.04-desktop-i386.iso" then you are downloading 11.04, not 10.04 :-)
Yes you can burn the iso to disc but you must choose "burn image" and not normal data settings.
Whether you can install it side by side with Windows depends on how many partitions Windows is currently using and also on whether there is any unallocated space on your hard drive for Ubuntu to install into (free space within partitions is not usable).

---

### Post by jadellah177 on 2011-07-26
Sorry i meant 11.04 and i know how to burn ISO to CD's


and about the Partitioning , my Hard drive have never partitioned ! so when i begin the installation how much u recommand to choose for the Obuntu Partioon


2nd: when i want to Unistall Ubuntu later !! and give the ubuntu partion back to windows, how may i do that?

---

### Post by Quackers on 2011-07-26
So is the hard drive empty at the moment?
If you intend to install Windows you should install that first.
You can then decide how much space to give to Ubuntu and how to go about that. It depends on the version of Windows and how many partitions it uses by default.

---

### Post by jadellah177 on 2011-07-26
I Have Windows7 32-bits and it Requires 16 GB available hard disk space (32-bit) 

so? my hard drive have 223GB and im plaining to give 

Windows => 200GB
Ubuntu => 23GB 

so?

---

### Post by Quackers on 2011-07-26
Do you intend to install Windows 7 from an installation disc or a recovery disc? It will still be necessary to install it first and then see how many partitions it has used. Windows 7 can use anything from 1 to 4 partitions by default, and as 4 is the maximum number of primary partitions on any mbr partitioned disc it has a big say in what happens after.

---

### Post by jadellah177 on 2011-07-26
i'm telling you , i have Windows7 and 155GB free Space !!!


now i've changed my mind ! im giving Ubuntu 17GB from the disk drive

is that good?

---

### Post by Quackers on 2011-07-26
Then if Windows is installed already, your disc has been partitioned!
If you look in Windows Disk Management screen you can find out how many partitions Windows is currently using. If Windows is using 3 or less primary partitions you can install Ubuntu using the "install alongside" option.
If Windows is currently using 4 primary partitions don't try to install anything.

---

### Post by jadellah177 on 2011-07-26
how about installing it INSIDE WINDOWS , and give it 17GB

Will i be able to choose the OS from Boot Loader?

Will i be Able to unistall it from Windows7 Control Panel ?

---

### Post by jadellah177 on 2011-07-26
Yeah, i've Founded 

9.77 GO for repairing or whatever
(C) 223.12Go NTFS for WIndows7

---

### Post by Quackers on 2011-07-26
Ah, so no unallocated space then.

If you use the wubi installer from inside Windows then you will be able to uninstall Ubuntu from the control panel, as I understand it, yes.

---


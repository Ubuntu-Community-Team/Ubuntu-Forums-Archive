---
title: "installed but won't boot"
date: 2021-06-07
forum: Installation &amp; Upgrades
---

### Post by brooksmm on 2021-06-07
I installed ubuntu from a USB onto the second drive of a computer that currently runs windows 7. The installation seemed successful, but I can't boot into linux; I've reinstalled and tried changing the boot loader locations, I've run boot repair, and I've changed the legacy/UEFI options, but it still gives me the "no boot filename received" error message. 

Most recently, I ran boot-repair and followed its instructions to purge and reinstall GRUB--now when I attempt to boot into linux I get the same error message but it also goes into GRUB rescue mode (where the only disk it seems to recognize is the hard drive, which is inaccessible and does not have linux on it). 

Here are the pastebins from the last two times I've run boot-repair:
(most recent) [http://paste.ubuntu.com/p/Rs2WH6y53C/](http://paste.ubuntu.com/p/Rs2WH6y53C/) 

(time before that^) [http://paste.ubuntu.com/p/CR9XgpXphQ/](http://paste.ubuntu.com/p/CR9XgpXphQ/)

I've never dual booted or even installed linux on a computer before and I've been wrestling with this for the past few days, any help will be greatly appreciated. Thank you.

Edit: here's another pastebin from the most recent BootInfo summary
[http://paste.ubuntu.com/p/dDqwQrPbKQ/](http://paste.ubuntu.com/p/dDqwQrPbKQ/)

Edit 2: I hadn't tried to boot up windows after purging and reinstalling GRUB via the boot-repair and now that I ma trying, it won't boot into widows either; only thing that comes up are a couple error messages (no such device, unknown filesystem) and rescue mode.

Update (Edit 3): the issues detailed here have been solved (thank you all), but other problems are still preventing linux from booting and it seems they may be impossible to fix without getting newer hardware. the two options my prof and I are now leaning towards are 1) wiping this comp and just updating widows and running linux through a windows subshell, or building a new computer since this is the oldest work station in the lab anyway. So the problem wasn't fixed, per se, but based on how each time I fixed a problem to do with dual booting another problem popped up that took me a bunch of time and sanity to solve I'm thinking that continuing to work on this is no longer worth the time in comparison to other possible solutions, rip

---

### Post by ubfan1 on 2021-06-07
Your Win7 is installed in legacy mode, so the usual recommendation is to install Ubuntu in legacy mode too.  How the installer media boots determines how the install is made, and your machine settings control that, so check your BIOS/UEFI settings and set it so legacy is enabled (first if both are possible). Compatibility mode (CSM is another way to say "legacy", each firmware is different.  The next issue is can your machine (you didn't say what model it is) boot a gpt partitioned disk -- some cannot.  
  It looks like you have set up your second disk with gpt, and have all the partitions needed for booting in either UEFI or legacy, but if you can only boot mdsos partitioned disks, you should just redo that back to the partitioning, and select msdos instead of gpt.

---

### Post by tea for one on 2021-06-07
Windows 7 in Legacy mode and Ubuntu in UEFI mode will give you constant problems.
Windows 7 is now unsupported and you should be using Windows 10.

I would start from scratch and install Windows 10 and Ubuntu in UEFI mode with GPT.
Each OS on a separate disk is ideal.

Further info [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Have you backed up all your data?

---

### Post by brooksmm on 2021-06-07
> **ubfan1 said:**
> if you can only boot mdsos partitioned disks, you should just redo that back to the partitioning, and select msdos instead of gpt.

First off, thank you so much. But also where in the process do I need to select msdos instead of GPT? during installation?

---

### Post by yancek on 2021-06-07
> But also where in the process do I need to select msdos instead of GPT? during installation? 				 

You can use the GParted Partition Manager which is on the Ubuntu Live/Install USB.  Open a terminal by simultaneously holding down the Ctrl+Alt+t keys and when the terminal opens, type:  sudo gparted   There is no password.  In the GParted window, on the extreme upper right click the down arrow and select the correct drive then click on the Device tab at the top of the GParted window and select Create Partition table.  This will delete anything on that drive so make sure you get the correct one.

---


---
title: "Dual Boot: Vista and Ubuntu (Vista overwrite MBR, Grub fails)"
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by jorgerosa on 2008-02-12
Dual Boot: Vista and Ubuntu in same PC. Ok, here goes:

I have instaled first Windows Vista Ultimate and then Ubuntu 7.10 in my PC.
All works fine... until i shutdown PC from Vista OS.

**Vista overwrites MBR  (Master Boot Record) on shutdown**, so, when PC starts again, Grub fails to display the dual boot menu.
(in my case, my PC starts in an endless start/restart loop).

**Solution?** I run Ubuntu Live CD, then in terminal, i do this: [here]("http://ubuntuforums.org/showthread.php?t=224351") and all goes Ok again! (Until i start Windows and shutdown PC again from this OS)
**Solution?** I force shutdown PC using the power button!  So, Windows has no time to mess around! :evil::evil::evil:

So, i have to follow above steps for the rest of my life, or there is a way to keep that Grub (MBR) untouchable? or any other better solution, please? Thanks!

---

### Post by rolandus on 2008-02-12
You might want to try using the Vista bootloader instead of grub. That way, Vista will play nice with it. There is a free program called EasyBCD that installs into Vista and can be used to add a second (Linux) entry to the Vista bootloader. 

I got this to work (mostly), and there are several resources I found by googling that guide you through it. 

Basically, I would start by installing EasyBCD and adding a second boot entry. Then the next time you boot the computer, you should see a microsoft-ish looking list with the two options on it (Vista and Linux). Try choosing the linux one and see if it works. If so, great! Otherwise, you might have to slightly tweak Ubuntu, but it's doable.

---

### Post by jorgerosa on 2008-02-12
**Thanks rolandus!**
But it fails :( (im sure ive donne all in the right way, i followed tutorials in the web) - The PC starts in that loop again (start/restart)....
Meanwhile, im loving my power-off button ;)

---

### Post by rolandus on 2008-02-12
Hmmm. Too bad. 

Does the Vista boot screen at least appear with the choices? I mean, does it enter the infinite reboot cycle only when you choose the "Linux" option?

If so, try the following:

1) Boot into Linux and Install GRUB to the boot partition (the partition of the HDD that Linux boots from). The default place to install it (as you have discovered) is the MBR of the HDD. To install to the boot partition, you need to run GRUB with root permission:

$ sudo grub

The grub prompt should appear:

grub>

Use the "find" command to figure out the numbers that GRUB has assigned to your boot partition:

grub> find /boot/grub/stage1

Use the "root" command to tell GRUB to treat this partition as the root

grub> root (hd0,1)  // replace (hd0,1) with whatever was returned by the "find" command

Tell GRUB to install to the boot partition:

grub> setup (hd0,1) // replace (hd0,1) with whatever was returned by the "find" command

Exit grub:

grub> exit

2) Now, reboot into Vista and run the EasyBCD program again. This time, when you create a new entry for Linux, check the little box near the bottom that says something like "GRUB is not installed to the MBR". 

3) Reboot and try it out.

I hope this fixes it. However, it is weird that your machine just reboots without at least giving some kind of error message....

---

### Post by Pumalite on 2008-02-12
How did you partition? If you used Ubuntu Live CD, there is your problem. Vista requires that you allocate space for Ubuntu from WITHIN Vista first, then install Ubuntu; otherwise Vista will not let you run anything in that computer.

---

### Post by jorgerosa on 2008-02-13
**Thanks, rolandus **:) - That were the steps i did first. But after shutdown from Vista, (overwrites the MBR and... here i go again to that loop).

**Pumalite:** "Vista requires that you allocate space for Ubuntu from WITHIN Vista first" - hmmmm...
I have insteled Vista first and 50% HD was formatted in NTFS and the other 50% was unallocated space (not formated at all). Them i instaled Ubuntu (from Live CD) in that unallocated space. This shows **[COLOR=Black]exactly[/COLOR]** how i have installed Dual Boot:  [How To Install Dual Boot]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first") (And all runs GREAT, the only problem is that Windows overwrite that MBR file on shutdown, btw, can i hide or move or protect that file in any way?)

---

### Post by sanjeevan on 2008-02-13
hmm, I have the same problem. It works fine if I practically don't do anything in vista. If I just turn on, go there, and reboot, nothing takes place. If I spend more than like 5 minutes, it over-writes it. Stupid vista. Yeah I made a ntsf partition using vista's shrink,create new volume methods.

---

### Post by zami on 2008-03-29
I'm having this problem as well.

I followed this tutorial
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
And I DO now see a menu when I reboot, offering

Vista
Ubuntu

Vista loads just fine.
Ubuntu loads the GRUB menu, which then loads nothing and requires a reboot

I could cry.  I've been at this for hours.  I can SEE all my files still in place but I'm just stuck in Windows.

-zami

---

### Post by inteja on 2008-03-29
Same problems here too.

On first try I was getting the infinite loop problem already reported. My Toshiba notebook had a few extra, factory setup primary partitions for recovery purposes, so (after making a recovery DVD) I started from scratch and repartitioned with one NTFS for Vista, another NTFS for shared data and the remainder unallocated for Ubuntu.

Vista and Ubuntu installed just fine but after any Vista shutdown the grub menu is wiped out and all I get is a flashing cursor on a black screen.

Currently I'm using the [Super Grub Disk]("http://supergrub.forjamari.linex.org/") to restore the grub menu and boot into my desired OS but this is far from ideal.

Any permanent solution would be much appreciated.

---

### Post by inteja on 2008-03-29
> **rolandus said:**
> 2) Now, reboot into Vista and run the EasyBCD program again. This time, when you create a new entry for Linux, check the little box near the bottom that says something like "GRUB is not installed to the MBR".

I just tried this and for me the key step was checking "GRUB is not installed to the MBR". The first time I tried, forgetting to check this option, and I couldn't boot into Ubuntu. After checking the option it worked.

Thanks rolandus!

---

### Post by inteja on 2008-03-30
Oops, I spoke too soon. After the latest reboot the Windows boot menu created by EasyBCD has been wiped out. I used Super Grub Disk to restore grub menu and boot into Vista.

So, I'm still looking for a permanent solution :(

---

### Post by inteja on 2008-03-30
This Microsoft knowledge base article might be just as applicable to dual-boot Ubuntu / Vista:
[Windows Vista no longer starts after you install an earlier version of the Windows operating system in a dual-boot configuration]("http://support.microsoft.com/kb/919529/en-us")

---

### Post by adrian15 on 2008-03-31
Hello, 

            I have developed a new option for Super Grub Disk.
Windows chainloads Grub!
which works even if you have Linux in a second hard disk (Usually if you have Linux in a second hard disk you cannot chainload it from Vista).

Ideal tester is the following one:

1st hard disk: Windows only
2nd hard disk: Linux

What you should do? Try to chainload Grub from Windows menu (either boot.ini or either the Vista one).

If you read normal instructions about root and setup command Grub is not installed correctly and linux.bin is not useful.

If you read [Windows chainload Grub Howto instructions]("http://www.supergrubdisk.org/wiki/Howto_Boot_Grub_from_windows#Classical_solution") it should work.

So please first recover Windows boot with ** Super Grub Disk (With Help) -> Windows -> Fix of Boot Windows** and then read the [Windows chainload Grub Howto instructions]("http://www.supergrubdisk.org/wiki/Howto_Boot_Grub_from_windows#Classical_solution").


adrian15

---

### Post by alsoknownas on 2008-03-31
In my experience you need to re-install grub to to MBR. This is how I've set my system up and it works for me :p

Open up a terminal in Linux (use a live CD if you cannot access the one on your hard drive) and type:
```
sudo grub
find /boot/grub/stage1
```
You should see something like this [screenshot](http://apc.simbient.com.au/system/files/images/ubuntu_vista_07.jpg)
Now here it should display where on your system you have linux installed "(hd0,1) or something similar.
```
root (hd?,?) *<wherever grub just told you ubuntu was installed*
```
Then type:
```
setup (hd0)
```
This installs grub to the MBR and overwrites Vista's bootloader. I have booted into Vista many times and it hasn't messed with this.

To add Vista to your GRUB options see here: [http://www.newlinuxuser.com/adding-other-operating-systems-to-grub/]("http://www.newlinuxuser.com/adding-other-operating-systems-to-grub/")

---

### Post by Dilligaf on 2008-03-31
Install grub to your linux partitions boot sector, not your MBR. Restore your vista boot loader by booting Vista cd and going to repair options. Install EasyBCD and add a linux entry pointing to your linux partition. This should make everything boot, I'm quad booting Vista, Ubuntu 7.10, Kubuntu, Ubuntu 8.04 using EasyBCD with no problems. If there are any problems ask in the EasyBCD forum, they're almost as helpful as these forums.

Mike

---

### Post by dstew on 2008-03-31
I am curious about the system of the original poster, Jorgerosa. It sounds like his PC has some "feature" that causes the MBR to be overwritten if it has anything other than the Vista bootloader in it. Jorge, if you are still out there, what is your hardware? Thanks.

---


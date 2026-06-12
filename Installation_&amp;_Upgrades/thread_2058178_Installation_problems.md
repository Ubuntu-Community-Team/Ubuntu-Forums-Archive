---
title: "Installation problems"
date: 2012-09-15
forum: Installation &amp; Upgrades
---

### Post by Rogoshin on 2012-09-15
I have just purchased an Acer Predator G 3610, and will in this respect install Ubuntu 12.04 on. However, I have run into some problems.

When I insert the installation disk, in comes a kind of dos screen with three options, not the normal Ubuntu installation screen. The three options are try Ubuntu, install Ubuntu, or check the disk for errors. I then selected Install, resulting in the computer is running in about ten minutes, and does so to a halt. I have let it stand for two hours, but nothing happens. If anyone has any information that can help me, I will be very grateful.

Computer Info.

Intel Core i5 processor 2320
6 GB DDR3 memory
NVIDIA GeForce GTX550Ti graphics card

---

### Post by Quackers on 2012-09-15
Welcome to UF :-)
You could be having a video problem. Try booting with the nomodeset boot option, as described in this thread

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Rogoshin on 2012-09-16
> **Quackers said:**
> Welcome to UF :-)
You could be having a video problem. Try booting with the nomodeset boot option, as described in this thread

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Well my problem is i do not even get the  bios splash screen. I get a different one where there is only the three options i mentioned. 

In the article he mentions 

  acpi_osi=
  acpi_osi="Linux"
  acpi_osi="Windows 2006"

I don't know what this is really. Is this something he gets from the prompt?

I neglected to mention that right before the splash screen i get this message "Prefix not set".

---

### Post by YannBuntu on 2012-09-17
Hi

> **Rogoshin said:**
> The three options are try Ubuntu, install Ubuntu, or check the disk for errors.

Is it the screen below? (if yes, your PC has an UEFI firmware)

[IMG]http://pix.toile-libre.org/upload/original/1347445084.png[/IMG]

Anyway, please indicate your [Boot-Info]("https://help.ubuntu.com/community/Boot-Info") URL, so that we know in which mode you need to install Ubuntu.

---

### Post by Rogoshin on 2012-09-17
> **YannBuntu said:**
> Hi



Is it the screen below? (if yes, your PC has an UEFI firmware)

[IMG]http://pix.toile-libre.org/upload/original/1347445084.png[/IMG]

Anyway, please indicate your [Boot-Info]("https://help.ubuntu.com/community/Boot-Info") URL, so that we know in which mode you need to install Ubuntu.

I tried to install from the alternative CD, but my computer just boots windows like bug 1050940. So I can't give you the BOOT info, if I understand this correct.

---

### Post by YannBuntu on 2012-09-17
1) When you boot on a liveCD (or liveUSB) of Ubuntu64bit or Ubuntu-Secure-64bit, NOT Alternate, do you see the above screen?

2) When you select "Try Ubuntu", does the Ubuntu desktop appear?

---

### Post by Rogoshin on 2012-09-17
> **YannBuntu said:**
> 1) When you boot on a liveCD (or liveUSB) of Ubuntu64bit or Ubuntu-Secure-64bit, NOT Alternate, do you see the above screen?

2) When you select "Try Ubuntu", does the Ubuntu desktop appear?

1. Yes i see the screen with the three options.

2. When i press try ubuntu, the screen just goes black. The disk is running for ten minutes, then it stop. The computer appears to do nothing. And the Ubuntu desktop does not appear.

---

### Post by YannBuntu on 2012-09-17
ok.
You may need to use the 'nomodeset' option.

Please:
1) boot on the liveCD (not Alternate)
2) when you see the above screen, press the 'c' key.
3) add the 'nomodeset' option (see [https://help.ubuntu.com/community/BootOptions#Changing_the_CD_Boot_Option_Configuration_Line](https://help.ubuntu.com/community/BootOptions#Changing_the_CD_Boot_Option_Configuration_Line) )
4) continue booting and tell me if the Ubuntu desktop appears
5) if yes, install Ubuntu, then use Boot-Repair -> Advanced options -> "GRUB options" tab -> tick the "Add a kernel option: nomodeset" option -> apply

---

### Post by Rogoshin on 2012-09-17
> **YannBuntu said:**
> ok.
You may need to use the 'nomodeset' option.

Please:
1) boot on the liveCD (not Alternate)
2) when you see the above screen, press the 'c' key.
3) add the 'nomodeset' option (see [https://help.ubuntu.com/community/BootOptions#Changing_the_CD_Boot_Option_Configuration_Line](https://help.ubuntu.com/community/BootOptions#Changing_the_CD_Boot_Option_Configuration_Line) )
4) continue booting and tell me if the Ubuntu desktop appears
5) if yes, install Ubuntu, then use Boot-Repair -> Advanced options -> "GRUB options" tab -> tick the "Add a kernel option: nomodeset" option -> apply

I am having trouble understanding the link. am i suppose to write initrd=/casper/initrd.lz quite splash -- vga=791. Because when i press c i only get a command line.

---

### Post by YannBuntu on 2012-09-17
Sorry I made a mistake. I think you need to press the 'e' key, not the 'c' one.

And: you don't need to write "initrd=/casper/initrd.lz quite splash -- vga=791", but only add 
```
nomodeset
```

---

### Post by Rogoshin on 2012-09-17
> **YannBuntu said:**
> Sorry I made a mistake. I think you need to press the 'e' key, not the 'c' one.

And: you don't need to write "initrd=/casper/initrd.lz quite splash -- vga=791", but only add 
```
nomodeset
```

I get a screen saying

setparams  ´try ubuntu whitout installing´

set gfxpayload=keep

linux /casper/vmlinux file=/cdrom/presseed/ubuntu.seed boot=casper quiet splash -- initrd /casper/initrd.12

Where am i suppose to add nomodeset?

---

### Post by YannBuntu on 2012-09-17
I would try this:

> linux /casper/vmlinux file=/cdrom/presseed/ubuntu.seed boot=casper quiet splash **nomodeset** -- initrd /casper/initrd.12

but this may also work:

> linux /casper/vmlinux file=/cdrom/presseed/ubuntu.seed boot=casper quiet splash -- initrd /casper/initrd.12 **nomodeset**

---

### Post by Rogoshin on 2012-09-17
> **YannBuntu said:**
> I would try this:



but this may also work:


I tried the first version and it worked, i now have installed Ubuntu. But am i suppose to boot right after, or edit the boot options before i boot. Because the system says that nothing will be saved for the next boot.

The info i got from bootrepair is the following

[http://paste.ubuntu.com/1210831/](http://paste.ubuntu.com/1210831/)

---

### Post by YannBuntu on 2012-09-17
Perfect :)

Then , you now just have to add the 'nomodeset' option to your installed Ubuntu:
1) run Boot-Repair --> Advanced options --> "GRUB options" tab --> tick the "Add a kernel option: nomodeset" --> Apply.
2) Reboot the PC without the CD

---

### Post by Rogoshin on 2012-09-17
> **YannBuntu said:**
> Perfect :)

Then , you now just have to add the 'nomodeset' option to your installed Ubuntu:
1) run Boot-Repair --> Advanced options --> "GRUB options" tab --> tick the "Add a kernel option: nomodeset" --> Apply.
2) Reboot the PC without the CD

I want to thank you for all the help, i now have Ubuntu 12.04 on my computer :guitar:

I just have some follow up questions now. When i want to install a new distro (Ubuntu 12.10), will i need to do the same then, or is this a permanent fix?

When i boot up now i get a new screen. It shows four options, one of them is to run ubuntu. It is no problem because Ubuntu boots shortly after. But is this something i should worry about?

---

### Post by YannBuntu on 2012-09-17
> **Rogoshin said:**
> i now have Ubuntu 12.04 on my computer :guitar:

good job :)

> **Rogoshin said:**
> When i boot up now i get a new screen. It shows four options, one of them is to run ubuntu. It is no problem because Ubuntu boots shortly after. But is this something i should worry about?

No, this is normal. This menu is called [GRUB]("https://help.ubuntu.com/community/Grub2"). It is the bootloader of Ubuntu. You can reduce its timeout by changing the value of "Unhide boot menu:10" in the Advanced options of Boot-Repair:
[IMG]http://pix.toile-libre.org/upload/img/1335263156.png[/IMG]

> **Rogoshin said:**
> I just have some follow up questions now. When i want to install a new distro (Ubuntu 12.10), will i need to do the same then, or is this a permanent fix?

- if you are new her, don't use 12.10 as it is still in development until November.
- when you will install 12.10 (in November), first check if you have the same problem or not. If the bug has not been fixed, you will probably need the same workaround.
- that's why you now need to create a bug report, so that devs can work on it. Here is how to create the bug report:

1) boot into your installed Ubuntu
2) [create your Launchpad account]("https://launchpad.net/+login") if you haven't yet
3) login to your account
4) open a terminal (Ctrl+Alt+T), then type the following command + press Enter:
```
ubuntu-bug linux
```
This will gather information.
5) Title of the bug: write "Nomodeset needed on Acer Predator G3610"
6) Description: "I need the nomodeset option in order to use Ubuntu 12.04 on my computer. Original thread on ubuntuforums: [http://ubuntuforums.org/showthread.php?t=2058178](http://ubuntuforums.org/showthread.php?t=2058178) "
7) Validate the report
8.) tell me the URL of the report so that I can follow-up

---

### Post by Rogoshin on 2012-09-18
> **YannBuntu said:**
> good job :)



No, this is normal. This menu is called [GRUB]("https://help.ubuntu.com/community/Grub2"). It is the bootloader of Ubuntu. You can reduce its timeout by changing the value of "Unhide boot menu:10" in the Advanced options of Boot-Repair:
[IMG]http://pix.toile-libre.org/upload/img/1335263156.png[/IMG]



- if you are new her, don't use 12.10 as it is still in development until November.
- when you will install 12.10 (in November), first check if you have the same problem or not. If the bug has not been fixed, you will probably need the same workaround.
- that's why you now need to create a bug report, so that devs can work on it. Here is how to create the bug report:

1) boot into your installed Ubuntu
2) [create your Launchpad account]("https://launchpad.net/+login") if you haven't yet
3) login to your account
4) open a terminal (Ctrl+Alt+T), then type the following command + press Enter:
```
ubuntu-bug linux
```
This will gather information.
5) Title of the bug: write "Nomodeset needed on Acer Predator G3610"
6) Description: "I need the nomodeset option in order to use Ubuntu 12.04 on my computer. Original thread on ubuntuforums: [http://ubuntuforums.org/showthread.php?t=2058178](http://ubuntuforums.org/showthread.php?t=2058178) "
7) Validate the report
8.) tell me the URL of the report so that I can follow-up

Well i did all the steps accept the last one. I cant seem to find the url:o

---

### Post by YannBuntu on 2012-09-18
Here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1052371](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1052371)

Thanks for having reported. Now let's wait the answer of kernel devs.
I'm pretty sure that they will ask you to test the very last version of kernel, so you can do it right now:

1) download the following 4 packages:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc6-quantal/linux-headers-3.6.0-030600rc6-generic_3.6.0-030600rc6.201209161835_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc6-quantal/linux-headers-3.6.0-030600rc6-generic_3.6.0-030600rc6.201209161835_amd64.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc6-quantal/linux-headers-3.6.0-030600rc6_3.6.0-030600rc6.201209161835_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc6-quantal/linux-headers-3.6.0-030600rc6_3.6.0-030600rc6.201209161835_all.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc6-quantal/linux-image-3.6.0-030600rc6-generic_3.6.0-030600rc6.201209161835_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc6-quantal/linux-image-3.6.0-030600rc6-generic_3.6.0-030600rc6.201209161835_amd64.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc6-quantal/linux-image-extra-3.6.0-030600rc6-generic_3.6.0-030600rc6.201209161835_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc6-quantal/linux-image-extra-3.6.0-030600rc6-generic_3.6.0-030600rc6.201209161835_amd64.deb)

2) install them (double-clicking on them, this will open the Software Manager, then click Install).
Remark: you may have to find the right order, as some packages need to be installed before other ones.

3) Reboot the PC. The GRUB menu will select the last kernel (v.3.6) by default. Check that it works (Ubuntu boots normally and is usable).

4) Now remove the nomodeset option by opening a terminal (Ctrl+Alt+T), and type:
```
gksudo gedit /etc/default/grub
```
Remove nomodeset from the GRUB_CMDLINE_LINUX_DEFAULT line.
Save the file.
Now type:
```
sudo update-grub
```

5) Reboot the PC. GRUB menu will appear like before. Choose the 1st entry (v3.6), and check if it works or not. (does Ubuntu boot normally and is usable?)
- If yes, then the bug has been solved in the v3.6 kernel. 
- If not, then it hasn't been solved yet, and your bug report will help the devs to fix it. And you will need to add the 'nomodeset' option again via Boot-Repair --> "Add a kernel option: nomodeset".

---

### Post by Rogoshin on 2012-09-18
> **YannBuntu said:**
> Here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1052371](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1052371)

Thanks for having reported. Now let's wait the answer of kernel devs.
I'm pretty sure that they will ask you to test the very last version of kernel, so you can do it right now:

1) download the following 4 packages:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc6-quantal/linux-headers-3.6.0-030600rc6-generic_3.6.0-030600rc6.201209161835_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc6-quantal/linux-headers-3.6.0-030600rc6-generic_3.6.0-030600rc6.201209161835_amd64.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc6-quantal/linux-headers-3.6.0-030600rc6_3.6.0-030600rc6.201209161835_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc6-quantal/linux-headers-3.6.0-030600rc6_3.6.0-030600rc6.201209161835_all.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc6-quantal/linux-image-3.6.0-030600rc6-generic_3.6.0-030600rc6.201209161835_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc6-quantal/linux-image-3.6.0-030600rc6-generic_3.6.0-030600rc6.201209161835_amd64.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc6-quantal/linux-image-extra-3.6.0-030600rc6-generic_3.6.0-030600rc6.201209161835_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc6-quantal/linux-image-extra-3.6.0-030600rc6-generic_3.6.0-030600rc6.201209161835_amd64.deb)

2) install them (double-clicking on them, this will open the Software Manager, then click Install).
Remark: you may have to find the right order, as some packages need to be installed before other ones.

3) Reboot the PC. The GRUB menu will select the last kernel (v.3.6) by default. Check that it works (Ubuntu boots normally and is usable).

4) Now remove the nomodeset option by opening a terminal (Ctrl+Alt+T), and type:
```
gksudo gedit /etc/default/grub
```
Remove nomodeset from the GRUB_CMDLINE_LINUX_DEFAULT line.
Save the file.
Now type:
```
sudo update-grub
```

5) Reboot the PC. GRUB menu will appear like before. Choose the 1st entry (v3.6), and check if it works or not. (does Ubuntu boot normally and is usable?)
- If yes, then the bug has been solved in the v3.6 kernel. 
- If not, then it hasn't been solved yet, and your bug report will help the devs to fix it. And you will need to add the 'nomodeset' option again via Boot-Repair --> "Add a kernel option: nomodeset".

Is this a stable kernel?

---

### Post by YannBuntu on 2012-09-18
No, it's the mainline kernel (integrating last functionalities and bug fixes).
You can remove it after the test (simply uninstall the 4 packages).

---

### Post by Rogoshin on 2012-09-19
> **YannBuntu said:**
> Here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1052371](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1052371)

Thanks for having reported. Now let's wait the answer of kernel devs.
I'm pretty sure that they will ask you to test the very last version of kernel, so you can do it right now:

1) download the following 4 packages:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc6-quantal/linux-headers-3.6.0-030600rc6-generic_3.6.0-030600rc6.201209161835_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc6-quantal/linux-headers-3.6.0-030600rc6-generic_3.6.0-030600rc6.201209161835_amd64.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc6-quantal/linux-headers-3.6.0-030600rc6_3.6.0-030600rc6.201209161835_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc6-quantal/linux-headers-3.6.0-030600rc6_3.6.0-030600rc6.201209161835_all.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc6-quantal/linux-image-3.6.0-030600rc6-generic_3.6.0-030600rc6.201209161835_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc6-quantal/linux-image-3.6.0-030600rc6-generic_3.6.0-030600rc6.201209161835_amd64.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc6-quantal/linux-image-extra-3.6.0-030600rc6-generic_3.6.0-030600rc6.201209161835_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc6-quantal/linux-image-extra-3.6.0-030600rc6-generic_3.6.0-030600rc6.201209161835_amd64.deb)

2) install them (double-clicking on them, this will open the Software Manager, then click Install).
Remark: you may have to find the right order, as some packages need to be installed before other ones.

3) Reboot the PC. The GRUB menu will select the last kernel (v.3.6) by default. Check that it works (Ubuntu boots normally and is usable).

4) Now remove the nomodeset option by opening a terminal (Ctrl+Alt+T), and type:
```
gksudo gedit /etc/default/grub
```
Remove nomodeset from the GRUB_CMDLINE_LINUX_DEFAULT line.
Save the file.
Now type:
```
sudo update-grub
```

5) Reboot the PC. GRUB menu will appear like before. Choose the 1st entry (v3.6), and check if it works or not. (does Ubuntu boot normally and is usable?)
- If yes, then the bug has been solved in the v3.6 kernel. 
- If not, then it hasn't been solved yet, and your bug report will help the devs to fix it. And you will need to add the 'nomodeset' option again via Boot-Repair --> "Add a kernel option: nomodeset".

I have a problem. I have changed the grub, but when i go into boot repair, the kernel options still state nomodeset. Ubuntu was able to boot, but i am not sure if nomodeset was off now.

Also the new kernel has changed my resolution on the screen so it is all tweaked.

---

### Post by YannBuntu on 2012-09-19
Please indicate your current [BootInfo URL]("https://help.ubuntu.com/community/Boot-Info"), so that we can check this.

---

### Post by Rogoshin on 2012-09-19
> **YannBuntu said:**
> Please indicate your current [BootInfo URL]("https://help.ubuntu.com/community/Boot-Info"), so that we can check this.

Here it is 

[http://paste.ubuntu.com/1214418/](http://paste.ubuntu.com/1214418/)

---

### Post by Rogoshin on 2012-09-19
I also get this message after the grub. Asking for casche, data fail.

---

### Post by YannBuntu on 2012-09-19
Hello

> Here it is

[http://paste.ubuntu.com/1214418/](http://paste.ubuntu.com/1214418/)

When you created this log, nomodeset was disabled. (have you changed things since?)
Did you choose the 3.6 kernel for creating this log? if yes, that's a good news :) , because it means that your problem has be solved in recent kernels. You won't need nomodeset any more with recent kernels.

> **Rogoshin said:**
> I also get this message after the grub. Asking for casche, data fail.

Is it the complete message you see just after you choose the 3.6 kernel ?
If yes, please report it in the bug report.

---

### Post by Rogoshin on 2012-09-20
> **YannBuntu said:**
> Hello



When you created this log, nomodeset was disabled. (have you changed things since?)
Did you choose the 3.6 kernel for creating this log? if yes, that's a good news :) , because it means that your problem has be solved in recent kernels. You won't need nomodeset any more with recent kernels.



Is it the complete message you see just after you choose the 3.6 kernel ?
If yes, please report it in the bug report.

Thank you for all the help. I posted a comment in the thread about what you said. And yes i used the 3.6 kernel to create the log. 

I am not sure if i posted the fix the right way in the bug.

---

### Post by YannBuntu on 2012-09-20
Good job :)
As the "nomodeset" bug is fixed in v3.6, you may want to create a new bug report for the "Asking for cache, data fail" error.

---

### Post by Rogoshin on 2012-09-20
> **YannBuntu said:**
> Good job :)
As the "nomodeset" bug is fixed in v3.6, you may want to create a new bug report for the "Asking for cache, data fail" error.

I dont have the 3.6 kernel installed anymore, because it made me feels uneasy. To make a bug report on the 3.6 kernel problem i would have to have it installed right?

---

### Post by YannBuntu on 2012-09-20
No problem, you can simply do it from here: [https://bugs.launchpad.net/ubuntu/+source/linux/+filebug](https://bugs.launchpad.net/ubuntu/+source/linux/+filebug)

Title: "Error message during boot with kernel3.6"
Description: "When booting on Precise with kernel3.6, i see a "Asking for cache, data fail" message during X seconds, then boots continues fine. See Bug#1052371 for Apport logs."

---

### Post by Rogoshin on 2012-09-21
> **YannBuntu said:**
> No problem, you can simply do it from here: [https://bugs.launchpad.net/ubuntu/+source/linux/+filebug](https://bugs.launchpad.net/ubuntu/+source/linux/+filebug)

Title: "Error message during boot with kernel3.6"
Description: "When booting on Precise with kernel3.6, i see a "Asking for cache, data fail" message during X seconds, then boots continues fine. See Bug#1052371 for Apport logs."

Thank you again. I have now posted the bug.

---

### Post by YannBuntu on 2012-09-21
thanks. 
FYI here is the link: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1053886](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1053886)

---


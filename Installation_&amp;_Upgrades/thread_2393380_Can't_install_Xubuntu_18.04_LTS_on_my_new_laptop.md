---
title: "Can't install Xubuntu 18.04 LTS on my new laptop"
date: 2018-06-02
forum: Installation &amp; Upgrades
---

### Post by pgslmatias on 2018-06-02
I just bought a new laptop that came without an OS. This is the laptop
[https://msi.com/Laptop/GL63-8RD.html](https://msi.com/Laptop/GL63-8RD.html)
chipset HM370, Nvidia GeForce GTX 1050, Intel Core i7-8750H, 8GB RAM DDR4, 256 GB SSD, 1 TB HDD


I have been unsuccessfully trying to install a Ubuntu variant there for a few days now. I've tried Mint and had many issues with it (see [https://ubuntuforums.org/showthread.php?t=2393303](https://ubuntuforums.org/showthread.php?t=2393303)) and so decided to install Xubuntu on a USB drive and try to install from there, figured there would be more help for Xubuntu than Mint.
Now I have the USB with a bootable Xubuntu, and I'm trying to install it to the computer.
I sometimes boot into Xubuntu (Try Xubuntu without Installing option) and everything seems fine, but sometimes I boot and whenever I try to run an application I get this error:´
Failed to execute default Terminal Emulator
 Input/output error.
And the only option I have is close. That error isn't just for the terminal, for example when I try to run the browser it says
Failed to execute default Web Browser.
 Failed to execute child process "/usr/bin/firefox"(Input/output error).

and so on and so forth, I can't even log out from the GUI because I get that error. However, if I do ALT+F4 it works to reach the log out menu, and the computer shuts down fine.
Other times though, I turn on the computer and boot into the USB and everything works fine without giving me that error in any application. I have no idea why, it seems to be random because I do everything exactly the same and sometimes everything works and other times nothing works.
When I first tried to install stuff, using the Install Xubuntu boot option, it gave me the error ubi-partman failed with exit code 141. I solved that error by formatting the ssd where I'm trying to install the OS following the second answer here: [Ubi-partman failed with exit code 141 from usb install]("https://askubuntu.com/questions/817344/ubi-partman-failed-with-exit-code-141-from-usb-install")
However, after I formatted the drive and ran the installer the installer abruptly stopped in the second to last menu. No error, no warning, it just stops working when I hit Continue and doesn't install anything.
Now one time I tried to run the installer it failed when I hit continue in the Updates and other software menu, with "ubi-partman failed with exit code 2". I quit the installation, tried again but got the same error so I rebooted and booted again into Try Xubuntu Without Installing. (on this time with the new ubi-partman crash, the browser opened fine, but the terminal and the log out button gave me the input/output error, first time I noticed it working for some apps and not for others).
Now, after rebooting all the applications worked fine. I tried running the installer, and it didn't give me that error (even though I did everything the same). I get to the Erase Disk and Install Xubuntu menu, select the SSD and press install now, and as usual the installer just crashed without errors or anything (this is the second to last menu I mentioned above). I shut down the computer (the apps still run fine after the installer crash by the way), and I boot into Install Xubuntu. In the Updates and other software menu, I pressed continue and it waited a couple minutes and then ubi-partman failed with exit code 141.
I have no idea what to do, I've tried installing with 3 different ISOs, nothing works, and it always fails in different manners.
This was all done with the BIOS set to Legacy Boot.
I just tried setting it to UEFI and then booting into Try Xubuntu Without Installing. It crashed again with no error in that same menu, the only difference was that it asked me to disable secure boot and for a password for booting in the install third party drivers menu. I then shut down the computer, boot into Try Xubuntu Without Installing and got the ubi-partman failed with exit code 2 error,
I'm absolutely lost. What should I do?

Edit: Tried booting with nomodeset option and I was able to proceed past that screen! I got an error in another screen, saying something about an error with partitions. I rebooted the computer with that option but was unable to get past that screen, the installer crashed again. There were changes to the SSD, it was encrypted (I'm installing with full disk encryption). I reformatted the drive to ntfs, like it was when I was able to get past that screen, but I haven't been able to get past that screen again. I have no idea why I got further in that try, it was the first time I tried nomodeset but in all the other times I have tried with that option I wasn't able to replicate what happened. I'm getting more and more lost, because I always get different errors and then am unable to replicate them when I want, even though I do everything the same.

---

### Post by Impavidus on 2018-06-03
A large number of seemingly unrelated low-level errors, that could be a hardware problem. Have you tried a different usb drive or a different usb port?

---

### Post by pgslmatias on 2018-06-03
You are indeed correct! It was a hardware problem. I bought a new USB drive, flashed it and installed from there and it worked! However, now that the OS is installed it doesn't work, I am getting internal errors everytime I boot after a few seconds and then only the mouse answers my input, I can't click on anything and I can't even open the terminal with Ctrl+Alt+T or shut down with Alt+F4. What can I do? I'm going to write a new post about the new issues.

---

### Post by oldfred on 2018-06-03
You need nomodeset on every reboot, until you install the nVidia driver from the Ubuntu repository.
You may also need to add the ppa to get the very newest driver as an install option.

If you install incorrect nVidia driver, you must totally purge old driver before installing new one, or you get conflicts and major issues.

       # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
ubuntu-drivers devices 
   [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices
You then can manually choose any in list.
sudo apt-get install nvidia-XXX  

Some older MSI need additional boot parameters also, issues are often common by brand:

 MSi GT72VR-6RE Dominator Pro - some settings required
[https://ubuntuforums.org/showthread.php?t=2365997](https://ubuntuforums.org/showthread.php?t=2365997)
Failing to Boot Ubuntu 16.10 in MSI GP72
[http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72](http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72)
[SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544) 

With very new system like this you often need newer kernel, drivers, & support software that is not yet in current distributions or is still being developed. It often takes 6 months to a year before a distribution has most or all the updates to have your install be easy or automatically work.

---


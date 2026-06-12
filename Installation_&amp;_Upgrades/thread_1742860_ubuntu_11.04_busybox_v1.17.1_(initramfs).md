---
title: "ubuntu 11.04 busybox v1.17.1 (initramfs)"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by rhyancute on 2011-04-29
after i install ubuntu 11.04 it will stop in (initramfs)
what im going to do?

BTW: my laptop is HP Pavilion DV6000

---

### Post by jtmoree on 2011-06-26
Did you ever figure this out?  It seems to me that any system update that creates a new initrd image for the boot process does not work and renders the system unbootable. 

I have had to re-install many times to figure this out.  My current workaround is once the system gets screwed I boot with the live cd and copy the original /boot/initrd.img-2.6.38-8-generic over the new one.  System boots fine after that.  I'm looking for bug reports but most boot issues for 11.04 are grub related.

---

### Post by zinadork on 2011-06-29
I am having the same issue on my Mom's system.  I am just going to reinstall the OS.  

On another issue, I am also running an HP Dv6.  Have you got the clickpad working properly.  Until the fix it, I am going to be pissed.  It is not some obscure configuration.  HP shipped tons of laptops with them.

---

### Post by myromance123 on 2011-07-02
I got this initramfs problem too...
First boot after install, so I install all the updates needed then I install AMD 11.6 Catalyst. Restart and I get initramfs (plus at grub there is NO timer...so you have to manually press Enter for it to work and pick an OS). Some have said that waiting for a bit or restarting forcefully then typing "exit" without the quotes at the initramfs screen gets you booting into Ubuntu as usual. This is NOT the case for me!

System specs:
Proc - AMD x4 965 3.42GHz
RAM  - Corsair 6GB DDR3 1333 ( 3x2GB sticks )
GFX  - AMD/ATi RadeonHD 4850 512mb (Catalyst 11.6)
Mobo - Asus M4A88T-V EVO/USB3

**Ubuntu 11.04 64bit dual boot Windows 7 **( Two different HardDrives). When I read some of the others who experience the same, it would seem to be that they are running 11.04 64bit on an AMD system as well... I don't think this is nice... I don't intend to switch over to Intel.

---

### Post by francais on 2011-07-05
Hi everyone.
I am having the same problem with Ubuntu 11.04 booting into busybox initramfs and I am also missing the autoboot timer in the grub menu.  I have successfully managed to continue booting from the initramfs screen into the standard (not the command text console) login window by repeatedly typing "exit" - without the quotes at the initramfs prompt or after "initramfs" if the prompt does not appear.  This usually results in triggering several more instances of initramfs but in eventually starting the script to boot into the standard logon screen after repeatedly typing "exit."  Needless to say this is not a very professional solution aside from being rather annoying!  Would greatly appreciate any assistance in helping me resolve this issue.  Have combed the net and multitude of forums but can't find a fix yet.
In advance thanks for assistance.
Pat

---

### Post by reallybadwithlinux on 2011-07-31
> **francais said:**
> Hi everyone.
I am having the same problem with Ubuntu 11.04 booting into busybox initramfs and I am also missing the autoboot timer in the grub menu.  I have successfully managed to continue booting from the initramfs screen into the standard (not the command text console) login window by repeatedly typing "exit" - without the quotes at the initramfs prompt or after "initramfs" if the prompt does not appear.  This usually results in triggering several more instances of initramfs but in eventually starting the script to boot into the standard logon screen after repeatedly typing "exit."  Needless to say this is not a very professional solution aside from being rather annoying!  Would greatly appreciate any assistance in helping me resolve this issue.  Have combed the net and multitude of forums but can't find a fix yet.
In advance thanks for assistance.
Pat

I have exactly the same problem as you, and I also can't find a solution anywhere. I tried to install Ubuntu in February and that's when it first happened, you won't believe how many times I've reinstalled Linux :D

Your false solution was awesome though, I can't believe that actually worked! After typing exit like 50 times, it randomly booted up. Gave me an message along the lines of 'You do not have the hardware required to run unity'. 

Have you managed to find a solution yet? If not, I'm sorry I can't be of any help either :)

---

### Post by francais on 2011-08-02
Hi "really bad with linux,"
I'm surprised to hear from this thread after so long...anyway, regretfully I don't have any super new fixes to our problem. Let me briefly explain...
Firstly I am definitely not a Linux guru and any "fix" I might suggest is one I picked up reading the multitude of forum entries dealing with this issue.  Second, I don't have Linux installed on a production machine, rather on an older (used to be Windows XP) PC that was laying around taking up space (now it's trying to be useful running Ubuntu 1104!) With the above in mind and noting that I do not have the required hardware to run Unity either, here is what I did based on suggestions from various forums:
1.  Download and burn Ubuntu 1104 Alternate CD iso and burn to CD
2.  Boot PC from 1104 Alternate CD, select language, select "Rescue a broken system".  Depending on your system this will take a while to generate a GUI.  Select language, keyboard etc... The rescue mode will then scan your system.  Provide the requested input, e.g. hostname, locale/time and so on.  Select the drive on which you have Ubuntu 11.04 installed.  When you get to the Rescue Operations screen, select reinstall grub boot loader and then select the device on which you want grub (usually /dev/sda).  Keep going through the rescue mode until completed and reboot the PC.  This should get rid of the initramfs boot. What it did on my PC is restore a grub UI with a timer.  However, after booting the selected OS my screen still goes blank (black screen) and after about three minutes I finally get a Ubuntu login screen. On that screen click your user name enter password and before you logon, change the logon type to Ubuntu Classic at the bottom center of the logon screen.
Not sure if any of this will help, give it a try, if it doesn't work out correctly you may want to reinstall Ubuntu 11.04 from the alternate CD.
Please keep me posted on developments; best of luck
pat

---

### Post by bhupinderjitbawa on 2011-10-08
hi , i have almost similar type of problem. i just bought acer aspire 5755G . with nvidia graphics.

i first created ubuntu 11.04 desktop USB 
then try to boot it stopped at :

> Busybox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built-in  shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) Unable to hold to find a medium containing a live file system.



then i tried kubuntu 11.04 USB

its stopped at:

> Busybox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built-in  shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) Unable to hold to find a medium containing a live file system.

then i tried linux mint 10 USB
it stopped at:

> Busybox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built-in  shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) Unable to hold to find a medium containing a live file system.


so does anybody have the idea whats going on??
i have tried using acpi=off and noapic but no solution..
any help would be appreciated

---

### Post by psrdotcom on 2011-10-10
May be this link can help to resolve the issue

[http://askubuntu.com/questions/15425/unable-to-find-a-medium-containing-a-live-file-system-error-when-installing](http://askubuntu.com/questions/15425/unable-to-find-a-medium-containing-a-live-file-system-error-when-installing)

---

### Post by psrdotcom on 2011-10-10
Try this link..
[URL="http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/"]
http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/[/URL]

This is what i have done .. and worked for me ..

---


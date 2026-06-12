---
title: "GRUB menu does not appear when dual booting with Win8.1"
date: 2017-04-11
forum: Installation &amp; Upgrades
---

### Post by Rahul_G on 2017-04-11
Hello,

I wanted to dual boot my HP laptop (running win8.1) with Ubuntu 16.04. Installed using a Live USB. now after installation GRUB menu does not appear at start-up. laptop boots directly into Windows.
Some info:
Had problems with Live USB booting. figured out that it had to do with the 2nd graphics card (radeon). so at the "try ubuntu" pressed e and inserted "nomodeset" option. after this the live USB boots up fine.
tried boot-repair, but not successful. report: [http://paste2.org/G09yNhEK](http://paste2.org/G09yNhEK)
Disabled Secure boot, virtualization options in BIOS. Moved Windows Boot to the last in the boot order as well.
Hardware: HP pavilion laptop, 500GB HDD, inbuilt intel graphicss + Radeon card. UEFI boot.

Any hints on how to proceed further and the dual boot up and running would be appreciated!

Thanks!

---

### Post by oldfred on 2017-04-11
HPs are not dual boot friendly.
They violate UEFI standard that says NOT to use description as part of UEFI boot. And only valid description is "Windows Boot Manager" for some strange reason.
But multiple work arounds depending on configuration.

If still booting Windows, many use the fallback or hard drive boot entry.
Your may now boot Ubuntu as Boot-Repair copied shimx64.efi to bootx64.efi. 
Check if any UEFI boot option labeled hard drive boots grub menu.

Your ESP - efi system partition is sda2. 
The efibootmgr assumes sda1 as default so you have to add parameters specifying drive & partition.

sudo efibootmgr -v
If none of your hard drive UEFI entries work, or you want one with your description, you can add one:
 sudo efibootmgr -c -g  -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' -d /dev/sdX -p Y
sdX is drive, Y is efi partition  
If sda2:
sudo efibootmgr -c -g  -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' -d /dev/sda -p 2

HP has many extra .efi files to do system maintenance/configuration.
Boot-Repair sees all those .efi files and assumes you need them in grub menu (probably not) and creates 25_custom with all those entries.
You can either delete some or all or turn off 25_custom completely so grub menu has fewer entries.

 # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub 

Boot-Repair did not copy shim to bootx64.efi before, and these users with HP had to manually copy files.

 HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by Rahul_G on 2017-04-11
Hey, Thanks for your reply. I will try the steps mentioned by you.
i'm new to this level of work, i did not completely understand your point "If still booting Windows, many use the fallback or hard drive boot entry. Your may now boot Ubuntu as Boot-Repair copied shimx64.efi to bootx64.efi."

All the remaining modifications can be done only from the terminal once booted into Ubuntu, right?

---

### Post by oldfred on 2017-04-11
You can run commands from live installer also.
I think HP now lets you boot ubuntu, but only if you choose it each time from f12 or whatever is UEFI menu in HP.

But you cannot set ubuntu entry as default boot. And even if you do Windows (with all systems) will update boot order to make Windows first on Windows updates.

But you should be able to set the fallback or hard drive entry.
That is the same default entry that all external devices use or /EFI/Boot/bootx64.efi. Windows & Linux use that on all installers or external drives as that is UEFI standard. It also works on internal drives as a fallback.

---

### Post by Rahul_G on 2017-04-15
Hi,

I tried the steps mentioned, but does not solve the problem. The laptop still boots into windows.
But as mentioned by you, if press 'esc' at the boot, it takes me to boot menu after pressing F9. There i can select ubuntu and start.
now there are few problems in the boot-up itself and after booting.
1. **nomodeset**:
i have to put a 'nomodeset' each time to ensure that i get to the desktop, else start-up hangs. 
following screen shown the info after booting with 'nomodeset':
[ATTACH=CONFIG]274559[/ATTACH]
this i believe is a graphics problem.
graphic cards:
[ATTACH=CONFIG]274560[/ATTACH]
2. **Brightness controls not working**:
in windows mode i can change the brightness by the F2 and F3 fn keys. but in Ubuntu mode, the brightness is max and i cant change it.
i tried looking for some solutions, but there were only workarounds - playing with the color scheme...
any help to get the default behavior working would be great.
ls /sys/class/backlight/ #does not return anything

3. **Heating issue:** The laptop heats up a lot! its as if it is operating on max power, when what i am doing max is trying to find solutions using firefox and terminal.

During this process, i ended up updating the kernel to 4.9 as one page suggested that to solve the display adapter problem. but no luck there.
then i again did the boot-repair steps, but this time went to advanced mode and ensured that all the options were correct. e.g. i had to uncheck the secure boot option. then executed the process. it returned with a success. i was mildly hopeful that the problem is solved, but again no success.
link to the report of the boot-repair: [http://paste2.org/5vBwbtyk](http://paste2.org/5vBwbtyk)
Info displayed after the finish of the boot-repair:
[ATTACH=CONFIG]274561[/ATTACH]

---

### Post by oldfred on 2017-04-15
I do not know AMD graphics. As I gather it is in a state of flux.
And you have to know which driver supports your specific card.

Once correct video is set, you should not need nomodeset.

Some turn off proprietary graphics as internal Intel graphics now are pretty good.

       [https://help.ubuntu.com/community/AMDGPU-PRO-Driver](https://help.ubuntu.com/community/AMDGPU-PRO-Driver)
AMDGPU-PRO 17.10 Released With Ubuntu 16.04.2 Support
[http://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-PRO-17.10](http://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-PRO-17.10)
AMDGPU & Radeon DDX Updated - Better 2D Performance, Tear Free, DRI3 Default Nov 2016 
   Ubuntu 16.10 vs. 17.04 Radeon Graphics Performance R9 270X, RX 480, and R9 Fury
[http://www.phoronix.com/scan.php?page=article&item=ubuntu-zesty-radeon&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu-zesty-radeon&num=1) 
   Also needs  X.Org Server 1.19
[http://www.phoronix.com/scan.php?page=news_item&px=Radeon-AMDGPU-1.19-Updates](http://www.phoronix.com/scan.php?page=news_item&px=Radeon-AMDGPU-1.19-Updates)
Ubuntu 16.04 How-To Install/Uninstall AMD Radeon&#8482; Software AMDGPU-PRO Driver
[https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx](https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx)

---


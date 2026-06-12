---
title: "HELP! Grub seems corrupt, cannot boot neither Ubuntu nor Windows"
date: 2017-06-08
forum: Installation &amp; Upgrades
---

### Post by hateregistering on 2017-06-08
I am unable to boot anything.
The bootloader (Grub, version ??) seems to be corrupt - the menu contains weird borders and when I select Ubuntu or Windows 10 (loader) (see images) I get lots of "error:can't find command xxxx". I have tried to push e to edit the boot (?) file, but it seems to me like there are problems before that file is executed.
I do not think I have done anything else than some kind of automatic update from within Ubuntu, that was recommended (but failed for some reason).
I have tried [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) but for some reason the screen goes dark before the program has loaded and I cannot see anything.
Any suggestions?

[ATTACH=CONFIG]275533[/ATTACH][ATTACH=CONFIG]275534[/ATTACH][ATTACH=CONFIG]275535[/ATTACH]

---

### Post by oldfred on 2017-06-08
If you press enter on Advanced options, can you then boot the recovery mode to a command line?

Grub terminal has just a few limited commands related to booting,  and is totally different than terminal in Ubuntu.

What brand/model computer? What video card/chip?
Ubuntu or one of the supported flavors?
 [https://www.ubuntu.com/about/about-ubuntu/flavours](https://www.ubuntu.com/about/about-ubuntu/flavours)

---

### Post by hateregistering on 2017-06-09
If you mean Boot-Repair then I have tried all options (fail safe mode, normal mode, .. I think there are 7 options or so (I do not have access to the computer at this time)) and all options lead to a dark screen (in fail safe mode the screen goes into sleep, but not in the no-fail-safe option).
I built the PC myself from different components a few years ago. I think my motherboard is ASUS brand, if your answer will depend on the models I will come back with that info after work. Video card brand is GeForce, have to come back with model info.
I have Ubuntu, no special flavor.

---

### Post by oldfred on 2017-06-09
If you have nVidia, you probably need nomodeset to boot installer and first boot.
If BIOS nvidia setting on installer is found by pressing a key while tiny accessibility icons are at bottom of screen, then f6.

If already installed, and you do not get grub menu, you need to press and hold shift key from BIOS until menu appears. If UEFI press escape key perhaps more than once from UEFI/BIOS screen to get menu.
With only Ubuntu installed, you do not normally get grub menu as you only have Ubuntu to boot, so it goes right to booting.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by hateregistering on 2017-06-10
If I edit and replace $vt_handoff with nomodeset there is no difference when pressing F10 (I guess F10 just tries that configuration..? the screen just says "Press Ctrl-x or F10 to boot", nothing about saving anything or something like that)
When you say "installer", do you refer to Boot-Repair or something else? When booting from my Boot-Repair's UNetbootin USB stick there are 5 options: Default, Help, 64bit session, 64bit session (failsafe), and Boot-Repair-Disk session. The results selecting the different options are:

Default: Boot-Repair-Disk icon with 5 dots that goes from grey to blue under for a few seconds, then my screen goes into sleep mode
Help: Log information on the screen which ends with "[drm] Cannot find any crtc or sizes - going 1024x768" (can send you screen dump if reqested)
64bit session: Same as for Default.
64bit session (failsafe): Log information on the screen, which disappears pretty quickly and the screen becomes dark, but the screen does not go in to sleep mode
Boot-Repair-Disk session: Same as for Default.

I believe I do have a motherboard DVI connector, do I need to (and can I do it without messing up other configuration or functionality) connect my screen to that connector to avoid monitor sleep and be able to see anything on the screen?

---

### Post by oldfred on 2017-06-10
I do not recommend the Boot-Repair ISO. I do not think Yann has updated it for several years, so now not current.
Better to just use Ubuntu live installer and add Boot-Repair to it.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use second option:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

You should be able to use whatever video connector works. 
Some UEFI/BIOS have settings to control which video is active.

---

### Post by hateregistering on 2017-06-11
I am not sure I got the steps right, but here is what I did:
1) Created USB stick using [https://help.ubuntu.com/community/Installation/FromUSBStick#Install_and_run_Startup_Disk_Creator_alias_usb-creator](https://help.ubuntu.com/community/Installation/FromUSBStick#Install_and_run_Startup_Disk_Creator_alias_usb-creator)
2) Started up the PC with the USB stick
3) Got into BIOS and booted from USB stick [ATTACH=CONFIG]275586[/ATTACH]
4) Pressed a key when keyboard icon appeared at the bottom of the screen
5) Pressed F6 and selected nomodeset [ATTACH=CONFIG]275584[/ATTACH]
6) This step I was not sure of:  Selected "Boot from first hard disk" - result was "Booting from local disk...  Boot failed: Press any key to retry..." 
  Note: I did try to press escape once more, but then a dialog box appeared "You are leaving the graphical boot menu and starting the text mode interface." - but I didn't go on from there cause I didn't know what to do from there anyway.[ATTACH=CONFIG]275583[/ATTACH]
7) Reset PC
8) Grub boot menu started up and looked wrong as usual
9) Pressed e - the config file was now a lot larger.  [ATTACH=CONFIG]275585[/ATTACH] However, the same error messages as before come and nothing will boot.

---

### Post by oldfred on 2017-06-11
You are trying to boot your install (first disk), not the live installer.
And from what I can see in screen shot, your install is or was in second disk or hd1 in grub.cfg settings. While UUID should override incorrect drive, sometimes there still are issues.
On installs to any second disk I sometimes have to manually edit drive number in grub like hd1 to hd0 as well as possibly other boot parameters.

Boot the live installer in live mode, do not leave the graphical interface of live installer.
Then add Boot-Repair and post link to report.

---

### Post by hateregistering on 2017-06-11
I am not quite sure what you mean with live installer, so I guessed it was this way:

1) setting nomodeset according to previous step 5)
2) Pressed enter to select "Try Ubuntu without installing"
3) Got into Ubuntu
4) Here I tried to click the "Ubuntu Software" icon, but nothing opened (did it crash..?). Then to try further I clicked "Install Ubuntu 16.04.2 LTS" that was on the desktop - even though I do not want to install anything - I would like to keep my previous Ubuntu installation if possible. But here I get nervous; everything after this point seems to have to do with reinstalling Ubuntu, which I do not want to do. 

Am I totally on the wrong path here?

---

### Post by oldfred on 2017-06-11
That is the live installer that you can then use to run Boot-Repair and post link to summary report.
It is a full working copy of Ubuntu, a bit slow from DVD or flash drive and not updateable.
Do not run the install options.
Use terminal to install Boot-Repair. If you reboot, you have to reinstall Boot-Repair as live image does not save anything. And what you can install may be limited by RAM.

---

### Post by hateregistering on 2017-06-11
I was able to start the program now and selected it to generate a pastebin url. However, the URL seems incomplete. This is the message I got:

"Boot Repair

Please write on a paper the following URL:
[http://paste2.org/](http://paste2.org/)


If you are experiencing boot issues, indicate this URL to people who help you. For example on forums or via email."

But when I visit that URL, I see nothing but an empty form.

BR
Joachim

---

### Post by oldfred on 2017-06-11
You are the third or fourth I have seen with no actual report(including me when run from inside my main working install).
Please add to bug report.
[https://bugs.launchpad.net/boot-repair/+bug/1692778](https://bugs.launchpad.net/boot-repair/+bug/1692778)

Not sure what issue is as many are getting full report.

Did it save a copy of the report on your system? It usually is too large to directly post, but you can manually copy to a pastebin site.

With my installed system it saves it in the standard log sub-directory. /var/log/boot-sav/log
Not sure where it saves with a live installer as have not run from a live installer for ages.

---

### Post by hateregistering on 2017-06-13
Ok, I added myself to the bug.

There is a log directory called /var/log/boot-sav/log/2017-06-13__17h24boot-repair06
In there there is a log file that ends with

"
=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to) and reinstall the grub2 of sdb3 into the MBRs of all disks (except USB without OS).
Grub-efi would not be selected by default because: no-win-efi
Additional repair would be performed: unhide-bootmenu-10s


=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sdb (256GB) disk!


=================== User settings
The settings chosen by the user will not act on the boot.

"

I guess I should try using that option ("Recommended repair (repairs most frequent problems)"), or what do you think?
What does the step
"Please do not forget to make your BIOS boot on sdb (256GB) disk!"
really mean - why sdb? How do I do that?

BR
Joachim

---

### Post by VMC on 2017-06-13
Not sure after reading this if your getting a grub menu, but if you are then push "c", then type "set", and see if the boot partition and boot location is what you expect. Info located near the bottom of screen.

---

### Post by hateregistering on 2017-06-14
> **oldfred said:**
> It looks like one Summary report is from a BIOS boot and other from UEFI boot.
And UEFI boot is showing entries in the UEFI for UEFI type booting.
But both reports do not show sda's partitions at all??

It also looks like sdb is a USB flash drive and sdc is USB based MMC card.

It looks like you must have had an install or UEFI would not have any entries.

Does UEFI/BIOS show sda the 500GB drive correctly now?
And from live installer does Disks utility and upper right corner icon use Smart Status show drive? And status of drive?

Are you referring to kenludlow's post now? Those are not from me.

---

### Post by hateregistering on 2017-06-14
> **kenludlow said:**
> Please look at these for me.


[http://paste.ubuntu.com/24851275/](http://paste.ubuntu.com/24851275/)
[http://paste.ubuntu.com/24851306/](http://paste.ubuntu.com/24851306/)

Boot-repair only allows me to print this information.

I am not familiar with these logs at all - what are you trying to say here?

---

### Post by oldfred on 2017-06-14
Yes, I saw Ken's  and did not notice different user.
I did move a third user with issues not related.
I do not think Ken's posts are intended to help, and should be in another thread. Moved, but not other posts that mention it.

---

### Post by hateregistering on 2017-06-16
> **oldfred said:**
> Yes, I saw Ken's  and did not notice different user.
I did move a third user with issues not related.
I do not think Ken's posts are intended to help, and should be in another thread. Moved, but not other posts that mention it.

Ok. Do you have any suggestion to my previous post?

---

### Post by oldfred on 2017-06-16
If your Ubuntu is installed in sdb drive, you only want grub installed to that drive. Do not run auto-fix, but use advanced mode and only install grub to Ubuntu drive.
In BIOS you should be able to set a boot order of which device/drive is first, second, etc.

---

### Post by hateregistering on 2017-06-17
> **oldfred said:**
> If your Ubuntu is installed in sdb drive, you only want grub installed to that drive. Do not run auto-fix, but use advanced mode and only install grub to Ubuntu drive.
In BIOS you should be able to set a boot order of which device/drive is first, second, etc.

I tried that and got the following:

(OS to use by default, I select Windows)

[ATTACH=CONFIG]275688[/ATTACH][ATTACH=CONFIG]275689[/ATTACH][ATTACH=CONFIG]275690[/ATTACH]

After the image upload to the forum I can only see one image - in one of the missing images it says "OS to boot by default: sdb3 (Ubuntu 16.04.2 LTS)" and in the other "Windows (via sdb3 menu)"

[FONT=Courier New]ubuntu@ubuntu:~$ sudo chroot "/media/ubuntu/4a218f8b-24a4-45ab-b964-b68d3ef1e44c" dpkg --configure -a
Setting up grub-pc (2.02~beta2-36ubuntu3.9) ...
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
grub-probe: error: cannot find a GRUB drive for /dev/sdc1.  Check your device.map.
Found Windows 10 (loader) on /dev/sdb1
Found Windows 10 (loader) on /dev/sdb2
done
Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: Generating /boot/initrd.img-4.8.0-41-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_01.bin for module i915
dpkg: dependency problems prevent configuration of libmagickwand-6.q16-2:amd64:
 libmagickwand-6.q16-2:amd64 depends on libmagickcore-6.q16-2 (>= 8:6.8.9.9); however:
  Package libmagickcore-6.q16-2:amd64 is not installed.
 libmagickwand-6.q16-2:amd64 depends on imagemagick-common (= 8:6.8.9.9-7ubuntu5.7); however:
  Version of imagemagick-common on system is 8:6.8.9.9-7ubuntu5.6.

dpkg: error processing package libmagickwand-6.q16-2:amd64 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libmagickwand-6.q16-2:amd64
ubuntu@ubuntu:~$ [/FONT]

Not sure what the error means, but when rebooting the problem is still the same as from the beginning.

After another reboot my wireless keyboard also stopped working. I managed to push the del key to enter the bios, but when inside there it stops working.

---

### Post by oldfred on 2017-06-17
I think you want the MBR options table to control which boot loader is installer in which MBR. You choose MBR &  install.

You have a dependency issue. Have you added a ppa to install [FONT=arial]imagemagick?[/FONT]

---

### Post by hateregistering on 2017-06-20
> **oldfred said:**
> I think you want the MBR options table to control which boot loader is installer in which MBR. You choose MBR &  install.

You have a dependency issue. Have you added a ppa to install [FONT=arial]imagemagick?[/FONT]

No, I am not familiar with neither ppa nor imagemagick.

---


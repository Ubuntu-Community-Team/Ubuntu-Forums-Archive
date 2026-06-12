---
title: "Trouble with Installation on Acer Aspire One Cloudbook 14. “Kernel panic - not syncin"
date: 2016-03-15
forum: Installation &amp; Upgrades
---

### Post by elb2 on 2016-03-15
Update below original post.

Hello all,

[COLOR=#111111][FONT=Ubuntu]I recently bought a new laptop (Acer Aspire One Cloudbook 14) and wanted to install Ubuntu (14.04.3) on it, I have never really used a linux OS (well a little bit on putty for a programming class, and just started using it on virtual box to follow along with a book I have) and want to mess around with one. I put it on a USB following this guide: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I erased Windows 10 and installed Ubuntu. I honestly don't remember how the installation initially went as I have been trying to fix this issue for over 12 hours, I know it didn't go too smoothly, as I remember the screen might have shown a few signs that there was something off with the installation, like blinking screen, and maybe an error/warning message or two (I know that incredibly vague, I have a terrible memory sometimes, just including this because I want to make it clear that my install wasn't 100% normal), but it did start up, the touch pad was not working, but other than that, it seemed fine.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]On the reboot however, I was unable to even log in.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]BOOT MODE: LEGACY[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]If I have the boot mode set to Legacy, it takes me to a GNU Grub thing if my hard drive is highest priority in boot order, listing a few options, if I select Ubuntu, that is when I get the messed up screen and "Kernel panic - not syncing: IO-APIC + timer doesn't work" error.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]If I have USB as highest priority (again in Legacy mode) it takes me to the installation menu, though I suspect it doesn't look the way it is suppose to, but that's how it looked when I first installed it, the difference now is, whether I select install Ubuntu or try without installing, I get the same kernel panic error I mentioned earlier.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]

[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]BOOT MODE: UEFI[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]If I run it in UEFI mode, it says "No bootable device" whether my hard drive (or whatever the equivalent is on this laptop) or USB is highest priority.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I believe I installed Ubuntu in Legacy mode by accident, which might have caused this issue?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have been searching online for many hours, but could not find an issue that was close enough to mine, and already tried many of the solutions of problems that were similar. Like disabling secure boot, trying different boot modes, and nothing is listed if I try to select a trusted UEFI file when hard drive is priority, if USB is priority, it just lists files that are on the USB, none of which can be selected.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thanks for any help.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
Pictures: [http://imgur.com/a/R8yVu](http://imgur.com/a/R8yVu) 

[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Laptop Specs: 

Intel® Celeron® N3050 processor Dual-core 1.60 GHz 
Intel® HD Graphics with Shared Memory 
2 GB, DDR3L SDRAM 
32 GB Flash Memory




UPDATE
So I downloaded a newer version of ubuntu (14.04.4) and put it on the USB. When booted from USB it takes me to a black screen where I have the following options:
1) Try Ubuntu without installing
2) Install Ubuntu
3) OEM install
4)Check disc for defects

But when I try to start Ubuntu, with or without installing, I just get a black screen. I pressed the 'e' key and tried adding nomodset after quiet splash but that didn't seem to do anything. Any ideas?



UPDATE 2
Okay, so I followed these instructions: 
[/FONT][/COLOR][COLOR=#000000]
> 
When you boot the live system, move your selection to 'Try Elementary OS without installing', then press 'E' on your keyboard (for editing the boot options).[/COLOR]> 
[COLOR=#000000]Move the cursor to the line where it says "Linux ....... splash screen" at the end of the line insert a space and then write 'modprobe.blacklist=dw_dmac,dw_dmac_core'.[/COLOR]
[COLOR=#000000]Hit F10 for booting. Now install Elementary OS and reboot.[/COLOR]


from this thread: [http://ubuntuforums.org/showthread.php?t=2289346](http://ubuntuforums.org/showthread.php?t=2289346)
(except I am using Ubuntu) and I was able to install Ubuntu, the screen flashed a couple of times during the process but it went smoothly otherwise. However, when I try to boot from my hard drive I get "No bootable device" exactly as it is shown here 
[http://itsfoss.com/no-bootable-device-found-ubuntu/](http://itsfoss.com/no-bootable-device-found-ubuntu/)
The problem is, when I get to step 3 in that link, where you select a UEFI file as trusted for executing, nothing shows. 

If I boot up from the USB, it takes me to the black screen with the menu I was at before I installed it, asking if I want to Try Ubuntu without installing, Install Ubuntu etc.

I feel like I am going in circles here, probably because I am.


[COLOR=#000000]UPDATE 3:
I used Windows Media Creation tool to reinstall windows 10, which did not ask me for a product key or anything so I guess it somehow knew that my computer had it before? And my desktop background was still there, but no other files, thought that was strange, I thought I wiped it when I installed Ubuntu. I am just glad I have my poor laptop running again. I will try to reinstall Ubuntu again tomorrow, this time following a guide more closely. Will update again tomorrow.




[/COLOR][COLOR=#000000]UPDATE 4:
EDIT: Read last update for more bad news (if you have this particular laptop) 

I finally got it running! For anyone who experienced similar issues, these are the steps I took:

1) Reinstalled Windows 10
2) Turned off fast start up in the power options menu in Windows
3) Change Boot Order in BIOS to boot from USB ( I also changed touchpad settings for my laptop to basic from advanced, but this may not be necessary)
4) Try Ubuntu Without Installing
5) Clicked Install when on Ubuntu Desktop
6) I replaced Windows 10, but this is up to you
7) Restarted, removed USB and Changed boot order so my hard drive was priority again
8) I actually got the 'No Bootable Disk' error again, my heart sank, BUT this time I was able to select a trusted UEFI file as shown on this website: [/COLOR][http://itsfoss.com/no-bootable-device-found-ubuntu/](http://itsfoss.com/no-bootable-device-found-ubuntu/)

[COLOR=#000000]

Possible reasons why I  had trouble with the first installation: I think I did not turn off fast startup in Windows. I installed Ubuntu in legacy mode, NOT EUFI, and I think I had secure boot disabled. 

So what I learned from this, definitely try before installing to see how it runs on your computer, and have Windows or whatever OS you are using ready in case you need/want to go back.

LAST UPDATE:
Okay, I spoke too soon. I was having issues with getting stuck on a purple screen when the computer would start, it would successfully log in 1/10 times, and after following these instructions: [/COLOR]http://askubuntu.com/questions/451638/ubuntu-14-04-loads-to-purple-screen-on-lenovo-g505s-nomodeset-wont-work/ from Taz D (the one about installing xubuntu desktop), that number went up to around 1/5, but I was not satisfied with that[COLOR=#000000] and after trying many other solutions online, and trying to install Xubuntu on it, I just gave up and traded laptops with my fiance. She has an HP 15, don't know the particular model. The installation on that laptop went pretty flawless, only thing that slowed me down was I did not know I had to click F9 when it was booting to select a boot device in order to access the USB.


[/COLOR]

---

### Post by elb2 on 2016-03-16
Bump. 

How can I change the thread title to reflect my most recent issue, or can a mod do it? I feel like if I could select a UEFI file for secure booting from the boot menu I could get it running, as that seems to be the solution I've read many times, sadly nothing shows up for me, and I can't seem to find anyone else who had this problem. I've also tried booting lubuntu, and mint from a USB, but having similar issues. Any ideas on why I can't see anything under the 'Select a UEFI file for as trusted for executing' option? As of right now, I am still stuck on 'No Bootable Device'

EDIT: See last Update on my first post to see what I did to resolve these issues.

---

### Post by Den_S. on 2016-03-24
See: [https://wiki.archlinux.org/index.php/Acer_Cloudbook](https://wiki.archlinux.org/index.php/Acer_Cloudbook)

---


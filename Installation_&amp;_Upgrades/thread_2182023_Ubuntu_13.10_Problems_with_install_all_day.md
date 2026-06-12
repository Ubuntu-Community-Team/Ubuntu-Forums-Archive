---
title: "Ubuntu 13.10 Problems with install all day"
date: 2013-10-19
forum: Installation &amp; Upgrades
---

### Post by TurnEmAndBurzum on 2013-10-19
I'm attempting to install *Ubuntu 13.1 *on a* Toshiba Quosmio* laptop with an * Intel Core i7, *and a *Toshiba Quosmio **x505 *motherboard.     
     I burned a DVD with the image downloaded from Ubuntu's website and I changed the order of my drives so that DVD will boot first. A logo with five dots lighting left to right shows for roughly 3-5 minutes until a command prompt appears with the following: *(intramfs) unable to find a medium containing a live file system. *&#8203;Any help is very much appreciated!

---

### Post by Cole_M on 2013-10-19
Have you checked the md5 sum of the ubuntu iso after completing the download? More info: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by TurnEmAndBurzum on 2013-10-19
'Says they match up. I've burned the image three times now at the slowest speed I can (6x.)  I explained my situation wrong in my original post.  The *(intramfs) unable to find a medium containing a live file system* message appears when I insert the dvd while my computers on and open the installer through Windows 8. Sorry. When I restart my computer with the DVD in the tray and the order of my drives changed I end up with a hard to describe glitched-to-hell screen... almost like giant white tetris L's on a black background... with an occasional green bar, lol.  Thanks for the response.

---

### Post by mmmm2 on 2013-10-19
It appears a Windows environment is incorrect for Ubuntu, but you've found that out. ;)

Have you read this? [https://help.ubuntu.com/community/GraphicalInstall ]("https://help.ubuntu.com/community/GraphicalInstall")

---

### Post by mmmm2 on 2013-10-19
This one may be helpful, too - [https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

---

### Post by TurnEmAndBurzum on 2013-10-20
[COLOR=#000000]"It appears a Windows environment is incorrect for Ubuntu, but you've found that out. [/COLOR][IMG]http://ubuntuforums.org/images/smilies/icon_wink.gif[/IMG]"     -Lol.

---

### Post by TurnEmAndBurzum on 2013-10-20
UPDATE:     So I'm working my way down the list of the second link you provided, mmmm2 (...*/Boot/FromCD.) *The only way I'm able to get to the *advanced welcome page*, with the five options and f1-f6 at bottom, is to press enter during this screen: 
[IMG]http://www.kameda-lab.org/_local/imagelab.tsukuba.ac.jp/ubuntu1204/pkg/Ubuntu_startup.png[/IMG] 
Which appears to be an equation involving a battery and the Survivorman logo...
     When I arrive at the * advanced welcome page* I select either *try Ubuntu without installing *or * install Ubuntu* and after some work on my computers part for a few minutes arrive at the aforementioned glitched to hell screen.
     I am presently learning about *bootparameters* as that's what I've worked down the list to. Wish me luck.

---

### Post by fantab on 2013-10-20
What machine is this? what os does it have? Try booting Ubuntu from a USB pendrive.

---

### Post by TurnEmAndBurzum on 2013-10-20
[COLOR=#000000]I'm attempting to install [/COLOR]*Ubuntu 13.1 on a Toshiba Quosmio laptop with an Intel Core i7, and a Toshiba Quosmio x505 motherboard.  *It's running *Windows 8*.  
 I've experienced the same issues with the pendrive as well... Is there any chance that I need to update the drivers for my GPU? *nvidia geforce gts 360m.  (*If that is the case then It'll be awhile as I cannot find them anywhere on their website.)
Also, I've attempted to install Fedora 19 and Mint 15 as well and the end results were the same glitchy screen.

---

### Post by fantab on 2013-10-20
Have you disabled 'Fast Startup' in Win8? This feature keeps the Windows in Hibernation inspite of being shutdown for faster startups. Technically windows is not shutdown. We need to shut it down.
[URL="http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"]http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html 
[/URL]
If there is an SSD and HDD in the picture then you will look for and if found 'disable Intel SRT', this is some sort of RAID used for 'cacheing'. Disabling it won't affect windows performace by much.
[http://superuser.com/questions/476777/properly-disabling-intel-srt](http://superuser.com/questions/476777/properly-disabling-intel-srt)

Also, [disable 'fast boot']("http://www.intel.com/support/motherboards/desktop/sb/CS-032034.htm").

---

### Post by TurnEmAndBurzum on 2013-10-20
fantab:  I was able to disable * fast startup* but could not find anything in the BIOS regarding *fast boot* or*Intel SRT. *I attempted to install from DVD with fast startup disabled and after a couple minutes on the screen I posted a picture of above, the monitor went back to glitch. What a pain in the @$$ this has been. I'm beginning to wonder if this is at all worth it. Thanks for your suggestions!

---

### Post by oldfred on 2013-10-20
Is Windows installed in UEFI mode or BIOS mode. 
The purple screen you posted is a BIOS boot, since your system is an i7 it will have UEFI, but you need to install Ubuntu in same mode as Windows to easily dual boot.

The purple screen is the accessiblity screen and the icons are a person hitting the keyboard to gain access to the menu. (no idea why they think that is better than just showing menu?). 
Since you have nVidia you will need nomodeset if that is the video mode it boots with. From menu use f6, choose nomodeset and boot.
If booting with Intel video different boot parameters will be required.

If Windows is UEFI, then from UEFI you need to boot Ubuntu in UEFI mode. You then get grub menu and need to manually add nomodeset. Use e for edit, scroll to linux line, and replace quiet splash with nomodeset.

       Backup efi partition and Windows partition before Install of Ubuntu.
If UEFI Windows:
Shows install with screen shots. (Both BIOS & UEFI grub).
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by TurnEmAndBurzum on 2013-10-21
Thank you oldfred.  Windows was installed in BIOS mode so I was able to select *modeset* from the menu and install without incident. So far so good; noticeably faster than Windows 8 and a much more intuitive GUI.  I'm pretty stoked that I just spent mere seconds finding, downloading and installing Unity Tweak Tool with a simple command. Thanks for your help everyone.

---


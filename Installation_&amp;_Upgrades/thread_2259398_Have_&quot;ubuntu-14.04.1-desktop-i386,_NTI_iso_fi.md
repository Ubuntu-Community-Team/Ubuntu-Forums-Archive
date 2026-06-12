---
title: "Have &quot;ubuntu-14.04.1-desktop-i386, NTI iso file&quot;, how to proceed?"
date: 2015-01-04
forum: Installation &amp; Upgrades
---

### Post by bob120 on 2015-01-04
I have downloaded this on my Acer T135 computer and  on a memory stick made  on my other HP Pavilion a1626n computer. I cannot install either  file onto the Acer.  I had/have problems with malware or an intruder, I'm using Eset trial security. 
Reinstalled 2005 version of xp home using the factory disc, delete the obsolete  programs (the NTI iso after the download) but cannot delete Norton security, always deleted OK on other installs. (this is not the problem, just another issue).
The NTI iso program is not on the computer, was deleted.  If I plug in the stick it opens the same NTI file as above in the title. Double click it and notepad opens. Left clip and a small popup lists : Open, Edit, Open with, Send to, Cut, Copy, Create shortcut, Delete, Rename, Properties. "Open with" lists : Notepad, Internet explorer or Choose program. "Choose program" lists : Recommended programs, -Internet explorer, -Notepad; Other programs, -Paint, -Windows media player, -Windows picture and fax viewer, -Word pad.
"Look on the web" option fails to connect to the internet, same with windows explorer.  Downloaded Firefox, had to link to the web thru a downloaded older firefox on a memory stick. New version won't connect either.

For prep I formatted drives D and E, left C, assuming Ubunto formats C on install.  After install I should have one drive only (?) Also pulled the battery checked at 2.9v, re-installed. In bios I done a reset. ( needs verifying on what was reset as internet instruction screens did not match mine).

The reason I could not download to a disc :  Device manager lists Play a factory music CD : my cdrom is recognised, then goes to "disc is busy" them '"no disc in drive". Cdrom does not work on either computer, I suspect a setting/bios issue caused by malware or an intruder. Spend alot of time searching/reading the wrong answers, or just the wrong questions.

What should I do?

---

### Post by yancek on 2015-01-04
I'm not really sure what you are trying to do.  You mention the Ubuntu iso in your thread title and no more.  Are you trying to or planning to install Ubuntu?  If so, and you seem to be using some version of windows (xp?), you will need to get the Ubuntu iso either on a DVD (too large for a CD) or on a flash drive.  You could boot the iso from your hard disk if you had a Linux bootloader already installed but it seems you only have some windows so that won't work.  Either a DVD or a flash drive is needed.

If you want to put Ubuntu on a DVD, you will probably need to download software to xp to use for that purpose or use software designed to put a Linux Live CD on a flash drive.
What is NTI and what does it have to do with Ubuntu.

Posting a few more details would probably help someone to help you.

---

### Post by bob120 on 2015-01-04
Yes I am trying to install Ubuntu, I have 2 different files. I had stated one is by download, The other is on a memory stick , a Dataright 4gb. (is that the same as a flash drive?)
I forgot all about SP3 issue. Since I last posted the Acer has been downloading SP3, I had confused the needed patch KB953356 with the SP3 file, explains why it did not work, SP3 would not download from Microsoft Download page. OK, S3 is working, auto updates is happening.
[LIST]
[*] 	 		 			:razz: 		

 	
[/LIST]
 I done this a week ago too. Then a reinstall that resulted in many issues. I don't want to repair/re-install files, just get  Ubuntu desktop installed. I stated in my first post that I have 2 computers, meaning that I can download to a memory stick if needed, CANNOT use either cdrom drives to obtain a disc. AFTER Ubuntu is functioning, then I will probably download to disc and  re-install it. I say that because Ubuntu website states flash is not a good option. I intend to purchase 64bit version for the HP. The Acer is only 32bit. Latter,  as the purchase option is limited to entering account info by internet...my  senior brain has not fossilized to that degree yet :) IF I can't phone in my credit card or mail a cheque then I will not buy.

So the memory stick has the latest Ubuntu (as the title states), this was downloaded from Ubuntu into the HP then placed onto the memory stick. Can it be used or is there special software needed/ Again neither cdrom works, both need fixing? Played with this a bit, read dozens of how to's that go nowhere. There are no upper or lower limit files in the regeditor. I suspect an intruder has made changes rather than malware (not in person, by internet). Both computers got into trouble after installing Brothers software disc for my printer, doesn't stand to reason that is the issue, just the trigger, perhaps wifi issues. I chose the USB option as I not want Brothers running thru my internet or phone connections. Its for print only on one computer.

Another hour for the 135 upgrade items to complete downloading, last week was 154. I am not able to backup by disc as I normally due monthly. Can I backup offsite to my Google account or somewhere else credible?

I hope Ubuntu OS will cure the deficiencies of this old computer, all the old unsupported OS should be gone (?)

yancek : NTI is an iso program supplied in the original xp sp2 installed disc software. I assume 2005 software is obsolete and delete them, most of these old programs lead to "buy me" pages. There is obviously more to un-install, what got left behind or its just a setting somewhere.
The problem is the Ubunto file went there as I stated in the title.  If you had read my complete post you would see I stated the memory stick does the same, goes to a non existing iso program. The NTI iso is NOT on the stick or the download, it wants to open the file. I'm supposed to get Ubuntu install pages, apparently software is not installed to handle the Ubuntu file.
I placed all the popup info intended for someone that KNOWS what it is, is it complete or is there items missing (like the needed installer software)?

Hope that  makes clear my issues of installing Ubuntu.

---

### Post by Impavidus on 2015-01-04
OK, I read your posts twice and I think I more or less understand your issue. Your Windows system thinks it has to open .iso files with an application known as NTI. It's a Windows convention to strip the extension (.iso) of the file name (ubuntu-14.04.1-desktop-i386.iso) and replace it with a file type in the next column (NTI iso file). In Linux we see extensions just as part of the file name, as a useful convention, but not mandatory. Many file names in Linux have no extension, or have double or triple extensions. So that causes some confusion.

If your computer is older, it may not be capable of running the full Ubuntu. There are some Ubuntu derivatives specially designed for older hardware, like Lubuntu and Xubuntu. Internally, they're almost the same, but perform much better on computers with weak graphics or low RAM memory. If you post some specifications of your hardware, we may be able to give more detailed advice.

You can either burn the .iso file to a dvd using any dvd burning tool, but you say that doesn't work. No problem, use a usb memory stick. And yes, loosely speaking a memory stick is a flash drive. Simply copying the file to the memory stick won't work, as that doesn't make the memory stick bootable. You'll need some special tools. Some are listed on this page: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick). Note that this will remove all current files from the memory stick. Some older computers (let's say more than 8 years old) cannot boot from a memory stick. In that case you'll need the dvd. Maybe you can ask a neighbour or family member to burn it for you. Nowadays, most people use a usb memory stick.

To install Ubuntu, insert the memory stick or the dvd into the computer and reboot. Make sure the boot priority has been set to usb or dvd first. Then Ubuntu should start. In Ubuntu, you'll find the installer. The current state of the software on your computer doesn't matter, everything will be wiped off the hard drive. And that is the entire hard drive, not just the C partition.

Although some download sites ask for a voluntary donation, Ubuntu and its family are free, both in the sense of free speech and of free ice creams. There is no need to buy anything.

---

### Post by bob120 on 2015-01-04
Thank you Impavidus for explaining my issues, this greenhorn  understands these descriptions. Not sure that 14.04.1 was my targeted download, did not get the page bookmarked. The version I need is consumer ready no codes needed to operate, can the smaller/older versions do that? 
Been years wanting Ubuntu but instructions have always been in developer language, never install and use. I only need simple and reliable, don't use movies or need any frame flashing images. Text and still photos suit me fine. 
So I need to stretch these 2 old computers, find newer next summer, hoping Ubuntu will replace xp's. If they fail I have a newer Acer Chromebook, useless for printing or filing info onto SD cards. 
SP3 was successful, looked grim this morning. Accessing websites now, updates done their magic. More updates before useful and I'll get paid versions of Eset tomorrow. they accept phone calls :)

---

### Post by yancek on 2015-01-04
If you are running xp, you need to download Ubuntu from the Ubuntu site.  It will download a single file with an .iso extension.  Make sure you get the 32bit version.  The download site is at the link below if you have not downloaded it yet.

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

If you already have the Ubuntu iso file or after you download it, you need to put it on a flash drive so that it is bootable.  There are a variety of ways to do this but one of the simplest is using the software unetbootin which you can download from the site below.  Make sure you download the windows version to xp and read the instructions.

 [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

After you have created the bootable flash drive with Ubuntu on it, you need to reboot the computer and set the BIOS to boot from the flash drive.  If you can't boot from a flash drive, you will need to use a DVD and burn the iso file of Ubuntu to the DVD by selecting the "burn as an image" option in your DVD burning software.  Then you will be able to boot the Ubuntu medium and begin the install.

Personally, if you have a computer which is old enough to have been using xp, Ubuntu might be too heavey and using Lubuntu or Xubuntu might be better.  The installation process is almost identical and the link below is a tutorial on installing Ubuntu.  If you read through the page, you will see there is no secret code and nothing really complicated.  You just need to be able to read and follow directions.

  [http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by Impavidus on 2015-01-05
Most computers designed to run Windows XP are not powerful enough to run Ubuntu. Ubuntu's derivatives Xubuntu (light) and lubuntu (extra light) have been designed to run better on older hardware. Apart from some components of the user interface, they are nearly identical and as easy to use. In some respects, Lubuntu and Xubuntu are even easier to use than Ubuntu, as the user interface will look more familiar to those coming from Windows.

Ubuntu, Xubuntu and Lubuntu:
[http://www.ubuntu.com/](http://www.ubuntu.com/)
[http://xubuntu.org/](http://xubuntu.org/)
[http://lubuntu.net/](http://lubuntu.net/)

Directly to the download pages:
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu/14.04.1](https://help.ubuntu.com/community/Lubuntu/GetLubuntu/14.04.1)

It will be best to install release 14.04.1 of one of these. You can test them before installing. Usually everything just works, especially on desktops, unless the hardware is very recent (which your's is not, I ssume). Do you know what processor, graphics card and how much RAM memory is in your computer?

---

### Post by grahammechanical on 2015-01-05
Here are some images of what you will see when you run the Ubuntu live session and after you have selected Install Ubuntu. Note the third image - Installation Type. This is where you must be careful. If you do not want Windows XP any more then select the second option - Erase Disk and Install Ubuntu. This option will wipe everything, including XP and all the malware, from the disk.

If you want to keep the Windows OS then select Install Alongside. Think carefully about this as it will be impossible to get Windows back without re-installing.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

As you can see the instructions are not in "developer language."  By the way, the same install method is used for Xubuntu and Lubuntu and all the official flavours of Ubuntu.

Regards.

---

### Post by bob120 on 2015-01-05
I was wrong on my download, it should have been Xubuntu 14.10-32 bit. Yancek link connected to this, thanks. Good info from everyone, thank you gentlemen. 
I got the Acer secure and running reasonable, downloading the 14.10 now. Cdrom problem continues, recognized in device manager but WMP shows no disc in drive. Must be settings.
Hp cdrom and card / stick drives are not recognized, open the case this week and check for connector issues. Due for a battery too.
I can get back to my original plans of Acer running XP Home as its only 80gb /1.25gb and the HP using Xubunto, its 200gb / 2gb, 2 more slots available if I need to go 4gb. Can also be setup for 64 bit.

---

### Post by mastablasta on 2015-01-06
WMP - windows media player? that is not a file manager and who cares if it shows a data disk or not. the important thing is what windows explorer shows it.

---


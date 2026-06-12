---
title: "Adding windows 7 to grub after I had deleted the old MBR"
date: 2012-05-17
forum: Installation &amp; Upgrades
---

### Post by guidoz on 2012-05-17
Hi everybody and greetings from Italy.

I have a small problem after messing around with my MBR. I want to say I'm not a beginner with PCs and I tried for a couple of days to find a solution on google, but I'm not much of an expert about the MBR.. so I'm afraid need your help. 

I'll try to explain shortly:

1 - I had only Win XP on my main PC till a year ago or so. Then I added Win 7 64bit in dual boot, but never deleted XP till a few days ago, when I deleted XP and installed Ubuntu 12.04 with the intention of having Ubuntu and 7 in dual boot.

2 - Unfortunately, deleting XP partition I probably also deleted the MBR.. I had imagined this in advance but I had thought I could easily fix it after installing Ubuntu.

3 - After installing Ubuntu I tried to configure grub (found the right location of win 7 partition - /dev/sda7 -, found out how to add it on grub and so on ), but it doesn't work. As I said I'm not an expert about MBR... so I guess, but I don't know for sure, that grub needs to find the original windows loader to launch windows... is this right? 

So, final questions: 

is there any way to fix this problem not having a windows recovery disk nor fast internet access at the moment (I'm currently using 3g connection, but I do have a monthly limit.. so can't downloading anything big for the moment)? I mean, it is possible to fix the MBR only using linux, or I'm right when i think I'd need to install the windows' bootloader first? If it is not possible to fix it just with what I have, what will I need to download as soon as I have a better internet access?

I hope my questions are clear.. I didn't want to make it too long, but if you need more details you can ask of course ^_^

Thanks,
Guido

---

### Post by oldfred on 2012-05-17
You were in tutorials, I moved you to Installation & Upgrades.

What you deleted were all the Windows 7 boot files as they were in the XP partition. Windows only boots from a primary NTFS partition with the boot flag and since XP was first, 7 installed its boot files into the XP partition. 

Is your Windows 7 install in a primary partition? If not you may have to recreate sda1 as a boot partition anyway.

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

You proably are missing bootmgr & the BCD. And you just about have to have a Windows repairCD or USB to fix it. Do you have a friend or neighbor with the same 32bit or 64 bit version of Windows 7?

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

We used to have a site, but it now charges $10 for a Windows repairCD download.

Have you totally overwritten the XP partition? If not you might be able to use testdisk to find the bootmgr & bcd files?

Download an run this script and then post results.txt that it creates:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---


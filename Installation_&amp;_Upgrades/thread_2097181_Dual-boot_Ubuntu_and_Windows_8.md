---
title: "Dual-boot Ubuntu and Windows 8"
date: 2012-12-22
forum: Installation &amp; Upgrades
---

### Post by nkenny94 on 2012-12-22
I'm really sorry and I know you must be sick because of these similar thread, but I gave up on install ubuntu. I just don't understand how do to it. I create a new partition and reset my laptop. Whenever I plug my USB in then the laptop doesn't boot the usb it just keep resetting. I did try to find some solutions but I couldn't found any. please help.

My laptop is HP-Envy m6.

---

### Post by ajgreeny on 2012-12-22
How did you write the iso file to the USB?
Is the USB bootable?
Is your laptop set up to boot USB as first device?
You may need to press a keyboard key to get it to boot to a USB device; read the laptop manual.

---

### Post by Filip II on 2012-12-22
For the dual-boot part of your problem here is a tutorial I posted earlier on another thread: [http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)

For the usb problem, go into the boot manager (press the f12 at start-up) and change the boot order, maybe the usb isn't listed first
 If the usb doesn't work for you, install Ubuntu by DVD.

---

### Post by EmmEight on 2012-12-22
All computers have a BIOS that tells the computer which devices to load first.

Usually they go something like this:

CD-Rom
Hard-Drive
Network Boot

Etc..


You need to restart your computer. When the computer first starts up hit f12 or delete or f2... (It will usually say boot manager or BIOS or boot menu or something of that nature)

Just read the screen, careful it can sometimes go away quickly.

After words just look through the settings and make sure your USB drive is set to number 1 on the list.

Sometimes you have to change your hard drive from "local drive" to "usb drive"

And then move it up on the list.

And of course you can always boot from a DVD...

---

### Post by oldfred on 2012-12-22
Someone posted this. 

HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)


Some have posted that you have to press keys right away as it boots very quickly.


Have you downloaded the 12.10 64 bit version as that has the newest grub2 that works with secure boot.

---

### Post by sudodus on 2012-12-22
> **ajgreeny said:**
> How did you write the iso file to the USB?
Is the USB bootable?
Is your laptop set up to boot USB as first device?
You may need to press a keyboard key to get it to boot to a USB device; read the laptop manual.

Hi nkenny94,
and welcome to the Ubuntu Forums :-)

You need to answer to our questions, otherwise we can only guess, what is your problem. Start with the first one:

How did you write the iso file to the USB?

---

### Post by Gremlinzzz on 2012-12-22
> **nkenny94 said:**
> I'm really sorry and I know you must be sick because of these similar thread, but I gave up on install ubuntu. I just don't understand how do to it. I create a new partition and reset my laptop. Whenever I plug my USB in then the laptop doesn't boot the usb it just keep resetting. I did try to find some solutions but I couldn't found any. please help.

My laptop is HP-Envy m6.
:popcorn:Put the usb in while the computers on then restart

---

### Post by nkenny94 on 2012-12-22
> **sudodus said:**
> Hi nkenny94,
and welcome to the Ubuntu Forums :-)

You need to answer to our questions, otherwise we can only guess, what is your problem. Start with the first one:

How did you write the iso file to the USB?

I know how to install ubuntu. i did it on my old laptop
use linuxinstaller or something like that from the website to write iso file to the usb. I did change the BIOS so the on the top of other thing. I just don't know why whenever I put my usb on then the laptop just keep reset and it won't run ... I did try to install from wubi and it say that I missing that wubi file or something

---

### Post by sudodus on 2012-12-22
> **nkenny94 said:**
> I know how to install ubuntu. i did it on my old laptop
use linuxinstaller or something like that from the website to write iso file to the usb. I did change the BIOS so the on the top of other thing. I just don't know why whenever I put my usb on then the laptop just keep reset and it won't run ... I did try to install from wubi and it say that I missing that wubi file or something
Good, we can skip the noobiest questions!

The resetting cycling indicates that the computer really tries to boot from something else than its standard internal drive.

- But just to check the USB stick: Test if you can boot your old laptop from it *now*! Some USB drives won't co-operate with some computers. It is worth trying another USB stick (other brand or model), or another tool to make it bootable. I have good experience with UnetBootin. You can also try to write the iso image directly to the USB stick with dd (low level writing to the block device). See this link:
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1958073[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1958073")

- Are you trying to boot from a USB 3 port? That might not work yet. Try all the other USB ports.

- Oldfred is probably the most experienced of us concerning boot and install issues, so please read his post very carefully, and try what he suggests!

---

### Post by nkenny94 on 2012-12-22
Well! I did try both 2.0 and 3.0 usb port but both doesn't work.. I pretty sure that my old laptop can boot with my usb. and both my laptop is hp
Hmm.. Can I install ubuntu in different way except from usb or dvd ?

---

### Post by sudodus on 2012-12-22
Yes.

But if you get (borrow/buy) a "USB to IDE and SATA cable" adapter, you can connect an old CD/DVD driver via USB and boot from a disk. This might be a good choice. That adapter can come in handy in the future too, also to connect internal drives temporarily.

You can remove your internal drive and attach it to an other computer, typically internally via a SATA port to a desktop or workstation with lots of space, but also externally via eSATA or this "USB to IDE and SATA cable".

And when it is connected out there, you can install Ubuntu into it. As long as you don't install any proprietary driver, it will be perfectly portable among most computers, maybe with the exception of new computers with other firmware than standard BIOS.

- What about the BIOS of your new computer?
- Have you downloaded and tested Ubuntu 12.10 64 bit version as that has the newest grub2 that works with secure boot?

---

### Post by nkenny94 on 2012-12-22
i think it have something to do with UEFI thing cuz my lap is wins 8.
how do I test that grub2 :-?

---

### Post by sudodus on 2012-12-22
Download the Ubuntu 12.10 64 bit iso file.
Run ```
md5sum 'filename.iso'
``` and compare the result with the posted md5sum. Wipe the pendrive and install from the new iso file into the it, and then try to boot from your revamped boot pendrive. Try to boot both laptops and let us know your result.

(The test of grub is when you test if it boots the new computer)

---

### Post by nkenny94 on 2012-12-22
OH gosh U need to tell me what do i do with md5sum :p do i run it on command promt ?
And how do I compare the result with the post md5sum ?

---

### Post by sudodus on 2012-12-22
> **nkenny94 said:**
> OH gosh U need to tell me what do i do with md5sum :p do i run it on command promt ?
And how do I compare the result with the post md5sum ?
Yes in a terminal window in linux (in your old computer).
Write the command and start it with the ENTER key!
The output of the command is a string with characters, and it should be the same as the posted md5sum (from Ubuntu's web page).

There is also a program for it in Windows, md5summer
[[COLOR="Red"]http://www.md5summer.org/about.html[/COLOR]]("http://www.md5summer.org/about.html")

---

### Post by nkenny94 on 2012-12-23
I quite don't get how to use it on windows =.= and my old lap is broken so I guess I can't use it anymore....
Is there anyway to install ubuntu to the laptop ?

---

### Post by sudodus on 2012-12-23
> **nkenny94 said:**
> I quite don't get how to use it on windows =.= and my old lap is broken so I guess I can't use it anymore....
Is there anyway to install ubuntu to the laptop ?
Don't give up so easily!

Try to solve the problem step-wise. First make sure that your boot USB drive really works. Then make it work also in your new computer.

If you cannot run md5sum, take the chance without making sure that the download was successful. Borrow someone's computer and test if it can be booted from your USB drive. If it works in one computer, it is likely to work also in your computer, unless there is something tricky with that particular computer.

And then start solving that problem with help from me and other people at the Ubuntu Forums.

---

### Post by gdubz on 2012-12-24
[FONT=Calibri][SIZE=3]I just got Ubuntu 12.10 to boot on a new HP Envy DV7 a couple of days ago. [/SIZE][/FONT][FONT=Calibri][SIZE=3]This is how I achieved dual boot with vendor (HP) installed Windows 8 / Ubuntu 12.10 on the machine that&#8217;s in the linked data sheet, with manufacturing date 08/12:[/SIZE][/FONT]
 
[[FONT=Calibri][SIZE=3]http://www.shopping.hp.com/shopping/pdf/c2h70ua.pdf[/SIZE][/FONT]]("http://www.shopping.hp.com/shopping/pdf/c2h70ua.pdf")
 
[FONT=Calibri][SIZE=3]The chipset is HM77 (35w Ivy Bridge i5 Dual Core processor)[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]I put the x-64 12.10 Live ISO on a USB stick for install. I think I used a USB 3.0 port.[/SIZE][/FONT]
 
[COLOR=#333333][FONT=Tahoma]In UEFI (F10 menu):[/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]&#8226; &#8226;Disable Secure Boot. I could not achieve boot in any configuration with it on. [/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]&#8226; &#8226;UEFI boot scheme (not Legacy BIOS). I tried Legacy mode, and can boot from disk/USB, but not from an installation on the hard drive. UEFI flies right by it during boot every way I tried with it on. [/FONT][/COLOR]
 
[COLOR=#333333][FONT=Tahoma]In Ubuntu:[/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]&#8226; &#8226;/Boot=EFI, /=EXT4, /Home=EXT4, SWAP=swap. With UEFI, [/FONT][/COLOR]
 
[COLOR=#333333][FONT=Tahoma]I don't beleive it matters if the partitions are primary or logical, because UEFI support >4 primary partitions...but just in case I made the EFI boot partition primary, and the other 3 listed as logical. Back on W8 All now 7 combined partitions (3 Windows, 4 Linux) show up as the same level without designation (primary or logical).[/FONT][/COLOR]
 
[COLOR=#333333][FONT=Tahoma]With this configuration I can boot with user intervention during the boot sequence: [/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]1) During the boot sequence, select F9 to obtain Boot options in UEFI (BIOS) [/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]2) In UEFI / BIOS, select the available Ubuntu Linux 2.6.32-21 option and proceed. [/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]3) Ubuntu GRUB boot option screen is now available. Select preferred option and proceed. [/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]4) I'm in.[/FONT][/COLOR]
 
Of note: The exact same procedure with Mint 14.1 did not work. No matter what configuration I tried, the install on the hard drive would not boot. UEFI / W8 flew right by it, and no option in UEFI for Mint was present.

---

### Post by sudodus on 2012-12-24
Thanks for sharing!

Merry Christmas :KS

---

### Post by Timmseth on 2013-02-23
Sorry for coming in to this so late but there hasn't been a satisfactory answer to OP as far as I can tell so I thought I'd share some different information. 

Windows 8 POST is so fast that boot from disk is disabled by default, here's how you do it instead.
[LIST=1]
[*]Obtain Ubuntu ISO and burn to CD / bootable USB
[*]Insert CD or Plug in USB with Ubuntu ISO on it.
[*]Log out of Windows 8.
[*]While holding the Shift key, click on the Restart button to restart the computer.
[*]Keep holding Shift until the Windows 8 Troubleshooting menu appears. (now you can let go of the Shift key)
[*]Under Advanced Options there is an item that allows you to boot from CD under the pretext of windows recovery. This option will boot from your Ubuntu CD as well.(If I remember correctly it has a picture of a CD on the tile even.)
[/LIST]

Hope it helps! 
-Cheers

Sources: Been using Windows 8 Pro 64bit since before it was officially released (dreamspark).
I used this method in a dual-boot Windows-Ubuntu just the other day.

---

### Post by sudodus on 2013-02-23
Welcome to the Ubuntu Forums, Timmseth, and thanks to you too for sharing this tip, that will be helpful for many people at the Ubuntu Forums :-)

Feel welcome to start your own threads, whenever you need help or want to discuss some issue.

---

### Post by cdoebbler on 2013-05-19
Windows 8 only seems to boot on my Asus S400C VivoBook laptop. I turned off the SecureBoot controller and have a bootable USB with the ISO for Ubuntu 13.10 on it. I also checked the ISO and it is fine and my HP Mini 100c 1100ez boots from USB fine. The problem is that the Asus S400C VivoBook does not boot from USB and just goes into Windows 8. I want to keep dual booting.

---

### Post by sudodus on 2013-05-20
Hi cdoebbler,

I don't know the Asus S400C VivoBook laptop. Is there some hot key to give a menu to select which device to boot from (HDD, CD/DVD, USB, network)? Try the Function keys (F1-F12)! Or can you set the boot order in the BIOS/UEFI menu system?

Is there some information about this in the manual?

---

### Post by oldfred on 2013-05-20
Microsoft published this list of boot keys used my many vendors.
 UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

You should get two boot options, one UEFI and the other BIOS/CSM. 

Have you also turned off fast boot in UEFI as that is intended to skip the UEFI & boot keys and just boot Windows a bit faster.

---


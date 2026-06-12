---
title: "Will boot from DVD but wont open Install"
date: 2014-11-15
forum: Installation &amp; Upgrades
---

### Post by Kehlan_Rutan on 2014-11-15
Hello Ubuntu Forums, I am relatively inexperienced with Ubuntu but I want to change that! I have two HDDs in my computer and have cleared off my second to put Ubuntu on and run my system in duel boot.  Tech Preview of Windows 10 is on my 1TB and Ubuntu will go on my 500 gig.  I downloaded the image from Ubuntu and burned it onto my DVD.  Opened the files on the disk to make sure that it burned correctly and it did.  

Restarted my computer, booted from the DVD.  I see a standard Ubuntu screen with a purpleish background and a man icon at the bottom, but then it goes a way and it appears my monitor loses signal for a second.  Then the screen is black with a flashing command line in the top left corner.  The line becomes solid and smaller and then stops flashing.  I am unable to do anything during this process but turn off my computer and boot into Windows.  

At first I thought it was a bad image or something became corrupted so I tried it again on a new DVD and the same thing happened.  Any help is appreciated.  Thanks.

---

### Post by sudodus on 2014-11-15
Welcome to the Ubuntu Forums :-)

I suspect you have problems with the ***graphics***, that the graphics driver does not work. Please specify your graphics chip/card.

But it could be something else too. Did you check the iso file with ***md5sum*** - See this link

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

The graphics problem might be fixed with a boot option, start with **nomodeset**

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


You might also have problems due to the **wifi**, that the wifi driver does not work. Please specify your wifi chip/card.


There are more tips about booting from USB at the following link and links from it

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Mark Phelps on 2014-11-15
> have cleared off my second to put Ubuntu on and run my system in duel boot

Be aware that by default, Ubuntu will install GRUB to the "first" drive, in this case, your Win10TP drive.

To prevent that, do the following:
1) have the Win10TP drive disconnected when you install Ubuntu
2) reconnect the Win10TP drive after the Ubuntu install is done and Ubuntu is working
3) Boot into Ubuntu, open a terminal and enter "sudo update-grub".  This will regenerate the GRUB configuration file and should add an entry for Windows, such that when you reboot, you will get a GRUB OS selection menu.

---

### Post by Kehlan_Rutan on 2014-11-15
Awesome, thanks for the quick replies.  Unfortunately my wife is pulling me out the door at the moment but I will try these when I get home.  My video card is AMD Radeon 7770.  CPU is i5 3570K on a ASRock Extreme 4 Z77 for my mobo. Thanks again.  Will give you guys an update tonight.

---

### Post by Kehlan_Rutan on 2014-11-15
OK so I opened up the md5sum.txt file in Notepad, I assume the Hash is the list of 31 characters at the start of the text.  What is showing on the Notepad is not on the list on the link provided by @sudodus.  Is this the cause of the issue?

---

### Post by sudodus on 2014-11-16
It is quite likely the problem (or one of the problems). For example

```
md5sum ubuntu-14.04.1-desktop-amd64.iso
```

should give the output

```
119cb63b48c9a18f31f417f09655efbd  ubuntu-14.04.1-desktop-amd64.iso
```

If it does not, download the file again until it matches the checksum, or use a ***torrent***. The torrent method has a built-in check of the md5sum, which is good if the internet connection is flaky.

---

### Post by Kehlan_Rutan on 2014-11-17
So I downloaded the torrent and also tried again through the website.  Each time it gives me the md5sum of cde56251d6cae5214227d887dee3bab7.  Am I looking in the wrong location? What's going on?

---

### Post by coffeecat on 2014-11-17
> **Kehlan_Rutan said:**
> OK so I opened up the md5sum.txt file in Notepad, I assume the Hash is the list of 31 characters at the start of the text. 

No.

> **Kehlan_Rutan said:**
> So I downloaded the torrent and also tried again through the website.  Each time it gives me the md5sum of cde56251d6cae5214227d887dee3bab7.  Am I looking in the wrong location?

Yes.

What you have managed to do is to open the md5sum.txt file in the ubuntu-14.04.1-desktop-amd64.iso file, the first line of which reads:

> cde56251d6cae5214227d887dee3bab7  ./pics/red-upperleft.png

That md5sum is the hash for the file ./pics/red-upperleft.png. If you look at the rest of the file, it lists hashes for every file in the ISO. To determine the md5sum for the ISO file itself in Windows, have a look here:

[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows)

Having said that, if you downloaded the ISO by torrent from a reputable source, you don't need to check the hash as that is done automatically at the end of the torrent download.

---

### Post by sudodus on 2014-11-17
If you get the same md5sum, we can guess it is correct (for that file).

[s]- Which file are you downloading (tell us the file name)?

- From where are you downloading it (tell us the link)?

- Which torrent file did you use, and from where did you download the torrent file?

Finally, please post the exact command, that you use to get the md5sum.[/s]

*Edit: coffeecat* found the answer. No need now to answer these questions.

---

### Post by Kehlan_Rutan on 2014-11-18
Unfortunately this is not resolved.  I used a verified torrent.  The top seeded one.  I also tried running the install with **nomodeset. **All I get is still the blinking cursor after the original screen when I am able to press 0 and get to the Ubuntu boot options.

---

### Post by sudodus on 2014-11-19
Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It will help us give relevant advice.

---

### Post by Kehlan_Rutan on 2014-11-19
It is a computer I built.

CPU = i5 3570k
GPU = XFX AMD 7770
Mobo = ASRock Extreme 4 Z77
RAM = 4 sticks of 4 gig G. Skill 1866 (16g)
And it is a hard wired connection.  
[COLOR=#000000]


[/COLOR]

---

### Post by sudodus on 2014-11-20
I suspect the graphics card, that there is no built in driver that works with it.

You tried the boot option **nomodeset**. Now try the boot option **text**. See this link, that describes where to enter it

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Then if it works to run in text mode, you can try to install a proprietary linux driver for your AMD graphics chip/card. I have Intel and nvidia graphics, but no experience of AMD graphics. I hope other people can chip in an give detailed help.

---

### Post by Kehlan_Rutan on 2014-11-22
In the link you provided I do not see a boot option **text.**  It is a shame that this is so difficult to run.  I have ran Ubuntu on this machine back in the day (I forget which version) but since have formatted my disks.

---

### Post by sudodus on 2014-11-22
You add it at the end of the line that you get with F6

```
... quite splash -- text
```

according to the link [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

> [SIZE=4]Changing the CD Boot Option Configuration Line[/SIZE]

 In  addition to displaying a popup menu, the F6 key also activates in-line  editing of the boot command. Pressing F6 brings up the popup menu.  Pressing *ESC*, whether selections were made or not, removes the popup window but opens the boot command for editing. The phrase "**Boot Options**"  is fixed on the left side of the screen. The  command scrolls off to  the left to leave the right end available for appending. The user may  add additional inputs before or after the "**-- **". Allow one space between each additional input. 
The "**-- **"  entry defines the boundary between options which are specific to the  installer and ones that are copied to the target system. Often you would  like to copy the boot option to the target system, so add the option at  the very end of the line, after the "**-- **". 

[LIST]
[*]Editing the boot command line.
[LIST]
[*][IMG]https://help.ubuntu.com/community/BootOptions?action=AttachFile&do=get&target=Boot-F6-Other-Manual.png[/IMG] 
[/LIST]

[LIST]
[*]Press the **F6** key.
[LIST]
[*]If desired, select one or more options with the arrow keys, then press *ENTER* or the SPACE key to select them. 
[*]Any popup menu option enabled when *ESC* is pressed is retained. 
[/LIST]
  
[*]Press *ESC*  to remove the popup screen. The boot command line is now available for  editing and will remain so as long as no popup menu is visible. 
[*]Leave a space following the "--" and add the desired option (A list of [Common Boot Options]("https://help.ubuntu.com/community/LiveCDBootOptions#Common%20Kernel%20Options")  which can be added to the command line is presented later on this  page.). If entering multiple options leave a space between each entry. 
[*]The command will be executed when *ENTER* is pressed and the boot sequence will begin. 
[*]The F1-F6 keys will still respond and the user can make additional menu selections. 
[*]The command line will be accessible for appending until *ENTER* is pressed. 
[*]Pressing *ENTER* will start the boot sequence. 
[/LIST]
  
[*]Example Entry.
[LIST]
[*]Above is an example of adding the *vga=771* option to the end of the Boot Options line. 
[*]Note there is a space following "--" and before the added option. 
[*]Ubuntu  now uses Grub 2 as its bootloader. The "vga=" option shown in the  example is deprecated in Grub 2 but will still work. After Ubuntu is  installed on a system the user should make the appropriate graphics mode  entries in the Grub 2 configuration files. 
[/LIST]
   
[/LIST]


---

### Post by Kehlan_Rutan on 2014-11-22
oh ok thanks.  I didn't see where this was called text boot or whatever.  My bad.

---

### Post by Kehlan_Rutan on 2014-11-25
Adding "text" at the end of the -- made my monitor turn off lol.  I made sure to leave a space after the dash.  Any other suggestions?

---

### Post by sudodus on 2014-11-26
I think that there are problems with the graphics chip/card

GPU = XFX AMD 7770

I have not much experience of AMD graphics. If you, who are reading this, have a good guess, please chip in and help :-)

---

### Post by Kehlan_Rutan on 2014-11-26
I thought maybe a different distro would be more compatible.  Just tried making a Linux Mint Boot.  Almost the same thing.  Takes me to the initial Mint screen and then my monitor blacks out with a small white box in the top right hand corner.  Linux does not like a diver somewhere.  I guess I could try taking out the GPU then running the Ubuntu install and then inserting the AMD driver afterwords?  It would still use the same diver though right?

---

### Post by ubfan1 on 2014-11-27
Take a look at question [http://askubuntu.com/questions/522177/intel-amd-hybrid-graphics-on-ubuntu-14-04](http://askubuntu.com/questions/522177/intel-amd-hybrid-graphics-on-ubuntu-14-04)  
Looks like 14.10 might be necessary.

---

### Post by Kehlan_Rutan on 2014-11-27
I will try this, but I don't think it will work because this individual was able to boot with is intel graphics using nomodeset.  I wasn't able to do even that.

---

### Post by Kehlan_Rutan on 2014-11-27
OK, so I tried this and was actually able to get some form of error.  Though I do not know what it means.  I tried installation normally and with nomodeset option.  I took a picture of my screen with my cellphone.  I hope this helps shine some light on the problem.
[ATTACH=CONFIG]258251[/ATTACH]

---

### Post by ubfan1 on 2014-11-28
Guessing some sort of error on the DVD.  Did you burn it as slowly as possible?  Run a media check on it if you ever get to the menu offering it.

---

### Post by Kehlan_Rutan on 2014-11-28
Yes, I have done four different dvd's and even tried Linux Mint.  All give me some sort of error after the initial boot screen.

---

### Post by oldfred on 2014-11-28
Did you install Windows in BIOS/CSM or UEFI boot mode. 
You want to be sure to install Ubuntu in the same boot mode.
Your hardware should work in either mode and how you boot install media is how it installs.

But Asrock's have issues with ports, even if it is just DVD in Asmedia port:
 Some have issues with Asrock and its asmedia ports
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)
AsRock Z77 Windows always reset to default
[URL="https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order"]https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order

[/URL] Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[URL="https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order"]
[/URL]

---

### Post by Kehlan_Rutan on 2014-12-02
I can't even "Try Ubuntu without Installing."  When I do, I get this error.[ATTACH=CONFIG]258342[/ATTACH]

---

### Post by oldfred on 2014-12-02
See post #25, That is an error on a drive which means some drive is still plugged into the Asmedia ports.

---

### Post by Kehlan_Rutan on 2014-12-09
Sorry for the long wait on this issue.  I have since reverted back to Windows 7 Professional so I would have to have installed Windows 7 through BIOS.  And I assume that I am doing Ubuntu the same way.  So how can I fix the port issue? I am sorry if it was stated in the links but this is all a little beyond me.  It might need to be spelled out.  Again I thank all of you for your help.

---

### Post by oldfred on 2014-12-09
You have to look at your computer manual. Some ports are standard SATA and others are Asmedia. 
Do not use the AsMedia ports. They cause conflicts.

---

### Post by Kehlan_Rutan on 2014-12-10
You guys are gentlemen and scholars.  This issue is resolved.  I have another question but I will make another topic for it.  Thank you all for the help.  Special shout out to @oldfred.

---

### Post by sudodus on 2014-12-11
Congratulations :KS

*oldfred* has helped thousands of people solve their problems (also me, more than once). Please tell us the details of your solution. It will help other people at our Ubuntu Forums :-)

Finally, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by Kehlan_Rutan on 2014-12-11
Basically I moved the SATA cable from the AsMedia supported SATA3 to a SATA2 port.  Booted up fine.

---


---
title: "Error 21 at Startup"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by asketchyfish on 2007-02-09
Whenever I try to boot my laptop with no Live CD in all I get is a:
Stage 1.5
Starting GRUB
Error 21

and then the computer freezes.
My version of Ubuntu is on an external hard drive and my main hard drive contains Microsoft Windows XP SP2.
I have tried the following at no avail:
Boot from Windows CD - same error
Edit menu.lst file - read only no permission to edit or save

I was wondering if there was a way to get around GRUB so at least Windows boots (paper due tomorrow saved on the Windows partition).

Cheers,
Andrew

---

### Post by Herman on 2007-02-09
Hello asketchyfish,
Is this a brand new installation that has never booted?
Or is it an established installation that has been booting okay but has suddenly decided not to play the game anymore?

Anyway, with USBdisks, your BIOS is probably the first place to look for problems. Make sure your CMOS (BIOS) is set properly to boot the USBdisk.
And/or you can try pressing either 'F8' key or 'F12' key during bootup for a menu of bootable devices you can select to boot from.
Make sure your USBdisk is always plugged in when you boot.
It sounds like you installed Ubuntu on a USBdisk, but you install grub to MBR on your main disk?
If that assumption is correct, then the reason you are getting error 21 is because the first stage of grub in the first hard disk's MBR is not able to find grub's stage2 files in the USBdisk's Ubuntu parititon.

Grub error 21............................................[GO]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21")

I have never tried installing an operating system to a USBdisk, so maybe someone experienced in that can help you more than I can.
If you still can't get it to boot you should be able to use a [Super Grub Disk  ]("http://supergrub.forjamari.linex.org/")to boot Windows with for now so you can get to work on your paper. 
Then when that's done and you have some spare time you can deal with the booting problems later.

Regards, Herman :)

---

### Post by Herman on 2007-02-09
>  Edit menu.lst file - read only no permission to edit or saveI'm only guessing, but that most commonly happens when people try to do things in Ubuntu the same way they are used to doing things in Windows. It won't do you any good if you just navigate through your file system and find the /boot/grub/menu.lst file and open it and expect to be able to modify it. 

In Linux we have the whole system securely locked so such things as spyware and viruses can't run on it. Well, it's not so much locked exactly, but there are rules called 'file permissions' that set who is allowed to do what to certian files. To do anything vital to the system you need to use your terminal (go 'Applications'-->'Accessories'-->'Terminal', and open the file with a 'sudo' command.
The word 'sudo' typed in before a command means the system will ask you for your password, then you will be logged in as the administrator (or 'root', in Linux terms), and you will have permission to edit the file.
For example,
```
sudo gedit /boot/grub/menu.lst
```The above command will open the file for you, then you can edit it and save the changes in the normal way and close the file.

If that seems like extra work then just remember how much of your valuable time you spend updating and scanning with all those antivirus and anti this and that apps all the time. Not to mention re-installing . You'll really love Ubuntu when you get used to it, we just do what we want to do, we don't need to waste our time worrying about malware at all.

However, in your case I am don't think at this stage that your menu.lst file is the problem, but I could be wrong.

Regards, Herman :)

---


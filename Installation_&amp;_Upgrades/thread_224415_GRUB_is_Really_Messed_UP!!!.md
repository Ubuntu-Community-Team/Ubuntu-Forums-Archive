---
title: "GRUB is Really Messed UP!!!"
date: 2006-07-27
forum: Installation &amp; Upgrades
---

### Post by Dural on 2006-07-27
I have a system consisting of two hard drives; one has Windows XP and is 80 GB and the other is Kubuntu Dapper Drake with 40 GB. I used fdisk -l to figure out which drives were labeled in Kubuntu, with dev/hdc being the Windows drive and dev/hde being the Kubuntu drive.

Earlier today, I kept having problems trying to fix the screen resolution with my computer. This problem had taken about 2 weeks of my time, so I eventually decided to give up and reinstall Kubuntu. When I used the live CD that I had burned, the install worked until it finally decided to copy the necessary files to the hard drive, where it locked up. I reset the computer and tried the install CD that had been sent to me by Shipit, but the graphical installer froze before the configuration. I restarted the computer again, hoping that the then-current Kubuntu installation and the Windows Drive would be okay. But that's when things got worse, much worse.

When the computer tried to boot, I got this message:
Grub Step 1.5 -> Error 15
I looked up information around the net and learned that this means that GRUB is missing some vital files, so it can't boot. I then searched around for solutions to fix GRUB, ranging from using Windows XP Recovery Console to fix the master boot record to using the Kubuntu Live CD to enter the terminal and reinstall GRUB. Unfortunately, these methods did not seem to work. I am really frustrated right now, because this is yet another major problem I have had with Kubuntu and now I neither have access to Kubuntu nor Windows XP. I don't know if I can even reformat the Kubuntu drive and start over. I'm fairly new to Linux, though all of these problems have defnitely helped me learn more about the command line. So I ask... can my system be saved? :confused:

---

### Post by navilon on 2006-07-28
You're in luck, more than likley your files are still on the hard drive. You could either hook the drive up to a separate computer that already has windows xp installed and see if the drive shows up in my computer. Your second option is to reinstall windows. If you run the windows xp install disk and see your partition on the list then just tell it to install to that partition (rather than deleteing it at this point) and windows will replace grub with its own boot loader.

Let me know how it turns out.

---

### Post by Herman on 2006-07-28
I suggest you download for yourself a copy of GAG Boot Manager and use that to boot Windows with for now until you manage to find a way to get Ubuntu or Kubuntu installed. [*Click Here*]("http://users.bigpond.net.au/hermanzone/p12.htm") for more information.

All bootloaders come in two or three pieces. The main body of the bootloader is installed either in the operating system partition and/or in the first track of your hard disk. 
The MBR contains three things; an 'IPL' (Initial Program Loader) for the bootloader,  a partition table, and a 2 byte 55 aa signature.

When you deleted the Kubuntu partition, you also deleted the main part of GRUB, and just left the MBR with Grub's 'IPL' (also called 'stage 1') pointing to where it usedd to be, but it isn't there anymore, so you can't boot (for now).

You can also over write your MBR's bootloader section with the 'IPL' or first stage of your Windows bootloader. There are several ways to do that.
1) Use Windows Install CD. _For Windows XP_
        Just put in your Windows XP install CD, and boot into the [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") and use the fixmbr command.
2)          You can download a self extracting file to make your own Windows 98 boot floppy disk from [Bootdisk.com]("http://www.bootdisk.com/").  The one I use is called 98SE OEM and I have used it to restore the bootsector on both my Windows XP Home Edition computer and also my Windows 98SE computer. Just pop the floppy in the drive and boot your computer to the     A:\_   prompt and use the command fdisk /mbr and your 'boot sector' will be back to normal again.
3) Download and run MbrFix.exe from [http://danieltmurphy.com/blog/?p=44](http://danieltmurphy.com/blog/?p=44) 
For more info, see this thread:[Cannot access WinXP after having deleted partition]("http://www.ubuntuforums.org/showthread.php?t=224273")

I think ( and hope) you will be able to re-install Kubuntu or Ubuntu alright soon, but one of those methods should at least help you boot Windows until you do have better luck re-installing.
Regards, Herman :D

---

### Post by Dural on 2006-08-06
Saw the fixmbr/Windows XP install CD suggestion on another site, but I couldn't use it because I do not remember the administrator's password to the computer. At first, I tried typing in the password for my account, but somehow it did not work despite the fact that the account had full administrative privledges. 
So I'm going to try the GAG idea, but I have one question before I try this.
On the GAG site, I saw this bit of info: 
[I]GAG can be installed to MBR at any time if you decide to, and performs very well there. GAG is much simpler to use than any other boot manager. A great advantage of using GAG is that it is 'operating system independant', so when you decide to uninstall an operating system, you can just go right ahead and delete the partition it's on.  It won't affect your ability to boot your other operating systems, because GAG installs to MBR and the first track of your hard disk.
For this reason, GAG is very convenient for serious Linux connoisseurs who like to experiment a lot and sample different distros. You can multiple boot a whole smorgasboard of operating systems and add or remove operating systems as often as you like. GAG is very simple to re-configure after an operating system (or hard disk) is removed and new one is added. It saves a lot of time and effort compared with reconfiguring the other types of bootloaders every time, unless you are a real masochist and happen to actually enjoy all that work.[/I]
Would it be possible to do this and fix Kubuntu?

---

### Post by Herman on 2006-08-06
>  Would it be possible to do this and fix Kubuntu? No, not likely. I'm sorry to say this, but you already explained how you have made at least two attempts to overwrite your original install, neither of which have succeeded in a complete installation. 
So you have not got an installation that would be likely be bootable, and even if it would boot, it is unlikely to work very well at all. 
You will need to try again and hope your computer and the kubuntu installer will complete the install one of these times if you keep on trying. I wonder what could be the problem that is interupting your install attempts? 
Sometimes if you keep trying you'll be lucky. Other times it just isn't meant to be. You might have to try something different to get an install that will work. Maybe try Xubuntu if you think it might be a shortage of RAM, and also try installing that from an 'Alternative' Install CD, for a more reliable install.
> I used fdisk -l to figure out which drives were labeled in Kubuntu, with dev/hdc being the Windows drive and dev/hde being the Kubuntu drive. Normally, they would be /dev/hda and /dev/hdb in a standard computer. This computer sounds like a special one. Well, I guess you had it working before, so I suppose it should be able to work again.
Good Luck with it, Regards, Herman :D

---

### Post by Dural on 2006-08-06
> **Herman said:**
> No, not likely. I'm sorry to say this, but you already explained how you have made at least two attempts to overwrite your original install, neither of which have succeeded in a complete installation. 
So you have not got an installation that would be likely be bootable, and even if it would boot, it is unlikely to work very well at all. 
You will need to try again and hope your computer and the kubuntu installer will complete the install one of these times if you keep on trying. I wonder what could be the problem that is interupting your install attempts? 
Sometimes if you keep trying you'll be lucky. Other times it just isn't meant to be. You might have to try something different to get an install that will work. Maybe try Xubuntu if you think it might be a shortage of RAM, and also try installing that from an 'Alternative' Install CD, for a more reliable install.
 Normally, they would be /dev/hda and /dev/hdb in a standard computer. This computer sounds like a special one. Well, I guess you had it working before, so I suppose it should be able to work again.
Good Luck with it, Regards, Herman :D


Allright, I'll reinstall the MBR, then I guess I'll wait unti the next release of Ubuntu/Kubuntu. Have you used SimplyMEPIS? Maybe that will be more suitable for right now.

---

### Post by Herman on 2006-08-06
The MBR is not sacred. It's just another sector of magnetic flux that can have code written to it and be overwritten just like any other sector on our disks. It is nothing really. You won't wear it out, you can write it and overwrite it as many times as you like. 

Knoppix with a persistent /home is very good. It will be very similar to Kubuntu (with KDE),  In fact, Knoppix is another Debian distro, so it is fairly closely related to Ubuntu. You might find that a lot better since your computer doesn't seem to handle hard disk installs well. 

Good luck with it, Regards, Herman :D

---

### Post by Dural on 2006-08-06
It seems for every problem solved, there's another one, but that's just how it is with computers , eh? :)

I installed GAG and I was able to boot into Windows XP and finish reinstalling it, but then this happened:

*Copy Error: Setup Cannot Copy The File licwmi.dl_*

I clicked on the browse button, and the file is there on the CD (Windows XP SP1 Professional Edition, but when I click on the file, then tell the setup to retry, it repeats the same dialog. I checked both copies of Windows XP SP1 and it seems they need cleaning. Can eyeglass cleaner be used to clean CDs? 

Should the above not work, what is a good site to get replacement Windows .dll files without the worries of viruses & spyware?

---


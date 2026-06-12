---
title: "noob install help"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by loumt123 on 2008-03-01
Hey everyone - 

  I'm having some trouble installing Ubuntu 7.10. I just nuked my harddrive with Dban. I don't know if that un-formatted it or what, but I burned the ubuntu iso cd ok, I put it in the drive, it recognizes it, i select the install option, and I get a black screen that says some thing like "Busy Box Intaframs" or something. It doesn't install. Anyone have a clue what I did wrong or what I should do? Do I need to reformat the Hdd? How would I do that?

---

### Post by Giradman on 2008-03-01
Hello, not sure 'what' DBAN does to the basic formatting of your HD, but you might want to provide some info on your system, esp. RAM - about 6 months ago, my IBM laptop's HD died - ordered a new one & used the 'alternate' Ubuntu CD (had only 256 MB of RAM; and I had tried the regular ISO), which worked for me on the 'new' HD - then, doubled the RAM - running fine; so not sure if the problem might be the HD, RAM, or some other issue - but, good luck! I'm sure others will 'kick in' soon! :)

---

### Post by dstew on 2008-03-01
Often when your live CD drops out to the initramfs prompt the problem is with your hardware. Often it is a memory problem. I recommend running the memory test from the Live CD menu, and if that is good, run the CD integrity test. How much RAM do you have?

---

### Post by loumt123 on 2008-03-01
I did the memory test and nothing out of the ordinary came up. I have 256 mb of ram. When i checked the cd for errors, it dropped out to the initramfs screen.

What should I do next? is there another way to do the install?

---

### Post by uberlube on 2008-03-01
did you specify the VGA for your monitor during the boot process for the CD?

---

### Post by loumt123 on 2008-03-01
no...how would i do that...what is it even? The selection screen shows up but it could be a monitor problem? What do i need to do?

---

### Post by uberlube on 2008-03-01
when your in the boot menu for the live CD press F6 to edit the boot command and delete 'quiet splash' and then add 'vga=791' and press enter. Let me know what happens.

---

### Post by loumt123 on 2008-03-02
I changed it to VGA=791 and the screen turned black when i started it. Also, remember i ran DBAN harddrive nuke. Does that unformat the harddrive? Would I need to reformat it maybe? if so, how. any help would be appreciated.

also, is there another way to go about the install??

---

### Post by Pumalite on 2008-03-02
After DBan, you have to format that drive with Gparted Live CD:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.

---

### Post by loumt123 on 2008-03-02
How should it be formatted? NTFS? 

 I used that cd and formatted a partition as NTFS, tried the ubuntu cd again, and it didnt work. Is there another way to go about isntalling it?

---

### Post by Pumalite on 2008-03-02
Try formatting ext3. Otherwise check your BIOS or check the drive with TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by loumt123 on 2008-03-02
I formatted to EXT3 and it didn't work again, but this time I got to read some text before it went to the initramfs screen.

  It said something about Bios Bugs and maybe an SMPC error or something. Advice?

---

### Post by dstew on 2008-03-02
> When i checked the cd for errors, it dropped out to the initramfs screen.The Live CD should never do this. This implies that the CD is defective. Did you check the .iso file MD5 checksum before you burned it? Did you burn it as an image, and not as a file? Did you burn at 4x or slower speed?

After all that, there are other ways to install Ubuntu besides the Live CD. The Alternate Install CD is next best. After that there are network installation schemes, and installing from an .iso that is on the local network or on the same machine. See [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by loumt123 on 2008-03-02
MY burner only burns at 16x at the lowest =/

whats the checksum?

---

### Post by Pumalite on 2008-03-02
[http://en.wikipedia.org/wiki/Md5sum](http://en.wikipedia.org/wiki/Md5sum)

---

### Post by wednesday allfather on 2008-03-02
Try formatting to FAT32, ext2, or ext3, yet?  I don't think Linux likes NTFS any more than Windows likes ext3.:popcorn:

---

### Post by loumt123 on 2008-03-02
I tried the alternate cd, and the problem now is it can't detect the cd rom drive. It boots the cd, I get to that step, but it can't detect my drive. I have no clue what to do there, but it's a laptop cd rom drive. How do I install this easier haha

---

### Post by Pumalite on 2008-03-02
Post the exact error message.

---

### Post by loumt123 on 2008-03-02
I think installation via USB stick may be the best way to go, but I can hardly make sense of the directions. I don't even know how to edit the isostick.sh file

So I download the script, and then do i copy and paste this "wget [http://www.startx.ro/sugar/isotostick.sh](http://www.startx.ro/sugar/isotostick.sh)
chmod u+x isotostick.sh
sudo ./isotostick.sh ubuntu-7.10-desktop-i386.iso  /dev/sdX1" into it somewhere? And do I replace the /dev part with the name of my usb stick? is that just what the cpu recognizes it as? how would i find this out.

---

### Post by Pumalite on 2008-03-02
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by loumt123 on 2008-03-02
lol....I know I read it and I just said I couldn't make 2 cents of the directions.

Like this part "Insert the USB device you want to use for the installer. A few seconds after plugging in the USB device run the dmesg command or sudo fdisk -l to find device it was assigned." 

I don't even know how to run the command..or for that matter I don't even know what syslinux is or where to get it.


EDIT:  I just downloaded syslinux 3.62, but how am i supposed to install it. Remember, this is my first time attempting to install linux on a computer and the computer im using to make the cds and stuff is a windows pc. How do i work syslinux from windows to ready the USB stick. this is soooo confusing.

---

### Post by Pumalite on 2008-03-02
Do you have a bad burner? You could download ImgBurn: [http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Install
Go to Mode>ISO>Burn

---

### Post by loumt123 on 2008-03-02
I don't think it's my burner I really don't know what it is all I know is when I stick the cd in the computer I want ubuntu on I'm noticing text that says "Bios Bug" and "smp errors detected"

I'm not sure if that's relevant or not.

---

### Post by loumt123 on 2008-03-02
Working from windows, how could I get the USB installer to work?

---

### Post by Pumalite on 2008-03-02
Burn a new CD with the instructions I gave you and the program I gave you the link to.

---

### Post by loumt123 on 2008-03-02
I burned a disc using that program at 4x, and still the same problem. After hitting install and after it says "Loading Linux Kernel" I get a black screen that says Bios Bug, MP Table Errors and then that goes and I get an Ubuntu screen with the Ubuntu logo and a bar under it that goes back and forth, and after that I get the initramfs screen. Where to now?

---

### Post by loumt123 on 2008-03-03
anyone? how about preparing a USB stick in windows...any idea?

---

### Post by Pumalite on 2008-03-03
Go to your BIOS and set it to 'default values'

---

### Post by loumt123 on 2008-03-03
ok, set it to default and now the cd wont boot.

---

### Post by Pumalite on 2008-03-03
Of course.

---

### Post by loumt123 on 2008-03-03
I'm no genius when it comes to computers. I did notice that the bios are set to recognize usb, so if I could figure out how to format this stick I could do it. 

  Otherwise, is there any info I should be looking for in the bios that could be a clue to anything?

---

### Post by loumt123 on 2008-03-05
.....

---

### Post by dstew on 2008-03-05
So, just to get back in the game, you want to install Ubuntu, but the CD-ROM refuses to work, for whatever reason. Is that right? And you want to install from a USB stick, correct?

Some questions before we start. Does your computer have the ability to boot the USB stick? If so, there should be a setting for that in your BIOS. Does your computer have a floppy drive? Does it have an ethernet cable connection? If so, do you have DSL or faster internet that you can plug into? Finally, what kind of working computer do you have, Windows or Linux (the computer you use to post to the forum)? Please answer all these questions the best you can, and we can come up with a plan.

---

### Post by loumt123 on 2008-03-05
According to my bios, it can recognize the usb stick. The computer is a notebook, so no floppy drive. It does have an ethernet cable connection, and I have broadband (cable) I think it's faster than DSL. I post on here from a windows or mac computer.

Thank you :)

---

### Post by Pumalite on 2008-03-05
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by loumt123 on 2008-03-05
pumalite, remember you sent me that link a couple pages back and I said I was on a windows computer and couldn't make sense of the directions, such as installing syslinux etc etc.

---

### Post by Pumalite on 2008-03-05
Sorry; let me think. Maybe this will do:
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

---

### Post by loumt123 on 2008-03-05
ah now this is something i can manage. I'll give this a go and post my results

---

### Post by loumt123 on 2008-03-05
woah woah woah what u just gave me screwed up this computer. now when i boot windows it's asking me about ubuntu? what is going on. 

 Let me clarify, I am posting from a WINDOWS computer.I am trying to install ubuntu on ANOTHER computer.

How in the heck do I uninstall the download from the link you just gave me that prompts me when I start windows? It was the first download on that link...I cant even find it to uninstall it ugh!

---

### Post by Pumalite on 2008-03-05
What did you do? And from where?

---

### Post by loumt123 on 2008-03-05
The first link from under "Automatic Process" it's trying to install ubuntu on this computer or something thats not what i want i need to install it on a computer that just had it's harddrive reformatted and wiped with no os on it

---

### Post by Pumalite on 2008-03-05
You have to stick to the computer you want to install on

---

### Post by loumt123 on 2008-03-05
that computer has always been the one whose hard drive I wiped, reformatted, and have been trying to install on since I posted here. 

Again, there is no OS on it, it is freshly wiped. The CDs will not work in it. I am trying to find another option to install ubuntu on it. THIS computer, the one I type here from, is the one with windows on it. Again, I do not want UBUNTU on the one I am typing from. However, this computer is the only way I could format a USB stick for the use of installing UBUNTU on the blank machine.

---

### Post by loumt123 on 2008-03-06
Anyone?

oh, and pumalite- ever since you told me to set my bios to default i haven't been able to boot ANY cd on start up...dban won't start, the harddrive partion cd wont start, etc.

---

### Post by dstew on 2008-03-06
If you can boot the USB drive you have several options. You can put the .iso file onto the USB and install it using the Gujin boot loader. See [http://ubuntuforums.org/showthread.php?p=4460146](http://ubuntuforums.org/showthread.php?p=4460146). You can create a [Live USB stick and install from there.]("https://help.ubuntu.com/community/Installation/FromUSBStick")You can install Ubuntu over the internet using the [unetbootin]("http://lubi.sourceforge.net/unetbootin.html") program.

Look over those pages, and let us know which method you want to try, and we can help you to do it.

---

### Post by loumt123 on 2008-03-06
well the computer i want to install it on is completely devoid of any OS and after following pumalite's instructions and setting my bios to default it won't even boot cds like dban. 

So, I don't think I can get it installed over the internet. Also, since that computer can't even recognize CDs now, I don't even think I can put it on the USB stick (apparently I need the computer to recognize the live cd to copy it onto the USB stick). If I can prepare the USB stick from this computer (without screwing it up) and stick it into the computer that doesnt have anything on it, that would be ideal.

Creating a live USB stick sounds like it would be ideal...that way I can stick the USB stick in the blank computer and install, but the only problem is to prepare it it seems like you need linux. I am running from windows so I don't know how i'd be able to prepare a live usb stick.

Can I prepare my USB stick using isostick.sh through windows? It says it's the easiest method, but I don't know how I'd make the script executable, or if you could make it executable in windows.

---

### Post by runnerdi7 on 2008-03-06
I am also in the process of installation, (posting from the live version) before install.  I am trying to install 7.1.  I go to install and get through the wizard up to the partition page.  It asks me to prepare partitions, but there is no slider, no HD and i can't type anything in.  Any suggestions?  Also, windows vista will no longer boot, the only way i access an OS is with the Ubuntu cd in.  Any help would be appreciated.

I am on a lenovo T61 

# Processor Intel Core 2 Duo T7300 @ 2.00GHz
# 4MB L2 Cache
# 800 MHz Data Bus Speed

Memory
# 1GB (1x1024)
# 3GB Max (std mem in 1 socket / 1 socket avail)
# Type: PC2-5300 667MHz DDR2

Drives
# 120GB Hard Drive (5400 rpm) featuring ThinkPad HDD shock absorber and Active Protection System
# DVD±RW (±R DL) DVD and CD burner
# Floppy drive not included

Display and Graphics
# 14.1" WXGA+ (1440 x 900)
# nVIDIA Quadro NVS 140M with 128MB
Windows Vista Premium Certification

---

### Post by dstew on 2008-03-06
> Can I prepare my USB stick using isostick.sh through windows?No, but you can prepare a bootable Ubuntu USB stick from Windows by hand. The isostick.sh script only runs in Linux.

If you want to make a bootable Ubuntu installation USB stick on your Windows machine, we can walk you through it. First, you need at least a 1 Gb stick. Download onto your Windows harddrive desktop the latest syslinux.zip file from [here]("http://www.kernel.org/pub/linux/utils/boot/syslinux/"). Unzip the archive. You should get a syslinux folder on your desktop. The syslinux.exe file is inside the win32 folder.

---

### Post by BobSongs on 2008-03-06
> **loumt123 said:**
> well the computer i want to install it on is completely devoid of any OS and after following pumalite's instructions and setting my bios to default it won't even boot cds like dban. 

So, I don't think I can get it installed over the internet. Also, since that computer can't even recognize CDs now, I don't even think I can put it on the USB stick (apparently I need the computer to recognize the live cd to copy it onto the USB stick). If I can prepare the USB stick from this computer (without screwing it up) and stick it into the computer that doesnt have anything on it, that would be ideal.

Creating a live USB stick sounds like it would be ideal...that way I can stick the USB stick in the blank computer and install, but the only problem is to prepare it it seems like you need linux. I am running from windows so I don't know how i'd be able to prepare a live usb stick.

Can I prepare my USB stick using isostick.sh through windows? It says it's the easiest method, but I don't know how I'd make the script executable, or if you could make it executable in windows.
[FONT=Verdana] Here are a different set of instructions. I've tried their site before and found that if you follow their steps without varying their suggestions: all works well.

[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

**Note**: you did a reset on your BIOS. That may or may not be effective. But since you have reset it you'll need to rummage through each screen of your BIOS to find the Boot area. Once there you'll need to reset the Boot Sequence to start with CD-ROM or USB. That's apparently the difficulty you're facing at the moment.

**Edit**: Oops. Looks like that link is a link to installing Ubuntu **to** a USB drive and not putting it on a USB drive to be installed on your hard drive (though it's possible what you set up on the USB has the installation icon intact on the desktop when you boot from the USB device - Testing that now, will post results). Sorry about that. But from what I've read in this post it appears your CD may be defective. Is it possible to download it on another system and test it there?
[/FONT]

---

### Post by loumt123 on 2008-03-06
Thanks for the help. First, I'm going to try to set the boot order and see if I can get any cd to boot (the ubuntu one, dban, just to make sure it works). If I can't, I'll continue with the syslinux option and extract it on to my desktop. I'll give an update later with my progress.

---

### Post by loumt123 on 2008-03-06
Ok, it's all extracted and I found the syslinux exe in the Win32 folder. 

Where do I go from here?

---

### Post by dstew on 2008-03-06
Copy the syslinux.exe file to your Windows root directory. I assume your USB stick is already formatted. When you plug it in, Windows should recognize it, and give it a drive name. Look in My Computer and find the USB drive. Let's say Windows named it F:. Then, to make the USB stick bootable, go to the Start menu, Run, and enter ```
syslinux -s F:
```If you get no errors, check to see if there is the file ldlinux.sys in the root directory of the USB drive. It is a hidden file, so you might have to use the Show All Files option in your View menu if you are using the Windows file exporer. Or, just do ```
dir /a F:
``` in the Run line.

---

### Post by BobSongs on 2008-03-06
[FONT=Verdana]OK.

Just to let you know and bring you up to date.

I'm surfing the web right now from my 4 Gb USB PenDrive. The site in my post above shows you how to install Ubuntu Gutsy Gibbon to a PenDrive with the option to install the system from the USB PenDrive to your hard drive.

Sweet. It is exactly as I said. I followed the set up which requires the LiveCD Ubuntu Setup disk. If your copy is flawless and the burn was successful then all should work according to PenDrive Linux's website.

I could, from this point, install Ubuntu on my hard drive. Since it's already installed... that's rather pointless. So, you've been given a new alternative that actually works.

Again: follow the site's instructions point by point without missing a step or deviating and you'll successfully install Ubuntu Gutsy Gibbon to a Pendrive.

Oh: a note. The boot seems to take forever. That's OK. Once it boots you're fine.[/FONT]

---

### Post by loumt123 on 2008-03-06
pardon my ignorance, but where can the root directory be found? is that just the main harddrive?

---

### Post by Pumalite on 2008-03-06
[http://www.faqs.org/docs/linux_intro/sect_03_01.html](http://www.faqs.org/docs/linux_intro/sect_03_01.html)

---

### Post by loumt123 on 2008-03-06
Pumalite, what you sent was for a linux file system. This is going into my windows root directory. I don't know where it is.

---

### Post by dstew on 2008-03-06
> pardon my ignorance, but where can the root directory be found? is that just the main harddrive?Yes, it is the top directory of the hard drive. If your hard drive is C:, the root directory is C:\ The root directory will usually have the boot.ini file, autoexec.bat, config.sys (at least in XP, don't know about Vista).

---

### Post by loumt123 on 2008-03-06
Ok, it's in the root, and my computer recognizes the usb stick as " UDISK 2.0 (E: ) " Would I type UDISK 2.0 or just E: . If just E, I typed that in "Run" and there was nothing on the USB stick that I could see.

---

### Post by dstew on 2008-03-06
Go to the Start menu, Run, and enter ```
syslinux -s E:
```

---

### Post by loumt123 on 2008-03-06
I ran that and it asked me to allow the program to run, I clicked allow, so I assumed it was doing something. No errors. Them I checked the USB stick, with seeing hidden files on, and could find nothing.

---

### Post by dstew on 2008-03-07
Can you copy any files to the USB stick? Make sure it is formatted, and not write protected. Check the properties of the USB stick (My Computer, highlight the USB drive, right click, properties). Some USB sticks have a write-protect switch, like the old floppy disks.

Also, just try to copy some file to the stick to see if you can write on it.

---

### Post by loumt123 on 2008-03-07
I can write to it easily.

Ok, update. I fooled around with the bios and got the CDs to boot again. I can now copy the live CD to the USB stick if someone posts a link for directions. Also, I can reinstall windows and install from windows if possible.

---

### Post by dstew on 2008-03-07
> I can write to it easily.At this point I cannot figure out what the problem is. Syslinux should have written the ldlinux.sys file to the root directory of the USB stick after the syslinux -s E: command. Are you sure that the command you used targeted the USB stick properly (that is, it was E: and not F: or G: )? You can also just test the USB stick to see if you can boot from it. Change your BIOS to boot from the stick. If it is bootable, you should get a boot:_ prompt. Of course, there is nothing on it to boot, but at least you know that the syslinux command worked, even though you cannot see the ldlinux.sys file.> Ok, update. I fooled around with the bios and got the CDs to boot again.Do you mean in your Windows computer, or in the computer you are trying to install to?

EDIT: Is your Windows machine XP or 98? Also, was the USB stick formatted FAT16, or FAT32?

---

### Post by loumt123 on 2008-03-07
The computer I'm trying to install to. I fixed the bios so It boots the cds like the live cd, and I'm pretty sure I recall a method in which you can copy the live cd over to a USB stick or something through the live cd main menu or something.

---

### Post by Pumalite on 2008-03-07
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by loumt123 on 2008-03-07
ok awesome i'm pretty sure the first link was what i was looking for. I searched the documentation site and googled it but couldn't find it.

By following the directions in the first link, can I install from that newly created usb stick, or is does it just run from the usb stick but can't install from it?\

ah wait i don't know if I can do that one...I have to download a zip file on the blank computer but there's no OS on it yet so I can't.

---

### Post by Pumalite on 2008-03-07
You said you had fixed your computer to boot a Live CD. That link I gave you is to INSTALL TO a Pendrive

---

### Post by loumt123 on 2008-03-07
ahhh I see I'm trying to install FROM a pendrive haha. Nothing I do seems to work, though :confused:

   If I could figure out why the computer goes to the initramfs screen every time i try to install from the live cd, maybe I can actually get it to install.

---

### Post by Pumalite on 2008-03-07
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by loumt123 on 2008-03-07
Ok, so I did an experiment. The computer will run a windows install cd and install it, but ubuntu will not install from the cd (i get brought to an initramfs screen). Could this knew knowledge help reveal my problem?

---

### Post by Pumalite on 2008-03-07
Maybe what you need is DBan your drive: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)
Then get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Delete anything left in your hard drive (if any) and make a NEW large partition of your whole hard drive, formatted ext3. Then install Ubuntu>Guided>Use Entire Disk

---

### Post by loumt123 on 2008-03-07
that sounds similar to what i did originally but I'll go through it again. What dban setting should I use? the most thorough wipe or the quick wipe?

---

### Post by Pumalite on 2008-03-07
Quick wipe.

---

### Post by loumt123 on 2008-03-07
still can't get it to install =/. but for what it's worth, i now have a freshly cleaned ext3 hdd

---


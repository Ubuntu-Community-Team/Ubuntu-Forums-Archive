---
title: "Flash BIOS, Or How To Up-Date BIOS?"
date: 2014-06-04
forum: Installation &amp; Upgrades
---

### Post by Adler on 2014-06-04
Hi All,

Firstly, I have searched through the Forum, and have not found any suitable answer to my question. I have a HP SPECTRE XT ULTRABOOK 13T-2100, and want to up-date the BIOS before I install 14.04 LTS. 

The machine was wiped to install 12.04 a while back, so I can't install the .exe file that you can download from the H-P site. 

Any help would be appreciated.

Adler
*Down On The Jersey Shore*

---

### Post by Proinsias on 2014-06-04
Try pasting the bios file to a fat32 or exfat formatted usb flash drive, the bios should detect it and you can update your bios without any OS on the machine.

---

### Post by Adler on 2014-06-05
> Try pasting the bios file to a fat32 or exfat formatted usb flash drive,  the bios should detect it and you can update your bios without any OS  on the machine. 		

Proinsias,

Thank you for the reply. I have downloaded a file called sp63472.exe from the H-P site. I can put this on a fat32 formated flash drive. However, things get a little hazy (LOL) what to do next. I assume I should boot my system, then direct the boot process to the USB Drive. Am I correct? I would have an OS on my machine, so do you mean wipe the drive, then do an install?

I look forward to hearing back from you.

Adler
*Down On The Jersey Shore*

---

### Post by LastDino on 2014-06-05
Usually there is function in your driver CD that allows you to update BIOS directly, every machine I've, has this available. To run .exe without windows would be possible from Wine, but I wont bet on its ability to do the job correctly.  

Here is description of methods possible.
[http://www.wikihow.com/Reflash-BIOS](http://www.wikihow.com/Reflash-BIOS)

---

### Post by Adler on 2014-06-05
>  		 				 				 					 				 		 			 				[INDENT] 					Usually there is function in your driver CD that allows you to  update BIOS directly, every machine I've, has this available.[/INDENT]



LastDino,

My machine came pre-installed with M$ 8. Finding the BIOS Driver, on the back-up DVDs, would be problematic. 

Adler
*Down On The Jersey Shore*

---

### Post by mörgæs on 2014-06-05
When I upgrade BIOS I create a bootable USB drive with Feedos, which can be done from Unetbootin. Copy the exe file to the USB stick and boot from here.

---

### Post by Proinsias on 2014-06-05
> **Adler said:**
> Proinsias,

Thank you for the reply. I have downloaded a file called sp63472.exe from the H-P site. I can put this on a fat32 formated flash drive. However, things get a little hazy (LOL) what to do next. I assume I should boot my system, then direct the boot process to the USB Drive. Am I correct? I would have an OS on my machine, so do you mean wipe the drive, then do an install?

I look forward to hearing back from you.

Adler
*Down On The Jersey Shore*

Once you have the file on the usb boot into the bios on the machine, depends on the model but often holding/tapping F2 or some other function key will do the trick. Once in the bios menu you should, hopefully, see an option to update the bios which upon accessing will prompt for the location of the file on the usb drive. The bios can then update itself from the file on the usb drive.

There should be no need to boot into the current OS or wipe/install anything to internal drives.

---

### Post by mörgæs on 2014-06-05
It's an exe file. It needs some operative system in which to run.

---

### Post by Adler on 2014-06-05
> It's an exe file. It needs some operative system in which to run. 		

mörgæs,

So, you are favoring the response, that Proinsias suggested?

Adler
*Down On The Jersey Shore*

---

### Post by Mark Phelps on 2014-06-05
If memory serves me correctly, all the downloads from the HP site, which are packages as .exe files, are actually self-extracting archives.  Once extracted, I believe that all you're going to see is a .bin file.

Keeping Windows on the PC, in dual-boot mode, enables such things as BIOS updates and firmware updates which, otherwise, are very difficult, if not impossible, to do.

---

### Post by tgalati4 on 2014-06-05
An option that worked for me:  I created a small partition (100 MB or so) on the main hard disk and put *freedos* on it using a tutorial I found on the web.  It shows up in GRUB so I can boot into *freedos* any time I need to.  Then put your *.exe files on there by simply copying the file or files to the partition from within linux.  Once booted in *freedos*, you get a DOS command line and you can run the executable which will bring up the flasher, make a BIOS backup (this is important), and flash the new BIOS.

---

### Post by Proinsias on 2014-06-05
I was thinking along the lines of this:

[http://h30434.www3.hp.com/t5/Notebook-Lockups-Freezes-Hangs/How-to-update-Bios-from-USB-flash-drive/td-p/687129](http://h30434.www3.hp.com/t5/Notebook-Lockups-Freezes-Hangs/How-to-update-Bios-from-USB-flash-drive/td-p/687129)

I recall using unzip to extract the .exe archive, pasting the files to the usb and selecting it in the bios from there....but that wasn't a HP machine, so ymmv.

---


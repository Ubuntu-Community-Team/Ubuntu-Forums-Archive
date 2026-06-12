---
title: "Problems Ubuntu Live USB Persistant casper-rw Larger than 4GB adjustment Not Working"
date: 2015-10-02
forum: Installation &amp; Upgrades
---

### Post by Mahogan on 2015-10-02
I have a Patriot 32GB USB 3 drive and have been following this method: [https://wiki.ubuntu.com/LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")

My goal is to actually buy a 128gb Live USB and use this as my go between from work and home and another location.  

I am having some problems getting the persistant storage space larger than 4gb

First problem, following the steps of Method 0, when using gparted to shrink the FAT32 as small as allowed and add a the rest of the drive space to a new EXT2 partition, when applying the changes gparted just crashes (dissapears) and the changes are not done.  I have tried this on several computers and several drives, all the same result (14.04LTS).  I have also tried this with gparted 11.04 and still get an error.

So I solved this by starting over and manually created two partitions, a 3gb FAT32 partition and the balance as an EXT2 primary partition (named this partition 28gb).  Then used Startup Disk Creator and installed the Live USB on the FAT32 partition.  Then mounted this, searched for the casper-rw file then deleted it.  Then with gparted, renamed the EXT2 partition from 28gb to casper-rw.

Then rebooted with this drive and it works and loads, actually am using this right now to write this question.  It shows both drive icons as mounted, the FAT32 as 4.1gb size and the EXT2 as 28.1gb size. 

Second problem, when testing to see if this actually is using the entire 28gb as usable storage space, program installs etc that remain live when rebooting, I attempted to copy a 5.8gb folder to the desktop, and I get a message that there is not enough space available.  So I tried copying the file to the casper-rw and the error gives permission denied.

So, question, what am I missing here?  According to the link above, it seems like using more then the 4gb is possible, but I just cant seem to get this working properly.

---

### Post by Skaperen on 2015-10-02
method 0 says: "Note that the maximum space that can be allocated for persistence is  limited to 4GB (maximum file size on a FAT32 filesystem is 4GB)."

i am guessing this is a FAT32 limitation.  FAT32 is probably used so you can access the persistent file in Windows.  do you need toyou can access the persistent file in Windows?  having nothing that runs Windows, i use ext4 for my persistent files.

life would be so much easier w/o Windows, even for me (i'd not have to sift through long documents so often), or deal with all the FAT stuff (i reformat all my devices, anyway), and google results would not have so much noise.

i just **dd** the latest .iso images to the flash drives (actually, i have my own program that works unbuffered, and shows progress numbers).  but i do understand that people with no bootable linux media around must make it with something else, the first time.

---

### Post by sudodus on 2015-10-02
Since you used the Startup Disk Creator, I understand that you are running Ubuntu (or an Ubuntu family flavour). I think the method you have used is good and *should* work. Maybe you have problems to buffer copying of huge files without a swap file. Maybe there is some other (small?) error preventing it from working for huge files.

If you want a tool to create a persistent live system with a working casper-rw partition directly (where the size is only limited by the size of the pendrive), you can try mkusb. See this link

[mkusb#Persistent_live_systems](https://help.ubuntu.com/community/mkusb#Persistent_live_systems)

*Edit:* I wanted to check if there is some limit at 4 GB file size in a live system without a swap partition. So I created a 5 GB file in my 'production computer' which is also a local ssh server. I connected via sftp and downloaded the 5 GB file to a persistent live system (LXLE 12.04.5 revisited, i386), and it worked. (There is not physical space enough in that system to have both a 5 GB source file and a 5 GB target file.)

---

### Post by yancek on 2015-10-02
If you created a 3GB FAT32 partition and put the Ubuntu iso on that partition you have a FAT32 partition 4.1GB in size which is right.  You won't be able to add more than 3GB in files/folders here as that is the maximum size available.  Since you have a 28.1GB Linux partition, you can put that much data on it.  It is not going to be available under your /home/user/Desktop.  The default for partitions is to make them available under the /media directory.  If you look under /media/ubuntu, you should see a casper-rw partition and that is where you copy the data.  You can boot the flash drive and use the sudo chown commad on that mount point to change the owner from root to ubuntu user.

---

### Post by Mahogan on 2015-10-02
Thanks for the replies. 

@Skaperen - it would be nice to share files from the Live Ubuntu persistant partition, as I use Inkscape and use these in Adobe Illustrator.  Question, you say you used ext4, I read that on a pen drive it is best to use ext2, not sure why.  I understand your thought on a world without windows, I have the same desire, but as a graphic designer in the industry, this will never happen for me.  I would like to format the persistant partition so that it could be read from windows, but plan on sharing my files via Ubuntu and copying them to a mounted windows folder.

@Sudodus - I too thought maybe there is an error in my pen drive, so I tried another drive and get the same problem.  I may try the install from a different computer to see if there is the same glitch but think that there will be no difference.  I will review the mkusb method, at first glance it seems difficult, I am a novice geek, so will have to re-read the instructions about 20 times before it might click. One thing I will mention is that I did also try this with the exact failed results that I am having with the Startup Disk Creator.  [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")

@Yancek - I was really surprised that when I manually created a 3gb FAT32 partition that after installing it reads 4.1GB.  I did 3gb because after several attempts at shrinking the FAT32 it was only about 2gb, so I figured 3gb was more than sufficient. So I am not sure what is going on there.  Concerning the 28.1GB partition, I went to the media/ubuntu location and see the casper-rw partition and open the folder and see two folders named 'upper', 'work', and a file named format.  When dragging any file, even small, to any of the folders or the casper-rw folder, it will not copy, no error message, just the icon is animated back to the source, so it does not work.  When you say  > You can boot the flash drive and use the sudo chown commad on that mount point to change the owner from root to ubuntu user.  can you please explain to a non-geek how to do this?

---

### Post by sudodus on 2015-10-02
> **Mahogan said:**
> Thanks for the replies. 

@Skaperen - it would be nice to share files from the Live Ubuntu persistant partition, as I use Inkscape and use these in Adobe Illustrator.  Question, you say you used ext4, I read that on a pen drive it is best to use ext2, not sure why.  I understand your thought on a world without windows, I have the same desire, but as a graphic designer in the industry, this will never happen for me.  I would like to format the persistant partition so that it could be read from windows, but plan on sharing my files via Ubuntu and copying them to a mounted windows folder.

ext2 is simpler than ext4, for example there is no journaling. I use ext4 with journaling turned off in the systems made with mkusb. The problem with journaling is that it wears the pendrive's flash memory with repeated writes (and the lifetime is much shorter than that of a hard disk drive.

Unfortunely Windows 'does not want' to read linux file systems, and the casper-rw file system must be a linux file system. But if you have a big FAT32 file system in the first partition, you can write files there and they will be available for Windows and MacOS.

*Edit:* 'plan on sharing my files via Ubuntu and copying them to a mounted windows folder'. This is possible, but safer to write to a separate data partition. But that partition must be on a *different* drive (internal or external), not on the persistent live pendrive.
> 
@Sudodus - I too thought maybe there is an error in my pen drive, so I tried another drive and get the same problem.  I may try the install from a different computer to see if there is the same glitch but think that there will be no difference.  I will review the mkusb method, at first glance it seems difficult, I am a novice geek, so will have to re-read the instructions about 20 times before it might click. One thing I will mention is that I did also try this with the exact failed results that I am having with the Startup Disk Creator.  [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")

I admit that I am prejudiced (because I made it), but I think it is easy to use mkusb ;-) [Install it via a PPA](https://help.ubuntu.com/community/mkusb/gui) and go ahead. Mkusb makes the FAT32 so that it is owned by the default user, so you can write to it directly. (In a system made with the Ubuntu Startup Disk Creator the FAT32 file system is owned by root (the superuser), and you need superuser privileges to write there.)
> 
@Yancek - I was really surprised that when I manually created a 3gb FAT32 partition that after installing it reads 4.1GB.  I did 3gb because after several attempts at shrinking the FAT32 it was only about 2gb, so I figured 3gb was more than sufficient. So I am not sure what is going on there.  Concerning the 28.1GB partition, I went to the media/ubuntu location and see the casper-rw partition and open the folder and see two folders named 'upper', 'work', and a file named format.  When dragging any file, even small, to any of the folders or the casper-rw folder, it will not copy, no error message, just the icon is animated back to the source, so it does not work.  When you say   can you please explain to a non-geek how to do this?

---

### Post by Mahogan on 2015-10-02
@Sudodus - Ok, I tried the mkusb, installed via PPA as suggested.  It did copy the iso to the usb and I booted from and tried to copy a 5.8gb folder to the desktop and get the error that there is not enough space.  So I canceled the copy and went to gparted and get this message:

> /dev/sdb contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition table, as it should.  Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?

I have never seen this before, not sure what to do.  Sorry, but I guess I must be confused.

---

### Post by sudodus on 2015-10-02
I think you created a live-only pendrive. You must 'have selected' ***persistent live*** in the main menu in order to get a persistent live pendrive.

[mkusb#Persistent_live_systems](https://help.ubuntu.com/community/mkusb#Persistent_live_systems)

---

### Post by yancek on 2015-10-02
>  I was really surprised that when I manually created a 3gb FAT32 partition that after installing it reads 4.1GB.

The 1.1GB Ubuntu iso is included which would make it 4.1GB.  As to the /media/ubuntu/casper-rw, you need to check the owner:group and permissions which you can do with:

```
ls -l /media/ubuntu
```

Check the output.  If you can't write to it, it is most likely because the owner:group is root:root.

If you have a /media/ubuntu/casper-rw directory you should be able to give user access with the command below, if the user is in fact ubuntu:

```
sudo chown -R ubuntu /media/ubuntu/casper-rw
```

I didn't use the method you did so if it doesn't work, you may need to use mkusb which does work.  It also worked with a persistent unetbootin and a separate partition.

---

### Post by Mahogan on 2015-10-02
@yancek - thank you for showing me how to use the commands.

@sudodus - That worked perfectly!   > You must 'have selected' persistent live in the main menu in order to get a persistent live pendrive.  It was a little confusing the "Toggle" Live vs Persistent, but after trying it a few times I see how it works now.

Now I have a 32gb pen drive with 7gb FAT32 and a 25gb EXT4 persistent.  I copied my 5.8gb folder to the desktop, installed inkscape and saved several files to the desktop,  rebooted and it is all there!

Now when my 128GB pen drive arrives from Amazon tomorrow, I will know exactly how to get this working!

Thank you all for your help!  This is Exactly what I needed!

---

### Post by sudodus on 2015-10-02
Congratulations and thanks for sharing your result :KS

---

### Post by Mahogan on 2015-10-02
Well, I guess I spoke too soon that this solved all my problems with the Live USB Persistent setup.  It does work great on the laptop that I installed it from, however when I tried booting from a different laptop, all I get is a Blinking Line on a black screen.  So I tried it on my desktop and get the same blinking line.  So I let it be and came back 20 minutes later and still a blinking line.

So it will not boot on another system.  Not sure why? 

If this is helpful, Here are the specs of my laptop that I set it up on where it works great.  ASUS Q400a, Intel Core I7, 8gb ram.  

The laptop where it does not work is MSI A6200, Intel Core I5, 6gb ram.  
The desktop where it does not work is an eMachines EL1358-53, AMD Athlon II X2 220, 3gb ram

JFYI,  I have tried booting both of these other computers from my previous USB setup (before the mkusb setup, as mentioned in my initial post) and all three computers booted just fine.

I also made another USB drive with the same mkusb setup and it does the exact same thing, so it is not the actual usb drive.

---

### Post by yancek on 2015-10-02
If your hardware on your other computers is capable of booting from a flash/usb drive, it should work.  I'm not sure you are saying in your last post that you have tried other flash drives on these other computers and they do boot, but the mkusb one doesn't.  Is that correct.  I'm not really familiar with mkusb as I've only used it once earlier this week but it did work as 'advertised' and I successfully booted it on my HP Desktop, an Acer notebook as well as in virtualbox.  It created 3 partitions, the first one of course the FAT32 then the second an iso9660 and the third the casper-rw as ext2.

Can you boot another Linux with the flash plugged in and check the /boot/grub/grub.cfg file on the first (FAT32) partition of the flash.  Did you have 3 menuentries on boot for persistent, Live and Recovery.  Not really sure what else to suggest other than to try it again.  As I said, I've only tried it once and it worked like a charm on multiple computers.

---

### Post by Mahogan on 2015-10-02
@yancek- Yes all these computers are capable of booting from a flash/usb drive and yes they all booted from a prior Linux install.  But now after using mkusb, only the computer that installed Ubuntu on the flash drive will actually boot.  I am able to see from gparted that it installed 3 partitions, a FAT32, an Unknown , with a red warning flag(where the iso seems located) and an EXT4 (casper-rw) partion.

When booting from the Live Persistent flash drive (on the computed that made it) it does show the three grub menu entries to boot Persistent, Live, etc.  However on the other computers, just the blinking line.  

Here is the content of the grub.cfg file

> set timeout=10
set default=0

menuentry "Ubuntu-14.04.3-desktop-amd64.iso - persistent live" {
 set root=(hd0,2)
 linux ($root)/casper/vmlinuz.efi boot=casper quiet splash persistent -- persistent
 initrd ($root)/casper/initrd.lz
}
menuentry "Ubuntu-14.04.3-desktop-amd64.iso - live" {
 set root=(hd0,2)
 linux ($root)/casper/vmlinuz.efi boot=casper quiet splash --
 initrd ($root)/casper/initrd.lz
}
menuentry "Ubuntu-14.04.3-desktop-amd64.iso - recovery mode" {
 set root=(hd0,2)
 linux ($root)/casper/vmlinuz.efi boot=casper ro recovery nomodeset
 initrd ($root)/casper/initrd.lz
}

---

### Post by ubfan1 on 2015-10-02
You didn't list the video in each computer, but the problems seems to be a video issue.  With persistence, the drawback is you will get specific video drivers installed, and when the USB is moved, you might be trying to use the wrong driver.  Without persistence, you shouldn't have that problem.  Try the "recovery" boot for the minimal video and see it that works.

---

### Post by Mahogan on 2015-10-02
@ubfan1 - I will have to look up the video of these computers, that is why I gave the model numbers, as I am not sure but will do some research.  On the other two computers with the blinking line, it never gets to the grub menu to try the "recovery" boot.

---

### Post by sudodus on 2015-10-03
> When booting from the Live Persistent flash drive (on the computed that made it) it does show the three grub menu entries to boot Persistent, Live, etc. However on the other computers, just the blinking line. 


I am very surprised that there is not even a grub menu in the other computers.

Maybe it is the pendrive, that the pendrive's hardware does not work with the other computers. In that case you should succeed if you try with another pendrive.

Maybe you have an issue with a hardware driver. Maybe there is an issue with the bootloader. Maybe grub in the host operating system is not complete, lacks some grub files, and therefore cannot install them into the pendrive, and those files are necessary to boot the other computers.

My experience is that mkusb makes persistent live drives of all Ubuntu flavours plus some community re-spins based on Ubuntu, and that it is portable between computers. I am interested in debugging this problem.

You wrote '14.04 LTS' in the opening post.
- What version and flavour did you use (for example standard Ubuntu 14.04.3 LTS or Xubuntu 14.04.1 LTS or a community re-spin)?
. As the host operating system (where you are running mkusb)?
. As the source operating system (the iso file)?

- Have you installed a proprietary driver for graphics or wifi?

- Have you removed some files that belong to the system from the pendrive?

- Have you changed the ownership or permissions of some directories or files that belong to the system in the pendrive?

If you have changed the persistent live system in any way, that might affect it's ability to boot, you can make another persistent live system and try it in all your computers before changing the system.
[hr][/hr]

One way to get a complete grub is to use a live-only system as host operating system. So make a live-only pendrive with mkusb from an ISO file of an Ubuntu flavour of version 14.04.3 LTS (an official Ubuntu flavour, not a community re-spin). With your computers you probably want amd64 (64-bits), so for example

```
ubuntu-14.04.3-desktop-amd64.iso
kubuntu-14.04.3-desktop-amd64.iso
lubuntu-14.04.3-desktop-amd64.iso
xubuntu-14.04.3-desktop-amd64.iso
```

A live-only system made with mkusb is cloned, so nothing is missing if the cloning operation was successful.

Boot into the live-only system, install mkusb and make the ISO file available to the system of the pendrive (from the internal drive or from another pendrive). Run mkusb to make a persistent live pendrive.

-  Does the live-only pendrive work in all your computers?

- Will this 'second' persistent live pendrive work in all your computers?

[hr][/hr]

***Edit:*** Are these computers running in BIOS mode or UEFI mode? mkusb should make persistent live drives, that work in both BIOS and UEFI modes, but they do not work with secure boot. *You have to** turn off secure boot** in the UEFI settings to make it work*.

---

### Post by Mahogan on 2015-10-03
@sudodus - thanks for the reply and the details. 

I am using Ubuntu 14.04.3 LTS on my ASUS Laptop and the eMachines, and Ubuntu 12.04.? LTS on the MSI Laptop.  When installing via mkusb, from the 14LTS environment, I have saved the ubuntu-14.04.3-desktop-amd64.iso on my desktop folder.


I tried another 16gb pen drive and a fresh persistent install via mkusb on my ASUS lapt, and get an error, "grub install error: cannot find EFI directory, a screenprint located here:

[http://mahogan.com/mkusb16.png]("http://mahogan.com/mkusb16.png")



To problem solve what is wrong with the other two drives that both fail.  It could be that since these were made on the ASUS Core I7 laptop that something in the bios, as you mention turn off secure boot etc is messing it up.

After discovering this error, I tried a different (brand new) 32gb pen drive, but _this time I used the eMachines desktop to do the install via mkusb.  It worked successfully, and it works great on both laptops._ 

Right now I am on my ASUS laptop via Ubuntu 14 installed on the hard drive, so I will make this post, then get into the BIOS and see if I can find the secure boot settings and update this post.

**EDIT:** Here are screenshots of my ASUS bios settings

[http://mahogan.com/advanced1.JPG]("http://mahogan.com/advanced1.JPG")
[http://mahogan.com/advanced.JPG]("http://mahogan.com/advanced.JPG")
[http://mahogan.com/boot.JPG]("http://mahogan.com/boot.JPG")
[http://mahogan.com/security.JPG]("http://mahogan.com/security.JPG")

Looks like the Secure Boot (at the bottom of the last screenshot) is disabled

---

### Post by sudodus on 2015-10-03
I can see in the attached screenshot, that the bootloader could not be installed. Something did not work correctly in the ASUS laptop. I suspect that some sequence of instructions did not finish before the next one was started. I have already added some 'tasks' into the mkusb script to make it wait for the previous task to finish and the system information to be updated. Maybe it is not enough in that computer and with that version of Ubuntu.

I will try to do what you do in Ubuntu 14.04.3 LTS (as host and as source iso file).

---

### Post by Mahogan on 2015-10-03
I'm not sure why it fails on my ASUS laptop.  I just tried the 16gb pen drive that I previously installed from the ASUS (the screenprint error) and reinstalled vis the eMachine desktop and the install works fine on all machines.  So it is not a problem with my pen drives, definitely something related to a setting on my ASUS.

---

### Post by sudodus on 2015-10-03
I ran mkusb in an installed Ubuntu 14.04.3 LTS (in BIOS mode) and it worked for me to install from **ubuntu-14.04.3-desktop-amd64.iso**. See the attached log file, for example lines 102-105

```
UEFI Bootloader:  Installing for i386-pc platform.
Installation finished. No error reported.
BIOS Bootloader:  Installing for i386-pc platform.
Installation finished. No error reported.
```

(I know since before that it works to run mkusb in a live session of Ubuntu 14.04.3 LTS (in BIOS mode)).

*Edit:* I tested to run mkusb in a live session of Ubuntu 14.04.3 LTS *in UEFI mode* to install from ubuntu-14.04.3-desktop-amd64.iso. And it works too. I agree: it seems that problem is just a setting on your ASUS or some hardware incompatibility.

---

### Post by Mahogan on 2015-10-03
So it seems that problem is just a setting on my ASUS or some hardware incompatibility?  For now, it seems that if I can get the install to work via mkusb on my eMachines and it works on all my other computers, then my problem is solved.

---

### Post by sudodus on 2015-10-03
There were a few problems, but finally you found a way around them :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by Mahogan on 2015-10-03
@ Sudodus ----  Yes.  Moral of the story, if there are problems that don't make sense, try a different computer!  :p  I will say, that mkusb is undoubtedly the best way to make a persistent live USB drive.  Hands down, now that I figured things out, I can make a new setup in just a few minutes and it works great!   Thanks for all your great help!

---

### Post by sudodus on 2015-10-03
You are welcome :-)

---


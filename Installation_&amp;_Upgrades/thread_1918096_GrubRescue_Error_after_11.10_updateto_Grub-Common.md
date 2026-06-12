---
title: "GrubRescue Error after 11.10 updateto Grub-Common"
date: 2012-01-31
forum: Installation &amp; Upgrades
---

### Post by bogan on 2012-01-31
Hi!,** Grub Rescue Experts**,

I am running two Medion Desktop computers, a Win7 machine with Ubuntu installed in an external HDD, and a Vista m/c with Ubuntu installed in the internal HDD . Both have 11.10, 3.0.0-15 and 10.04 LTS, 2.6.32-38 installed, and, after a lot of help from these Forums were both working satisfactorily, if a bit slowly, until the most recent efforts of Update Manager.
  The Win m/c is not affected, as I have not done the latest update.    
 
I had just installed the latest NVIDIA driver on both 10.04 on sda6 & 11.10 on sda8 { though I do not think this is the cause of my problems} when Update Manager, wobbled its Icon so I activated it.
 
It showed 28 items including a couple of grub items one of which was grub-common. During the Applying changes there was an option to choose where Grub should be installed, but no option for sda8, so I left it at the default.
 
On rebooting,the Grub 2 menu had been replaced by v1.98 with 25 entries in white text on a black screen.
 It booted OK to both 10.04 & 11.10 and I ran update-grub in both, with and without xorg.conf, without any change.
 In 11.10 Grub Customizer still retained all its settings  but saving it also had no effect. Update grub showed that the background image was detected but not displayed.
 
Although everything else seemed to be working correctly, I wanted my Customizered boot screen back, so I ran the code from the “How to restore the Ubuntu/XP/Vista/7 bootloader” Thread  >> “How to restore the grub bootloader”:> First you need to find out what your drives are called. You can do this by going to a terminal and typing:```
sudo fdisk -l
``` From that you need to find the device name of your Ubuntu drive, something like “/dev/sda5&#8243;.
So, still in the terminal, type:```
sudo mkdir /media/sda8
 sudo mount /dev/sda8 /media/sda8
```And then, to reinstall the grub:```
sudo grub-install --root-directory=/media/sda8 /dev/sda
``` Push enter and you’re done! Of course you need to replace “/dev/sda5&#8243; and “/dev/sda” with what you found in the fdisk output.The result on rebooting was no grub menu but a black screen with a “File not found” message and a grub rescue prompt.
 
I then followed the instructions in the next section although it was intended for Ubuntu < 9.04, booting from a 11.10 Live CD but the code seemed to only address the contents of the CD not either of the installed file systems.
 
I know nothing of the grub rescue commands or actions. What do I do now ??
'ls' showeda list of six hd0 partitions, all as 'msdosx', x= 9>5 & 1
Studying the Rescue threads:  Does the 11.10 live CD/USB contain BootRescue ?

Chao!, **bogan**

---

### Post by drs305 on 2012-01-31
Boot Repair is probably what you need. It's not installed on the LiveCD by default but you can download and run it from the LiveCD. Click the Boot Repair link in my signature line to get to it's thread.

If BR can't fix things, it has an option to run the boot info script. Run the script, post the contents of RESULTS.txt, and we can take a look at your boot file status to give us an idea of how to proceed.

---

### Post by bogan on 2012-01-31
> **drs305 said:**
> Boot Repair is probably what you need. It's not installed on the LiveCD by default but you can download and run it from the LiveCD. Click the Boot Repair link in my signature line to get to it's thread.

If BR can't fix things, it has an option to run the boot info script. Run the script, post the contents of RESULTS.txt, and we can take a look at your boot file status to give us an idea of how to proceed.
Hi!,** drs305**,

Thanks for the very prompt response. Will get Boot Repair and report back,

Chao!,** bogan**.

---

### Post by bogan on 2012-01-31
Hi!, **drs305,**   Well, Well!!  That was some ride!

Quick report:
 Grub Rescue prompt has gone; Grub menu is back, [ but still in v1.98 format, white text on black] and both 11.10 & 10.04 Ubuntu boot and look [at first glance] normal, as does WIN Vista.

But, and it's a big BUT, Something very strange has happened!.

Booting to 10.04, when I open the Home folder and select Documents, what I get is the contents of Windows C:/users/alan/Documents!! exactly the same as if I selected 'Boot>users>alan>Documents' from the side bar.

As far as I can see, I have not checked everything, only the Desktop folder is also not as I expect, and that is empty, where it should show two Folders: Current & Manuals. But see Update note below.

Booted to 11.10 everything looks normal, except if I open Documents via the '115Gb FileSystem'[10.04] Sidebar entry>home>alan, when it is the same as above.

Longer Report:
 When I tried to boot from an 11.10 LiveUSB, the Bios recognised it, but would not boot from it; though it did when I made it a couple of weeks ago. It did, however, boot from the LiveCD I made at the same time.

I downloaded Boot-Repair, as per your link, and ran it. I got several error or warning messages but eventually it said everything was repaired and to re-boot, with the results as above.
 It made a bootinfo file and  referred to a URL: hhtp//paste.ubuntu.com/823980 and said to refer it to whoever. This should be a link, hopefully:[http://paste.ubuntu.com/823980](http://paste.ubuntu.com/823980)

I copy/pasted the whole Terminal screen to the file: BootRep31.12.1.txt attached, in case that is relevant.

I also ran update-grub and Grub Customizer again but the results in grub menu, were the same, 25 entries, white on black; with 10.04 still the first entry.

So I then booted to 10.04 and installed grub-customizer there, and ran it. I now have the grub menu reduced to just the six entries I wanted, with 11.10 now first, but still white on black and no background image.

Do I need to re-install Grub2 ??  If so would you please give me a link or detail the commands necessary and from where to run them ?

Update: After a lot of restarts and cold re-boots I am thoroughly confused by the Documents hiatus.
Booted to 11.10 I now find that selecting root>home>alan opens a list shown as "< home" [ not < home/alan ] it contains all the folders and files that I would expect to find in the 'alan' folder, and the Documents folder there is the correct Ubuntu one.

It seems that opening the home folder from the Launcher actually opens $home which is actually /home/alan.

If I open Documents from the '115GB FileSystem'[10.04] sidebar entry the /root/home/alan folder opens and lists correctly, but the Documents folder is the one with the Windows documents displayed. 

Update 2: I have just read through the bootinfo file and it is a complete mystery to me that the Linux partitions are listed as sde6 & 8 instead of sda6 & 8 as Disk Utility sees them; as for the SysLinux in sda ????
WHAT DO YOU MAKE OF IT ?

Chao!,** bogan**.

---

### Post by drs305 on 2012-01-31
The 'sde' designation may be due to the SATA slot you plugged the cable into. 

One general comment about RESULTS.txt. Although Grub appears to have been installed in the MBR, it's also installed in a large number of partitions. These writings to the PBR won't hurt Ubuntu, but generally speaking when asked where to install G2 you select the *drive* but not the specific partition. Installing on a partition makes Grub more likely to break.

As far as reinstalling Grub, usually you want whichever Ubuntu you plan on using most to control Grub. Otherwise you will try to update grub but the commands won't appear to change the menu. In reality, the Grub files are changed but if it's not the *controlling* Grub they won't be reflected in the Grub menu you see during boot. So...

Boot into the Ubuntu you want to consider the main OS. Then simply run this command (if sde is the designation of your Ubuntu drive and the one the BIOS boots):
```
sudo grub-install /dev/sde
```
This command will write instructions to the sde MBR and the MBR on boot will normally send Grub to the currently-running partition to find the boot files.

As far as the Document situation, I'll try to reread your post but I'm not sure I grasped it after a reading or two. If your Grub issues get resolved in this thread you may want to start another describing that problem. But we probably are not at that point yet. Note that the HOME in the left panel of Nautilus is a shortcut to *your* home folder; so it's not really a link to '/home', but really to '/home/alan'.


Syslinux on sda: sda looks like a thumb drive. Syslinux is often the linux system installed on bootable flash drives.

---

### Post by bogan on 2012-02-01
Hi!, drs305,
Thanks for your response,

You Posted:> The 'sde' designation may be due to the SATA slot you plugged the cable into. I am not sure what this referrs to; What cable ? 
The extrenal drive, usually listed as sdb, is purely a Data drive and is directly plugged in to the external Usb socket in the case top. Presumably doubling as a Sate3 port.
Both Ubuntu partitions are on the internal HDD and Disk Utility, Disk Usage Analyzer and 'fdisk -l' all show them as sda6 for 10.04LTS and sda8 for 11.10, so that is what I entered.

Nonetheless, I tried as you suggested and after a long pause the result was :```
 alan@alan-MS-7318:~$ sudo grub-install /dev/sde
[sudo] password for alan: 
/usr/sbin/grub-setup: error: no such disk.
alan@alan-MS-7318:~$   
```So I then did the /dev/sda bit and after another long pause got:```
alan@alan-MS-7318:~$ sudo grub-install /dev/sda
Installation finished. No error reported.
alan@alan-MS-7318:~$ 
```> One general comment about RESULTS.txt. Although Grub appears to have  been installed in the MBR, it's also installed in a large number of  partitions. These writings to the PBR won't hurt Ubuntu, but generally  speaking when asked where to install G2 you select the *drive* but not the specific partition. Installing on a partition makes Grub more likely to break. Should I attempt to remove/repair these superfluous MBR/Grubs?  or is it too complex and chancy ?> As far as reinstalling Grub, usually you want whichever Ubuntu you plan  on using most to control Grub. Otherwise you will try to update grub but  the commands won't appear to change the menu. In reality, the Grub  files are changed but if it's not the *controlling* Grub they won't be reflected in the Grub menu you see during boot. Yeah, I was aware of that and it is why I installed and ran Grub Customizer in 10.04 as the Update had made it the first entry instead of 11.10, as I wanted & had previously.
That edited the entries, but it still showed Grub v 1.98 and no background image.

I am going to reboot now to see if that has changed.

Edit: Yes!!  I have got my Customized grub menu back exactly as before, without having to run Grub Customizer again. Thanks a million.

I have an idea as to how the Documents wierdness came about, I need to do some checking in my other, Win7 m/c, to be more sure.

Chao!, **bogan.**

---

### Post by drs305 on 2012-02-01
Regarding the sda vs sde designations: What I referred to was that with SATA drives the socket the drive is connected to on the motherboard determines the designation (I think). If you plug the drive into the first one, it's sda. If you put it into the 5th, it becomes sde. It appears that the boot info script may be taking its information from the motherboard settings, while the OS is resetting them to what you would expect to see (sda, sdb, etc). I'm no expert on this by any means and there could be a totally different explanation. In any case, I'd not worry about 'sde' any longer since the only place it has appeared for you is in the boot info script.

Don't worry about the extra Grub information in the partition boot records (PBR). You don't want to install Grub there in general but once it's there it's easiest to just leave it. You aren't using it and you'll never know it's there except with the boot info script.

Happy Ubuntu-ing.

---

### Post by bogan on 2012-02-01
Hi!, **drs305,**
Thanks for your comments.
I think the multiple grubs were due to my ignorance about Installation procedures. The requester asking where Grub should be installed offering a list of possibilities, had a Help button that said something about "unless you have a separate Boot partition" and "If you are in doubt select them all", so that is what I did. 
 I still have no idea whether what I have includes a 'separate Boot partition', or not, or if it matters.

I am still a bit worried about all the errors that Boot Repair threw up, but everything appears to be OK for now, so I will mark this as 'Solved'.  :)

Regarding the Documents hiatus,
 I am sure that it was a complete coincidence of timing that I first noticed when I went to Downloads to copy the NVIDIA driver from 11.10 to 10.04 that what should have been in </home/alan/ in 11.10 was instead shown as in <Home. Presumably this has been so since 11.10 come out but I never noticed it as significant.[I did not then 'see' the upper case 'H', nor, if I had, would I have understood its significance.]

My confusion was made worse because, for some reason, Desktop Manager decided at that point to open all my Windows with Hidden files shown.
 So instead of the half-dozen Icons I expected, I got a whole list down the screen with Backup, Desktop, Documents, Downloads, & Pictures etc in the middle, with lots of things I did not recognize.
Add to that when I opened Documents to find the screen full of Windows Drawers and files, and I began to think the trouble with the Grub Rescue black screen was just a symptom of something much more serious.

So, why Windows in an Ubuntu folder?

First clue: The Vista m/c is a backup to my Win7 m/c and 10.4LTS is a back up to 11.10, so it hardly ever gets used except for updating, or trying out things before I use them in the Win7 m/c.

Second: The latest addition to the Ubuntu //alan/Documents was dated 04/June/2011 whereas the latest in Windows //alan/Documents was 03/June/2011.
 ie the last folder was added **AFTER** the Windows content had been copied over to Ubuntu. And 04/06/11 was a significant date. I had a Windows crash and in trying to use Ubuntu 9.04 to rescue my data, that crashed as well and I had several weeks haunting these Forums before it was sorted. The added folder contained the drafts of my Posts.

It is clear to me now, that at some stage of copy/pasting files from one partition to another, or an USB Flash Stick, as backup, and copying them back again, I made a mistake and copied from Windows to an Ubuntu folder, instead of a Windows one, or vice versa. [ Note the similarity of the Paths.]

So I am just going to delete all the Windows bits and consider the Mystery Solved as well.

Chao!, **bogan**

---


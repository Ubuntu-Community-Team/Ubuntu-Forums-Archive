---
title: "Installing Ubuntu 14.04 on a new HP Desktop"
date: 2014-06-26
forum: Installation &amp; Upgrades
---

### Post by rolfUser on 2014-06-26
Okay. This is challenging. 
I just bought a brand new HP computer with WIndows 8.1 pre-installed.
I had all of my old files from my old computer already backed up, and my plan was  to dual boot Ubuntu 14.04 to run alongside Windows 8.1.  

I set my partitions -- Windows will only let me shrink the C drive to about 50%,
I deactivated "Fast Startup", as instructed, and downloaded the latest release from Ubuntu, the 64-bit version, and then I formatted my USB drive  from this site: [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Here is where it gets difficult. Instructions from sites like these two made it look easy:
[http://www.makeuseof.com/tag/how-do-i-install-ubuntu-on-a-new-windows-8-computer/](http://www.makeuseof.com/tag/how-do-i-install-ubuntu-on-a-new-windows-8-computer/)
[http://elabualg.wordpress.com/2013/10/22/dual-boot-ubuntu-and-windows-8-uefi/](http://elabualg.wordpress.com/2013/10/22/dual-boot-ubuntu-and-windows-8-uefi/)

Once I reached the BIOS setup screen, the menus were laid out different from what is shown in the two above links. From there, I disabled "SecureBoot". And then while still in BIOS, I set the Boot Order to have the USB port be read before the boot manager. 

I noticed that I did not see an option to perform some action via my USB drive. BIOS acknowledged that a flash drive was inserted, but no option to boot for installation.   Did I do something wrong or are the protocols a little different from what it says in the instructions above?

After saving and exiting, the next screen is a console, or a terminal.    The background is black, not dark violet or anything.  There is 5-10 lines of text that instruct me to press TAB for a list of available functions or actions or files. 
Below this is a line that reads:   grub>    or     GRUB>      I don't remember. I can type in it. When I hit TAB, a list of 15-20 lines appears, but I have no idea what to type, or if I was supposed to be on this screen to begin with.
 
I have installed Ubuntu 12.04 to Windows XP before and I never had come across this kind of a challenge.   I'm sure someone knows what to look for, the right questions, and the right solutions. I know that instructions can become outdated overtime and that different PCs use different conventions for certain things. 

My objective is to install Ubuntu 14.04 to run alongside Windows 8.1. I have my bootable USB drive in hand. So what next?

---

### Post by mastablasta on 2014-06-26
> **rolfUser said:**
> 
Below this is a line that reads:   grub>    or     GRUB>      I don't remember. I can type in it. When I hit TAB, a list of 15-20 lines appears, but I have no idea what to type, or if I was supposed to be on this screen to begin with.
 
This (in lassic MBR install and BIOS) usually used to indicate something is wrong with the image either bad download or bad "burn" to USB.

> 
My objective is to install Ubuntu 14.04 to run alongside Windows 8.1. I have my bootable USB drive in hand. So what next?

Check the md5sum of donwloaded image. if it's a match then try the USB on another computer preferably the one you know works with linux.: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

otherwsie something is wrong here as sytsem is not loading only the boot mnagaer seems to have loaded. might be good to get the other lines (maybe make a picture of screen with camera)

---

### Post by LastDino on 2014-06-26
Check that USB on some other computer, then we can head towards some other direction.

---

### Post by rolfUser on 2014-06-27
I went here [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

and followed directions for Windows, except I performed the action on the same Windows PC I am having problems with. 
I performed the comparison to the ISO file that I copied and pasted to my USB drive.
I made a screenshot of the message I got and posted it to this message.

[CENTER][ATTACH=CONFIG]254274[/ATTACH]
[/CENTER]

After clicking where it says "Compare", a message pops up saying: MD5 Check Sums are different.

---

### Post by LastDino on 2014-06-27
That means you need to download the iso again since the one you downloaded seems to be corrupted, Please try to use torrent version as torrents have less chance of corrupting your downloads.

Where did you downloaded Ubuntu from?

---

### Post by oldfred on 2014-06-27
+1 on LastDino's suggestion of new download. 
And then reinstall to flash drive.
 How to create a bootable Ubuntu USB Flash Drive - unetbootin
[http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/](http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/)
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
      
 Most find this works best
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
Pendrive also has page on booting ISOs
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

And some suggest this installer:
Usb installer from Windows
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
SOLVED!!! Used rufus to create bootable USB and it worked! I've tried UUI and unetbootin before. 
[http://rufus.akeo.ie/](http://rufus.akeo.ie/)

 No need for a separate /boot partition unless installing a server type configuration with RAID or LVM, both of which erase entire drive.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[URL="http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system"]http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system

[/URL]Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[URL="http://www.runtime.org/driveimage-xml.htm"]http://www.runtime.org/driveimage-xml.htm
[/URL]
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

    [URL="http://www.runtime.org/driveimage-xml.htm"]
[/URL]

[URL="http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system"]
[/URL]

---

### Post by rolfUser on 2014-06-28
I'm going to try downloading the ISO from a Torrent. Then I will try the Rufus formatting when I am done.

My first question:
Should I, and is it safe to delete EVERY file from my USB drive before reformatting with Rufus?
A message popped up saying that either Windows or a device will no longer work properly if I delete the **uui folder**.

next question:
I'm not familiar with Torrents.
I tried going here  >>  [https://kickass.to/ubuntu-14-04-lts-desktop-64bit-iso-t9007063.html](https://kickass.to/ubuntu-14-04-lts-desktop-64bit-iso-t9007063.html)
and my Avast! antivirus detected a virus.
Instead of a 964MB file, it downloaded an application less than a megabyte. I don't know if this will cause problems for my computer. I should probably ask about this. Am I okay to download from this site or are there safer alternatives?

---

### Post by LastDino on 2014-06-28
I usually just format the USB, no need to delete files separately/individually. So, probably yes.

While that link looks ok, I strongly suggest sticking with official one as I've never tried the one you've posted.
[http://releases.ubuntu.com/14.04/](http://releases.ubuntu.com/14.04/)
As to select what from there, see the screen shot given.

[ATTACH=CONFIG]254301[/ATTACH]

That will download 30kb file of torrent and you can open it with any torrent manager you may have on your windows. Example: Utorrent.
Google for learning best practices of using torrents.

---

### Post by rolfUser on 2014-06-29
> **LastDino said:**
> I usually just format the USB, no need to delete files separately/individually. So, probably yes.

While that link looks ok, I strongly suggest sticking with official one as I've never tried the one you've posted.
[http://releases.ubuntu.com/14.04/](http://releases.ubuntu.com/14.04/)
As to select what from there, see the screen shot given.

[ATTACH=CONFIG]254301[/ATTACH]

That will download 30kb file of torrent and you can open it with any torrent manager you may have on your windows. Example: Utorrent.
Google for learning best practices of using torrents.

Hi. Thanks for all the assistance so far. I appreciate it.
I went with Utorrent and clicked the link that you pointed out.

Then I tested the ISO with winMD5Sum.
I got the same error message as last time. That's weird. I'm getting suspicious.
I do have another PC. It runs Windows 7. I'm going to try doing this same stuff on that PC. 
That's what I was supposed to do anyway.  Maybe something is wrong with Windows 8.1, I don't know.

---

### Post by rolfUser on 2014-06-30
Something strange happened.
I noticed that I could not copy and paste the hash onto NullRiver. I can only paste all the characters minus one. ????
So I tried a different program: [http://www.winmd5.com/](http://www.winmd5.com/)
re-downloaded the same file via torrent, and the test checked out!

I'm going to try to install the operating system or "distro" onto my computer now.
I'll fill you in on what happens.

---

### Post by rolfUser on 2014-06-30
Booting the PC, I once again came across a terminal-like screen.
This time, I deleted all the files on my thumb drive and then reformatted using Rufus [http://rufus.akeo.ie/](http://rufus.akeo.ie/)
Upon booting the PC this time, an option to install ubuntu was present. it was like the holy grail or something. I finally made it.

But there is a new contingency. I'm sure I need advisement on this one.
During setup, the system says that it does not recognize or detect an operating system on the PC. That's strange.
I took a picture of the screen to show you.

[ATTACH=CONFIG]254356[/ATTACH]

I want to keep both operating systems so that I can just pick one when on start-up.
What should I do in this case   when the system thinks Windows is not present???

Notice that the first option CANNOT BE ALTERED no matter how many times I click to try to change it.  This is not what I want. 
The other ones I can select or deselect. I'm afraid to move forward if it ends up costing me.

---

### Post by oldfred on 2014-06-30
It is not seeing Windows which is a problem. 
Do you have the always on hibernation or fast boot off?
Did you use Windows partition tools to shrink Windows and reboot so it can run chkdsk and make fixes it needs first? But do not create partitions with Windows.

But always better to use Something Else. But it requires you to create your own partitions. 
These are for second drive as Something Else is really required for those installs, but yours will be similar.

       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

 Install to external drive. Also any second drive.
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

### Post by rolfUser on 2014-07-02
> **oldfred said:**
> It is not seeing Windows which is a problem. 
Do you have the always on hibernation or fast boot off?
Did you use Windows partition tools to shrink Windows and reboot so it can run chkdsk and make fixes it needs first? But do not create partitions with Windows.




To answer the first question, I did deactivate **Fast Startup and Secureboot**[B]. [http://elabualg.wordpress.com/2013/10/22/dual-boot-ubuntu-and-windows-8-uefi/](http://elabualg.wordpress.com/2013/10/22/dual-boot-ubuntu-and-windows-8-uefi/)
 That's the best I can do to answer that question. I'm not that savvy with computers, and I'm not sure what you are referring to. Sorry.  Please elaborate, so that I know where and how to check, and to make adjustments if it is necessary.


The second question about my Windows partitions: This is all  I did regarding partitions:
[/B][ATTACH=CONFIG]254402[/ATTACH] 
Also. I am not sure I understand that question either. Please forgive me. Elaborate please.

p.s. I actually wanted to shrink my Windows partition all the way down to just 40GB, but the system would not let me.
225.96GB is the smallest size I am allowed to bring it to.

---

### Post by oldfred on 2014-07-02
Best not to create any partitions with Windows, but use gparted.
Ubuntu will not install to a NTFS formatted partition as it needs Linux format usually ext4.

Use Something Else and choose existing NTFS partition you created, be careful not to choose Windows install. select change and make it / (root) and format as ext4. Best to also add a 2 or 3GB swap partition also.

       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

 Install to external drive. Also any second drive. Or any install with Something Else
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

If not familar with installing new systems you should make a full backup, just in case.

 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

And you should always have a current version repairCD or flash drive for every system you install. Your Ubuntu live installer is fine for that, but then you need a Windows disk.
      
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by mastablasta on 2014-07-03
> **rolfUser said:**
> [B]

The second question about my Windows partitions: This is all  I did regarding partitions:
[/B][ATTACH=CONFIG]254402[/ATTACH] 
Also. I am not sure I understand that question either. Please forgive me. Elaborate please.


delete the ubuntu partition and leave it as empty space.

---

### Post by rolfUser on 2014-07-03
> **mastablasta said:**
> delete the ubuntu partition and leave it as empty space.


Is this what you meant?
[ATTACH=CONFIG]254437[/ATTACH]


I rebooted and took pictures of the screen after selecting "something else".
I'm going into very unfamiliar territory.
Here is the top:
[ATTACH=CONFIG]254434[/ATTACH]







Here is the same window, but scrolled to the bottom:
[ATTACH=CONFIG]254435[/ATTACH]







From here, what I want to do is shrink the Windows partition down to just 40GB. Okay.. so that's.... 40960 MB
But then, how do I label this partition, what is it mounted to, I'm nervous.

I know that I want make sure that I can leave as much space as possible for **Ubuntu.** I'd use the space to store my backed-up files.
I'm learning now that you have to create a few partitions for Ubuntu reserved for different things like /home, /boot, and /
I'm learning that you can make them as big or as small as you need them to. But how would I know what's best? 
I used to think everything is stored in the hard drive and that's it. 

[http://elabualg.wordpress.com/2013/10/22/dual-boot-ubuntu-and-windows-8-uefi/](http://elabualg.wordpress.com/2013/10/22/dual-boot-ubuntu-and-windows-8-uefi/)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

---

### Post by mastablasta on 2014-07-04
i do no see any empty space on your Picture. empty space is unformated disk space. it means there is no NTFS format or any other disk format there. just raw disk, no file system.

some i found on internet: [http://www.techulator.com/attachments/Resources/8354-63635-extend-c-drive-in-windows-8-using-unallocated-space.png](http://www.techulator.com/attachments/Resources/8354-63635-extend-c-drive-in-windows-8-using-unallocated-space.png)

note the unalocated disk space! that is space with no disk file system on it. this is empty disk space where one can install other file system and computer operating systems (such as Linux, FreeBSD, mac, RiscOS, MS-DOS, FreeDOS, whatever...).

even if oyu do manually, do not touch anything with EFI or NTFS next to it when doing changes!

one hting i do not know is where GRUB is installed in UEFI. someone else Will have to tell you that. i only have BIOS systems at home= oldish PC :-(

---

### Post by yancek on 2014-07-04
The last image you posted shows a partition:  Ubuntu Volume (F:) as 223GB.  When you boot Ubuntu to install it, it will definitely not show up as F but more likely something like sda5, not sure what the partition name will be.  The other problem is that it is formatted ntfs so installing Ubuntu on that partition formatted for windows won't work.  If you can boot the Ubuntu installation medium and open GParted and post that, it would be easier for someone to help you.  You can format the partition with a Linux filesystem during the install.

---

### Post by rolfUser on 2014-07-04
I this looks better.
[ATTACH=CONFIG]254464[/ATTACH]


Installation window would look different and I made sure to snap pictures.
The top:
[ATTACH=CONFIG]254465[/ATTACH]

The bottom:
[ATTACH=CONFIG]254466[/ATTACH]

---

### Post by yancek on 2014-07-04
You last image shows 240GB of free space between sda4 and sda5 so that would be where to install Ubuntu.  You should be able to create whatever partitions you want there and install.

---

### Post by rolfUser on 2014-07-04
> **oldfred said:**
> Best not to create any partitions with Windows, but use gparted.
Ubuntu will not install to a NTFS formatted partition as it needs Linux format usually ext4.

Use Something Else and choose existing NTFS partition you created, be careful not to choose Windows install. select change and make it / (root) and format as ext4. Best to also add a 2 or 3GB swap partition also.


I took notes from a two sources and wrote out a a plan for I would install.
Does this look like it could?


1.    /boot &#8211; System boot installation

Size: Arround 300 MB should be enough
Partition type: primary
File system type: ext2
Mount Point: /boot


2.    /   &#8211; File system installation

Size:** 50 GB (51200 MB)**
Partition type: Logic
File system type : ext4
Mount Point: /


3.    /home &#8211; personal files storage

Size: variable[INDENT]*240.2 GB (unallocated space) - 50 GB (/) - 4GB (swap) - 300MB (/boot)*[B]
= 185.9 GB (190368.8 MB[/B])
[/INDENT]
Partition type: Logic
File system type : ext4
Mount Point: /home


4.    swap &#8211; Virtual memory dedicated partition

Size: depends on the RAM,
**My PC specs mentions:**[INDENT][I]AMD Quad-Core A4-5000 Accelerated Processor
4GB DDR3 system memory[/I][B]
So my best guess is to leave the Size for swap partition at 4GB (4096MB).[/B]
[/INDENT]
Partition type: Logic
File system type : swap area



[http://elabualg.wordpress.com/2013/10/22/dual-boot-ubuntu-and-windows-8-uefi/](http://elabualg.wordpress.com/2013/10/22/dual-boot-ubuntu-and-windows-8-uefi/)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

---

### Post by rolfUser on 2014-07-04
There is one important question regarding /boot.

Why is 300 MB sufficient?
Should it not be much higher than that?
I am just assuming that /boot is place to put the files from my formatted USB drive.
The files uploaded to it add up to about 961MB.
Add the ISO of 964, and you have 1.88GB of data. 

Is this how much space I actually should set aside for /boot?

---

### Post by yancek on 2014-07-04
> Why is 300 MB sufficient?

As an example,  my boot directory on Ubuntu 12.04 with just three kernels is about 83MB.  Not much gets installed here except kernel and initrd files.

> I am just assuming that /boot is place to put the files from my formatted USB drive.

No, it's not.  It is where the boot files go.  The rest goes on the system file which is symbolized by the forward slash or root symbol: /
You set this mount point during the install.

---

### Post by rolfUser on 2014-07-05
Hopefully, these will be the last question(s) I have to ask before proceeding.
[ATTACH=CONFIG]254502[/ATTACH]

I set my partitions, but before installing, should I install to the first item on that list, the one that reads 500.1 GB?
There are other file locations, but I am assuming that the first one is fine.
Well, what would end up happening if I selected /dev/sda1 or /dev/sda2, as opposed to /dev/sda?
I should probably know this.

---

### Post by rolfUser on 2014-07-05
I have a new problem.
After installing, I rebooted to see if Windows was still working.
That may have turned out to be a mistake. 

I did not think that I had to perform the **Boot Repair**, because I knew that I had previously disabled **secure boot**.
But after looking a t Windows, I tried rebooting to see Ubuntu.
But it booted straight to Windows.

So I inserted my USB drive, trying to boot to my newly installed Ubuntu distro.
The best I can do is to select the "Try Ubuntu" option from the grub menu which appears at startup when I boot with my USB drive.
I followed directions for boot repair on Ubuntu.
Then I went to Windows to finish boot repair by going to **Admin Command Prompt** to enter the appropriate command.
That's it, right? Wrong.

**_Here's the problem: _**
I did not get the option to select either Ubuntu or Windows at startup.
In fact, I cannot get either to boot.
I just get that grub> terminal that I complained about when I formatted my USB with this: [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

The only reason I am able to use my PC at all is because I booted with my USB drive and am using the **preview version of Ubuntu**, despite having already installed it.

I suspect that the problem might be that I went into BIOS shortly after successful installation, and changed the boot order to check for USB drives first, instead of Windows Boot Manager. I thought that if I did this, I could just bypass the boot repair process altogether.

I think I need to restore the boot order back to what it was before. I also disabled Secure Boot, once again while I was at it. The defaults reseted. I thought I had to adjust them again, but instead, it may have caused a new problem.

No matter what I try, I cannot enter the BIOS. Is this what I should do?
Any help would be much appreciated.

---

### Post by rolfUser on 2014-07-05
Nevermind. I figured out how to access BIOS, but the boot order had no affect on the problem.
There is something else that I have to come clear about.

When I perform the boot repair, I have to open a termial. I enter the commands, and the boot repair window appears.
Eventually, I have to open a new terminal and enter new commands.

When the computer was done processing the commands from the **second terminal**, I think this is where I made the mistake:
I tried restarting, but the **first terminal** looked like it was still loading, or something.  I think the mistake is holding down the power to force a shut down.

The PC booted to Windows, and I entered this into the Admin Commnad Prompt:
bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

The next line appearing says the operation was a success.
Then I restarted... and the grub> terminal appears.

No Windows, no Ubuntu. I need my flash drive to send me to the preview version of Ubuntu, and thats how I am able to use these foruns,
I don't know what to do.

---

### Post by rolfUser on 2014-07-06
Well... what can you tell me?

For example,
Do commands performed on the preview version of Ubuntu have any real effect on my PC?  If not, then I would have to undo the effects of  **bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi** on Windows and try to access the installed version of Ubuntu.

Is it possible to switch from the preview version to the installed version of Ubuntu?

I selected the Install Ubuntu icon at the top left of the screen to see what would happen.
[ATTACH=CONFIG]254519[/ATTACH]

Partitions are still where I left them. 
[ATTACH=CONFIG]254518[/ATTACH]

---

### Post by mastablasta on 2014-07-07
for starters stop just doing things for no reason if you do not know what you are doing. you disabled secureboot enabled it, disabled some other things. do you know what the consequences of those actions are? because as you can see there are consequences to each action you too.

i would turn off secure boto for starters. it s not really needed. 

next the empty grub:> means that grub can not find Linux and Windows partitions. this usually happened if grub was installed in the wrong place. what "boot repair" tool does (among other thigns) is it installs or updates grub.

---

### Post by rolfUser on 2014-07-09
I figured that the best thing to do was to refresh both operating systems.
Its an HP computer, so I hold down Esc, and select SYSTEM RECOVERY.
From there, I opt to have my PC refreshed, so that all the setting would be reset, while still keeping my files.
It worked as I thought it would -- I was able to access Windows.

Then I put in my USB drive to boot Ubuntu. I tried to access Boot Repair, but the system would not let me.
So selected the option to erase all my Ubuntu files and reinstall, knowing that this could reset my settings.
And it worked.
When I perfromed the Boot Repair, this time, I took care to let the computer work, and it did for a good hour.
When the operation was complete, there was an error message, just as it said it would happen.
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

I also copied down this link to share because it looks important:
[http://paste.ubuntu.com/7768542/](http://paste.ubuntu.com/7768542/)

After that I am supposed to reboot and access Windows to finish the Boot Repair.
But now the comptuer will not let me do that. Instead I keep getting this screen.
[ATTACH=CONFIG]254596[/ATTACH]
When I enter BIOS SETUP, I have Secure Boot, Fast Boot, and Legacy Sources all disabled, and I still get that screen.
Also under BIOS setup, when I look at the Boot Order, **Windows Boot Manager** is not there. **Ubuntu** is there, but when I put it at the top of the list, save and exit, my PC just ignores it and this same screen comes up. 

It gets worse. I cannot access SYSTEM RECOVERY anymore. When I try to do that, this same screen comes up.
So how am I supposed to access Windows to complete the boot repair?

---

### Post by oldfred on 2014-07-09
You erased the entire hard drive on your reinstall. So you do not have your recovery partition any more nor any Windows, just Ubuntu. Did you make a full backup of efi partition and Windows partitions?
You have to use Something Else to correctly choose partition(s) to overwrite.

Please add to this bug report (I already linked this thread, but it does not add to count).
 Reinstall says overwrite Ubuntu but it also erases existing Windows.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)


The error shown is from UEFI/BIOS boot order and it is trying to boot PXE or network? 
If an HP computer it may only boot Windows by default.

       It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)

    
Variety of work arounds:
       [http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

---


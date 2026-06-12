---
title: "Installation/Upgrade of Ubuntu 12.04.1 dual-boot on a HP Pavillion DV6-6140us"
date: 2012-09-10
forum: Installation &amp; Upgrades
---

### Post by SmallWorld on 2012-09-10
In Dec2011 I posted  how to turn an out-of-the box HP DV6-6140us into a dual-boot machine that runs both Windows 7 64bit and Ubuntu 11.10 32bit.  That post is at: 
[http://ubuntuforums.org/showthread.php?t=1893523]("http://ubuntuforums.org/showthread.php?t=1893523")

Today I upgraded Ubuntu on this same machine from 11.10 32bit Desktop Edition, to 12.04.1 64bit Desktop Edition.  **TO SUMMARIZE**, Ubuntu 12.04.1 64bit works great on the 6140us except that installing the fglrx video driver (aka ATI Catalyst driver) manually seems to work a little better than installing it via Ubuntu's Prioprietary Software service.

Before upgrading my system from 32bit to 64bit, I did run Update Manager just to see if it could successfully upgrade my system from 11.10 32bit to 12.04.1 32bit.  The Update Manager was indeed able to upgrade me from 11.10 32bit to 12.04.1 32bit with most of my system settings intact, but the new video driver ran about as fast as cold tar, and the wifi no longer worked - the wifi card wasn't even recognized.  These could be easy fixes, but I just proceded to a clean install of 12.04.1 64bit.


For anyone who needs it, I will provide detailed instructions and results for two techniques of installing 12.04.1 on the 6140us in a dual-boot configuration:

1 - Upgrading a dual-boot machine running 11.10 32bit (or any other version of Ubuntu) to a machine running 12.04.1 64bit, by using an Ubuntu Live USB stick to overwrite the existing Ubuntu partitions.

2 - Building a dual-boot system starting with a 6140us that is running only one OS (Windows 7).  Note that I did not actually go through with this.  Rather I will give instructions based on my Dec2011 instructions for building a dual-boot system with 11.10 32bit.  I updated my Dec2011 instructions with better grammar, and I replaced all 11.10-32bit-specific instructions with 12.04-64bit-specific instructions.


**_SOME BACKGROUND_**
My system is in OEM/out-of-the-box hardware configuration.  The DV6-6140us runs an AMD Llano APU, consisting of an AMD A8-3500M CPU and an AMD Radeon HD 6620G GPU.  OEM configuration has a Broadcom 4313 802.11b/g/n wifi card, 6GB of memory, and a 640GB hard drive.  It sells with Windows 7 preinstalled.

Always backup your data files before installing, rebuilding, or even upgrading Ubuntu.  Don't forget bookmarks, stuff in your home folder, and I always type up any complex changes I've made to system settings in case I need to redo them.

I used an Ubuntu Live bootable USB stick.  Using an Ubuntu Live CD or DVD installer may require different steps.

For those reading Technique 1, know that my hard drive was already partitioned into the following for running Ubuntu 11.10:
--sda1 is ntfs Windows SYSTEM
--sda2 is ntfs Windows C drive
--sda3 is the extended partition containing sda5, 6, and 7
--sda4 is ntfs Windows Recovery ("D:RESTORE")
--sda5 is a fat32 partition I created for data
--sda6 is my 2.8GB linux-swap partition
--sda7 is an ext4 drive with all Ubuntu files, mount point is /


**_Technique 1 - Overwriting 11.10 32bit with a clean copy of 12.04.1 64bit_**
Boot from your USB stick by pressing Esc and F9 when the BIOS is loading.  Let the USB load up to the point where it asks whether you want to Try or Install Ubuntu.  Connect to wifi using the icon at top right of the screen, then select Install Ubuntu.  Choose to download updates and 3rd party software.  The interface may then freeze up for a few minutes before advancing.

Once the software asks you what kind of Installation Type you want, choose Something Else.  You'll need to Change any partitions you used as mount points, so as to reflag them as mount points.  I use only one partition with a mount point, an Ext4 partition with a mount point of /.  I Changed this partition to flag it with these same settings, and I also flagged it for formatting.  Flagging the / mount point will automatically set the Device for Boot Loader Installation.  Continue, let the installer finish, and restart.

Ubuntu 12.04.1 should load without any problems.  It will then suggest that you activate some proprietary drivers using the icon at the top of the screen.  Don't do this yet.  If you wait a minute more it will soon suggest that you run the Update Manager to install some updates.  Run the Update Manager, and restart.

Now you have a choice on your Proprietary Drivers.

I had ok luck activating the fglrx Driver, but the fglrx Updates would fail, and even installing the Updates via the terminal (sudo apt-get install fglrx-updates) didn't actually update what the fglrx Driver hadn't already installed.  If you install the fglrx Driver, it will provide Driver Packaging version 8.96.7.  This driver worked ok, but I didn't test it much.

Your OTHER choice is to ignore the fglrx activations that Ubuntu offers you, and to instead manually install the latest video driver, currently Catalyst 12.8 (with Driver Packaging Version 8.98.2).  To do this, download the latest version of Catalyst from [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx").   Download the file, open it with Archive Manager, and extract the .run file to any folder.  (If you already installed fglrx, you'll need to remove it now and restart.)  Open a terminal (icon at top left of screen, type 'terminal' and click on the Terminal icon), navigate to the folder with the .run file, and type
```
sudo sh ./xxxx
```
Where xxxx is the .run file.
Choose the Automatic settings, let it finish, and restart your system.

After choosing the second of these two choices, my system is now running Driver Packaging Version 8.98.2.  Glxgears runs at 5000-7000fps in Gnome Classic No Effects, and 2D video (eg 1080 video on YouTube) works great.  5000-7000fps is a hair faster than the glxgears speed I saw in Ubuntu 11.10 32bit.  Anyhow, wifi works, suspend works, the fan works, sound works, the computer generally works great.  I haven't tried the optical drive, bluetooth, or HDMI yet as I never use them.  Fin.


**_Technique 2 - Turning a Windows-7-Only System into a 12.04.1 64bit Dual-Boot System_**
OK, Windows 7 comes preinstalled with four primary partitions:
--SYSTEM, which contains a Windows bootloader if I understand right.
--C, which contains the Windows OS and user files. 
--D:RESTORE, which contains the Windows restoration drive
--HP_TOOLS, which contains some software allowing a user to update the BIOS while running Windows.

Because a hard drive can have a maximum of four primary/extended partitions, you needed to delete one partition to make room for Ubuntu. The HP_TOOLS partition isn't really necessary. The only time it's helpful is when the computer is new and you need to update a bunch of drivers all at once.

So if you haven't done so recently, boot into Windows and run the HP Support Assistant to check for and update all the drivers and flash the BIOS. Once that is done there is no longer any use for HP_TOOLS.

Next, restart Windows for good measure, then uninstall HP Support Assistant. The reason to uninstall is I've read that if you delete HP_TOOLS and then run HP Support Assistant, it will forcibly rewrite HP_TOOLS which would be disastrous. You can always reinstall HP Support Assistant, and HP_TOOLS for that matter, via free utility software on the HP web site.

Then restart Windows again for good measure.  Then click on the Windows icon at the lower left of the screen, right click on My Computer, select Properties, select Manage, then find and select Disk Management. Right click on your C drive where it is displayed in the lower part of the screen. Shrink the C drive significantly. This will make room on your hard drive for the Ubuntu install.  I also used this room later on to create a large FAT32 data partition to share my data files between Windows and Ubuntu.  So I shrank the C drive down to 120GB.  Disk Management will shrink the C drive without requiring a reboot.

At this point I installed the free version of MiniTool Partition Wizard to do the following two things, but you might be able to do the following two things with Disk Management: 1) Delete the HP_TOOLS partition. 2) Create a logical partition for data if you want to.  This is when I made my FAT32 data partition.  It should be a logical partition, and should not be flagged as bootable.  If creating a data partition, make sure to leave at least 60GB or so of empty space for Ubuntu.  When finished, shut the computer down.

Insert your Ubuntu Live USB stick, and activate it by hitting Esc when the BIOS is loading and then hit F9.  Let the USB load up to the point where it asks whether you want to Try or Install Ubuntu.  Connect to wifi using the icon at top right of the screen, then select Install Ubuntu.  Choose to download updates and 3rd party software.  The interface may then freeze up for a few minutes before advancing.

Once the software asks you what kind of Installation Type you want, choose Something Else.  The installer continues, and should now recognize all three of the remaining Windows partitions.  In the empty space you created by shrinking the C drive earlier, create a swap partition (I used 3GB), and an ext4 logical/extended partition with a mount point of /.  Flagging that / mount point will automatically set the Device for Boot Loader Installation.

If you want to create any other logical partitions, now is the time and here is the place.  I already created that FAT32 data partition as I mentioned earlier, but you could also create it now.  Creating such a data partition is optional.

Continue with the installation, let the installer finish, and restart.

For the remaining steps, go to "The OS should load without any problems." in Technique 1 and continue from there.

---

### Post by SmallWorld on 2012-09-29
Oh man, scratch the above advice to install the latest-and-greatest fglrx driver.  Version 8.96.7, the default that Ubuntu installs, works just fine (5500fps on glxgears).

With 8.98.2 still running on my system, I ran Ubuntu's Update Manager on 26Sep2012.  After restarting I was no longer able to boot into a GUI - the fglrx drivers were not working so it would dump me into a command line.

So:
[B]-- Ignore my advice above.  Be happy with 8.96.7.  It seems to work fine.  Installing the fglrx updates still does nothing, but that's fine.

-- If your fglrx driver gets all messed up after an update like mine was, try:[/B]

Boot into recovery mode
Connect to the internet via ethernet
Choose to enable networking
Choose to boot into a root terminal
Type:
```
apt-get purge fglrx*
apt-get update
apt-get install fglrx
```

This got me up and running again.


As an addendum, there's a problem with Chrome's Pepperflash plugin that currently affects the dv6-6140us.  Namely, the speaker makes popping/ticking/clicking noises whenever I had GMail open.  I fixed the problem by disabling Pepperflash, per [http://ubuntu-with-wubi.blogspot.com/2012/07/weird-clicking-noise-in-chrome.html]("http://ubuntu-with-wubi.blogspot.com/2012/07/weird-clicking-noise-in-chrome.html")

---


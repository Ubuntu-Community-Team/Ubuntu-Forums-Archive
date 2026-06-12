---
title: "How do I install 14.04 in EFI along with Windows 8?"
date: 2014-10-11
forum: Installation &amp; Upgrades
---

### Post by davy jones on 2014-10-11
My problem is a little tricky, and therefore I'm summing the entire issue up with as much detail as possible because I urgently need help.

I have Dell Inspiron 3521 which came with Windows 8 pre-installed. The  BIOS version is A05. It has 4 GB RAM. The system has dual graphics -  integrated Intel(R) HD 4000 and a Radeon HD 8700 - total of 2 GB. It is a  64 bits system. I installed 12.04 in it which used to boot in Legacy.  It is not a WUBI install.

A few days ago, I clicked on the 'upgrade hardware support' option in  Update Manager. This screwed up my system. The graphics driver, flgrx,  no longer worked, and my boot partition became completely full. I  managed to purge flgrx but wasn't able to reinstall it properly. I did a  clean-up using Ubuntu Tweak, so that it would clear up the boot  partition. After I did that, Ubuntu just would not boot. It would get  stuck on a screen that says "could not write bytes: Broken pipe".

I booted from a Boot Repair disc which basically made me remove GRUB  from Legacy and install it in EFI. This is what the bootinfo was before  it did its thing -
[[COLOR=#dd4814]http://paste.ubuntu.com/8533672/[/COLOR]]("http://paste.ubuntu.com/8533672/")

 And this is what it was after -
[[COLOR=#dd4814]http://paste.ubuntu.com/8533762/[/COLOR]]("http://paste.ubuntu.com/8533762/")

Whatever it did, did not work, because the exact same thing is still  happening. Now since I have to boot in UEFI, the GRUB screen shows up  every time.

Now I think my only choice is to install 14.04, but I need detailed,  step-by-step instructions on how to go about doing this in my current  situation, which is summed up above. I need to know whether 14.04 will  use the same mount point or not. I also need to know how to install it,  because there doesn't seem to be an option to boot from the DVD drive in  UEFI. I would also need to back up my data, and if possible I would  like my settings and applications to remain unchanged. I know this is a  tall ask, but I thought it might be possible, since upgrading to 14.04  from Update Manager claimed to leave your settings unchanged, and I have  a lot of different settings here and there along with several apps and  it's a real pain to get them all back manually (which is why I like to  install LTS versions and just leave them be for as long as possible).

This is a code red situation, so I need help ASAP, and I need detailed instructions. I would be owe a big one to anyone who can provide me with that. Thanks in advance.

---

### Post by oldfred on 2014-10-11
You can also use Boot-Repair to convert back to legacy/BIOS/CSM boot if desired.

But Boot-Repair did the rename, undo that before you do anything. And do not use any auto install option. See warning in link in my signature.

       Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   With the renamed file you cannot directly boot Windows from UEFI menu as it really is shim.
And a Windows update may rewrite the bootmgfw.efi file overwriting the shim version, so then if you can only boot the Windows version you have to rerun boot repair. If you can boot Ubuntu entry in UEFI menu, undo the rename.

   Boot-Repairs rename copies this /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi, becomes this:
/EFI/Microsoft/Boot/bkpbootmgfw.efi

That should fix booting with Windows from UEFI menu. And since a Dell you may be able to boot Ubuntu, but I do not know dual video with Intel and AMD?? Drivers are implemented differently with UEFI and BIOS and may be part of your issue.

You really need to do backups when system is running. Do not know a way to export installed apps except from a running system. But you should be able to backup /home from a live installer if needed.

      
 Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

I thought Dell needed sputnik to work with 12.04, but all of sputnik was incorporated into 14.04.
       Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)
New Haswell Sputnik - Dell orbits Linux a third time with revamped Sputnik notebooks
[http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/](http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/)

---

### Post by ajgreeny on 2014-10-11
Hybrid graphics of Intel/AMD are not well supported yet so you may have some problems with that, but I do not have any way to help you there apart from suggesting that **you should not ask the system to install third party packages as you install**, as that will pull in the AMD driver which may cause you problems.

As for installing in dual boot with UEFI, I will point you to [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI") which should have all the answers you need.  Read it carefully and come back again with any questions it does not answer to your satisfaction.

---

### Post by ubfan1 on 2014-10-11
Your boot partition still looks full.  Try removing some old kernel packages.

---

### Post by davy jones on 2014-10-12
Thanks for the quick replies.

Oldfred, I don't have a problem booting Windows. It is booting normally. Only Ubuntu is not. It was in Legacy earlier when it stopped working so I don't know if changing the boot back to Legacy will help. Also, the Boot Repair live disc doesn't let me access my Documents folder, even though it lets me enter /home, so I can't back up my files this way. Will it be any different with the Ubuntu 14.04 live disc?

Ajgreeny, I tried [https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode) because it seemed like my problem. But the 'separate /boot/efi partition' option was already ticked. There was also an option of 'separate /boot partition' which was ticked. I unticked it and Boot Repair did several things - it reinstalled GRUB, cleared old kernels and reintalled the last one. Here is the output -
[http://paste.ubuntu.com/8545918/](http://paste.ubuntu.com/8545918/)

But this did not help me in booting Ubuntu, so I ticked the 'separate /boot partition' box again. This is the output after that -
[http://paste.ubuntu.com/8546000](http://paste.ubuntu.com/8546000)

This has also not helped. When I tried to boot Ubuntu now, it gave me a black, terminal-like screen asking for my login and password. After I entered those, it stayed on the same screen with a terminal like prompt (username@systemname$). I had no idea what to do with that so I entered 'sudo reboot'. After rebooting, it got stuck on the 'Ubuntu loading' screen again.

One thing I should mention is that Boot Repair tells me to select the boot file sda1/EFI/ubuntu/grubx64.efi in BIOS, but I don't know how to do this. There is no such file in the GRUB menu when the system starts.

So the problem is still not solved. My first priority right now is to get my data out, and I really want to know how I can boot Ubuntu because I've tried so many things and nothing has worked.

---

### Post by grahammechanical on 2014-10-12
> [COLOR=#000000]select the boot file sda1/EFI/ubuntu/grubx64.efi in BIOS, [/COLOR]

Notice, it says BIOS not Grub. The machine needs to be loading from sda. With Grub installed into sda it will then use grubx64.efi and then look in /boot in the Ubuntu partition for it configuration file which it uses to give us the Grub boot menu. Boot Repair is simply stating the obvious to cover all situations. I notice this from the second Pastbin link in you last post.

> [COLOR=#666666]===================[/COLOR] Final advice in [COLOR=#AA22FF]**case **[/COLOR]of recommended repair
Please [COLOR=#AA22FF]**do **[/COLOR]not forget to make your BIOS boot on sda1/efi/.../grub*.efi file!

[COLOR=#666666]===================[/COLOR] Default settings
Recommended-Repair
This setting would reinstall the grub-efi of sda7, using the following options:        sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot backup-and-rename-efi-files

[COLOR=#666666]===================[/COLOR] Settings chosen by the user
Boot-Info
This setting will not act on the MBR.

No change has been performed on your computer.

You did not accept the recommended repair this time. The first running of Boot Repair should have fixed the problem. So, may be this is not a Grub problem. Boot Repair does not fix or even attempt to fix loading/boot problems that happen after Grub has launched the Linux kernel.

Perhaps we are all barking up the wrong tree.

Regards.

---

### Post by oldfred on 2014-10-12
Your UEFI is also a boot manager, where grub is a boot manager and a boot loader. Boot managers give you a menu of boot options. Where BIOS only gave you hardware drvices, UEFI reads efi partition and gives all the installed systems as additional choices.

You have to use f2 or del or whatever your UEFI/BIOS key is or many systems have a one time boot key. And then you see the UEFI boot options or its menu.

Are you booting this from grub menu to get to Windows?
 menuentry "Windows UEFI bkpbootmgfw.efi" {

That is the renamed by Boot-Repair Windows boot file. If grub is not working then you cannot boot Windows.

You have a /boot partition. With most desktop installs, I suggest not to have that as a separate partition. It adds to confusion and as ubfan1 pointed out (and I missed) that your boot partition is full. You have to regularly delete old kernels if you have a separate /boot. You should even if you do not, but then have more room before entire / (root) partition is full.

You have the separate /boot partition, but still have a previously unused /boot folder in / (root). But when you unchecked the separate /boot partition, Boot-Repair reinstalled grub and installed a new kernel in your boot folder. And it updated grub to remove the entry to use kernel in /boot partition, but to use kernel in /boot folder. And it commented out the entry in fstab to use the /boot partition.

When you then redid it with /boot partition checked it reverted to using the /boot partition, but it looks like it did not rerun a sudo update-grub so your actual boot is still from the /boot folder not the full /boot partition. If you are at terminal and run sudo update-grub then it will reset and only boot from /boot partition.
Clear as mud?

I think it may be better to uncheck /boot partition, in effect obsoleting it.

And it seems your issues are related to video drivers.
Do you know which video mode you are booting with Intel or Radeon? Or is your system separate video ports on system? Or can you set which mode you boot with in UEFI/BIOS?

I think most of the suggestions by ubfan1 link are for Intel driver. Often nomodeset works for nVidia or AMD to get into low quality graphics. With AMD it may depend on model whether you want proprietary driver or not.
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

Dell with Intel/AMD dual video 
[http://ubuntuforums.org/showthread.php?t=2240312](http://ubuntuforums.org/showthread.php?t=2240312)

Summary report did not show this, but it should be available if you have booted in UEFI mode. And then in UEFI menu you should have same options. Often you have two ubuntu entries, one is grub and the other shim for secure boot.
 # from liveDVD or flash and use efibootmgr
modprobe efivars
sudo efibootmgr -v

---

### Post by davy jones on 2014-10-12
Thanks for replying quickly. I was also getting the feeling that Boot Repair cannot fix whatever problem I have, but now when I try to boot into Ubuntu, it does freeze on the screen that says 'could not write bytes: Broken pipe'. Instead it gives me a terminal-like screen asking for my login and password. After I enter it, it tells me that the new version of Ubuntu, 14.04, is available and gives me a command prompt (username@systemname:~$). I don't know what to do in this situation. How do I get it to get me into my desktop??

---

### Post by davy jones on 2014-10-12
Hey, I have muxed system as far as I know, and before that ill-fated hardware support upgrade, I had selected the Intel card on Catalyst Control Centre to save power. I don't think I can set it on UEFI/BIOS, because I went through a long process to install flgrx last year. I'll try to change it to nomodeset in GRUB and post what happens.

Thanks again for these detailed instructions. They really help because I'm very tech-challenged :-)

---

### Post by davy jones on 2014-10-12
I followed the instructions - pressed 'e' in the GRUB menu, changed 'quiet splash' to nomodeset and pressed F10 - and it seemed like the system ran some processes, because there was a lot of text on the black screen (I think it ran fsck), but it gave the terminal like black screen again asking me to enter my login and password and then giving me a command prompt.

EDIT: I booted with Boot Repair disc to uncheck the 'separate /boot partition' like you said. It was already unchecked in the Advanced Settings. I clicked Apply and it did its thing. The output was this -
[http://paste.ubuntu.com/8547252](http://paste.ubuntu.com/8547252)

Now, there is a change. When I try to boot into Ubuntu, instead of the black terminal screen asking me for my login and password, it just freezes on a blank screen. If I change 'quiet splash' to nomodeset and press F10 now, the GRUB menu goes away, but it just freezes on the background (with "Debian The Universal System" at the bottom). What do I do now?

---

### Post by oldfred on 2014-10-12
It still is video issue causing it to not boot. Not sure why you would get different places just by  having different boot partition or folder. Perhaps one is older kernel and somehow that makes a difference.

If Intel video is the default when booting, you often need the other settings, not nomodeset in ubfan1's post above. You force the Intel to use correct X by & for your screen.

---

### Post by davy jones on 2014-10-12
So what do I do now?

---

### Post by oldfred on 2014-10-12
Did you try the Intel video settings instead of nomodeset?

---

### Post by davy jones on 2014-10-12
How do I do that?

---

### Post by oldfred on 2014-10-12
Post #7, the suggestions in link by ubfan1 are mostly Intel based. But you may need to just experiment with all of them.

Also in #7 was link to another user with similar Intel/AMD. That may have more details that are better.

---

### Post by davy jones on 2014-10-13
I honestly don't know how to implement any of this. Most of the links seem to be instructions for when you're actually able to boot into Ubuntu and login. The only one that makes sense is [http://ubuntuforums.org/showthread.p...0#post12871710]("http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710"). But I'm unclear on where exactly to add this and I don't want to mess things up even more badly by adding it somewhere it's not supposed to be, or by incorrect syntax. For example, this says that I'm supposed to add this to the Linux line, but I don't know at what point I should add it, and whether I should add it as a continuous code or line by line like it says here (since the Linux line seems to be continuous right now).

---

### Post by davy jones on 2014-10-13
Any ideas?

---

### Post by oldfred on 2014-10-13
All the boot options are just like adding nomodeset.
You said in #10 that you changed nomodeset on the linux line by replacing quiet splash.

Some suggest adding it to that line, but I prefer to replace the quiet splash so you see the boot process. While it scrolls by pretty quick, you sometimes can catch an error. Where is stops of often several lines past the main issue.

You can also try the recovery boot line in menu, and if that works you can get to a terminal sign on and run commands. That gives text menu with several options. Usually need to choose the add Internet option, so you can run updates from repository.

---

### Post by davy jones on 2014-10-13
I tried to boot after adding the code I mentioned in #16 and it led me to an eternal blank screen again. I added it right at the end, just to be clear. Was that correct?

Also, I've gotten to that terminal sign on a few times, but I just don't know what commands to run to try to fix my problem, or at least identify it.

I think now after trying so many different things, I just need a way to properly install/upgrade to 14.04 without deleting my data on /home. Best thing would be if I could actually back it up, but if there's a guarantee that /home would not be touched in an upgrade, I can still do it since there doesn't seem to be another choice. My last bootinfo is in #10. Given all this, how do I go about installing 14.04?

---

### Post by oldfred on 2014-10-13
Did you try each of these instead of nomodeset? but change from example to your exact monitor X by Y size, not 1280x1024:

i915.i915_enable_rc6=1
video=1280x1024-24@60
video=VGA-1:1280x1024-24@60

With any major change there are no guarantees. 
That is why we always (or should) suggest backups of both Windows & Ubuntu.

Do not use any auto reinstall option, it will erase your entire hard drive even if it just says it is overwriting a previous Ubuntu. Only use Something Else. Fix will not be in any current ISO.
       Reinstall says overwrite Ubuntu but it also erases existing Windows. 
Sept 2014 Fix being released for one drive installs, but mulitple drive installs must use Something Else.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

      
 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

From live installer you should be able to backup /home. But be sure to include hidden files & folders also. If you changed a lot of hardware configurations, you should also backup /etc but if a new verson do not just restore it. New version may need different settings, better to use /etc backup as reference if needed.

If you can boot to a terminal you can try running updates.


 sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

---

### Post by davy jones on 2014-10-14
I added each of the options after the end of all the text, but in the same line, this time changing 1280x1024 to 1366x768, my screen resolution. Zilch. The exact same blank screen every time. I also tried to boot in recovery mode, but even that got stuck on this screen -

[ATTACH=CONFIG]257198[/ATTACH]

I don't know much about this, but I'm beginning to think that unchecking the 'Separate /boot partition' option has made a change. Please correct me if I'm wrong.

Just to be clear, I did shrink the Windows partition on my laptop from Windows only, but created the Ubuntu and another data partition using GParted from the Ubuntu LiveDVD when I installed 12.04 a year ago. So does [http://ubuntuforums.org/showthread.p...0#post12611710]("http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710") apply to me? If I back up Windows using Macrium Reflect, will I be able to restore everything in the Windows partition in case anything goes wrong? And does "Linux Boot CD" mean an Ubuntu LiveCD or USB?

How do I backup /etc? Will backing it up mean that I can restore the different apps I installed? Or can that be done by backing up the hidden files and folders of the various apps in /home?

Lastly, do I need to worry about whatever Boot Repair has done until now? Looking at the last bootinfo in #10, can I just go ahead with installing 14.04 or do I need to do something else? And do you think that getting different results after unchecking the 'Separate /boot partition' option in Boot Repair the last time is anything significant?

---

### Post by oldfred on 2014-10-14
I have not used Macrim, have not had Windows for a couple of years. But I believe it creates a boot disk to restore Windows and it uses Linux?

You should use Something Else to reinstall. You chose existing partition with change button on partition screen. Just reuse existing partitions. I do not recommend the separate /boot for most systems.

The tick & untick of separate /boot determines whether the kernels & grub in /boot partition or in /boot folder in / (root) partition are used. And it seems like you did the total reinstall with both so they should be the same. But it seems the grub.cfg is not updated so it may be always using one version? If you have re-run Boot-Repair since post #10 then it may have changed.

The settings for all your apps are in /home, so backing that up includes your user settings & your files. I do prefer a separate /home or data partition(s), so user data is separate. A separate /home is easier for a newer user as you just create and configure during Something Else manual install. 

Data partitions are more advanced as you have to separately create a partition, format it either NTFS if using Windows or ext4. And if a Linux format you have to set ownership & permissions. And you have to manually mount in fstab so it can easily be used. Not really difficult if used to terminal and somewhat familiar with Linux. But not really for a new user who is not familiar with partitions, mount & terminal use.

If you have installed a lot of applications, you need to export list. This list is very long as it also includes all the dependencies. You will not be reinstalling anything already installed by default. It is just a text file.

       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

My rsync backup includes an export of packages and save into /home. Then my backup of /home has a current copy of all installed apps.
If you have manually modified any system settings like Ethernet, grub, Network or others those would be in /etc and maybe that should be backed up. I edit grub manually and try to remember to just copy those files into /home so my default backup of /home includes that without full backup of /etc.

---

### Post by davy jones on 2014-10-14
The data partition I currently have is NTFS. Should I back up all the data on that as well? Also, I have a Cryptkeeper encrypted folder in /home. If I just copy it, can I access it after I install Cryptkeeper on 14.04? Or is there a way to decrypt it using the Live DVD?

I really appreciate the effort you're putting in. I owe you big time already. I'll probably owe you more by the time this thing gets done :-)

---

### Post by oldfred on 2014-10-14
It never hurts to have too many backups.

Even those of us who know better get caught. Systems internally know if we have backed up or think since we are just making a quick easy change do not make the backup. 
If system knows we did backup it always works to make changes. But if we did not do backup, it makes our fingers type the wrong thing and destroy system. :)

---

### Post by davy jones on 2014-10-14
I tried to boot using the Live DVD, just to back up my data this time. It just would not boot in UEFI. However, it wasn't like it just didn't detect a bootable disc and moved on. It just froze on the Dell screen on which you can hit F2 to enter setup and F12 for boot options. I then changed the boot mode to Legacy and selected the DVD drive in boot options. Now the disc has booted, but it still won't let me access my data on /home. It opens /home, and even displays the hidden files and folders of all the apps, but when I go to Documents and click on a subfolder inside it that has all my data, it says that I do not have permission to access it.

---

### Post by oldfred on 2014-10-14
Does gksudo nautilus from terminal work?
Even though live installer does not have an admin user or password?

---

### Post by davy jones on 2014-10-14
It says that gksudo is not installed when I run the command.

Also, I was able to access the boot folder in the / partition and it turns out that there is no file in the efi folder in it. But the efi folder in the /boot partition has a Boot folder that has a bootx264.efi file and a bootx264.efi.grb file. There's also an Ubuntu folder which has a grubx64.efi file.

---

### Post by oldfred on 2014-10-14
Install gksudo, even with live installer you can add just about anything. It just will not be saved and if you reboot you have to add it again.

sudo apt-get install gksudo

Are you sure the efi partition you are looking at is not the live installer's partition?

Post this:
sudo parted -l

---

### Post by davy jones on 2014-10-15
Something weird is happening when I run gksudo nautilus. The first time I ran it gave me this -

```
(nautilus:9070): GLib-GIO-WARNING **: Missing callback called fullpath = /root/.config/user-dirs.dirs


(nautilus:9070): GLib-CRITICAL **: Source ID 169 was not found when attempting to remove it

(nautilus:9070): GLib-CRITICAL **: Source ID 170 was not found when attempting to remove it

(nautilus:9070): GLib-CRITICAL **: Source ID 171 was not found when attempting to remove it

```

It said that a /root/.config/nautilus directory had to be created by me or I should give permissions to do so. But the second time I ran the same command, I was able to access the subfolder I needed to in /home/Documents, but I cannot seem to copy it to anything. It says I don't have the permission to do it. And the second I try to view the properties of this subfolder, a window saying that I don't have permissions appears momentarily and the whole Files window closes down. It gives the following output in the terminal -

```
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

**
ERROR:nautilus-properties-window.c:1839:schedule_owner_change_timeout: assertion failed: (NAUTILUS_IS_FILE (file))
ubuntu@ubuntu:~$ gksudo nautilus
**
ERROR:nautilus-properties-window.c:1839:schedule_owner_change_timeout: assertion failed: (NAUTILUS_IS_FILE (file))
ubuntu@ubuntu:~$ gksudo nautilus
**
ERROR:nautilus-properties-window.c:1839:schedule_owner_change_timeout: assertion failed: (NAUTILUS_IS_FILE (file))
```


Output of sudo parted -l -

```
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  525MB   524MB   fat32           EFI system partition          boot
 2      525MB   567MB   41.9MB  fat32           Basic data partition          hidden
 3      567MB   701MB   134MB                   Microsoft reserved partition  msftres
 4      701MB   1226MB  524MB   ntfs            Basic data partition          hidden, diag
 5      1226MB  109GB   108GB   ntfs            Basic data partition          msftdata
 7      109GB   130GB   21.0GB  ext4                                          msftdata
 8      130GB   131GB   512MB   ext4                                          msftdata
 9      131GB   152GB   21.0GB  ext4                                          msftdata
10      152GB   157GB   5000MB  linux-swap(v1)
11      157GB   157GB   1049kB                                                bios_grub
12      157GB   990GB   833GB   ntfs                                          msftdata
 6      990GB   1000GB  10.3GB  ntfs            Microsoft recovery partition  hidden, diag


Model: PLDS DVD+-RW DU-8A5HH (scsi)
Disk /dev/sr0: 4700MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac

Number  Start   End     Size    File system  Name   Flags
 1      8192B   24.6kB  16.4kB               Apple
 2      3979MB  3989MB  9568kB               EFI
```

sda8 is the /boot partition.

---

### Post by oldfred on 2014-10-15
I know one of the complaints was that it was too easy to just boot a live installer and destroy a system. So maybe they have changed things. 
But you can run repairs and fix a system from a live installer, so not sure why you have issues.

I am sure you can chroot into your system as that is how we fix it if need be. Boot-Repair also uses chroot to to a full uninstall of grub.

If you have a separate /boot partition or any other system partitions as separate partitions you must also mount those. Some instructions on chroot leave that out as most Desktop installs do not have more than / & possibly /home as separate partitions.

       UEFI chroot
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

Some other examples
      
 drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

---

### Post by davy jones on 2014-10-16
Sorry, but I'm finding the instructions on these pages hard to understand and follow. Can you please simplify them? For starters, by the same version, do you mean that I should create a Live CD of 12.04? And is this only to reinstall grub or will it help me get my data out as well? Also, can running all these commands harm the Windows installation in any way?

---

### Post by oldfred on 2014-10-16
If you have your 14.04 flash drive that should be ok. It just is current version or newer, but some users pull out a three year old cd and find it does not work well.

There is a bug in the installer where if Windows is not seen it can be overwritten, and on a reinstall it will not see Windows and may say it is replacing Ubuntu but erases entire drive. You must use Something Else to reinstall. If you have existing partitions it is better to use Something Else anyway. Do you have a separate /home? If so you also must use something Else and choose /home also but DO NOT format it.

Is it the chroot you do not understand?
What are you backing up and where are you copying the data to. Another hard drive?

Did none of the fixes get you booting?

 Reinstall says overwrite Ubuntu but it also erases existing Windows. 
Sept 2014 Fix being released for one drive installs, but mulitple drive installs must use Something Else. And fix is not in current versions.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by davy jones on 2014-10-16
Yes I don't understand exactly how chroot works which is why I haven't actually tried the fixes in any of the links in #30 since I don't want to accidentally cause irreparable damage. I want to know where I would start implementing it, given the state of my system right now. I have not made any changes using Boot Repair since #10. 

> I booted with Boot Repair disc to uncheck the 'separate /boot  partition' like you said. It was already unchecked in the Advanced  Settings. I clicked Apply and it did its thing. The output was this -
[http://paste.ubuntu.com/8547252](http://paste.ubuntu.com/8547252)

The efi-grub files situation is what I mentioned in #27.

> Also, I was able to access the boot folder in the / partition and it  turns out that there is no file in the efi folder in it. But the efi  folder in the /boot partition has a Boot folder that has a bootx264.efi  file and a bootx264.efi.grb file. There's also an Ubuntu folder which  has a grubx64.efi file.

 Given all this, where should I start with chroot? Or is it an issue I can just fix with Boot Repair? Also, will the whole chroot thing affect the Windows installation?

I've always selected the Something Else option while installing so I plan to do the same. But installing 14.04 is a bridge too far right now, because first I need to backup my data in any way possible - either from the Live CD or after getting the OS to boot somehow.

I have three partitions in the Ubuntu install - /, /home and /boot. I'm trying to get the data in /home - my apps and settings as well as my documents etc - and back it up to an external hard drive.

---

### Post by oldfred on 2014-10-16
I am not sure if from a chroot you can get the list of installed apps, but I would think so.

I really prefer not to have the separate partition for /boot as most desktops do not need it. And it adds to the confusion as we are having. It also needs more maintenance so it does not get full. As you show many kernels in your /boot partition.

Chroot is CHange ROOT or you boot with a working kernel from installer but switch so entire rest of system is working from your install. It should not do anything to Windows unless of course you tell it to delete Windows. You should also have the backup of Windows before anything else. Did you backup Windows?

I do not know if Boot-Repairs reinstall of grub & kernel without /boot means we can chroot without it or not. This does not include the /boot mount. You do have to only use command line once in chroot. That is why I suggested using live installer first.

# anything after # is a comment do not copy. If you get any errors post those, rest of commands may not then work.
       sudo mount /dev/sda7 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot /mnt
#Then run whatever commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain you mounted the correct partition).
apt-get update
apt-get upgrade
       apt-get dist-upgrade
           apt-get -f install
dpkg --configure -a
# see if this exports a list of installed apps, if so copy that to some other drive so it does not get overwritten on update.
      dpkg --get-selections > ~/my-packages
# You also then may need to manually mount /home and copy it to another drive using terminal commands.

#When done:
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

---

### Post by oldfred on 2014-10-16
I just booted my 14.04 live installer.
With gksu nautilus I was able to copy a file from my /home into another flash drive partition that I have permissions set to be usable.

I did have a few issues getting gksu or gksudo installed. I had to add the universe repository and install from command line. But then gksu nautilus worked and I could copy file.

---

### Post by davy jones on 2014-10-16
For some reason gksudo nautilus is not working for me. I can access the folder, but I can't copy it. When I try to view the properties so I can try to change the permissions, it opens a window saying that I don't have the permissions and Nautilus shuts down so quickly that I don't have the time to do anything.

I'll try the rest of this as soon as I backup Windows. Thanks.

---

### Post by oldfred on 2014-10-16
I am not sure you can change permissions with Live installer. But you should be able to copy.

---

### Post by davy jones on 2014-10-17
I've run these commands -

sudo mount /dev/sda7 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.confsudo chroot /mnt

I have become root in the terminal, and I mounted my /home partition using mount /dev/sda9 /mnt but I don't know how to access the files now. It's not happening through Nautilus as usual, and I don't know how to get into it from the terminal.

---

### Post by davy jones on 2014-10-17
Can't seem to unmount /mnt. It gives the following output -

umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

This is an emergency since I'm stuck in the live session until I can unmount /mnt

---

### Post by oldfred on 2014-10-17
I would remember the elephants. And if that does not work then power down, but you may have to run chkdsk on NTFS and e2fsck on ext4 partitions to fix them if they were not closed correctly. 

       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[xhttp://kember.net/articles/reisub-the-gentle-linux-restart/](xhttp://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by davy jones on 2014-10-17
But is there no other way to unmount /mnt? Isn't running fsck or chkdsk risky because it might delete data?

And what about the rest? How do I copy /home? As I've indicated before, my data is the number one priority. I have to get it out at all costs and I can't do anything that will compromise the data. Only after I've copied it safely will I want to fix the boot issue and install the upgrade.

---

### Post by oldfred on 2014-10-17
What are you copying data to?

I use rsync to copy to another drive. And K3b to copy most important data to DVDs in a semi-regular basis so if I delete or change something and backup to another drive also gets changed & I need original copy. 
I also copy some data to flash drive, but usually use Nautilus or sometimes rsync or cp commands.

---

### Post by davy jones on 2014-10-17
I've tried to copy the data to an external hard drive but it says I don't have the permission. That was with gksudo. I thought chrooting would give me the permissions to copy it but it hasn't. Or maybe I need to open nautilus from the terminal after becoming root and then try?

---

### Post by oldfred on 2014-10-17
Your chroot is command line only. 
I do not think you can use Nautilus in the chroot.

But just chrooting would not change settings and may be why you had issues with chroot and then opening same location with Nautilus.

What format is external drive's partitions? NTFS is wide open, but if ext4 you have to give yourself ownership & permissions to use it. Then Nautilus would let you copy to it.

Post this, use Nautilus to auto mount any external partitions first:
mount
sudo fdisk -lu
sudo parted -l

---

### Post by davy jones on 2014-10-17
EDIT: Okay, I just decided to try my luck with gksudo one more time, and even though the only thing I did differently this time was select 'copy to' and then choose my external hard drive instead of doing the regular copy-paste, it is miraculously copying my data now.

The external drive is NTFS only. This is the output -

```
ubuntu@ubuntu:~$ mount
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sda7 on /media/ubuntu/d7de0c35-3a40-40c1-af5b-1f19f4d86ded type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sda9 on /media/ubuntu/ac6616d9-90d8-48cf-ba7a-29b466e556bf type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sda8 on /media/ubuntu/c5e81b96-c6bc-412b-b740-8ef206d672be type ext4 (rw,nosuid,nodev,uhelper=udisks2)
ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x933c6254

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
ubuntu@ubuntu:~$ sudo parted -l 
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  525MB   524MB   fat32           EFI system partition          boot
 2      525MB   567MB   41.9MB  fat32           Basic data partition          hidden
 3      567MB   701MB   134MB                   Microsoft reserved partition  msftres
 4      701MB   1226MB  524MB   ntfs            Basic data partition          hidden, diag
 5      1226MB  109GB   108GB   ntfs            Basic data partition          msftdata
 7      109GB   130GB   21.0GB  ext4                                          msftdata
 8      130GB   131GB   512MB   ext4                                          msftdata
 9      131GB   152GB   21.0GB  ext4                                          msftdata
10      152GB   157GB   5000MB  linux-swap(v1)
11      157GB   157GB   1049kB                                                bios_grub
12      157GB   990GB   833GB   ntfs                                          msftdata
 6      990GB   1000GB  10.3GB  ntfs            Microsoft recovery partition  hidden, diag


Model: PLDS DVD+-RW DU-8A5HH (scsi)
Disk /dev/sr0: 4700MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac

Number  Start   End     Size    File system  Name   Flags
 1      8192B   24.6kB  16.4kB               Apple
 2      3979MB  3989MB  9568kB               EFI
```

---

### Post by davy jones on 2014-10-17
So thankfully, I've been able to get my data out. The next step would be to try to generate a list of apps by chrooting and using the commands you told me.

After that, there is still the issue of installation as I'm still unclear about what to do with the whole efi-boot situation. Also, my computer refuses to boot the live CD in UEFI, so I need to know how to do that as well, otherwise it'll get installed in Legacy. So far what I've been doing to boot from the live CD is to start the system, immediately hit F12 for Boot Options, then insert the CD (if it is in the tray on startup the system hangs on the Dell startup screen), and then under the Legacy Boot options, select the DVD drive and hit enter.

Really appreciate the help so far. Almost on the home stretch now!

---

### Post by oldfred on 2014-10-17
I do not know why DVD is showing a Mac partition, that is not a standard installer?

On my new motherboard I had to change a lot of UEFI settings to get it to correctly boot flash drive in UEFI mode. It kept wanting to boot in BIOS only. Even a setting that said UEFI first would not boot. Only UEFI only would work. And I had to turn on allow boot from USB or external or something. And the UEFI only settings were under the CSM/BIOS boot menu? 

Not sure with your system what UEFI/BIOS settings are required. Every one seems to be different. But check that you have allowed boot from USB in UEFI and secure boot is off. Sometimes new menus open up when you change a setting.

And only use Something Else. You should be able to reuse existing / and /home. I still do not suggest using /boot as a partition.

If external drive is NTFS you will lose permissions & settings. For all your data you can easily reset that, but system files probably cannot be restored as many have different settings not just root and various sets of ownership. Every one of your data files in /home are really just one setting and you are the owner so easy to change to correct settings if you have to restore.

---

### Post by davy jones on 2014-10-18
I downloaded 14.04 from the Ubuntu site and burned it on a DVD like I always do so I'm guessing it's a standard installer only.

I don't understand this whole thing about NTFS external drive. Do you mean that just copying the hidden files and folders of the apps and copying them back won't restore them? Or will even running the command that you told me to export a list not work? How do I make it work?

I'm uploading pictures of my BIOS menu. The Dell startup screen gives me options of F2 for setup and F12 for boot options. The first 4 are shots of the F2 setup and the last one is what I get when I press F12.

[ATTACH=CONFIG]257322[/ATTACH][ATTACH=CONFIG]257319[/ATTACH][ATTACH=CONFIG]257320[/ATTACH][ATTACH=CONFIG]257321[/ATTACH][ATTACH=CONFIG]257318[/ATTACH]

I've always kept Secure Boot off, but I can't find any setting that would allow me to boot from DVD drive in UEFI mode.

---

### Post by oldfred on 2014-10-18
I have only used Flash drives in recent history. They are reuseable, faster and now a lot lower in cost than before. I live too near a Microcenter store and the prices are always cheaper the next time I go in. Now USB3 versions on only slightly more than USB2 versions and USB3 flash drive is still 10% faster in my old USB2 port.

I so not see any setting either, but again sometimes changing settings somewhere else makes a difference.

You can install in BIOS mode, and use Boot-Repair to convert install to UEFI. All it really does in uninstall grub-pc(BIOS) and install grub-efi-amd64(UEFI).

Some of this may apply to any Dell with Intel chips.
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

 Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)


Have you updated UEFI/BIOS to latest version from Dell? Also if you do update you may have to reset some settings. With BIOS I had to reset everything and forgot a lot so I did do screen shots for next time. New UEFI remembers more settings in its NVRAM.

---

### Post by davy jones on 2014-10-19
Unless it is necessary to use a flash drive to be able to install in UEFI, I would prefer to do it through the DVD. I would also not like to meddle with the UEFI/BIOS version unless absolutely necessary because as I've proven, I'm not very tech savvy and doing unnecessary updates can lead to disaster for me.

I've turned off fast startup from Control Panel like it says in [http://www.everydaylinuxuser.com/201...e-windows.html]("http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html"). Secure Boot is already off from the BIOS. When I followed the instructions in this tutorial, i.e, pressing the power button and restart while holding the shift key, it led me here -

[ATTACH=CONFIG]257347[/ATTACH][ATTACH=CONFIG]257348[/ATTACH]

Do you think that if I insert the live CD and select the DVD drive, will it boot the disc in UEFI instead of Legacy? How will I know if it has booted it in UEFI and not Legacy? Is it advisable to fix this issue after installation using Boot Repair? By advisable I mean is there any chance of it causing harm to the system?

Also, do you think I need to fix the current boot-efi issue *before* I install or is that not necessary since my current Ubuntu install space will be repartitioned anyway?

---

### Post by oldfred on 2014-10-19
That looks more like a Windows screen on rebooting, but I do not know Dell's default UEFI/BIOS screen.

Another Link for a Dell user.
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)

---

### Post by davy jones on 2014-10-19
#48 has the BIOS menu on my laptop. The problem right now is that I don't know how to tell whether the live CD has been booted in UEFI or not. If I knew that I would try to do some trial and error. Although given all that has happened so far resulting from a single update and a cruft cleanup, I'd rather just install it in Legacy mode and then convert it to an EFI install using Boot Repair.

Is it possible that a live USB will boot in UEFI mode when a DVD doesn't?

---

### Post by oldfred on 2014-10-19
This shows both screens.
If you get grub menu you are in UEFI mode. If purple screen then BIOS mode.

 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Both DVD & flash drive should boot in either mode, but your UEFI/BIOS may not allow it or need setting to permit it.

---

### Post by davy jones on 2014-10-19
I think I'll just install it in Legacy and use Boot Repair to convert it later since I don't see a choice. But I want to know how to actually install it after selecting Something Else. You may have already seen the various partitions on my drive in the bootinfo paste bin. I'm uploading pictures of the partitions I saw in the install process because I want to be completely sure before I install.

[ATTACH=CONFIG]257355[/ATTACH][ATTACH=CONFIG]257356[/ATTACH]

I want to re-use the current / and /home partitions, but I since I want to remove the /boot partitions, and also reduce swap space, I want to know how to do that without damaging anything else.

---

### Post by oldfred on 2014-10-19
From your Bootinfo summary in post #10.
> UUID=96ff2bf7-5776-4d15-b5d8-c48d97652995 swap swap sw 0 0
UUID=365315F110F42CE7 /media/Data ntfs-3g defaults 0 0
UUID=ac6616d9-90d8-48cf-ba7a-29b466e556bf /home ext4 defaults 0 2
UUID=d7de0c35-3a40-40c1-af5b-1f19f4d86ded / ext4 defaults 0 1
#UUID=c5e81b96-c6bc-412b-b740-8ef206d672be /boot ext4 defaults 0 2
#UUID=c5e81b96-c6bc-412b-b740-8ef206d672be    /boot    ext4    defaults    0    2

      >  /dev/sda7        d7de0c35-3a40-40c1-af5b-1f19f4d86ded   ext4       
/dev/sda8        c5e81b96-c6bc-412b-b740-8ef206d672be   ext4       
/dev/sda9        ac6616d9-90d8-48cf-ba7a-29b466e556bf   ext4       
/dev/sda10       96ff2bf7-5776-4d15-b5d8-c48d97652995   swap

    

 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)



So / (root) is sda7 and you want to use change botton and set format as ext4 and mount use as / . With sda9 which is /home you want to set mount as /home but DO NOT tick the format button so it keeps current data. It should auto reuse swap. If you want you and delete sda8 and resize / before installing to use that space. It should default to sda as where to install grub2 boot loader. You already have the bios_grub for BIOS boot install. And if you boot into install you should be able to use Boot-Repair from either live installer or even inside your install to convert to UEFI. It uninstalls grub-pc(BIOS) and installs grub-efi-amd64(UEFI).

---

### Post by davy jones on 2014-10-20
Deleting the /boot partition and increasing the / size has to be done using GParted from the live CD? Will it definitely auto re-use swap or should I point it to the current swap partition to make it use that just to be safe? Also, if I'm given the choice of a 'primary' or 'logical' for these partitions, which should I select?

---

### Post by oldfred on 2014-10-20
I do prefer to use gparted for all partitioning changes, and then just select which partition is which (root, /home, etc) with Something Else installer. It has always seemed a bit easier in gparted than  the installer. You may have to swap off, but with gpt it may not be required unless you also want to edit/move/change swap partition.

You have gpt partitioning. There is no primary, extended, nor logical partitions. With gpt there is only one type essentially the same as primary. Since I have gpt I and use gparted I have not seen the specification or noticed the requirement to specify type of partition.

I had two swap partitions on my old drive and the installer added both  when installing to a different drive. Not sure how I ended up with two. I think I experimented with an auto install to see what it did and that created a second swap.

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by davy jones on 2014-10-20
So I should delete the /boot partition and expand / into that area using GParted only?

---

### Post by oldfred on 2014-10-20
I would as I have always thought gparted was easier.

---

### Post by davy jones on 2014-10-21
I installed 14.04, but as expected, there are issues.

I finally did it using a live USB. I got it to boot using Power->Restart while pressing shift and then selected the EFI USB drive device. I instantly knew I had booted in UEFI because of the screen. I deleted the /boot partition using GParted and resized / to fill up the empty space. I selected format for / in Something Else but not for /home.

When I restarted after the installation, I got to this screen -

[ATTACH=CONFIG]257396[/ATTACH]

When I booted next, I pressed F12 to go to the boot options. These were the options in UEFI -

[ATTACH=CONFIG]257397[/ATTACH]

I had to manually select the bottom Ubuntu one (the one selected), and then it showed a pink grub screen which had the option of Ubuntu, Ubuntu Advanced Settings, and Windows Boot Manager. Selecting Ubuntu gets me into the new 14.04 install, but selecting Windows gets me the same screen as in the first picture. Even if I select the Windows Boot Manager option in the BIOS boot options, I still get the same screen.

Basically, Windows isn't booting, and I have to manually select a particular option in the BIOS boot options to be able to boot into Ubuntu every time. Also, the middle Ubuntu option, presumably the 12.04 one, is still there. How do I fix this?

---

### Post by oldfred on 2014-10-21
I think you still had grub installed in gpt's protective MBR, so if you try to boot with BIOS it will see MBR and give grub error.

You have two ubuntu entries. One is grub (UEFI without secure boot) and the other shim (UEFI secure boot). 
If only one works do you still have secure boot on? There is an issue that grub will not boot Windows from grub menu when secure boot is on.

From the orginal UEFI menu, not grub menu can you boot into Windows? You may also have a one time boot key often f12 or f10, but varies by brand even model of system.

If not run Boot-Repair, but make no fixes. Just post like to the boot info summary report.

---

### Post by davy jones on 2014-10-21
Secure Boot is still off. I did not make any changes in the BIOS for the installation. Selecting either Ubuntu option in the F12 boot options is leading me to the same place - the grub menu from where I can boot Ubuntu but clicking on Windows gives me that screen. So I don't know which one is grub and which is shim. I can't even boot into from the BIOS menu (after pressing F12 and selecting Windows). Here is the bootinfo - [http://paste.ubuntu.com/8615927/](http://paste.ubuntu.com/8615927/)

Also, the 14.04 install is a bit buggy and erratic, most of the things can be sorted out after the boot issue is resolved, but I need help with installing the flgrx driver because my fan is constantly running right now and the battery is draining too fast. This tutorial [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD) is not working for me.

EDIT: I tried to install the flgrx driver, but something weird has happened. AMD Catalyst Control Centre has been installed but the graphics driver is not installed, or is not working. I managed to get as far creating the packages from the latest version using the AMD site and then installing them. I was careful to change the name in the code to that of the driver I'd downloaded. When I try to run sudo aticonfig --initial or sudo amdconfig --initial it just says "no supported adapters detected".

---

### Post by oldfred on 2014-10-21
I only have nVidia so do not know about AMD drivers. 
But with nVidia I prefer to only install from repository which is using system settings and additional drivers. Installs from AMD may have issues working with Ubuntu. 

Also I understand chip/card version with AMD makes a big difference as the very newest do not work well yet and the very old are discontinued and you have to find a legacy driver.

You still have this:
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

That is really the Windows efi file. And the standard Windows file bootmgfw.efi is really grub so that is 
why booting Windows just loops back to grub.
 
You need to restore the Windows version to bootmgfw.efi. Normally the undo in Boot-Repair will do that, but with your changes I am not sure.

 Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
**To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.**

   Any rename either manually or with Boot-Repair of bootmfgw.efi will need to be redone after a Windows update as it will restore Windows files.

---

### Post by davy jones on 2014-10-21
Sorry but I don't understand. What should I do now? Run the recommended repair? Or use advanced options? What all should I tick/untick in that?

There was nothing in the Additional Drivers for me, so I had no choice but to try to install the AMD driver. The thing is, the driver was working perfectly well in 12.04 until I installed that upgrade. I'd selected the integrated card in Catalyst Control Centre and that had doubled my battery life.

---

### Post by oldfred on 2014-10-21
What model AMD chip?

You need to run the bolded command I posted above. I think that is in advanced mode in Boot-Repair, but have never used it.

---

### Post by davy jones on 2014-10-21
Okay I'll run Boot Repair tomorrow and post the outcome.

The new install has been very buggy and erratic. The first few times I checked Additional Drivers, it showed nothing. This time, it has shown me the options. I had purged flgrx from terminal earlier to have a clean slate. An open source driver was being used and I've changed it to the proprietary one - flgrx. There was another option - flgrx updates, but I've selected flgrx, and it's worked.

The install's bugginess is not just limited to this. Weird things are happening in Gnome Flashback Compiz, which I selected because I've always used Gnome and don't like Unity. There is no menu on top of Nautilus windows, so I can't access Files, Edit, Go etc. Also, I can't add bookmarks in Nautilus.

Cryptkeeper doesn't always launch on the first click. Sometimes I've to click it multiple times for the icon to appear on the top panel. Video thumbnails are not being generated. I can't find Mount Manager in Software Centre which I need to make sure that my data partition mounts on startup. My hidden files are showing automatically on startup even though I did not select that option. I enabled switching applications through Compiz so that alt+tab works but it doesn't happen automatically on startup.

EDIT: The install is really buggy and I'm beginning to think that it's because my settings in /home were preserved and that's causing some sort of conflict. I downloaded Nemo and set that as my default file manager, set up my bookmarks and preferences etc. It still wouldn't show me video thumbnails so I decided to delete the ~/.cache/thumbnails folder like I read somewhere and log out. When I logged out, it said that my system was running in low graphics mode and gave me options of running in low graphics mode for just one session or reconfiguring graphics etc. This is despite the fact that flgrx is supposedly installed and I've made a selection in CCC. I selected the first and tried to log in but it just froze on a black screen with a cursor. I restarted it and now it has not remembered any of my settings. Nautilus is still the default browser, but there are icons for Home, Computer, and Trash on my desktop that I never put. My wallpaper is not showing and neither are the bookmarks I selected in Nemo. The fan is constantly running.

There is suddenly a mnt folder in / which wasn't there before. My data partition which was booting in /media/username, booted from /mnt instead. There is a Bootinfo and boot-sav folder in /mnt and a boot-sav folder in / as well. I think this might've been because to get the data partition to mount on startup, I used Disks to turn the automatic mount options off for the data partition. It sounds stupid, but I thought that would make it mount on startup since it showed the mount on startup option checked.

I'm also unable to remove these icons from my desktop. Even after I undid what I'd done in Disks and restarted, everything is the same except for the fact that the data partition is booting where it was supposed to be, but the /mnt and bootinfo, boot-sav folders are still there. What do I do?

---

### Post by oldfred on 2014-10-21
Did you go back and  look at some of the specific threads on Dell?

I do not have a Dell and cannot help on most issues. 

And now title is not what your new issues are. So users that may be able to help will not see this thread or read it as it now is long.

Best to pick an issue and start a thread just on that issue. Make sure title shows both computer model & issue as best as you can fit it in title and explain issue. Show version installed and which gui you are running.

I do only mount my data partitions in /mnt/data. Not sure how Disks does it as I only manually edit fstab.

---

### Post by davy jones on 2014-10-22
I ran Boot Repair. I selected Advanced Options and checked the Restore EFI backups option and did not touch anything else. This was the output -
> 
An error occurred during the repair.

Please write on a paper the following URL:
[http://paste.ubuntu.com/8624586/](http://paste.ubuntu.com/8624586/)

In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] 

You can now reboot your computer.


The boot files of [The OS now in use - Ubuntu 14.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

Now Windows boots by default without a grub menu showing up. If I want to get to grub, I still have to press F12 on startup and choose the Ubuntu entry in the boot options. From grub I can select either Ubuntu or Windows, but it's obviously still a problem since I have to go into boot options every time.

---

### Post by oldfred on 2014-10-22
Your Dell should let you change UEFI boot order and boot ubuntu. Many other system do not and we rename bootx64.efi and copy grub inot /efi/Boot as bootx64.efi and set UEFI to boot hard drive.

I would first see if in UEFI you can change boot order to ubuntu first. 
If not see if using efibootmgr will let you change to make ubuntu entry first. 
And if none of those work we can rename bootx64.efi. And then in UEFI change to hard drive first in boot order.

These are essentially the same:
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order](http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order)
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)

---

### Post by davy jones on 2014-10-23
I managed to change the boot order in the BIOS menu. Now it's working. But just to confirm do you think I need to worry about this output that Boot Repair gave me the last time?
> 
The boot files of [The OS now in use - Ubuntu 14.04.1 LTS] are far from  the start of the disk. Your BIOS may not detect them. You may want to  retry after creating a /boot partition (EXT4, >200MB, start of the  disk). This can be performed via tools such as gParted. Then select this  partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

Thanks a tonne for all the help, mate! Really appreciate it. Cheers!

---

### Post by oldfred on 2014-10-23
The far from start of disk, is for old BIOS with IDE drives and some BIOS when installed to USB drives. 

I have yet to see anyone with the boot issue caused by far from start of drive with a newer UEFI based system.

---

### Post by davy jones on 2014-10-23
Cool. Thanks a lot again! I honestly don't remember getting help for such a long period from anyone!

---

### Post by oldfred on 2014-10-23
You are welcome. :)

---


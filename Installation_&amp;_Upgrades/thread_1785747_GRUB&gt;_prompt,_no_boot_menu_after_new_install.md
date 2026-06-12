---
title: "GRUB&gt; prompt, no boot menu after new install"
date: 2011-06-18
forum: Installation &amp; Upgrades
---

### Post by CrankyOldMan on 2011-06-18
Hi!

I've used Ubuntu three years, but don't  know much about installing it.  My system is down and I need help.    This is a dual boot Windows 2K / Ubuntu 9.04) laptop that a friend put together for me. 

Wednesday I opened the update manager I got a pop-up saying  support for 9.04 was ended and I wouldn't get any more security updates.   I was presented a selection  to upgrade to 9.10, so I ran it.  The upgrade  ran smoothly, and I was up and running just fine.   

Last night I reopened the update manager and discovered  9.10 is also "end of life".  I was offered an update to 10.04 LTS.    I had good luck with the first upgrade, so what the heck.....
The files downloaded smoothly, but the installation was a disaster, with many error messages.  It tried to revert to 9.10, but froze.  On reboot, all I had was a few cryptic lines of code on a black screen.  

At this point I should have contacted someone to see what, if anything, I could do to save 2 years of email and data, but I decided to abandon it, and do a fresh install.   I already had a 10.10 "Live CD".    I booted it up,   formatted the old Linux partition  (SDA7, XT2), and installed there.   Everything ran smooth as silk.  No error messages.  However, I expected to be told my Windows installation had been found, and was not.  

On reboot, I now have a black screen with a GRUB> prompt.    No boot menu.    I know I've lost my email and data.  How do I get Ubuntu working again?

---

### Post by mörgæs on 2011-06-18
Hi, welcome to the fora.

You could try this:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by YesWeCan on 2011-06-18
We need to have a look at what is actually on your disk. Would you boot your live CD and download bootinfoscript: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
and run it and post the RESULTS.TXT contents here, inside code tags (#)?

---

### Post by CrankyOldMan on 2011-06-19
> **mörgæs said:**
> Hi, welcome to the fora.
 
You could try this:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
 
 
Thanks. I will see if it helps.

---

### Post by CrankyOldMan on 2011-06-20
> **YesWeCan said:**
> We need to have a look at what is actually on your disk. Would you boot your live CD and download bootinfoscript: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
and run it and post the RESULTS.TXT contents here, inside code tags (#)?

Thanks for answering. Please give me a bit to get back to you on this.  My system boots EXTREMELY slowly from the LIVE CD.  We're talking about 45 minutes just to get to a desktop.

In the meantime, can anyone here answer this question for me?  Do the versions of Ubuntu from 10.XX up still support PATA drives, or do they require SATA drives and AHCI support?  

I find it curious that I upgraded my laptop from 9.04 to 9.10  without problems, but the moment I tried to upgrade to 10.04 LTS, it blew up.  And my attempt to do a fresh install of 10.10 left me with a flashing cursor and no boot screen.

My desktop (which I haven't mentioned here before), also had a Win XP and Ubuntu 9.04 boot.  When I did a fresh install of Ubuntu 10.10, I got the same exact symptoms as the laptop.  (No boot menu.).  The desktop has SATA drives and AHCI support in the BIOS, but I don't run AHCI For reasons I prefer not to get into.  If I turn on the AHCI support, I get a Grub2 boot menu.   (But it hoses Windows.) 

If Ubuntu or Grub2 now expects SATA and AHCI, I don't know what I can do.  There is no SATA controller in the laptop, and enabling AHCI on the desktop is not as simple as putting drivers into Windows.  Not on this motherboard.

---

### Post by CrankyOldMan on 2011-06-21
> **mörgæs said:**
> Hi, welcome to the fora.

You could try this:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


Sorry for the delay.  Finally got around to looking at this boot repair utility.  It is not available in the version of Ubuntu  I have installed.  I did manage to download the GRUB2 utility disk and it allowed me to boot, but not fix my installation.

---

### Post by CrankyOldMan on 2011-06-21
> **YesWeCan said:**
> We need to have a look at what is actually on your disk. Would you boot your live CD and download bootinfoscript: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
and run it and post the RESULTS.TXT contents here, inside code tags (#)?

I have attached the results.txt file for you.  I  was able to boot my installation with a Super Grub2 utility disk and run the script.  Hope that didn't screw up the script.  The LiveCD takes 45 minutes to boot, and I didn't want to wait.    Why does the RESULTS.TXT file show Grub Legacy is  installed?!!!  How on earth did that happen?   Doesn't Ubuntu 10.10 install Grub2 by default?   

This is the sequence of actions I have taken with my laptop...   After the update from 9.10 to 10.04 LTS failed, I did a fresh install from an Ubuntu 10.10  CD.  I installed to SDA7 and Grub was written to the MBR.    No error messages....    I was left with a flashing cursor in place of a Grub boot menu.   And no more Windows.    

I repaired the MBR with a Windows installer disk, and now can again boot Windows.   I didn't want to screw up my Windows boot  again by reinstalling Grub to the MBR, so I decided to chainload Grub through the Windows BOOT.INI file.    To do this, I booted from the LIVE CD, reinstalled Grub to SDA7, and then tranferred the bootsector to the file "LINUX.INI" using the "DD" command.     When the BOOT.INI menu shows, and I select "Ubuntu", all I get is a  "GRUB>" prompt.    

I found the procedure to reinstall GRUB2 at [http://help.ubuntu.com/communiity/Grub2](http://help.ubuntu.com/communiity/Grub2).  I used "Method 3 (Chroot)  Everything worked ok, but I had to use "SUDO GRUB-INSTALL --FORCE  /DEV/SDA7".  

I know everyone is going to tell me to put Grub in the MBR.  But I don't want to screw up Windows again.   This has happened to me before...   I wish Grub didn't fight Windows for the MBR.   Grub may work fine 90% of the time, but I don't know why I should keep screwing up my Windows boot while I troubleshoot Grub. I have to get online to see these posts.  I don't have another computer.

---

### Post by YesWeCan on 2011-06-21
No wonder you are cranky! ;)
Have you now got your laptop booting into both Windows and Ubuntu?

1) Which version of Ubuntu are you now using, 10.10 32-bit?
2) What model is your laptop? How much RAM has it got?
3) 45 minutes to boot from CD is dysfunctional. It should take a couple of minutes.
On the menu run "check disc for defects" to make sure the CD burn was ok.
It may be struggling with drivers, most often video drivers. Sometimes selecting 'F6 - nomodeset' at the live CD menu will remedy this.
4) All versions support PATA
5) When you install Grub's MBR to a partition it whines and spits and won't do it unless you use --force. This is normal.
6) Once 10.10 is running check for available hardware drivers.
7) Yes, you are using the old Grub. Upgrade to Grub2: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
8 ) You appear to have 1GB of swap. Be aware with a laptop that goes into suspend you should have as much swap as RAM.

> I know everyone is going to tell me to put Grub in the MBR. But I don't want to screw up Windows again. This has happened to me before... I wish Grub didn't fight Windows for the MBR. Grub may work fine 90% of the time, but I don't know why I should keep screwing up my Windows boot while I troubleshoot Grub. I have to get online to see these posts. I don't have another computer.
I agree. Grub breaks the standard MBR system. There are good reasons for this (there always are!) but it can make life a pain for same drive dual boots.

The work-around you have implemented is great in principle. There is a gotcha - the Grub boot code (in MBR or PBR) locates the next file /boot/grub/core.img using an absolute sector address. When the boot code is in MBR a copy of core.img is put in the 50 sectors or so immediately afterwards and it never moves. When boot code is in the PBR it uses the /boot/grub/core.img sector address at the time of grub-install. It is possible for core.img to change location, for various reasons, and Grub is then totally trashed (this is why grub-install whines and requires --force). You would have to reinstall it using a CD which is a nuisance.

I think the best solution, if your laptop supports it, is to install Grub to the MBR of another device, like a USB or a drive that does not contain a Windows boot-loader. The Grub MBR and core.img do not need to be on the same device as /boot/grub.

---

### Post by YesWeCan on 2011-06-21
BTW if your live CD has the same Grub version as your HD Ubuntu  you don't need to use chroot to reinstall Grub.
[COLOR="Navy"]sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt --force /dev/sda7[/COLOR]

---

### Post by CrankyOldMan on 2011-06-21
Thanks!  And Sorry for the delays.  Been busy with work and home repairs.   You've give me a  lot to digest here.  Please allow me till tomorrow night to answer all of your questions.  
   
I still don't understand how I wound up with Grub Legacy.  This is Ubuntu 10.10 32 bit.  Doesn't the installer default to Grub2?  And what about that procedure I used to reinstall (Grub)?  (see the link I posted earlier)   Isn't that a proper reinstall routine for Grub2?  And if I already have Grub Legacy, do I HAVE to remove it and install Grub2?   

My laptop is a 2003 Gateway 600 YGR with 1.8Ghz Pentium and 768MB of RAM.    1MB is the largest SWAP file partition my partitioning software would create.  Is it too small?  I've already checked the installer CD for defects.  No problem found.  I will try F6 "Nomodeset tomorrow night.   You're going to have to explain this driver business to me.

--------------------------------------------------------------------------------------
Regarding the desktop.  I finally got it booted into my Ubuntu 10.10 32 bit installation tonight.  What I did was install the Grub bootsector  to a USB drive, then I  put the USB drive to the top of the boot order in the BIOS.   Wasn't that your suggestion!!!!   Guess you and I were both thinking similar.  

Can you tell me how to get the thumb drive  bootsector over to my first HD partition, so I can chainload GRUB from the Windows Boot.ini?    I didn't have any luck with the old procedure I used with Ubuntu 9.04   That is, I mounted the first partition, then tried to DD the bootsector to a file on the first partition.  

sudo mount -t vfat /dev/sda1 /mnt     
sudo dd if=/dev/sdb of=/mnt/bootsect.lnx bs=512 count=1

Is there something wrong with the above routine.?

---

### Post by YesWeCan on 2011-06-22
I think I get what you are trying to do. Grub needs more than just the MBR code, it also needs another 50 or so sectors of stuff. The relevant files in /boot/grub are boot.img and core.img. I think what you may need to do is concatenate these two into a single, new file.
cp boot.img bootsec.lnx
cat core.img >> bootsec.lnx

I am eager to know if this works. I hadn't considered this approach before.

[edit]
No that will not work! However, if the Windows bootloader works the way I think it might then it is even simpler, you just need core.img. The only reason boot.img is used is to run core.img and this is because boot.img will fit in the 446 bytes before the partition table in the MBR sector. I believe the boot.img code needs to know the absolute sector where core.img is and it won't. I'll try this out myself.

[edit2]
Neither of those work in my Windows 7 system. The BCD bootloader runs the binary but it hangs. I suspect Grub's absolute addressing is the issue. I'll look into this further because this approach is really good.

---

### Post by YesWeCan on 2011-06-23
Ok it works!
I used VirtualBox with 2 HDs:
sda Ubuntu 11.04 (Grub in MBR)
sdb Windows 7 (standard MBR)

This is what I did
1) Booted into Ubuntu on the HD
1a) Backed up my Windows disk MBR
1b) Installed Grub to the MBR of the Windows disk
1c) Restored the Windows MBR (now have Win MBR in sector 0 and core.img in sectors 1 to 50 or so).
1d) Copied /boot/grub/boot.img to C:\grub.bin
2) Booted into Windows
2a) Added a BCD entry for grub.bin
3) Rebooted into Windows, this time seeing a boot menu with choice of W7 or Grub. Choosing Grub brings up the Grub boot menu.

I initially assumed that /boot/grub/core.img is the same as that which gets installed. I tried 3 sources of core.img to put on the Windows disk:
a) The file /boot/grub/core.img. This booted to a Grub rescue prompt. I could manually boot Ubuntu from here. This core.img was not able to locate /boot/grub on its own.
b) I copied the core.img sectors at disk start from my Ubuntu disk to the Windows disk. This booted to a blank screen.
c) As I described above. Apparently, when grub-install embeds  /boot/grub/core.img it adds some disk-specific code. So you need to install to the Windows disk and then remove the unwanted Grub MBR.

*Possible alternative:*
I know that when Grub is installed to the Ubuntu / partition the /boot/grub/core.img file is modified because it is booted directly by the PBR code. So it may be you can use this modified core.img at the MBR area, provided Ubuntu is on the same disk as Windows. But this doesn't gain much aside from avoiding backing up and restoring the MBR.

I am using Windows 7. I have not tried this with XP. I must remark that adding a boot entry to BCD is a chore :-x. Perhaps a tool like EasyBCD would make this easier.

Benefits of this method:
1) The MBR is standard. No Grub conflicts. No worries about Windows fixing the MBR and breaking Grub and no worries about losing the ability to boot Windows if the Ubuntu installation is removed.
2) This avoids the reliability issues when Grub is installed to a PBR, where the location of core.img can change and break the boot process.

Drawbacks:
1) Grub core.img is still in the "no mans land" of sectors after the MBR. This is not ideal because, occasionally, some other apps use this area and can overwrite core.img.
2) If you upgrade Ubuntu version and/or change Grub version you might have to repeat the backup MBR/install Grub/restore MBR procedure. May need to copy boot.img to grub.bin again too. Not hard but a manual process.

---

### Post by CrankyOldMan on 2011-06-24
Thanks again for all your hard work, YesWeCan.  I'm sorry I couldn't respond earlier.  The house has been flooded, and that has caused quite a disruption in my life.   

You have give me quite a lot to digest.... I hope we are still talking about my laptop aren't we?  (I should have reserved my comments about my desktop for another thread.)   

What is VirtualBox? Some sort of simulator on which you Ubuntu Guru's setup and diagnose problems?  I don't know how to backup the windows MBR, or restore it. Can you tell me how?  All I have ever done is use the Windows install disk to re-create the MBR.  And how do you view sectors, or see what is installed in them?

You lost me when you talked about adding a "boot entry to BCD".  Is "BCD" the Windows 7 equivalent of XP's "boot.ini" file?   I know nothing about Windows 7.  

If I understand correctly, either method you suggested can run into problems: A. when other programs write to the affected sectors, or B. when I do an update to Ubuntu.  That's a disappointment.  My goal in building this multi-boot was to have Windows for my CAD application, and Ubuntu for safe, reliable internet browsing, email, etc.  If performing updates is going to cause problems, (as happened last week when I lost all my email and personal data), then maybe running two OS's on one drive is not for me.

Maybe I should just run Ubuntu on the laptop, and implement a two drive system on the desktop.  Will that be update safe?     I had tried to avoid that approach... It bothers me to have a second hard drive wasting power when I am only using one.

---

### Post by YesWeCan on 2011-06-24
> **CrankyOldMan said:**
> You have give me quite a lot to digest....
Sorry about that. :)

> I don't know how to backup the windows MBR, or restore it. Can you tell me how?
You just use dd like you did in post #10.
[COLOR="DarkGreen"]sudo dd if=/dev/sda bs=512 count=1 > WinMBR[/COLOR]
and to restore
[COLOR="DarkGreen"]sudo dd if=WinMBR of=/dev/sda[/COLOR]

Note: if you just want to backup the boot code and not the partition table:
[COLOR="DarkGreen"]sudo dd if=/dev/sda bs=446 count=1 > bootcode[/COLOR]

To view the code in hex and ascii formats:
[COLOR="DarkGreen"]cat WindowsMBR | hexdump -C[/COLOR]

> You lost me when you talked about adding a "boot entry to BCD".  Is "BCD" the Windows 7 equivalent of XP's "boot.ini" file?
Yes. BCD (boot configuration data) is used in Vista and W7. 

> If I understand correctly, either method you suggested can run into problems: A. when other programs write to the affected sectors, or B. when I do an update to Ubuntu.
Case A risk is small and will be the same as when Ubuntu is installed conventionally. Case B should only arise if Grub changes version, such as when you change from Ubuntu 11.10 to 11.04.

> If performing updates is going to cause problems, (as happened last week when I lost all my email and personal data), then maybe running two OS's on one drive is not for me.
I have upgraded from 9.04 to 9.10 to 10.04 to 10.10 without any issues. This is what Canonical recommends rather than "clean installs". It is not clear what caused your problems but I doubt it was the dual-install.

The main reason to have Windows and Ubuntu on separate disks is to stop booting conflicts and the inconvenience of manual restoration of either the Windows MBR or the Grub MBR.

The normal install of Ubuntu & Windows on the same disk with Grub in the MBR works fine except when:
1) Windows has an update or for any other reason checks the boot system and discovers alien code in the MBR. It will repair the MBR.
2) Ubuntu is deleted. The Grub loader relies on files inside the root partition.
3) The rare case when a Windows application writes in sectors 1 -63. Grub then needs reinstalling.

I don't think this is a a big deal for someone who knows how to restore the MBR code.

It seems to me that most people who want to dual boot start off with Windows OS and want to protect it from harm. The Grub MBR breaks the Windows boot system. So you might have expected Ubuntu to be designed to be easy and reliable to add to the Windows boot menu. Sadly no because Ubuntu has not been designed to be MBR-compliant.

> Maybe I should just run Ubuntu on the laptop, and implement a two drive system on the desktop.  Will that be update safe?     I had tried to avoid that approach... It bothers me to have a second hard drive wasting power when I am only using one.
The OS power management settings should minimize power consumed by unused disks. Separate disks avoids the booting conflicts. I don't think it makes Ubuntu any more "update safe". You mentioned VirtualBox - this creates a virtual PC within a PC and has many advantages. You could run VB in Windows and install Ubuntu to it. This allows you to have Ubuntu OS running inside a Window. Zero conflicts. It is handy to be able to run both simultaneously. The disadvantage is some loss in performance (your uP is running two OSes at once) and some minor functionality restrictions. You really need 2GB or more of RAM.

---

### Post by CrankyOldMan on 2011-06-26
Again sorry for my delay in responding.  Still busy with the house here.  You have given me superb advice, and I really appreciate it.   Guess I have some decisions to make about what direction I go, but I'm leaning towards backing up the MBR (just in case), and having a go with a GRUB boot menu.  Windows 2k is pretty old.  I doubt Microsoft is going to post any update anymore.  At least one that will screw up GRUB.  I do wish you would clarify something about backing up the MBR.   What do you suggest I back the MBR  up TO?  The Linux partition?   

---------------------------------------------------------------

---

### Post by CrankyOldMan on 2011-06-29
Still there YesWeCan?  I finally got a chance to get back to my computer and try your ideas.  (Been taking care of elderly parent and a flooded house.)

Unfortunately, I still am not able to boot my Ubuntu 10.10 installation without Super Grub 2.  

Below is what I did.  Maybe you can figure out what I did wrong.

I inserted SuperGrub in my CD player.  It found and booted my installation.  I opened a terminal window and ran the following commands:

sudo dd if=/dev/sda bs=512 count=1 > WinMBR  (save MBR to my Home folder)
cat WinMBR |hexdump -C  (displayed the MBR)
sudo mount /dev/sda7 /mnt  (mount the install partition at /mnt
sudo grub-install --root-directory=/mnt --force /dev/sda7  (install grub)
cp /boot/grub/boot.img c:\linux.new  (copy boot.img to the root of C:)
sudo dd if=WinMBR of=/dev/sda   (restore windows bootsector)

I then opened the Windows 2000 boot.ini file with the text editor and added this line:  C:\linux.new = "Ubuntu Linux"

When I rebooted and selected "Ubuntu Linux" I got a flashing cursor.  


I recall when I viewed the hexdump of the saved Windows MBR there was note about a missing file.  (I don't know how to interpret the MBR.)  I do see a Windows boot menu presenting me with a choice of Windows or Ubuntu.   And I have no problem getting into Windows.

I also recall that when I forced the Grub install, I got an error message about a missing core.img.

---

### Post by mörgæs on 2011-06-29
Are you aware that Windows 2000 is out of support and hence a major security threat?

---

### Post by YesWeCan on 2011-06-30
> **CrankyOldMan said:**
> Still there YesWeCan?
Yes, I'm still working on getting a life :P
> I also recall that when I forced the Grub install, I got an error message about a missing core.img.
This will be the problem. According to your posted RESULTS.txt the file is there. So this is a mystery. If you browse /boot/grub do you see a core.img file?

It is important that you live CD Ubuntu is the same version as on the HD.

You may need to purge and re-install the Grub application itself. [https://help.ubuntu.com/community/Grub2#Purge](https://help.ubuntu.com/community/Grub2#Purge) & Reinstall

---

### Post by CrankyOldMan on 2011-07-01
> **mörgæs said:**
> Are you aware that Windows 2000 is out of support and hence a major security threat?

Threat to whom?   Only reason I'm running it now is because my Linux installation broke when I tried to upgrade it.  (I did a fresh install but that won't boot.) The Windows 2K is just there so I can run a few old CAD programs.  I wouldn't even have the networking enabled if I had something else to get online with.

---

### Post by CrankyOldMan on 2011-07-01
> **YesWeCan said:**
> ......According to your posted RESULTS.txt the file is there. So this is a mystery. If you browse /boot/grub do you see a core.img file?

It is important that you live CD Ubuntu is the same version as on the HD.

You may need to purge and re-install the Grub application itself. [https://help.ubuntu.com/community/Grub2#Purge](https://help.ubuntu.com/community/Grub2#Purge) & Reinstall


I've have core.img.   Same Live CD as the version I just installed.  

Please explain something to me. I was looking over your original posts.  I thought you wanted me to: 

1. Backup the MBR 
2. Re-install Grub to the MBR.
3. Save the Grub bootcode to a file (bootsect.lnx)
4. Restore the Windows MBR.
5. Add bootsect.lnx to the windows boot menu (boot.ini)  

The command you asked me to install Grub with was: 

sudo grub-install --root-directory=/mnt --force /dev/sda7

Doesn't that put Grub on the Linux install partition?  Or am I misunderstanding the syntax?

---

### Post by CrankyOldMan on 2011-07-05
Anymore ideas on this boot problem? I hate to quit now.  I feel like I am so close..  I can use a SuperGrub2 CD to boot my Ubuntu installation, but it's not very fast.

Hope I didn't put anyone off, by not replying in a timely manner.   I was trying to keep up with the posts, but a series of crises at home and work have made it difficult.

---

### Post by CrankyOldMan on 2011-07-30
After months of trouble trying to get Ubuntu to boot on either my laptop or desktop, I stumbled across an application called "Boot Repair".   Five minutes of work on each machine, and I can now boot Ubuntu  (and Windows) on either of my machines.    I don't know why this application fixed my machine..  I had numerous error free manual installations of Grub to the MBR  (or the Ubuntu partition), but never got useable results. My only remaining problem (on the desktop) is that Maverick Meerkat does not locate the Windows partition.  I have posted this as a new thread.  

Thanks again to the people here.  I would like to mark this thread as "solved", but I am not sure how to do that.

---


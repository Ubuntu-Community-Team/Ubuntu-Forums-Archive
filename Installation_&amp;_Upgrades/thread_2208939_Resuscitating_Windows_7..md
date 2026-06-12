---
title: "Resuscitating Windows 7."
date: 2014-03-03
forum: Installation &amp; Upgrades
---

### Post by Vyst on 2014-03-03
Currently running: Ubuntu 12.10.

Awhile back I swiped Windows from my HP laptop in preference over Ubuntu, and recently I've found myself in need of it again. For business purposes I need to attend a webinar format which doesn't support Linux, and I've decided to get Windows back on my computer. I'm not quite sure how to do it, so I came here for help. The current situation of my computer is a little weird (and vague), but I'll give what I got:

The laptop came with Windows 7 and I originally dual booted Ubuntu onto it. Everything worked fine until one day I installed a new release (I think I went from 10.04 to 11.04) and the whole system collapsed on itself--I couldn't boot Ubuntu or Windows. My girlfriend at the time was more familiar with Ubuntu than I was and reassured me that she could get it working, and promptly got it up and running again. 

While she was doing this she asked me if I wanted Windows dual booted back onto the computer, to which I made unpleasant faces. She then asked me if I wanted the *possibility *to ever reboot Windows on the computer. I initially said no but managed to convince me to do that. My computer has been in this state since.

Now that I suddenly had the idea to re-dual boot Windows, I restarted the computer and selected "Windows 7 (loader) (on /dev/sda1)" from the initial purple selection screen and was promptly told I needed a startup/recovery disk in order to proceed. I don't have one (and I'm not sure I ever did). 

Furthermore, I've been reading around online and have heard mention that rebooting Windows has a tendency to wipe the entire drive. While I do have everything backed up on an external hard drive, this isn't really something I wish to deal with. Anyone able to give me some advice how to reboot Windows 7 without wiping my hard drive? I went to the HP website, and I found that I can order a 4-disk recovery set for about 20 bucks, which seemed strange to me that I would need 4 disks to do that, and I feel there should be a simpler solution available.

Thanks for any help!
-Dylan

---

### Post by westie457 on 2014-03-03
Could you post the output - between ```
 tags of [code]sudo fdisk -l
```
and/or a screenshot of Gparted please.

For the [code] tags copy the text in the terminal and paste into a 'go advanced' reply here then highlight the text and click on the # sympol in the top of the message window.

This will show us the current partitions of your hard drive and hopefully allow an easy solution.

Thank you.

---

### Post by Mark Phelps on 2014-03-03
IF you can still boot into Win7, then use the Backup feature to create and burn a Win7 Repair CD.  If you boot from that and run Startup Repair three times, it will restore Win7 native boot capability.

However, that can only restore booting capability; it can not be used to restore the entire OS.

So, we would need to know if the OS partitions or Recovery partition are still intact.

---

### Post by Frogs Hair on 2014-03-03
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01867418&cc=us&dlc=en&lc=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01867418&cc=us&dlc=en&lc=en)

---

### Post by Vyst on 2014-03-03
Here's what I got:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x471a47b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          411646   976560127   488074241    5  Extended
/dev/sda5         4317184   101971967    48827392   83  Linux
/dev/sda6       101974016   964315135   431170560   83  Linux
/dev/sda7       964317184   976560127     6121472   82  Linux swap / Solaris

```

---

### Post by oldfred on 2014-03-03
Please attach images not post inline. Not everyone has high speed Internet and you tie up their systems.

Windows 7 normally installs to two partitions, one a 100MB boot partition that is hidden in Windows and large system partition. 
You are only showing the boot partition.

---

### Post by westie457 on 2014-03-03
Hi Vyst,

Things are not looking to good for you. The only NTFS partition only contains the Windows boot files. There is no Windows main partition.

Suggest you order the discs from the vendor and back up all of your personal files in your Home partition while waiting for the discs to be delivered.

A clean install of Windows and Ubuntu will be quicker and less strain on your nerves than resizing your current partitions.

---

### Post by Mark Phelps on 2014-03-03
> I found that I can order a 4-disk recovery set for about 20 bucks, which seemed strange to me that I would need 4 disks to do that, and I feel there should be a simpler solution available.

Unfortunately -- not -- as others have already mentioned, there is no Windows OS partition on the PC anymore.

As to why 4 disks -- HP sometimes includes their drivers on a separate disk, and if they have two 2-disk sets, one for 32-bit and one for 64-bit, that makes up 4 disks.

Either way ... the price is dirt cheap for a fully working version of Win7.

---

### Post by Vyst on 2014-03-03
Woops! Sorry about the picture. I took it down. Does the site here host a place to upload pictures for me to link them, or do I need to use my own server space?

Too bad on the recovery situation. I'll order the disks. However, before I do that, I want to make sure they're the correct disks. When I look on the HP website, I find that there is no ordering option for the 32-bit Windows, just the 64-bit. I don't remember what I had before, but as I'm running 32-bit Ubuntu now, I'm guessing I was running 32-bit Windows before. Mark Phelps mentioned that this may be because the 4-Disk set is contains both versions, but I want to make sure before I order them. This is the recovery kit:

[https://h10025.www1.hp.com/ewfrf/wc/mediaOrder?softwareitem=629287-001&cc=us&dlc=en&lc=en&os=4063&product=4317149&sw_lang=](https://h10025.www1.hp.com/ewfrf/wc/mediaOrder?softwareitem=629287-001&cc=us&dlc=en&lc=en&os=4063&product=4317149&sw_lang=)

Second, I want to ensure that I'm doing backups properly before I wipe anything off the computer. I'm currently using Simple Backup to backup to an external hard drive. First, is this program good enough for what I need right now, and second, if it is, what directories do I need to include in the backup to make sure I got everything?

Thanks for everyone's help!
-Dylan

---

### Post by oldfred on 2014-03-03
You can attach screenshots & very long output (with size limits) using the paperclip icon in advanced editor.

 Guide to Forum features:
[http://ubuntuforums.org/showthread.php?t=2054969](http://ubuntuforums.org/showthread.php?t=2054969)
[http://ubuntuforums.org/showthread.php?t=1006656](http://ubuntuforums.org/showthread.php?t=1006656)
Forum do & don't
[http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580)

Most newer systems should be running 64 bit, with both Windows & Ubuntu. Any system with 2GB or more RAM will be faster and 64bit will work even with less (with Ubuntu). 

It looks like your serial number will define what versions you get.

---

### Post by Vyst on 2014-03-03
Thanks for the links!

> **oldfred said:**
> Most newer systems should be running 64 bit, with both Windows & Ubuntu. Any system with 2GB or more RAM will be faster and 64bit will work even with less (with Ubuntu).

Great. I'm going to order it, then.

---

### Post by Bucky Ball on 2014-03-03
Did it just yesterday. Working on a friend's laptop. 12.04 LTS installed first. Left a 40Gb NTFS partition as the FIRST partition on the first drive (sda). 

There was one DVD labeled 'Windows 64bit'. Installed it to the 40Gb partition (just choose it when prompted), after install booted from a Boot Repair 64bit USB stick, ran the 'Recommended Repair', reboot, done. Works faultlessly.

No, didn't need more than the one disk, or the one partition for that matter.

---

### Post by Vyst on 2014-03-06
Alright, the repair DVDs arrived today. Can anyone point me to a useful and concise article that will take me over the steps of starting my computer over and dual-booting it? Bucky Ball just suggested I install Ubuntu first, but I'm not sure how to go about doing it that way (simply haven't done it before).

Second, I want to make double-extra mega sure I do my backups properly. Using the default settings for Simple Backup (that is, the default settings associated with directory selection), will this be enough to bring my Ubuntu settings back around to the way they were after doing the repair?

Thanks again for everyone's help!
-Dylan

---

### Post by Tom 6 on 2014-03-07
Hi :)  
How about installing Win7 onto a Virtual Machine inside Ubuntu?  That way you can have loads more interaction between apps in Win7 and apps in Ubuntu.  

The dual-boot method is better if you already have Windows installed and are a little scared of removing it but since that has already been done a virtual machine might be better.  

The other problem with the Virtual Machine approach is that you are then splitting the available resources, such as Ram and Cpu, between the 2 OSes.  Win7 must need over 1Gb Ram and Ubuntu needs at least 1Gb too.  To see how much Ram Ubuntu can see try this on a command-line
free -m

Errr, you can always get a command-line by doing 
Ctrl Alt t
but if that seems scary there are plenty of other ways.  Hmm, when forums and places suggest doing things on the command-line you can always check the voracity of their suggestion by using a "--help" or "-h" tag after the initial command.  For example 

free --help 

should show a quick-guide cheat-sheet on how to use the command "free".  It's reassuring to find that it's not going to do something mad to your machine! I've never yet seeen any seriously bad advice on any non-Windows forum but i still check anyway.  


Before i tried it i thought Virtual Machines sounded waaay out of my league but they turn out to be remarkably simple.  You can make it more complicated later on if you feel the urge but it's mostly kinda point&click.  I tend to go with VirtualBox from Oracle as it's in the repos already.  Just open the "Ubuntu Software Centre" or "Synaptic" or something and use the search feature to find a "virtual machine".  

Regards from 
Tom :)

---

### Post by Tom 6 on 2014-03-07
Hi :)  
Errr, if you do just go for a normal install of Win7 then early on it should allow you to choose which partitions to install too.  Windows wont be able to see the Ubuntu ones nor the Swap so it will only show the Ntfs one.  If that IS 40Gb or over then i would just install straight onto that.  

Win7 can be squeezed onto smaller but it's unhappy and slow.  You ideally want at least 20% empty space on a partition running Windows.  

Once you have installed Windows it overwrites your MBR so that you can only boot into Windows.  DO NOT PANIC.  Your Ubuntu is still there.  You just need to find how to fix "Grub2".  I tend to do a google search for 
"Community Documentation" Grub2
and then follow the instructions somewhere near the end.  

Grub2 re-overwrites the MBR but as a boot-loader it's far superior to the Windows one and almost always DOES spot all the different OSes.  So after fixing that you do get a choice of booting into Windows or Ubuntu.  
Regards from 
Tom :)

---

### Post by Vyst on 2014-03-07
Hi Tom,

Thanks for the input. Unfortunately for the VirtualBoxes, I already have one and I still wasn't able to access the webinar that prompted this whole thread. Well, I was able to get the video, but I couldn't get the audio to work. As this happens periodically with me with different programs, I figured I might as well put Windows back on the machine so I can have a fail-safe when I come across something in the future that isn't Linux-compatible. Thus I'm going to go ahead with the dual boot.

But same question as before, the one that makes me the most nervous, is a full backup with the Simple Backup program enough to restore my settings after I use the repair disks? My harddrive has become quite a labyrinth of directories, and it would really throw me for a loop if they reorganized themselves. Additionally, I have most of my stuff in an encrypted folder. That shouldn't affect anything, right?

Thanks again,
-Dylan

---

### Post by oldfred on 2014-03-07
Are you backing up encrypted data? That may be the most important part as there is no recovery of that data from any drive or partition corruption issue.

I do not use encryption and prefer to backup just my data as I can reinstall easily.

Then the issue is partitions and drives. Windows will only install to the primary NTFS formatted partition with the boot flag and it puts its boot partition and boot loader in the MBR of the drive set as boot in BIOS. If not the same drive as main install it can overwrite Linux partition on the BIOS boot drive corrupting them.

---

### Post by Vyst on 2014-03-11
Help!

So I successfully backed everything up, stuffed in the Repair Disk, reformatted my computer back to Windows 7, downloaded Ubuntu 13.10 (ubuntu-13.10-desktop-amd64.iso), mounted it, and attempted to restart and begin the Ubuntu installation process. I get the standard purple Ubuntu loading-up screen then suddenly I get a screen-wide terminal with the following:

```
BusyBox v1.20.2(Ubuntu 1:1.20.0-8.1ubuntu1) built-in shell (ash)

(initramfs) help
```

There was some more text in between saying I could type "help" for a list of built-in commands. I'm not sure what's going on here. Is 13.10 possibly incompatible with my computer? I've had to deal with Windows for a day and I'm already starting to tear my hair out. :/ Can anyone give me an idea what's happening?

---

### Post by Vyst on 2014-03-11
Just to add, I would be really interested in being able to have access to someone over the phone. If you're knowledgeable enough to help me out and wouldn't mind sharing your phone number, I would greatly appreciate it. Thanks!

---

### Post by Bucky Ball on 2014-03-11
If you want live support please try the [IRC channel]("http://ubuntuforums.org/showthread.php?t=69068").

We do not encourage the exchange of personal information via posts on threads in the public domain (and such information will be removed). If people are happy to exchange personal information, do it via a PM, but you do so at your own risk.

---

### Post by Tom 6 on 2014-03-13
Hi :)  
I'm glad to hear you got Windows working!  However, i am curious if you have solved the problem with the LiveCd yet?  

I suspect it's something that re-downloading and creating a new DVD might solve, or even better would be to make a bootable Usb-stick because it's faster.  Sadly Ubuntu has finally, inevitably, become tooo large to fit on a Cd so we need touse Dvds or usb-sticks or something.  
Regards from 
Tom :)

---


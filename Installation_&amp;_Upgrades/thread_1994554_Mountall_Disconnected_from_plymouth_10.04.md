---
title: "Mountall: Disconnected from plymouth 10.04"
date: 2012-06-02
forum: Installation &amp; Upgrades
---

### Post by wilmac73 on 2012-06-02
> **jimbo99 said:**
> Several messages fly by, the screen flickers a few times, then I'm presented with this the message mountall: disconnected from plymouth.
 
I've followed various threads that have similar errors. I've attempted the solutions in those threads, to no avail.
 
After the above message is displayed I can't type at the keyboard to log in. I've managed that machine in the past from SSH so I tried to SSH into it. That allows me access to the box and it's how I tried those other thread's attempted solutions.
 
 Originally Posted by **dino99** [[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9948374#post9948374") 
[I]sudo apt-get update
sudo apt-get install -f

sudo dpkg --configure -a
sudo dpkg-reconfigure jockey
sudo dpkg-reconfigure plymouth
sudo dpkg-reconfigure gdm[/I]
Originally Posted by **dino99** [[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9948374#post9948374") 
[I]sudo apt-get update
sudo apt-get install -f

sudo dpkg --configure -a
sudo dpkg-reconfigure jockey
sudo dpkg-reconfigure plymouth
sudo dpkg-reconfigure gdm[/I]
Originally Posted by **dino99** [[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9948374#post9948374") 
[I]sudo apt-get update
sudo apt-get install -f

sudo dpkg --configure -a
sudo dpkg-reconfigure jockey
sudo dpkg-reconfigure plymouth
sudo dpkg-reconfigure gdm[/I]

 
Those were tried with no solution to the problem.
 
I reinstalled the video drivers which had caused similar errors on several of my other Ubuntu boxes in the past.
 
Of all the releases of Ubuntu, so far, this one has been the worst when it comes to upgrades.
 
Suggestions?
Hello everyone. I am nwew to the forum and I cannot log into my system after upgrading to Ubuntu 10.04. I get Errormsg which says Mountall: Disconnected from plymouth. I tried all the above options to no avail. All I get is The Ubuntu 10.04 Purple screen and it says hit S to Skip, M for Manual repair or w for wait. "None of those options work when I hit any of those buttons absolutely NOTHING Happens. I get no log in screen what so ever. I am not super savvy but I was going to try geeksquad for help because I really need my files but I saw so many horror stories on the forum regarding using them. I really need serious help restoring my computer. Please someone help me.  I wanted to speak with someone but cannot find assistance by phone. I have been wihtout my comuter for a week aleeady and it is killing me.

---

### Post by oldos2er on 2012-06-02
Post moved to its own thread.

---

### Post by wilmac73 on 2012-06-03
> **oldos2er said:**
> Post moved to its own thread.
 
Thank you, Oldos2er. I didn't know I needed to start a new thread.

---

### Post by oldos2er on 2012-06-03
> **wilmac73 said:**
> Thank you, Oldos2er. I didn't know I needed to start a new thread.

From the Posting Guidelines ([http://ubuntuforums.org/index.php?page=policy):](http://ubuntuforums.org/index.php?page=policy):) 

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

Hope that helps.

---

### Post by wilmac73 on 2012-06-04
> **oldos2er said:**
> From the Posting Guidelines ([http://ubuntuforums.org/index.php?page=policy):](http://ubuntuforums.org/index.php?page=policy):) 
 
"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."
 
Hope that helps.
 
 
I was perusing the forums rules and had a question. How long does it normally take before someone will help you with a technical issue. Also if your thread is not answered in a reasonable time frame can you bump it so it isn't lost in cyserspace with no response?
 
The reason I ask is because I ahven't received a response in almost 2 days already.
 
Thanks again for your help.

---

### Post by oldfred on 2012-06-04
If you hold shift key from BIOS until menu appears, do you get grub menu?

If seems like grub is loading but you have to add some parameter to get it to boot to terminal or gui.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by wilmac73 on 2012-06-04
> **oldfred said:**
> If you hold shift key from BIOS until menu appears, do you get grub menu?
 
If seems like grub is loading but you have to add some parameter to get it to boot to terminal or gui.
 
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
 
Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
 
 
Thank you Oldfred. How do you access the Bios? I think I have accessed Grub before but I don't know what to do once Iam in there. I have Grub up now. It says Minimal BASH -like line editing is supported. For the first word, TAB lists possible command completion.  Anywhere else TAB lists possible device or file completions. ESC at any time exits.

---

### Post by oldfred on 2012-06-04
If you have grub> , it has boot issues.

Download this into the Ubuntu liveCD or download the full liveCD it has. Run the BootInfo and post link.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by wilmac73 on 2012-06-05
> **oldfred said:**
> If you have grub> , it has boot issues.
 
Download this into the Ubuntu liveCD or download the full liveCD it has. Run the BootInfo and post link.
 
Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.
 
I burned the boot repair to a disc. How do I run the program from the disc? It doesn't give me that option when I restart the computer.

---

### Post by wilmac73 on 2012-06-05
> **oldfred said:**
> If you hold shift key from BIOS until menu appears, do you get grub menu?
 
If seems like grub is loading but you have to add some parameter to get it to boot to terminal or gui.
 
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
 
Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
 
I have to hit C to enter commands in grub. I don't know what you mean when you say hit shift from the bios. I started having this problem when I upgraded to ubuntu 10.04 I could no longer get to a log in screen.
 
When I do get the Purple Ubuntu 10.04 screen it says "The disk drive for / is not yet ready or present." Continue to wait; or press S to skip mounting or M for manual recovery. None of those options work what so ever. The screen just sits idle.

---

### Post by Dave_L on 2012-06-05
> **wilmac73 said:**
> How do you access the BIOS?

> I burned the boot repair to a disc. How do I run the program from the disc? It doesn't give me that option when I restart the computer.

When the computer boots, there should be a brief message displayed about how to enter the BIOS. Typically it requires pressing a key such as Delete or F1. You may only have a couple of seconds, so you have to be quick.

In the BIOS, there should be a setting for "boot order" or similar, that allows you to specify that the computer boot from an external disk.

---

### Post by wilmac73 on 2012-06-05
> **Dave_L said:**
> When the computer boots, there should be a brief message displayed about how to enter the BIOS. Typically it requires pressing a key such as Delete or F1. You may only have a couple of seconds, so you have to be quick.
 
In the BIOS, there should be a setting for "boot order" or similar, that allows you to specify that the computer boot from an external disk.
 
I got to the BIOS menu. IT says that the option to select USB or CD Rom drive is not available. Try f1 to retry or f2 for set up utility. FYI I do have a dual operating system w/ windows on my computer but i do not use it and haven't for a couple of years. How would I set up utility so I can log in using the disc?

---

### Post by oldfred on 2012-06-05
Do you have a one time boot key (f12 on my system)? The BIOS screen usually shows one key to get into BIOS and another to choose device to boot just this one time. You have to hit that key while BIOS screen is still showing.

Did you burn ISO to CD or just copy it? It has to be burned or extracted and copied including bootability, not copied as one large ISO to the CD.

---

### Post by wilmac73 on 2012-06-05
> **oldfred said:**
> Do you have a one time boot key (f12 on my system)? The BIOS screen usually shows one key to get into BIOS and another to choose device to boot just this one time. You have to hit that key while BIOS screen is still showing.
 
Did you burn ISO to CD or just copy it? It has to be burned or extracted and copied including bootability, not copied as one large ISO to the CD.
 
I do not have a one time boot key. f12 gives me a list of option:
 
Onboard SATA hard drive
Onboard USB CD Rom drive
System set up
Hard Drive Diagnostics
Boot Utility Partition
 
The other option ios f2 for system set up
 
I did burn ISO to a CD and I copied fiole to USB disk as well.

---

### Post by oldfred on 2012-06-05
This is your one time boot key:

> Onboard SATA hard drive
Onboard USB CD Rom drive
System set up
Hard Drive Diagnostics
Boot Utility Partition

If CD is a SATA device it should be under the OnBoard SATA hard drive? My flash drives also appear under hard drives also.
Some times you still have to turn on boot in BIOS to let you boot other devices.

---

### Post by wilmac73 on 2012-06-05
> **oldfred said:**
> This is your one time boot key:
 
 
 
If CD is a SATA device it should be under the OnBoard SATA hard drive? My flash drives also appear under hard drives also.
Some times you still have to turn on boot in BIOS to let you boot other devices.
 
The SATA hard drive is on but when I select it I'm taken to windows log in screen. I check system set up and SATA drive is on in BIOS but I still can't log in using that drive.

---

### Post by oldfred on 2012-06-05
If you just copied files to USB flash that does not copy the MBR or allow it to be bootable. You need to follow the install instructions on the Ubuntu site or use this:

Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

How to create a bootable Ubuntu USB Flash Drive - unetbootin
[http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/](http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/)

---

### Post by wilmac73 on 2012-06-05
> **oldfred said:**
> If you just copied files to USB flash that does not copy the MBR or allow it to be bootable. You need to follow the install instructions on the Ubuntu site or use this:
 
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
 
How to create a bootable Ubuntu USB Flash Drive - unetbootin
[http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/](http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/)
I followed the instructions from this link you provided:
How to create a bootable Ubuntu USB Flash Drive - unetbootin
[http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/](http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/)[/
 
I have the Unetbootin files on USB.. I changed my BIOS settings to boot from USB drive and made sure I set the system parameters to boot from the USB drive as instructed but the system still says device is not available. I double checked the BIOS to make sure the USB drive was selected as the boot option & that the USB drive is on in the BIOS but that didn't work either. It says device not available. When Iselect SATA harddrive ittakes me through the menu options to select ubuntu or windows ans  of course when I select Ubuntu it says Mountall Disconnected from Plymouth. My system has a separate option for USB drives but It still won't boot from the USB.

---

### Post by wilmac73 on 2012-06-06
> **wilmac73 said:**
> I followed the instructions from this link you provided:
How to create a bootable Ubuntu USB Flash Drive - unetbootin
[http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/](http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/)[/
 
I have the Unetbootin files on USB.. I changed my BIOS settings to boot from USB drive and made sure I set the system parameters to boot from the USB drive as instructed but the system still says device is not available. I double checked the BIOS to make sure the USB drive was selected as the boot option & that the USB drive is on in the BIOS but that didn't work either. It says device not available. When Iselect SATA harddrive ittakes me through the menu options to select ubuntu or windows ans of course when I select Ubuntu it says Mountall Disconnected from Plymouth. My system has a separate option for USB drives but It still won't boot from the USB.
 
Bump. I haven't heard anything in a day.

---

### Post by oldfred on 2012-06-06
I know nothing about plymouth. 

My usb flash drive boots from the hard drive menu not from any of the many USB selections my motherboard offers. It took me a while to realize my USB flash did not boot from USB. Only coincidently did I find it was seen as another hard drive device.

---

### Post by wilmac73 on 2012-06-06
> **oldfred said:**
> I know nothing about plymouth. 
 
My usb flash drive boots from the hard drive menu not from any of the many USB selections my motherboard offers. It took me a while to realize my USB flash did not boot from USB. Only coincidently did I find it was seen as another hard drive device.
 
Plymouth has something to do with the upgrade to ubuntu 10.04 that I did when I lost the ability to log in  to my computer.. Many others have had the same issue I had since upgrading and found fixes. Alot of what is in this thread I tried to no avaiol. Can you look at this threadf and see if  you can get a better understanding of what I am dealing wiht. It is hard to explain since I am not super techy. Use link below to get to the thread in ?tion. I will try the other options in the boot menu and see if any work
 
[http://ubuntuforums.org/showthread.php?t=1602767](http://ubuntuforums.org/showthread.php?t=1602767)

---

### Post by wilmac73 on 2012-06-06
I was able to get in to my computer a couple of times and I tried these attempts to fix it which didn't work and now I cannot get in at all anymore.
 

 
[I]sudo apt-get update
sudo apt-get install -f

sudo dpkg --configure -a
sudo dpkg-reconfigure jockey
sudo dpkg-reconfigure plymouth
sudo dpkg-reconfigure gdm[/I]

---

### Post by oldfred on 2012-06-06
Can you get a grub menu? If only one install you may have to hold shift key from BIOS until menu appears.

Have you tried recovery mode from grub menu (if you can get it)?

---

### Post by CharlesA on 2012-06-07
*pokes thread*

I ran into a similar message when I had to add "nobootwait" to one of my devices in fstab. That was a server install, not a desktop install tho.

The machine booted fine even with the error.

> When I do get the Purple Ubuntu 10.04 screen it says "The disk drive for / is not yet ready or present." Continue to wait; or press S to skip mounting or M for manual recovery. None of those options work what so ever. The screen just sits idle.

As for this error, have you run fsck on that device?

What does /etc/fstab look like?

Boot from a livecd and run a fsck on the device hosting / and see if it returns any errors.

EDIT: Run the boot info script so we can get some more info how everything is set up:

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript
```

---

### Post by wilmac73 on 2012-06-07
> **oldfred said:**
> Can you get a grub menu? If only one install you may have to hold shift key from BIOS until menu appears.
 
Have you tried recovery mode from grub menu (if you can get it)?
 
I have tried recovery mode and I get the same error msg stating mountal disconnected from plymouth and other a long list of script with error msgs comes up and then nothing happens. I can add command lines and edit in grub as well but I don't know what to do of if that will help.

---

### Post by wilmac73 on 2012-06-07
> **CharlesA said:**
> *pokes thread*
 
I ran into a similar message when I had to add "nobootwait" to one of my devices in fstab. That was a server install, not a desktop install tho.
 
The machine booted fine even with the error.
 
 
 
As for this error, have you run fsck on that device?
 
What does **/etc/fstab** look like?
 
Boot from a livecd and run a fsck on the device hosting / and see if it returns any errors.
 
EDIT: Run the boot info script so we can get some more info how everything is set up:
 
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript
```
 
I am not tech saavy so I do not know what the bold is above, though I have seen it discussed in other threads I looked at in relation to my problem. I have been trying for days to run a live cd from a usb but that isn't working. If you look through the thread you can see my earlier responses in regards to the drive not being available. How do I run boot info script?

---

### Post by oldfred on 2012-06-07
I think we really need to get a liveCD or USB working as you should be able to boot a repair CD in case of future problems anyway. 

To see fstab or run bootinfoscript, you need the working liveCD. But you can add boot parameters at the grub menu by pressing e and adding the parameters.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place

From liveCD you also need the nomodeset, but also other parameters.

---

### Post by wilmac73 on 2012-06-07
> **oldfred said:**
> I think we really need to get a liveCD or USB working as you should be able to boot a repair CD in case of future problems anyway. 
 
To see fstab or run bootinfoscript, you need the working liveCD. But you can add boot parameters at the grub menu by pressing e and adding the parameters.
 
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
 
From liveCD you also need the nomodeset, but also other parameters.
 
I tried adding the NOMODESET command in the grub menu and when I selected control X to boot it gave me an error which said:
 
 /init: conf/conf.dsplash: line 1: Update initramfs: not found
Mountall: Disconnected from Plymouth
init: plymouth main process (249) killed by SEGV signal
 
Itried it again right before posting this and I got  back to the purple ubuntu screen I referenced earlier.
init: plymouth-splash main process (332) terminarted with status 2

---

### Post by oldfred on 2012-06-07
I forgot that you have 10.04, I think nomodeset is for newer kernels and not required with 10.04. You still may need other boot parameters.

Can you boot 12.04 liveCD or even download Puppy, Knoppix or one of the very small systems just to see if system still boots?

What system is this? How much RAM,. video card etc.

---

### Post by wilmac73 on 2012-06-07
> **oldfred said:**
> I think we really need to get a liveCD or USB working as you should be able to boot a repair CD in case of future problems anyway. 
 
To see fstab or run bootinfoscript, you need the working liveCD. But you can add boot parameters at the grub menu by pressing e and adding the parameters.
 
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
 
From liveCD you also need the nomodeset, but also other parameters.
 
I just tried the NOMODESET command from grub and got a different error which said:
 
Mountall{ sawpon /host/ubuntu/disks/swap.disk {291} killed by SEGV signal
Problem activating swap:/host/ubuntu/disks/swap.disk
error occurred while mounting.
press s to skip or m for manual recovery. 
None of those buttons do anything

---

### Post by wilmac73 on 2012-06-07
> **oldfred said:**
> I forgot that you have 10.04, I think nomodeset is for newer kernels and not required with 10.04. You still may need other boot parameters.
 
Can you boot 12.04 liveCD or even download Puppy, Knoppix or one of the very small systems just to see if system still boots?
 
What system is this? How much RAM,. video card etc.
I am using a dell dimension e310 using a dual OS windows xp and ubuntu. I no longer use windows at all. 
I don't know how to access RAM and video card info.
 
Where can I download a 12.04 live cb from?

---

### Post by CharlesA on 2012-06-07
That's a Wubi install?

Download the ISO here:
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

---

### Post by oldfred on 2012-06-07
Are you trying to run full Ubuntu not Lubuntu?

[http://reviews.cnet.com/desktops/dell-dimension-e310-pentium/4507-3118_7-31594474.html](http://reviews.cnet.com/desktops/dell-dimension-e310-pentium/4507-3118_7-31594474.html)

Says only 256K memory default which is not much nowadays. Full Ubuntu needs 512MB. Your system may have more and says it can hold up to 2GB.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by wilmac73 on 2012-06-08
> **oldfred said:**
> Are you trying to run full Ubuntu not Lubuntu?
 
[http://reviews.cnet.com/desktops/dell-dimension-e310-pentium/4507-3118_7-31594474.html](http://reviews.cnet.com/desktops/dell-dimension-e310-pentium/4507-3118_7-31594474.html)
 
Says only 256K memory default which is not much nowadays. Full Ubuntu needs 512MB. Your system may have more and says it can hold up to 2GB.
 
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
 
Mine says 2gb of space 
memory speed 533mhz
 
I am running Ubuntu. I never heard of Lubuntu or Kubuntu or the other versions until I perused this site and others looking for a fix for my dilemma.

---

### Post by wilmac73 on 2012-06-08
> **CharlesA said:**
> That's a Wubi install?
 
Download the ISO here:
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)
 
I am downloading the ISO now. 
 
What is a wubi installation?

---

### Post by wilmac73 on 2012-06-08
> **CharlesA said:**
> That's a Wubi install?
 
Download the ISO here:
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)
 
I burned the ISO to disc and when I tried boot from the disc I got the same error message. Mountall:disconnected from plymouth
 
I tried selecting CD ROM as boot option and it says device not available.

---

### Post by wilmac73 on 2012-06-08
> **oldfred said:**
> Are you trying to run full Ubuntu not Lubuntu?
 
[http://reviews.cnet.com/desktops/dell-dimension-e310-pentium/4507-3118_7-31594474.html](http://reviews.cnet.com/desktops/dell-dimension-e310-pentium/4507-3118_7-31594474.html)
 
Says only 256K memory default which is not much nowadays. Full Ubuntu needs 512MB. Your system may have more and says it can hold up to 2GB.
 
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
 
I finally got a working live cd for ubuntu 12.04. I am waiting for the system to finish logging in from cd now. The other one I made didn't work but the new one i tested did work amd I am loading it now.It seems to be loaind very slowly. I have passed the purple ubuntu screen and I see the mulit-colored screen before the desktop should start loading but it seems to be taking a while to load up.

---

### Post by wilmac73 on 2012-06-08
I got in using the live cd. It says Try ubuntu without installing
install ubuntu
check disc for defects
test memory
boot from first hard disk
 
Which one do I select?

---

### Post by CharlesA on 2012-06-08
Select try ubuntu without installing

---

### Post by wilmac73 on 2012-06-08
> **CharlesA said:**
> Select try ubuntu without installing
 
I did select that option and nothing happened. It is sitting on the piurple ubuntu screen and doing nothing. I am going to restart and try again.

---

### Post by wilmac73 on 2012-06-08
> **CharlesA said:**
> Select try ubuntu without installing
 
I tried again & nothing happened. It just sits on the purple ubuntu screen and does nothing. it has 5 red dots under the ubuntu logo then the screen goes black.

---

### Post by CharlesA on 2012-06-08
> **wilmac73 said:**
> I tried again & nothing happened. It just sits on the purple ubuntu screen and does nothing. it has 5 red dots under the ubuntu logo then the screen goes black.
Hmmm. How long did you let it sit? I've had older boxes take upwards of 10 minutes to boot from a livecd.

---

### Post by wilmac73 on 2012-06-08
> **CharlesA said:**
> Hmmm. How long did you let it sit? I've had older boxes take upwards of 10 minutes to boot from a livecd. 
 
Only a few mins. Should I let it sit on the black screen to see what happens? The  disc seems to stop spinning in the drive and it sits seemingly idle.

---

### Post by CharlesA on 2012-06-08
> **wilmac73 said:**
> Only a few mins. Should I let it sit on the black screen to see what happens? The  disc seems to stop spinning in the drive and it sits seemingly idle.
Give it 10 minutes and see what happens.

If it still has a black screen try hitting:

Ctrl + Alt + F1

---

### Post by wilmac73 on 2012-06-08
> **CharlesA said:**
> Give it 10 minutes and see what happens.
 
If it still has a black screen try hitting:
 
Ctrl + Alt + F1
 
It sat idle for over 10mins. When I hit ctrl+alt+FI g to a lack screen that says
 
[EMAIL="Ubuntu@ubuntu:~$"]Ubuntu@ubuntu:~$[/EMAIL]

---

### Post by CharlesA on 2012-06-08
Ok.

Type these commands into that terminal:
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript
```

---

### Post by wilmac73 on 2012-06-08
> **CharlesA said:**
> Ok.
 
Type these commands into that terminal:
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript
```
 
I entered each line and got a bunch of script going up on my screen and weird errors and a documentation: https//help.ubuntu.com/
 
comes up periodically. it is still flashing script as I type this every few seconds.

---

### Post by wilmac73 on 2012-06-08
> **wilmac73 said:**
> I entered each line and got a bunch of script going up on my screen and weird errors and a documentation: https//help.ubuntu.com/
 
comes up periodically. it is still flashing script as I type this every few seconds.
 it just stopped flashing script and now says:
 
Ubuntu@ubuntu:~$

---

### Post by CharlesA on 2012-06-08
Ok try hitting ctrl + alt + f7 now and see what happens.

---

### Post by wilmac73 on 2012-06-08
> **CharlesA said:**
> Ok try hitting ctrl + alt + f7 now and see what happens.
 
I just did it., the screen turned purple and has the ubuntu logo on it with 5 red dots under it.

---

### Post by wilmac73 on 2012-06-08
> **CharlesA said:**
> Ok try hitting ctrl + alt + f7 now and see what happens.
 
The disc drive stopped and it is still sitting idle with a purple screen after 15 mins.

---

### Post by CharlesA on 2012-06-08
Something is wrong with that machine, but I do not know what.

Sounds like it might be video related, but I am not sure.

---

### Post by wilmac73 on 2012-06-08
> **CharlesA said:**
> Something is wrong with that machine, but I do not know what.
 
Sounds like it might be video related, but I am not sure.
 
I wish I knew too. It is driving me crazy and I need the files I have on it.

---

### Post by CharlesA on 2012-06-08
It might be easier to just take the hard drive out and put it in another machine to get your files.

---

### Post by wilmac73 on 2012-06-08
> **CharlesA said:**
> It might be easier to just take the hard drive out and put it in another machine to get your files.
 
How would I go about doing that? 
 
Is there anything else i can try?

---

### Post by CharlesA on 2012-06-08
> **wilmac73 said:**
> How would I go about doing that? 
 
Is there anything else i can try?
Depends on the type of computer. I didn't see any specs listed.

---

### Post by wilmac73 on 2012-06-08
> **wilmac73 said:**
> Mine says 2gb of space 
memory speed 533mhz
 
I am running Ubuntu. I never heard of Lubuntu or Kubuntu or the other versions until I perused this site and others looking for a fix for my dilemma.
 
I am using a dell dimension e310 using a dual OS [windows]("http://ubuntuforums.org/showthread.php?t=1994554&page=4#") xp and ubuntu. I no longer use windows at all.

---

### Post by CharlesA on 2012-06-08
See here:
[http://support.dell.com/support/edocs/systems/dim3100/en/sm/parts0.htm#wp1043338](http://support.dell.com/support/edocs/systems/dim3100/en/sm/parts0.htm#wp1043338)

Just take the hard drive out and put it in another machine and copy the files off it.

---

### Post by wilmac73 on 2012-06-09
> **CharlesA said:**
> See here:
[http://support.dell.com/support/edocs/systems/dim3100/en/sm/parts0.htm#wp1043338](http://support.dell.com/support/edocs/systems/dim3100/en/sm/parts0.htm#wp1043338)
 
Just take the hard drive out and put it in another machine and copy the files off it.
 
 
I will look into that option and see if I can do that. 
 
Are there any fixes in this thread that can help me?
 
[http://ubuntuforums.org/showthread.php?t=1602767](http://ubuntuforums.org/showthread.php?t=1602767)
 
I see some info there that applies to my problem but I do not know how do the commands from the launch pad. Below is one fix offered from the link I provided and it speaks to the fact that my mountall error hits before the plymouth splash screen. This is exactly what is happening to me. Can you walk me through trynig this luanch pad fix to see if it works.
 
Originally Posted by **garvinrick4** [[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10018202#post10018202") 
[I]Do you all get a plymouth splash screen or does mountall hit before graphic drivers and fail to get your splash screen? If so make drivers hit before / mounts.
This is a fix from launchpad. Will force graphic drivers to hit before mountall package.
I have used for that purpose. If you feel problem is different and you get a splash then
just save for reference. This is only to get plymouth to start and nothing else.

Code:
sudo -i
Code:
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splashupdate-initramfs -u
[/I]

---

### Post by oldfred on 2012-06-09
Those commands require you to at least get to a command line. You may be able to do something from liveCD, but I still would suggest boot parameters both liveCD or when trying to boot.

Back in Post #6. It may not be nomodeset, but other parameters. Often have to experiment, if there is no posted info on your exact model. Usually someone has used the same computer somewhere and posts what option(s) work.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by wilmac73 on 2012-06-09
> **oldfred said:**
> Those commands require you to at least get to a command line. You may be able to do something from liveCD, but I still would suggest boot parameters both liveCD or when trying to boot.
 
Back in Post #6. It may not be nomodeset, but other parameters. Often have to experiment, if there is no posted info on your exact model. Usually someone has used the same computer somewhere and posts what option(s) work.
 
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
 
 
thank you Oldfred. I will try your suggestion once I get home and then respond to you at that time. Around 6pm. I am @ work right now. I truly appreciate all of your help as well as CharlesA.

---

### Post by wilmac73 on 2012-06-09
> **oldfred said:**
> Those commands require you to at least get to a command line. You may be able to do something from liveCD, but I still would suggest boot parameters both liveCD or when trying to boot.
 
Back in Post #6. It may not be nomodeset, but other parameters. Often have to experiment, if there is no posted info on your exact model. Usually someone has used the same computer somewhere and posts what option(s) work.
 
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
 
I have a log in screen up after changing the boot option and adding nomodeset on the command line. When I tried each boot option individually nothing worked. When I tried adding the command and selecting an option it worked. Now I tried to log in but it says my log in info it says authentication failure & I dk why? I am the admin and I used both my regular log in info and the admin as my user name and still I get the same problem. What log in info should I use.? None of myh log in details are working

---

### Post by oldfred on 2012-06-09
Your user id and password are the one's you used to install system, unless you are using the liveCD. Then it is just hit enter. The default user on the liveCD is ubuntu but you do not normally have to type that in.

---

### Post by wilmac73 on 2012-06-09
> **oldfred said:**
> Your user id and password are the one's you used to install system, unless you are using the liveCD. Then it is just hit enter. The default user on the liveCD is ubuntu but you do not normally have to type that in.
 
 
TY I am usingf the live cd and I am in now. What do I do next?

---

### Post by oldfred on 2012-06-09
Frankly I have lost track.

I think we wanted you to download this into liveCD and run the Boot-Info. That should give a link to the report showing your entire system.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by CharlesA on 2012-06-09
> **oldfred said:**
> Frankly I have lost track.

I think we wanted you to download this into liveCD and run the Boot-Info. That should give a link to the report showing your entire system.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.
Yep.

The commands to run are here:

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript
```

---

### Post by wilmac73 on 2012-06-09
> **oldfred said:**
> Frankly I have lost track.
 
I think we wanted you to download this into liveCD and run the Boot-Info. That should give a link to the report showing your entire system.
 
Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.
 
I tried to run the boot repair ande realized I accidentally had the original live cd for ubuntu 10.04 not the new live cd for 12.04. I am now trying to see what combination of kernel options gets me to log into ubuntu 12.04 so I can run the boot repair. burned boot repair in to a usb drive but still could not accees it under the old 10.04 live cd i was logged into, forcing me now to try to do the same with the 12.04 cd.

---

### Post by wilmac73 on 2012-06-11
> **CharlesA said:**
> Yep.
 
The commands to run are here:
 
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript
```
 
I have tried every boot option to try and boot from the live cd for 12.04 and I can only get the the screen with the different boot options. I have tried them all and even found a longer list of options I tried using the link you gave me but none of them work. I only get to the purple ubuntu screen with 4 or 5 red dots then it turns black after a few minutes. 
 
At one point I got a message from my computer that said try booting the irqpoll option which I tried under different boot options from nomodeset to nodmraid then edd=on and all the others and cannot get to a log in screen. I know the disc is good because I can log into it on my son's lap top which is what I am using now since my desktop is not giving me the ability to log in. 
 
When I it the ctrl+alt+f2 I get a black screen which says
 
welcome to ubuntu 12,04 lts (gnu/linux 3.2.0-23 Generic-pae i686) 
documentation: https//help.ubuntu.com
ubuntu@ubuntu: ~$ 
 
and when i hit ctrl+alt+f7 I get a blank black screen.

---

### Post by oldfred on 2012-06-11
Somewhere between 10.04 & 12.04 they integrated video into the kernel and it often needs some help. I have nVidia and have had to use nomodeset on every CD or USB to install and on first boot until I get nVidia driver installed. Some others also will also boot with nomodeset.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd & immdiately press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'.

---

### Post by wilmac73 on 2012-06-11
> **oldfred said:**
> Somewhere between 10.04 & 12.04 they integrated video into the kernel and it often needs some help. I have nVidia and have had to use nomodeset on every CD or USB to install and on first boot until I get nVidia driver installed. Some others also will also boot with nomodeset.
 
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
**To install Ubuntu, boot from the cd & immdiately press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.**
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'.
 
I tried selecting the nomodeset option in the list (the bold)and then I actually typed it in at the end of the command line and neither worked.

---

### Post by oldfred on 2012-06-11
If you boot to this you have booted to the command line with the liveCD.

ubuntu@ubuntu: ~$ 

So the issues are all with video and video display.

---

### Post by wilmac73 on 2012-06-11
> **oldfred said:**
> If you boot to this you have booted to the command line with the liveCD.
 
ubuntu@ubuntu: ~$ 
 
So the issues are all with video and video display.
 
Ok. Is there anything I can do in regards to this issue?

---

### Post by oldfred on 2012-06-11
I am grasping at straws.

AT Ubuntu@ubuntu copy & paste this, does it suggest a video driver?:

jockey-text -l

---

### Post by wilmac73 on 2012-06-12
> **oldfred said:**
> I am grasping at straws.
 
AT Ubuntu@ubuntu copy & paste this, does it suggest a video driver?:
 
jockey-text -l
 
I am at work right now., but when I get home this evening I will try this and see what happens. I will be home at 6pm today.

---

### Post by wilmac73 on 2012-06-12
> **oldfred said:**
> I am grasping at straws.
 
AT Ubuntu@ubuntu copy & paste this, does it suggest a video driver?:
 
jockey-text -l
 
When I entered jockey-text -l, I didn't get a drive suggestion it says says segmentation fault (core dumped)

---

### Post by oldfred on 2012-06-12
Your Dell supposedly has this which is an early version of Intels video chip.
Intel GMA 900 Dynamic Video Memory Technology 3.0  

And normally the Intel chips work. But some require this:
i915.modeset=1 

I am out of ideas.

---

### Post by CharlesA on 2012-06-13
> **oldfred said:**
> I am out of ideas.

Same. It would probably be easier to just pop the hard drive out and put it in a working machine in order to get the files off the drive.

---

### Post by digitalramble on 2013-03-14
> **oldos2er said:**
> Post moved to its own thread.

Hm.  Where would I find this?  I don't see a link?

---

### Post by CharlesA on 2013-03-14
> **digitalramble said:**
> Hm.  Where would I find this?  I don't see a link?

It means they moved the OP's from another thread, so there is no link because if there was one, it expired a long time ago.

The OP is from around 9 months ago.

---


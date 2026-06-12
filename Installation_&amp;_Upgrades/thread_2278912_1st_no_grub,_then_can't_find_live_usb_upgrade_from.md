---
title: "1st no grub, then can't find live usb: upgrade from 14.04 to 15.04"
date: 2015-05-19
forum: Installation &amp; Upgrades
---

### Post by Malik_Rumi on 2015-05-19
I had a series of issues with my wifi, so it was recommended that I try a 15.04 live usb and if that worked, just upgrade and forget about it. So I got the iso and put it on the same usb drive that I had 14.04 on. When I burned, it erased all the 14.04 stuff. But when I restarted, grub was nowhere to be found and I went straight into Windows 8.1. I then told Windows to reboot to the usb (there were 3 other icons for ubuntu, but clicking on them just restarted windows).  The reboot brought up a black and white grub screen (my 14.04 one had been purple) and then I booted into 15.04 on the live usb. I was able to navigate around, and most importantly, got online with my wifi, so it seemed to ok. Then I went to work. That was this morning. When I came back this afternoon, 15.04 was offering me 4 options. It looked like suspend, restart, off, and something else, but I'm not sure because as soon as I moved my mouse the whole thing went away and the machine rebooted into Windows. 

So I told Windows to reboot into the usb again. This time there were 5 ubuntu icons on the windows reboot gui. I don't know what that's about or how relevant it is.

But instead of 15.04, I got white letters on a black screen with this message:

> 
4.420514 ACPI PCC probe failed
4.576206 usb usb1-port2: couldn't allocate usb-device starting version 219
4.688205 xhci_hcd 0000:00:14.0: ERROR: unexpected setup address command co
4.892390 xhci_hcd 0000:00:14.0: setup error: setup address command for slot2
5.096536 usb 2-2: device not accepting address2, error -22
6.551142 sd 3:0:0:0: [sdb] no caching mode page found
6.551194 sd 3:0:0:0: [sdb] assuming drive cache: write through

BusyBox v1.22.1 built in shell (ash)
Enter HELP for commands
(initramfs unable to find a medium containing a live file system


NOTE: Entering help was impossible. The screen accepted zero keyboard inputs.

Maybe my drive has failed, but it was fine this morning and no one has been home to mess with it. What are my options here? Thanks.

p.s. : fwiw, I can see, open, and read text files like license and readme from the live usb from windows, so the usb drive is not dead.

---

### Post by Vladlenin5000 on 2015-05-19
The main point from your other [thread]("http://ubuntuforums.org/showthread.php?t=2278807") (where perhaps you should have follow up instead of a new one) is that you must boot the USB in UEFI mode.

---

### Post by Malik_Rumi on 2015-05-19
I'm sorry, I may have confused you unintentionally.
1. I just offered my two cents in the thread you linked to. That was not my issue.
2. The thread I referred to that brought me here was from the wifi and networking sub-forum.
3. The issue I am writing about here all started this morning (5/20/15). 

As an update, clearly the usb drive is ok. I have been googling around and learned that there is a bug in Startup Creator when going from 14.04 to 15.04. [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) and scroll down to 'known issues'.

There is also a fix for this, but it has not been approved for merging into the distro and apparently is unavailable [https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801).

It seems that somehow creating the live usb for 15.04 got rid of my grub2, although that makes zero sense to me. After rebooting again, I was able to get the 15.04 live usb to open, and I ran Boot Repair, which reported success. But despite that report, the machine still boots directly into Windows. My pastebin is [http://paste.ubuntu.com/11235052](http://paste.ubuntu.com/11235052). I have to try changing the boot order as suggested by Boot Repair if windows still comes up, but I got the email notice of your response so I came here to respond first. I'm wondering if just installing 15.04 to my hard drive would fix these issues or be a source of new ones?

---

### Post by Malik_Rumi on 2015-05-21
I am hoping someone who knows what they are talking about will come along and help me here. 

The update is that after following the instructions on the wiki about using win32 disk manager, I came up with a usb that windows reported only had 2kb. I finally found out how to fix all that, and then burned the iso for 15.04. Grub comes up, but it has different options that I have never seen before, including system setup, efi/ubuntu/mokmanager.efi, windows boot uefi.loader and windows uefi bootmgfw.efi. Notably what is missing here is 'try ubuntu' or anything that will install 15.04.

I decided to try 'advanced' ubuntu options, and was confronted with no less than 8 versions, 3.16.0 -37 thru -30, one each along with it's recovery mode. Going with -37 puts me into the 14.04 I had originally, but the usb stick is labelled at 15.04 amd64. Opening that up in the file viewer there are a number of folders, including one labelled ubuntu that has a curved arrow on it. Clicking that opens into an identical folder, and clicking on that ubuntu does the same thing, recursively down 4 levels before I stopped. 

So, I still have no effective grub that automatically offers me what OS to boot into as I had before the 1st time I tried the 15.04 live cd. Nevertheless, I can get into ubuntu thru telling windows to boot to the usb. I have two ubuntus, 15.04 on the usb and 14.04 on the hd. But nowhere have I seen anything like 'try ubuntu' or 'install ubuntu' or anything like that that I had when I did the live cd for 14.04. 

I mentioned in an earlier post how I got boot repair and it said it worked but I still booted into windows. Tonight when I put boot repair into the terminal I got 'command not found'.

I would appreciate some help and suggestions. Thank you.

---

### Post by Vladlenin5000 on 2015-05-21
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If yours is different than the process outlined in the link above it's either a problem with USB flash drive (most likely) -or- you aren't booting from it at all -or- you aren't booting in UEFI mode (and you should because your factory installed Windows 8.1 definitely is in such mode).

---


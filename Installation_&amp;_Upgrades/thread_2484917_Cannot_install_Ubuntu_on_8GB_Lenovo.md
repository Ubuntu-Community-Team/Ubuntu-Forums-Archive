---
title: "Cannot install Ubuntu on 8GB Lenovo"
date: 2023-03-14
forum: Installation &amp; Upgrades
---

### Post by bhubunt on 2023-03-14
Hi All,
I have a Lenovo Thinkpad x230, 8GB ram, that currently has *no* OS on it. It used to have Ubuntu 20.04 on it in the past, but for some reason, I am now unable to install a new Ubuntu OS.

Just now I tried to install Ubuntu 18.04 but it won't work. I was able to log into Ubuntu 18.04 through a live session. But when I clicked on the button saying "Install Ubuntu," I got the following message: 

"You need at least 8.6 GB disk space to install Ubuntu. This computer has only 7.8 GB."

Why won't Ubuntu install now, when the computer had Ubuntu on it in the past, with the same ram?

On the following Ubuntu installation guide it says you only need a minimum of 2.5 GB: [https://ubuntu.com/server/docs/installation](https://ubuntu.com/server/docs/installation)

So what's going on?

Prior to trying this installation, I did a Lenovo diagnostics check and the laptop passed all checks, so there is no problem with the laptop.

Thanks for helping me out.


P.S. I know Bionic Beaver is an older version, but I wanted to upgrade to 20.04 LTS after the installation. As it is, something is blocking me from installing Ubuntu 18.04, even though I have enough ram....

---

### Post by MAFoElffen on 2023-03-14
It says the hard disk is full, not that the RAM is not enough... 

If you do not care what is on the old hard disk, do this... Download 22.04.2... Create a LiveCD USB. Boot from the USB Install media. Select "Try".

In the upper right, select "Activities". Type in GParted. Select the Icon to start it.

It should show you all the patitions on your internal hard disk and the USB drive. Ensure you are on the internal hard disk. Right-click on each partition, and select Delete. After you have done that for all the partitons on that drive, select the green check mark to apply those operations. Close Gparted.

Double click on the install Ubuntu Icon on the Desktop. After the Language and Keyboard panels, select "Erase and install to full disk" option. Finsh the installation, and reboot when asked.

Tell us how it goes. Don't be afraid to ask any questions...

18.04 only has a few weeks before it is End-Of-Support. 20.04 has about 2 years left of support. There is no reason for you not to start out fresh with Current Ubuntu 22.04.2, which has 4 years of support left.

---

### Post by yancek on 2023-03-14
>  You need at least 8.6 GB disk space to install Ubuntu. This computer has only 7.8 GB."

As pointed out above, the message says the disk has a limited amount of space available.  There is no reference to RAM (memory) so you appear to be confusing the two.  The message indicates that there is only 7.8GB of free space available so you need to create more as suggested in the post above.

---

### Post by ActionParsnip on 2023-03-14
Ubuntu 18.04 has less than 4 weeks support. Use Jammy (Ubuntu 22.04)
[https://releases.ubuntu.com/jammy/ubuntu-22.04.2-desktop-amd64.iso.torrent](https://releases.ubuntu.com/jammy/ubuntu-22.04.2-desktop-amd64.iso.torrent)

---

### Post by bhubunt on 2023-03-14
Hi MafoElffen and Yancek,
Yes, you are right: my Thinkpad has 8 GB ram memory and 128 GB on the SSD.

It's bizarre there are less than 8GB left on the SSD, for, as far as I know, I have no data on the laptop and there is no working operating system.

Question for MafoElffen: so GParted is preinstalled on Ubuntu [COLOR=#000000] 22.04.2? Is it also included with 20.04? 

[/COLOR]So you are recommending that I delete all partions and proceed with no partitions, then? 

You say: [COLOR=#000000]Ensure you are on the internal hard disk.

[/COLOR]How do I ensure I am on the internal hard disk? Can you post screenshots of how this works?

---

### Post by tea for one on 2023-03-14
> **bhubunt said:**
> so GParted is preinstalled on Ubuntu 22.04.2? Is it also included with 20.04? 
Gparted is included in the live session of both 22.04 and 20.04.
It is removed after you install Ubuntu to a SSD/HDD.
> How do I ensure I am on the internal hard disk? 
Boot into a live session, open a terminal and enter:-
```
sudo parted -l
```
Please post the output in code tags and, I'm sure, help will be forthcoming.

---

### Post by MAFoElffen on 2023-03-14
+1 on the command posted in last post... or
```

lsblk -o name,size,type,fstype,mountpoints | grep -v 'loop\|snap'

```

---

### Post by bhubunt on 2023-03-14
Ok.

So to make sure I do everything right:

1 I first boot into a live session
2 Then I type Gparted into Activities
3 And then I type [COLOR=#000000][FONT=&amp]sudo parted -l into the terminal?
and what is step 4? Is step 4 that I then just start deleting partitions on Gparted?

Additional question: is there anything that can go wrong with the hard drive this way? [/FONT][/COLOR]

---

### Post by ajgreeny on 2023-03-14
Also bear in mind that the link you showed in your first post was about the server edition of Ubuntu, ie one with no GUI desktop; is that what you want or are you expecting a full desktop version of Ubuntu after installation?

---

### Post by MAFoElffen on 2023-03-14
> **bhubunt said:**
> n the following Ubuntu installation guide it says you only need a minimum of 2.5 GB: [https://ubuntu.com/server/docs/installation](https://ubuntu.com/server/docs/installation)

I missed that you mentioned "server in your post...

At your last post... No. You combined steps...

First, before doing anything else, please answer if you are trying to install Server Edition or Desktop Edition...

---

### Post by bhubunt on 2023-03-15
I am just trying to install the desktop edition. 

Right now I'm posting during a live session on the Lenovo Thinkpad, using Ubuntu 20.04 on a USB Stick, a version of Ubuntu with which I am familiar.

However, when I opened GParted, only my USB showed up, see screenshot 1, and almost all the buttons were dead buttons, that is, would not work. 

The second screenshot shows the disk analysis. Once again, only the usb stick is visible and something called a 2.2 GB loop device. What does that refer to?

The third and fourth screenshots document part of the installation process. For some reason, the usual installation steps are missing. There is no option to "erase disk and install Ubuntu," nor is there an option to encrypt and so on (as explained in the Ubuntu tutorial [https://ubuntu.com/tutorials/install-ubuntu-desktop#6-drive-management](https://ubuntu.com/tutorials/install-ubuntu-desktop#6-drive-management)). I have used this very same installation stick several times and so I am puzzled why these features now are missing.

As you will see in thumbnail 4, once again, as with GParted, almost all the fields are dead fields, nothing to fill in and only the usb stick is listed. 


Here are the logs on pastebin:

this one is the security log of this live session: [https://pastebin.com/h8e06NK9](https://pastebin.com/h8e06NK9)

and this one the longer log:
[https://pastebin.com/xqaZg4Lm](https://pastebin.com/xqaZg4Lm)

Finally, this is the long journal txt: [https://pastebin.com/K7saBSbq](https://pastebin.com/K7saBSbq)

Your thoughts are appreciated.

---

### Post by bhubunt on 2023-03-15
Deleted post because log posted on pastebin, see previous message.

---

### Post by MAFoElffen on 2023-03-15
Go back to your last post and Edit > Advanced Options > Select the output of your "Errors" and then select the "#: Icon to wrap the output wit CODE Tags. Please, if you post raw output or commands, they should be wrapped in CODE Tags, either than way or like this: 
[noparse]```
Commands and Raw Ouput here.
```[/noparse]

There is no sense in trying to install until the USB Media can see you internal disk.

Please go into your BIOS Settings and see if the BIOS sees you internal disk. [https://support.lenovo.com/us/en/troubleshoot/lpt000487](https://support.lenovo.com/us/en/troubleshoot/lpt000487)

If so, then go to Hard disk options, then SATA Mode... And ensure it says "AHCI", instead of RAID.

If it was on something different and you changed it... Then save the changes, reboot, and retry. Tells us how that goes.

Is there a reason why you are 'set' on installing 20.04 (almost 3 years old now) instead of 22.04.2? You have skirted around questions about that.

---

### Post by bhubunt on 2023-03-15
Hi,
Thanks for the feedback. No, the bios does not recognize the hard drive. How can I fix this?

About 20.04: I am not against 22.04.2 but I am familiar with Ubuntu 20.04. Right now, there are so many technical issues I have to deal with that I feel more comfortable working with 20.04.

I removed the raw post, as it is also posted here: 
[https://pastebin.com/h8e06NK9](https://pastebin.com/h8e06NK9)

I will insert code in future postings.


BTW, what is the 2.2 GB loop device?

---

### Post by tea for one on 2023-03-15
> **bhubunt said:**
> No, the bios does not recognize the hard drive. How can I fix this?
That does not bode well, it could be hardware failure.
You can try a few things:-

[LIST]
[*]Open up the PC and check that the drive is securely connected.
[*]Try another internal drive (if you have one).
[*]Boot into a live Ubuntu/Xubuntu session and attach another USB stick to see if it is recognised.
[*]Reset the UEFI firmware to default.
[/LIST]

---

### Post by bhubunt on 2023-03-15
Hi,
Just a quick reply: the laptop did recognize the USB stick; I actually could open the USB stick and look at its files. The only thing the laptop would not do with the stick is allow me to copy new files onto the stick -- there was some kind of block, about which I posted in another thread. 


> **tea for one said:**
> That does not bode well, it could be hardware failure.
You can try a few things:-

[LIST]
[*]Open up the PC and check that the drive is securely connected.
[*]Try another internal drive (if you have one).
[*]Boot into a live Ubuntu/Xubuntu session and attach another USB stick to see if it is recognised.
[*]Reset the UEFI firmware to default.
[/LIST]


---

### Post by slickymaster on 2023-03-15
*Thread moved to **Installation & Upgrades**.*

---

### Post by tea for one on 2023-03-15
> **bhubunt said:**
> The only thing the laptop would not do with the stick is allow me to copy new files onto the stick -- there was some kind of block, about which I posted in another thread.
Have a look at the settings in your UEFI firmware and check the following (if they exist on your PC):-

Disable Secure Boot
Disable Fast Boot 
Disable Legacy mode 
Enable Legacy USB Support 
Change SATA mode to AHCI where the default is RAID or Intel RST 
Disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology) or FTPM (Firmware Trusted Platform Module)
Disable Optane memory and storage
Disable Device Guard (some Lenovo devices)
Disable OS Optimised Defaults (some Lenovo devices)

---

### Post by bhubunt on 2023-03-15
> **slickymaster said:**
> *Thread moved to **Installation & Upgrades**.*


There are still unresolved issues in the thread, but thanks for putting my question in the right thread.

---

### Post by bhubunt on 2023-03-15
> **tea for one said:**
> Have a look at the settings in your UEFI firmware and check the following (if they exist on your PC):-

Disable Secure Boot
Disable Fast Boot 
Disable Legacy mode 
Enable Legacy USB Support 
Change SATA mode to AHCI where the default is RAID or Intel RST 
Disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology) or FTPM (Firmware Trusted Platform Module)
Disable Optane memory and storage
Disable Device Guard (some Lenovo devices)
Disable OS Optimised Defaults (some Lenovo devices)

I recognize most of them, but will check again. Can you also tell me what the correct setting should be or does your post already include the right settings?

---

### Post by tea for one on 2023-03-15
Unfortunately, there is no such thing as "right settings".
UEFI firmware is controlled by the vendor and I'm simply trying to point out where an obstacle may be present.

Trial and error is often a tortuous process but sometimes, it can lead to a successful outcome.

---

### Post by bhubunt on 2023-03-15
> **tea for one said:**
> Unfortunately, there is no such thing as "right settings".
UEFI firmware is controlled by the vendor and I'm simply trying to point out where an obstacle may be present.

Trial and error is often a tortuous process but sometimes, it can lead to a successful outcome.

Hi,
I made the requested changes but still cannot install Ubuntu 20.04.

I am in a live session right now on the same computer and once again got a similar system log report, indicating that there is an issue located in Partman.... 

Below is a screenshot of the section of the log that deals with the problems in Partman. And here is a section of the actual log dealing with Partman [https://pastebin.com/M6W0jmcV](https://pastebin.com/M6W0jmcV)

Also have a look at the log for the previous live session which similarly had major problems with Partman and partitions.  (I will add code in future postings)  [https://pastebin.com/h8e06NK9](https://pastebin.com/h8e06NK9) 

I am no good at understanding logs but perhaps someone else could give it a try.

Looking forward to an analysis or reactions.

---

### Post by MAFoElffen on 2023-03-15
From what I see... And don't see... If the Original Poster (OP) has done what was asked (no storage found in BIOS, resetting BIOS to defaults, checking the physical connections, checking settings in BIOS)... Then I would suspect that is has a bad hard disk and it needs to be replaced.

EDIT: This is based on the OP saying that the drive was once recognized, and has Ubuntu 20.04 installed on it (already). So the drive was previously recognized by the BIOS. So it isn't a firmware problem, where it was never recognized. And I doubt he has changed his BIOS settings since then... It sounds like it was sitting there, and when he went back to it, it didn't boot again... (because the drive has failed to come up.)

It could be a PSU problem, where that specific plug is not providing power to the drive... But the possibilities of things are dwindling.

---

### Post by bhubunt on 2023-03-16
> **MAFoElffen said:**
> From what I see... And don't see... If the Original Poster (OP) has done what was asked (no storage found in BIOS, resetting BIOS to defaults, checking the physical connections, checking settings in BIOS)... Then I would suspect that is has a bad hard disk and it needs to be replaced.

EDIT: This is based on the OP saying that the drive was once recognized, and has Ubuntu 20.04 installed on it (already). So the drive was previously recognized by the BIOS. So it isn't a firmware problem, where it was never recognized. And I doubt he has changed his BIOS settings since then... It sounds like it was sitting there, and when he went back to it, it didn't boot again... (because the drive has failed to come up.)

It could be a PSU problem, where that specific plug is not providing power to the drive... But the possibilities of things are dwindling.


Hi MaFoElffen,
Thanks for your valued reflections.

I would like to point to a few unsolved questions: how come there is less than 8 GB on the 128 GB internal drive of this Thinkpad x230? When I use a live Ubuntu *18.04* installation stick, it can read the exact GB -- 7. 8 GB -- from the internal drive, meaning that this drive is legible to the installation program as to its exact storage capacity. See the thumbnail below 

I should also add that I *never* had any data in the amount of 120 GB on the drive to begin with. So how come 120 GB is supposedly used up on the internal drive, as the Ubuntu 18.04 installation indicated? Could it instead be the case that partitions were applied to this drive, so that the space available for actual installation is less than 8 GB? 

And a related question: is there any way in which I can look at what is on the internal drive through the terminal? If so, could you post the commands or link showing the steps?

Here is the log of this 18.04 Ubuntu live session on Pastebin: [https://pastebin.com/2dKhsAGe](https://pastebin.com/2dKhsAGe)

---

### Post by MAFoElffen on 2023-03-16
The only storage recognised by your system:
```

07:51:01 kernel: sd 6:0:0:0: [sda] Attached SCSI removable disk
07:51:01 kernel:  sda: sda1 sda2
07:51:01 kernel: sd 6:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
07:51:01 kernel: scsi 6:0:0:0: Direct-Access     [COLOR=#ff0000]Kingston DataTraveler 3.0[/COLOR] PMAP PQ: 0 ANSI: 6

```
The kernel saw two partitions on your USB drive. /dev/sda1, in your screen shot in post #11, it said that that partition was about 27.87 GB. In the same post, another screenshot ID'ed the drive as being 31 GB...  Kingston sells that drive in a 32GB model... So I am thinking the installer tried to calculate what may have been left as unallocated on the only drive it saw, the USB drive. (I cannot explain that the math there doesn't add up right. But it is close.) 

That is not the internal 128 GB drive, that your system does not see anywhere in the logs. And you confirmed that your BIOS no longer sees.

Note: I am just sincerely trying to help you. I volunteer my time and experience here to help Users in need.. I admit that I have only done computer support professionally for about 35 years now. I do not appreciate what sounds like you want to argue with what I am suggesting and what I see. I can only go off the information you have posted. I do not "have to" help you. But maybe we are both just reading between the lines and those feelings are not really there. I hope not.

---

### Post by tea for one on 2023-03-16
> **bhubunt said:**
> is there any way in which I can look at what is on the internal drive through the terminal? If so, could you post the commands or link showing the steps?
Yes, there is, but just to check if the internal disk is available:-

Boot into a live Ubuntu session
Open Disks (gnome-disk-utility)
Is your internal disk visible? 

Alternatively, from a live session, please supply the info requested in either post 6 or 7.

---

### Post by MAFoElffen on 2023-03-16
Observation: Post #11 has a screen shot (the second attachment) showing his system storage as seen through the gnome-disk-utility... 

+1 on the commands from Posts #6 & 7... He just needs to post the output 'within' Code tags. (I think he temporarily posted the output in post #12, but originally without code tags. He then deleted it when asked if he could edit his post to add code tags around the output... Which wasn't what was intended. The output he had displayed was somehow corrupted / didn't display correctly.)

@bhubant -- To add Code tags, it is simple if you just type it like this:
[noparse]```

<<Paste your output here>>

```[/noparse]
I added special formatting to display that without processing the formatting on that. If you do it like that, it will wrap your output with the proper tags. Or you could follow the instructions from post #13.

---

### Post by tea for one on 2023-03-16
> **MAFoElffen said:**
> Observation: Post #11 has a screen shot (the second attachment) showing his system storage as seen through the gnome-disk-utility... 
Observation skills second to none - I missed that screenshot.

Looks increasingly like a dead (or disconnected) internal drive as mentioned in post 23.

---

### Post by bhubunt on 2023-03-16
> **tea for one said:**
> Yes, there is, but just to check if the internal disk is available:-

Boot into a live Ubuntu session
Open Disks (gnome-disk-utility)
Is your internal disk visible? 

Alternatively, from a live session, please supply the info requested in either post 6 or 7.

Could you please provide the bash version of this for the terminaL I would like to use a non-graphical means of checking the disk. 

I already posted screenshots in post 11. Only the installation USB and a 2.2 GB loop (about which I still would like to know more...) were visible. 

Sorry about the missing tag files for code...I now know how it works and will clean up posts later...

---

### Post by bhubunt on 2023-03-16
> **MAFoElffen said:**
> The only storage recognised by your system:
```

07:51:01 kernel: sd 6:0:0:0: [sda] Attached SCSI removable disk
07:51:01 kernel:  sda: sda1 sda2
07:51:01 kernel: sd 6:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
07:51:01 kernel: scsi 6:0:0:0: Direct-Access     [COLOR=#ff0000]Kingston DataTraveler 3.0[/COLOR] PMAP PQ: 0 ANSI: 6

```
The kernel saw two partitions on your USB drive. /dev/sda1, in your screen shot in post #11, it said that that partition was about 27.87 GB. In the same post, another screenshot ID'ed the drive as being 31 GB...  Kingston sells that drive in a 32GB model... So I am thinking the installer tried to calculate what may have been left as unallocated on the only drive it saw, the USB drive. (I cannot explain that the math there doesn't add up right. But it is close.) 

That is not the internal 128 GB drive, that your system does not see anywhere in the logs. And you confirmed that your BIOS no longer sees.

Note: I am just sincerely trying to help you. I volunteer my time and experience here to help Users in need.. I admit that I have only done computer support professionally for about 35 years now. I do not appreciate what sounds like you want to argue with what I am suggesting and what I see. I can only go off the information you have posted. I do not "have to" help you. But maybe we are both just reading between the lines and those feelings are not really there. I hope not.


Hi there,
No, I am not trying to argue with you at all! I am just trying to understand, hence the questions I ask, since unlike you I am not a coder. I have already learned a lot from you and the other helpful forum members.

---

### Post by tea for one on 2023-03-16
> **bhubunt said:**
> Could you please provide the bash version of this for the terminaL I would like to use a non-graphical means of checking the disk. 
From a live Ubuntu session, open a terminal and enter:-
```
sudo parted -l
```
Please supply the terminal output (it has been requested more than once).

If the disk is healthy, then the device will be recognised (e.g sda or nvme0n1 or mmcblk0).

---

### Post by MAFoElffen on 2023-03-16
@tea for one --

I asked him in this thread: [https://ubuntuforums.org/showthread.php?t=2484943&p=14135067#post14135067](https://ubuntuforums.org/showthread.php?t=2484943&p=14135067#post14135067) ...if he could run the [UbuntuForums 'system-info' script]("https://ubuntuforums.org/showthread.php?t=2484943"), and to post the URL of where it uploads to, so we can see what is going on, and what all his 3 current threads are concerning. That report should give us more details about his system, and how Linux sees it.
 
That information should answer a lot of these questions.

---

### Post by bhubunt on 2023-03-16
> **MAFoElffen said:**
> 
The kernel saw two partitions on your USB drive. /dev/sda1, in your screen shot in post #11, it said that that partition was about 27.87 GB. In the same post, another screenshot ID'ed the drive as being 31 GB...  Kingston sells that drive in a 32GB model... So I am thinking the installer tried to calculate what may have been left as unallocated on the only drive it saw, the USB drive. (I cannot explain that the math there doesn't add up right. But it is close.) 

.

Hi,

To check your suggestion that the 18.04 Ubuntu installer was actually calculating the available space on the Datatraveler USB stick as being only 7.8 GB, I just inspected the stick. However, as the thumbnail below shows, there are 29.7 GB free on that stick.

Perhaps then the installer was reading the available space on the internal drive, after all? I still wonder if a partitioning of the drive occurred, such that only a small section of the drive is left -- too little for an Ubuntu installation. I will try Tea for One s suggestion to look via the terminal. 

I will also get to your other questions later tonight.

---

### Post by bhubunt on 2023-03-16
> **tea for one said:**
> From a live Ubuntu session, open a terminal and enter:-
```
sudo parted -l
```
Please supply the terminal output (it has been requested more than once).

If the disk is healthy, then the device will be recognised (e.g sda or nvme0n1 or mmcblk0).

Hi, 

I just entered ```
sudo parted -l
```

And this is what came up

```
 Warning: The driver descriptor says the physical block size is 2048 bytes, but
Linux says it is 512 bytes.
Ignore/Cancel?  
```

This seems to indicate that the problem with my internal drive is indeed related to partitioning, as someone on the Superuser forum had this happen to them after they changed the partitioning --

[https://superuser.com/questions/1130966/the-driver-descriptor-says-the-physical-block-size-is-2048-bytes-but-linux-says](https://superuser.com/questions/1130966/the-driver-descriptor-says-the-physical-block-size-is-2048-bytes-but-linux-says)

Not sure who could have done the partitioning on my drive, though...

I wonder whether I will be able to fix this problem based on the solutions offered on the superuser forum? Which solution do you recommend?

---

### Post by tea for one on 2023-03-16
Can you just Ignore the warning and see if there is any terminal output?
You may have to type [COLOR="#0000FF"]Ignore[/COLOR] - I can't quite remember because I haven't seen this warning recently.

---

### Post by MAFoElffen on 2023-03-16
No. You are misinterpreting what that is showing you. I will let 'tea for one' explain to you what the second attachment really says... What is used, and not used within the mounted, first partition, /dev/sda1... The installer tries to calculate on unallocated space of storage... Space that is outside of a partition, that is left on a storage device. I think he may have different wording that you may understand. Remember that your computer currently does not see your internal 128 GB disk, so it cannot calculate from what it does not see.

Please do the commands and run the script so we can see that report. To see if that is any different.

---

### Post by bhubunt on 2023-03-16
> **tea for one said:**
> Can you just Ignore the warning and see if there is any terminal output?
You may have to type [COLOR=#0000FF]Ignore[/COLOR] - I can't quite remember because I haven't seen this warning recently.

Sure. Super grateful for all your help MAFoElffen and Tea for One.

Here is the answer 

```
 arning: The driver descriptor says the physical block size is 2048 bytes, but
Linux says it is 512 bytes.
Ignore/Cancel? ignore                                                     
Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sda: 31.0GB
Sector size (logical/physical): 2048B/512B
Partition Table: mac
Disk Flags: 

Number  Start   End     Size    File system  Name   Flags
 1      2048B   6143B   4096B                Apple
 2      6150kB  8673kB  2523kB               EFI


```

---

### Post by tea for one on 2023-03-16
This thread has a life of its own................

The only device visible to [COLOR="#0000FF"]parted[/COLOR] is your 31/32GB Kingston DataTraveler 3.0. (an external device)
Why is it formatted with [COLOR="#FF0000"]mac[/COLOR] partition table?
There is no sign of your internal drive (yet?)

I've never seen a mac partition table on a USB device with an Ubuntu iso.
Therefore, I do not completely trust the results already provided.

Please create a USB with gpt partition table together with an Ubuntu iso.

Boot into a live session and again run:-
```
sudo parted -l
```

Please post the terminal output.

---

### Post by bhubunt on 2023-03-16
Here is the output 

```
 Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sda: 31.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  31.0GB  31.0GB  fat32        Microsoft Basic Data  msftdata

``` 

Only the USB stick is recognized...

---

### Post by tea for one on 2023-03-16
Thank you.
Internal disk is invisible therefore it is either disconnected or damaged?

Can you replace it?

---

### Post by MAFoElffen on 2023-03-16
This is as deep a terminal command as I will give you
```

grep . /proc/diskstats

```
Example output
```

mafoelffen@Mikes-B460M:~$ grep . /proc/diskstats | grep -v 'loop'
 259        0 nvme0n1 471363 991 35565189 96120 8383457 1 197391655 181874 0 786840  506151 589441 11 132325632 170925 210473 57231
 259       1 nvme0n1p1 1483 991 56286 139 58 1 95 11 0 372 158 28 0 959096 6 0 0
 259       2 nvme0n1p2 227 0 25192 34 0 0 0 0 0 192 34 0 0 0 0 0 0
 259       3 nvme0n1p3 2952 0 637576 452 1161 0 22992 20 0 556 486 36 0 3800 13 0 0
 259       4 nvme0n1p4 466265 0 34831015 95454 8382238 0 197368568 181841 0 785768 448202 589377 11 131362736 170905 0 0
   8      16 sdb 512 0 39456 134 5 0 0 31 0 220 196 0 0 0 0 5 31
   8      17 sdb1 107 0 5800 32 5 0 0 31 0 112 63 0 0 0 0 0 0
   8      18 sdb2 140 0 14072 37 0 0 0 0 0 88 37 0 0 0 0 0 0
   8      19 sdb3 129 0 13368 41 0 0 0 0 0 76 41 0 0 0 0 0 0
   8       0 sda 1520706 1393 1411401048 45417413 1663134 23681 283007656 70375190 0 38201992 137687122 0 0 0 0 198939 21894519
   8       1 sda1 1520584 1393 1411395248 45417224 1663134 23681 283007656 70375190 0 38201696 115792414 0 0 0 0 0 0

```
That  is the how Linux sees storage devices in an uninterpreted format...  That the Linux utilities look at to come up with their output.

If  that query cannot see your internal drive, then "no other" software  will. If that does not see anything then the answer is confirmed that  your drive is just not working. 

*** Your laptop is almost 10 years old. The average estimated lifespan of a hard drive is 3.5 years. The estimated lifespan of an SSD is 10 years. The average price for a mainstream branded 1TB SSD today is $50 USD. (And prices are forecasted to keep going down in the next few months.) I think it is time to budget for a new drive that will bring new life to your old laptop.

From my 11 year old Lenovo ThinkPad T520 laptop that I am posting this from:
```

mafoelffen@Mikes-ThinkPad-T520:~$ lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL | grep -v '/snap/' | sed 's/^[\|,`]-/\|_/g'
NAME     SIZE FSTYPE   LABEL     MOUNTPOINT                         MODEL
sda      1.8T                                                       Samsung SSD 870 QVO 2TB
&#9500;&#9472;sda1   550M vfat     {SYSTEM}  /boot/efi                          
&#9500;&#9472;sda2   128M                                                       
&#9500;&#9472;sda3   900G ntfs     {Windows}                                    
&#9500;&#9472;sda4   983M                                                       
&#9500;&#9472;sda5    30G                                                       
&#9492;&#9472;sda6 931.4G ext4               /                                  
sdb      1.8T                                                       Samsung SSD 870 QVO 2TB
&#9500;&#9472;sdb1 931.5G ntfs                                                  
&#9492;&#9472;sdb2 931.5G ext4               /home/mafoelffen/Disk2             
sdc    931.5G                                                       Dogfish SSD 1TB
&#9492;&#9472;sdc1 931.5G ext4     mSATA1    /home/mafoelffen/mSATA             


```
/dev/sda is in the original drive bay. /dev/sdb is a drive caddy tray that replaced the original SATA DVD drive. /dev/sdc is directly plugged into the WWAN connection port. 3 SSD drives, of 5TB storage, in a laptop... Your Laptop is similar to mine.

---

### Post by bhubunt on 2023-03-17
Hi Tea for One and MaffoElffen
Thanks so much for your help. I will get to your latest remarks in a next post, but I first want to report that I was just  live hacked on this computer, while in a live session on the same 18.04 Ubuntu installation stick.

I had my suspicions already last night, because of the strange results in posts 39 and 37. I actually executed the ```
 sudo parted -l  
``` command twice on the same Kingston USB stick. Tea for One asked me to make a new USB stick, but I used the same stick twice, rather than making a new one. Afterwards, I was puzzled why the very same stick in one terminal post came up with a strange Mac partition table, as noted by Tea for One, when in the next terminal the same stick suddenly had a different and correct partition table.  I can only conclude that the partition table on the stick was changed in the interim, but not by me. 

Still puzzled, I got up early this morning to report this strange phenomenon of the changing partition table on the same USB stick to you, when I was live hacked.

Let me explain how I know.

The first thing I did when I was on this live session [while there was _no_ Lan connection to the internet, btw], was look for the logs app  in Activities. To my total surprise there suddenly was no Logs App on this installation stick, when there was last night, so I quickly made a screenshot of this, see below, the thumbnail says "no results" for logs.

 Moments later the other apps in the Activities window suddenly slightly changed size and it seemed as if a "wave" passed through the apps, and when thereupon I entered "logs" into the Activities search box, the logs app "magically" had reappeared, see second thumbnail.  

With the logs back, I quickly downloaded the log and put it on pastebin. [https://pastebin.com/771Q9D9E](https://pastebin.com/771Q9D9E)

I should explain that at the beginning of this session, when the Logs App was removed, I was _not_ connected to the internet via lan. Also, this Lenovo x230 does not have wifi or bluetooth, and yet, when I clicked on the software update app, a download of the software catalog was in progress, even though I was not connected to my modem.

---

### Post by MAFoElffen on 2023-03-17
But that is going to be normal for a LiveUSB media... Remeber me explaining to you in a post in your I/O thread about the Live Image Environment being non-persistent? That when it powers done, than anything that you have done is lost... Because the Live Image itself, is read-Only? That the running image only exists in a ram disk?

So you were not hacked, and that is all normal.

Sit down. Relax. Remember to breath.

Where are you with either doing those commands and with running the system-info script?

---

### Post by bhubunt on 2023-03-17
[QUOTE=MAFoElffen;14135171]This is as deep a terminal command as I will give you
```

grep . /proc/diskstats

```


Hi,
Thanks for the helpful ref. I will definitely try this terminal command later today.  I should also mention that I bought this Lenovo x230 refurbished in 2021, so the hard disk is only about one and a half years old.

Also, you are probably very busy, but might you have time to have a look at the log of this morning's session? [https://pastebin.com/771Q9D9E](https://pastebin.com/771Q9D9E)

---

### Post by bhubunt on 2023-03-17
To Tea for One,
Thanks for the suggestion.

---

### Post by bhubunt on 2023-03-17
> **MAFoElffen said:**
> This is as deep a terminal command as I will give you
```

grep . /proc/diskstats

```
Example output
```

mafoelffen@Mikes-B460M:~$ grep . /proc/diskstats | grep -v 'loop'
 259        0 nvme0n1 471363 991 35565189 96120 8383457 1 197391655 181874 0 786840  506151 589441 11 132325632 170925 210473 57231
 259       1 nvme0n1p1 1483 991 56286 139 58 1 95 11 0 372 158 28 0 959096 6 0 0
 259       2 nvme0n1p2 227 0 25192 34 0 0 0 0 0 192 34 0 0 0 0 0 0
 259       3 nvme0n1p3 2952 0 637576 452 1161 0 22992 20 0 556 486 36 0 3800 13 0 0
 259       4 nvme0n1p4 466265 0 34831015 95454 8382238 0 197368568 181841 0 785768 448202 589377 11 131362736 170905 0 0
   8      16 sdb 512 0 39456 134 5 0 0 31 0 220 196 0 0 0 0 5 31
   8      17 sdb1 107 0 5800 32 5 0 0 31 0 112 63 0 0 0 0 0 0
   8      18 sdb2 140 0 14072 37 0 0 0 0 0 88 37 0 0 0 0 0 0
   8      19 sdb3 129 0 13368 41 0 0 0 0 0 76 41 0 0 0 0 0 0
   8       0 sda 1520706 1393 1411401048 45417413 1663134 23681 283007656 70375190 0 38201992 137687122 0 0 0 0 198939 21894519
   8       1 sda1 1520584 1393 1411395248 45417224 1663134 23681 283007656 70375190 0 38201696 115792414 0 0 0 0 0 0

```



Here is my output 

```
 
7       0 loop0 704255 0 1410584 586232 0 0 0 0 0 19824 164012 0 0 0 0
   7       1 loop1 13349 0 28680 1129 0 0 0 0 0 1228 0 0 0 0 0
   7       2 loop2 4316 0 9222 379 0 0 0 0 0 464 12 0 0 0 0
   7       3 loop3 410 0 1410 20 0 0 0 0 0 256 0 0 0 0 0
   7       4 loop4 16896 0 35816 2171 0 0 0 0 0 1304 240 0 0 0 0
   7       5 loop5 42 0 234 3 0 0 0 0 0 16 0 0 0 0 0
   7       6 loop6 36 0 656 7 0 0 0 0 0 8 0 0 0 0 0
   7       7 loop7 65 0 184 6 0 0 0 0 0 24 0 0 0 0 0
   8       0 sda 11605 187 1602018 16409 0 0 0 0 0 18032 652 0 0 0 0
   8       1 sda1 11520 187 1598914 16282 0 0 0 0 0 17976 616 0 0 0 0
   8       2 sda2 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
   7       8 loop8 41 0 226 5 0 0 0 0 0 16 0 0 0 0 0 


And  

grep . /proc/diskstats | grep -v 'loop'
   8       0 sda 11635 187 1604610 16444 0 0 0 0 0 18084 652 0 0 0 0
   8       1 sda1 11550 187 1601506 16318 0 0 0 0 0 18028 616 0 0 0 0
   8       2 sda2 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0

And 

ubuntu@ubuntu:~$ lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL | grep -v '/snap/' | sed 's/^[\|,`]-/\|_/g'
NAME     SIZE FSTYPE   LABEL                    MOUNTPOINT                     MODEL
loop0    1.9G squashfs                          /rofs                          
sda      7.2G iso9660  Ubuntu 18.04.4 LTS amd64 /cdrom                         DataTraveler 3.0
&#9500;&#9472;sda1     2G iso9660  Ubuntu 18.04.4 LTS amd64                                
&#9492;&#9472;sda2   2.4M vfat     Ubuntu 18.04.4 LTS amd64                                
ubuntu@ubuntu:~$ 



 
```

Curious to hear your reflections. The disk is 1.5 years old, not 10 years. I bought this Lenovo x230 in 2021. But it looks like the internal drive is not recognized. Only the USB stick is....Thanks for this awesome command line.

---

### Post by bhubunt on 2023-03-17
> **MAFoElffen said:**
> 
So you were not hacked, and that is all normal.



Alas it is not -- my email with a strong password was also hacked.

---

### Post by MAFoElffen on 2023-03-17
Brand new drives are not exempt from catastrophic failure...

Just because it was sold as refurnished does not mean that the hard disk was replaced with a new component. I did refurbishing of old electronic hardware at a non-profit computer recycler. We refurbish some computers that are above a minimum spec, to resale or donate to some people or organizations. Equipment that did not meet spec's was recylcled as per the pieces/weight of.

If the company was reputable,,, Then they did their due diligence. Which would mean that the hard disk was tested at that time, and "at that time", that the HDD passed certain hardware tests. I am assuming that when it is opened up, that is is the original drive.

I still have an Acer Laptop here that I bought in 2006, that is 32 bit and has an SCSI PATA drive (before SATA came out) that is chugging along with Debian Sid. That doesn't mean that it might not fail in the next hour, day, or year.

---

### Post by bhubunt on 2023-03-19
Thanks so very much for your help troubleshooting, MAFoElffen and Tea for One. And everyone else, of course.

---


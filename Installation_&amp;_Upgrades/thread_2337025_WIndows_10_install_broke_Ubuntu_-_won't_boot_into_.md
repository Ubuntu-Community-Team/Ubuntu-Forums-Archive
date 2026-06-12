---
title: "WIndows 10 install broke Ubuntu - won't boot into Ubuntu"
date: 2016-09-13
forum: Installation &amp; Upgrades
---

### Post by Jonners59 on 2016-09-13
I am using 16.4 xubuntu and have recently installed Windows10 for some apps that only work on MS.

This  broke the boot/Grub, which I fixed using the repair tool, but the  Ubuntu install will not bootup fully.  It stops at a command line  with:
```

Welcome to emergency mode!  After logging in type  "journalctl -xb" to view system logs.  "systemctl reboot" to reboot,  "systemctl default" or D to try again to boot into default mode.
Press Enter for maintenance
for press Control-D to continue):
```

I have a seperate /usr partition, and I am wondering if the Windows 10 install somehow damaged that.

I have tried boot repair several times.  The last was [http://paste.ubuntu.com/23172690/](http://paste.ubuntu.com/23172690/)
Two others: 23159426 and 23159919

I have never had Boot Repair not work for me.

Can you please advise/help?[IMG]https://ssl.gstatic.com/ui/v1/icons/mail/images/cleardot.gif[/IMG]

---

### Post by oldfred on 2016-09-13
It looks like you have newer Windows that uses fast start up or always on hibernation?
You may have to turn that off whenever Windows does updates.
I prefer to have Windows on one drive and Ubuntu on another drive if you have more than one drive. Then you can keep a Windows boot loader in the MBR of the Windows drive to directly boot Windows. Grub only boots working Windows so you may often need to directly boot it.

Boot-Repair used to only recognize /boot as an extra partition that would need mounting when it does a repair. But I see it mentions /usr.

What does this show?
journalctl -xb

---

### Post by Jonners59 on 2016-09-14
SO chuffed you picked this up OldFred..  How are you?  Been a long time.

It is a prob doing anything, I only have the WIndows OS working at that is bare bones as I don't have apps on it.  WHen I do a reboot I'll try the cmd and see what I get and feedback.  If it is long, I will prob need to take a photo.  Is there anything I can do via the Windows 10?

How could I save the output and what should I expect...?

Cheers :-)

---

### Post by oldfred on 2016-09-14
I also see boot flag * on sdb2 a Linux partition.
Boot flag should only be on the NTFS primary partition with Windows boot files or your sdb1.
Boot-Repair for whatever reason sometimes moves it to incorrect location.

Flag is only important if booting with Windows boot loader as grub just looks for Windows files & knows to jump to correct partition. But flag is also important if repairing or reinstalling as Windows has to see correct partition for install.

In BIOS boot mode, Windows major updates or reinstalls has been known (for years) to delete a Linux logical partition. It does not correctly see Linux partitions, and rewrites partition table without it. Data is still there. Since your partitions on sdb are all primary, you probably are ok, but best to keep documentation on partitions like the pastebin. I have found pastebins get obsolete after awhile, so save a copy or detailed partition list as part of normal backup.

---

### Post by Jonners59 on 2016-09-14
Cheers Oldfrd.

I may need to come back to you for a couple of those points, but will change the boot to sdb1 only.  Hope that works

---

### Post by Jonners59 on 2016-09-14
YES!!!!!

OK, don't know what fixed it but found something out by mistake that may be of use to others.

I rebooted from Windows 10 to boot in to the Boot Repair CD, but had forgotten to put it in the drive, until it was too late, the GRUB screen was up before the draw closed.  It then booted in to Ubuntu, and worked.  I found that it was booting in to my account, but using the BR CD.  Yes, the screen res was awful and couldn't do a great deal, but at least everything worked and was safe.  Up to me to decide what next: backups, fixes, etc.  As it was I just used gParted to change the boot label and I used Ubuntu Tweek to clean the machine, then rebooted, taking out the BR CD.

It worked, again, though the res was awful.  Only option was Default and that was something like 800 x 600.  So I went in to additional drives and changed to the latest nVidia, rebooted and all worked GREAT....


Now, a couple of things.

9 times in 10 when in GRUB the mouse does not work, which makes changing options a no goer - how do I fix?
"but best to keep documentation on partitions like the pastebin."  what's this and how....?

---

### Post by oldfred on 2016-09-14
The pastebin you posted has many details on install.
Boot-Repair uses an older tool bootinfoscript for part of its output which can be run from command line. I use that as part of my rsync backup, just to have documentation on system configuration.

You can just save MBR partitions to a test file with this:
       First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX >parts_ parts.txt 

Grub used to use BIOS settings for keyboard/mouse or USB. My older system I had to turn on USB support in BIOS. Both Windows & Ubuntu had their own drivers, but grub relied on BIOS. So check if you have USB support or settings to turn it on in your BIOS.

---

### Post by Jonners59 on 2016-09-15
Thanks Old Fred
Will need to looik in toi this later, for now the CPU fan has also stopped.  Never rains.  New one on order.  Hope it's that not the board!

Also read that fastboot in 10 can cause probs so should be turned off.

[IMG]http://www.tenforums.com/attachments/tutorials/12684d1424033491t-fast-startup-turn-off-windows-10-a-fast_startup-3.jpg?[/IMG]

---

### Post by oldfred on 2016-09-15
And major Windows updates may turn it back on.
Check before rebooting if a major update occurs.

But best to always have a Windows repair recovery flash drive and the Ubuntu live installer for the current versions of all operating systems you have installed.

And good backups as a way to restore when system goes totally wrong.

---

### Post by kurt18947 on 2016-09-15
I don't know if this would work for Jonners59; it may not due to inadequate hardware support but running Windows 10 as a guest OS in Virtualbox  works pretty well and avoids these problems. There are issues with other VM software such as missing Windows drivers.

---

### Post by Jonners59 on 2016-09-15
Thanks kurt18947, but I have run  number of VMs and there are limits.  I use it for one app that builds websites (Serif) which i use rarely, and another bunchof apps to build and repaire my family's smartphones.  I find they do not work in VMs...  ANd yes, tried the Linux version but they do not work and are complicated.  But BIG thanks forthe idea.  :-)

---

### Post by Jonners59 on 2016-09-18
> **oldfred said:**
> It looks like you have newer Windows that uses fast start up or always on hibernation?
You may have to turn that off whenever Windows does updates.
I prefer to have Windows on one drive and Ubuntu on another drive if you have more than one drive. Then you can keep a Windows boot loader in the MBR of the Windows drive to directly boot Windows. Grub only boots working Windows so you may often need to directly boot it.

Boot-Repair used to only recognize /boot as an extra partition that would need mounting when it does a repair. But I see it mentions /usr.

What does this show?
journalctl -xb

Oldfred
A grub question.  I am finding that 9 times out 0f 10 when I boot and get in to GRUB my keyboard stops working hence I can not select anything other than the preffered OS/image.  How can I fix this, do you know, please?

Jonners59

---

### Post by oldfred on 2016-09-18
My old BIOS system had to have USB keyboard & mouse enabled in BIOS. Both Windows & Ubuntu had their own drivers, so that setting did not matter once booted.
My newer UEFI systems have a variety of USB port settings, I typically make sure they all are on, even though some say it may slow boot.

---

### Post by Jonners59 on 2016-09-19
> **oldfred said:**
> My old BIOS system had to have USB keyboard & mouse enabled in BIOS. Both Windows & Ubuntu had their own drivers, so that setting did not matter once booted.
My newer UEFI systems have a variety of USB port settings, I typically make sure they all are on, even though some say it may slow boot.

Sorry, didn't make it clear.  Works fine in BIOS every time, it is only in GRUB I get the problem....

---

### Post by oldfred on 2016-09-19
Do you have a BIOS setting? As that is what grub uses.
Internally BIOS may always work with keyboard, but once you boot settings in BIOS must be on for grub to be able to use keyboard & mouse.

---

### Post by Jonners59 on 2016-09-19
Interesting.  So having it work in BIOS should make it work in GRUB as GRUB uses the BIOS setting...  So....  My keyboard and one of my mice/mouse both plug in to the old PS/2 (I think that is what they used to be called) sockets and not the USB, because it's faster, more direct (when I have had MB troubles it has been a god send) and it frees up USB ports.  Maybe I need to change that.  I'll try USB instead for the keyboard.

Yes, two mice/mouse.  I have found that the PS/2 connected is more reliable and I use it when the battery runs out on the blue-tooth one.  Talking of which, after all the below resolved I have found that there is a long lag or that the bluetooth mouse sticks before moving.  Really annoying.

---


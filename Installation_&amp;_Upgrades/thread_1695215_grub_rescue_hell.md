---
title: "grub rescue hell"
date: 2011-02-25
forum: Installation &amp; Upgrades
---

### Post by gpaez on 2011-02-25
First of all, I am absolutely new, so I am sorry if I am breaking protocol. So here is my problem:

I have an Acer Aspire One netbook, in which I was running two OS: Ubuntu and Windows XP. After having some problems with Ubuntu, I decided to erase it: I deleted the Ubuntu Partition (that at the time was actually called "Unknown Partition", but it was Ubuntu). After restarting the computer, I was (am) stuck in something that can only be called "grub rescue hell".

Now, I have read a lot of the threads about this subject, but none of them seem to work. I can barely use any commands (ls, set), and I have tried reinstalling Ubuntu (through an USB drive, changing booting priorities to USB FDD) and also I've tried using a Windows XP Recovery .exe file (also through a USB drive). Even though the computer seems to be "loading" the flash drive, at the end I have the exact same message in a black screen:

[B]error: no such partition.
grub rescue>[/B]

I should add that the computer belongs to my wife, and that I was trying to "help". You know how that usually goes. So PLEASE HELP ME... and get me our of grub rescue hell! :confused::confused::confused:

---

### Post by cristian.ene on 2011-02-25
welcome to my world! i fu*ked up my girlfriend's laptop :popcorn:

I might have found a solution...i am writing the usb stick as i type. :)

If it'll work for me,...i'll share the news!

---

### Post by Rubi1200 on 2011-02-25
Hi,

@gpaez and cristian.ene

Before potentially messing anything else up, I suggest you both do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

The results will help us to determine the problem so we can offer advice to help solve things.

Thanks.

---

### Post by cristian.ene on 2011-02-25
Gpaez... first of all... can you boot with live cd? pressing TRY UBUNTU... if that works,.. do what gpaez told you to

IF THAT DOES NOT WORK,...and you want to FRESH install ubuntu... 

Download this,... 

[http://sourceforge.net/projects/unetbootin/files/UNetbootin/494/unetbootin-windows-494.exe/download](http://sourceforge.net/projects/unetbootin/files/UNetbootin/494/unetbootin-windows-494.exe/download)  it's called unebooting
after that... run it,..
choose  disk image iso and browse for your ubuntu iso
insert your usb stick, and choose it's letter

after that,.. it's easy :)

---

### Post by gpaez on 2011-02-25
Hi cristian.ene, Rubi1200:

It seems like I am out of luck. :(  I've tried several times booting the Ubuntu Live USB, and I even used UNetbooting. And the results are exactly the same: after taking a few minutes during the boot, the netbook goes to the same black screen:

[B]error: no such partition.
grub rescue>[/B]

Is there any way to fix or find out what's going on directly from that grub rescue screen? Because booting and rebooting with the Live USB is not working...

Thanks.

---

### Post by Rubi1200 on 2011-02-26
Are you choosing the option to try or install?

Do you have any other LiveCD distros around?

I suggest trying either Knoppix or Slax.

The problem is this:

if you deleted Ubuntu you also deleted GRUB in the MBR. However, sometimes data is left over and leaves you with the message you see.

If you just want Windows back, the fix is to restore the Windows bootloader.

Give it a try first:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---


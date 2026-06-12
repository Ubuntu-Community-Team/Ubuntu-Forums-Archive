---
title: "Problems booting from hard disk after installation"
date: 2012-07-17
forum: Installation &amp; Upgrades
---

### Post by PrinceJamal89 on 2012-07-17
I have a PC that I'm working on for a friend of the family. 
 
Gateway E-3400
Intel Pentium 3 Processor (940 MHz)
246 MB of RAM
20 GB Hard Drive
The computer was designed for Windows 98, but it had XP installed when I picked it up.
 
When I first got the PC, it had a bucket list of problems, and the computer itself is old. I'm not going to list them, but the best advice I had been given was to format the drive and reinstall the operating system. 
 
I tried to install XP first, but given that I didnt have a valid product code, I couldn't complete the installation.(I already know I can "get" one regardless). Instead of buying a new copy of XP or generating a key, I decided to go with a free OS instead. I tried Xubuntu before, but it kept freezing to the point of needing a hard restart.
 
Now I'm trying to put Lubuntu 12.04 on the computer. When I went through the installation with the default settings it never completed the installation so I had to do a hard restart. When I created the partitions myself (once using ext3, another time with ext4, and the last time with FAT32) I was able to complete the installation. 
 
But I kept getting this error:
 
```

stdin: error0
Generating locales...
en_US.UTF-8... done
(some other info related to the above)
pwconv: failed to change the mode of /etc/passwd- to 0600
/usr/lib/python2.7/dist-packages/LanguageSelector/LocaleInfo.py:256:UserWarning: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

```
 
When I try to restart the computer (booting from the hard drive) it doesnt load. All I get is the blinking underscore, like a command prompt. I could leave it, and it would be in the same place when I came back. When I boot from the Live CD it works fine, as long as I don't try to install Lubuntu then.
 
When I created the aprtitions using FAT32, I created a /windows partition, a swap partition, and a root "/" partition using the ext3 or ext4(I tried both). Does the error message mean I need to create a /usr parition too?
 
Thanks for the help

---

### Post by Rex Bouwense on 2012-07-17
Welcome to the forums.  A couple of questions.
First, when you boot from the CD does everything work?
Second, when you tried to install any of the times did you choose use the entire disk?
You exceed the minimum requirements for a Lubuntu install so it should have installed.  Did you check the download (MD5Sum) and burn the ISO at a low speed?
Would you please post a screen shot of your partitions using GParted from the CD?
We will get this thing sorted out.

---

### Post by PrinceJamal89 on 2012-07-21
Thanks, 

According to GParted here's how the disk is set up:

/dev/sda1 FAT32           13.95 gb
/dev/sda2 extended(ext3)  4.1 gb
/dev/sda3 swap            381 mb
/unallocated              223.94 mb

Yesterday I browsed through a book on Ubuntu at the book store. In the section on troubleshooting the installation, it said if the computer can't boot from the hard drive, grub either isn't installed, or had problems installing. The book said the fix for this was 

1) Boot from ISO disk
2) Select "Try Ubuntu Without Installing"
3) Open Terminal
4) Enter "sudo grub-install /dev/sda"
5) remove the disk when done and reboot the computer.

When I tried this, I was given this:

Error Message: /usr/sbin/grub-probe: Error: cannot find a device for /boot/grub (is /dev mounted?)

---

### Post by oldfred on 2012-07-21
Linux will not install to a Windows FAT32 partition. You need Linux formated ext3 or ext4 partitions.

With 20GB a default install of the entire hard drive is probably the easiest. It should create / (root) and swap. With 256K of RAM swap should be 2X RAM or at least 512MIB.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by PrinceJamal89 on 2012-07-22
> **oldfred said:**
> Linux will not install to a Windows FAT32 partition. You need Linux formated ext3 or ext4 partitions.

With 20GB a default install of the entire hard drive is probably the easiest. It should create / (root) and swap. With 256K of RAM swap should be 2X RAM or at least 512MIB.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

That was my original approach the very first time I tried the installation. I usually have the most problems whenever I try a default installation. A few times I couldn't go all the way through with that type of installation. It would either freeze, or if I did complete the installation, I would get the error message that I outlined in my first post. The default installation uses the entire 20gb for ext4. I don't know how much, if any, swap space is left or created. 

Now for some reason, whenever I install the OS using the custom partitions, I'm able to complete the installation, but unable to install/activate the grub.

But, I'm trying the standard installation again... this time I expanded the progress bar so i could see the messages as they came up. The first error message I saw so far was something about New York and the domain failure (after the map for you to select your location came up, but before I made a selection). Now its a blank screen(with the cursor for the mouse still visible) and the systems non-responsive. Its been like that for about 10 min now. I gave it some time in case it was struggling to reformat the drive.

UPDATE (3:18 am)

The mouse cursor disappears off and on, but the monitor is still blank. The CD and the CPU lights are both on solid.

UPDATE (4:57 am)

Ended up having to do a hard restart and re-doing the installation(I did the default installaiton). It finished and as the desktop loaded I got an internal error message. It reads:

> 
Executable Path: /usr/bin/ubiquity-dm
Package: ubiquity 2.10.16
Problem Type: Crash
Title: ubiquity-dm crashed with OSError in_execute_child():[Errno 2] No such file or directory
Traceback(too long to type)
Unreportable Reason: Your system partition has less than 24mb of free space available,
which leads to problems using applications and installing updates. Please free some space


I also tried to activate the grub through the command line as i had done earlier, but i got the same error message as I listed a few posts ago.

Maybe I need to try a different distro?

---

### Post by efflandt on 2012-07-23
If your computer only has 256 MB RAM you probably have to use the alternate installer [https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO) because I think the regular installer needs 384 MB RAM.

What is the size of the partition you are installing on now?

What video card does it have (**lspci** from a live session)?

---

### Post by PrinceJamal89 on 2012-07-23
> **efflandt said:**
> If your computer only has 256 MB RAM you probably have to use the alternate installer [https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO) because I think the regular installer needs 384 MB RAM.

What is the size of the partition you are installing on now?

What video card does it have (**lspci** from a live session)?


I downloaded the ISO for the alternate install. Tried the installation. For the partition, I told it to use the whole drive, but instead of using the default option every time, I told it to create an LVM along with using the entire disk as needed. 

These were the notes that I took of error messages:

During the initial install I got this message:
```
[!!] Select and Install Software
Installation Step Failed
An installation step failed. You can try to run the failing item again from the menu, or skip it and choose something else. The failing step is:
Select and Install Software
```

This message came up while the step was at 85% both times.

The first thing I did was rerun the step. Same message.
This time I skipped the step and chose the one after it which was 
"Install GRUB boot loader on hard drive"
The installation finished after that > disk ejected > System restarted. When the system rebooted, a text based, command style prompt came up. I followed the notes that I had taken from a book on troubleshooting Ubuntu installations at the book store:

1) I logged in using the user information I had entered.
the prompt changed to "username@PCName:~$ _"
Like the notes from the book said, I entered:

sudo apt-get update
sudo apt-get -f install
sudo apt-get instal lubuntu-desktop (the book said "ubuntu-desktop" but when I entered that the first time I gave me a 'file not found' message, so I used "lubuntu" the second time)

(I reinserted the iso disk when prompted)

After this a list/blur of file names appeared, this message followed:

```
0 upgraded, 750 newly installed, 0 to remove and 0 not upgraded
need to get 0 B/289 MB of archives
After this operation 878 MB of additional disk space will be used
```

I entered 'y' at the prompt to continue

It showed a Percentage and said "num%[working]"; then at 73% it said:

```
73%[working}[388.158220]end_request: I/O error, dev sr0 sector 1303008

73%[working][389.248680]end_request: I/O error, dev sr0 sector 1303160

95%[working][436.322793]end_request: I/O error, dev sr0 sector 1045972
95%[working][437.402959]end_requst: I/O error, dev sr0 sectr 1046004

Failed to fetch cdrom:(ISO Name and release was here/pool/universe/g/gnome-system-tools/gnome-system-tools_3.0.0-2ubuntu1_i386.deb    Hash Sum mismatch

[same iso name and verison text as above]/main/s/samba/smbclint_3.6.3-2ubuntu2_i386.deb    Hash Sum mismatch


E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

I also burned the iso at the lowest speed possible (4x). What could be keeping all of the files from downloading?

---

### Post by oldfred on 2012-07-23
the error messages look like it cannot read CD. Still may be a bad burn. Or is CD on its last legs.

It might help to clean lens:
How to clean CD lens:
[http://members.iinet.net.au/~herman546/p27.html](http://members.iinet.net.au/~herman546/p27.html)

---

### Post by PrinceJamal89 on 2012-07-24
I've gotten the same kind of messages with every operating system I've tried to install(Puppy Linux, Xubuntu, Lubuntu), there was always one directory or another that couldn't be installed, copied, or loaded. But I pulled them all from the same stack. I'll check the disks for scratches and dirt.

Plus I use the app from freeisoburner.com so I'm sure that could be a problem,too. I'd just hate to have to find new disks and a new iso burner.

Or maybe I need to check them with a [http://en.wikipedia.org/wiki/Md5sum](http://en.wikipedia.org/wiki/Md5sum)

---

### Post by mastablasta on 2012-07-24
with md5sum you check the downloaded image against the image on server.
 
go default for now (ext4 and all) since disk is small. your CPU is also a bit old but i guess it should still be supported. 
 
you can use a USB stick if you have it to boot from it instead of using new CD every time. if you continue with the CD you should verify the data after it's burned and as mentioned you CD player might have a bad lense.
 
if you can't boot from usb by default from bios you can use PLOP disk boot manager which can be installed on a floppy disk.
 
since you say xubuntu was freezing before could also mean you have a hardware error.

---


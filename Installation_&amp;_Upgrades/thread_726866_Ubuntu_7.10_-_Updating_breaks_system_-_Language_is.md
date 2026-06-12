---
title: "Ubuntu 7.10 - Updating breaks system - Language issues"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by AbdulRahiem on 2008-03-17
[FONT=Times New Roman][COLOR=Black]After dabbling with Debian a long time ago, when kernel versions were still 0.97 and the like, I decided to get back to it. My memory from that time is very stale.

I tried about 10 distros, but only two allowed me to easily connect to the internet through my GSM modem, Ubuntu and Mepis. In the end I opted for Ubuntu as it would automatically connect during booting, while Mepis required me to connect manually each time.

A few days ago I reinstalled Ubuntu 7.10 from scratch on my HP Pavilion dv2297ea. Everything worked well. This was after my previous installation got broken upon updating/upgrading packages. The same happened again and the boot process won't complete. I suppose I should have copied the system disk before upgrading. If I get my system back up, it is the first thing I shall do. I spent several hours searching this forum and although there were many similar issues, none of them seem to address my problem.

In my installation I use Dutch as user interface and basic system language. For default keyboard I use US English International (essential, because I frequently need to enter accented characters). I also have the Arabic keyboard layout installed. Setup installed the NL keyboard, but I removed this as it is of no use to me (punctuation characters all in the wrong places).

When attempting to update/upgrade (more than 800 packages), the process did not complete. Information details flashed past too quickly to be able to read them properly, but I noticed that in most cases there was a complaint about the locale settings not being available. Somehow, it seems, the update process deleted such settings. (System language Dutch; keyboard US English with dead keys; timezone Asia/Kuwait.)

After the aborted (by the system) update, I tried to reboot. A cold boot was impossible. When pressing Shut Down, it immediately looped back to the Login Screen. It did so repeatedly, so, in the end, there was no other choice but to just power off. Before powering off, I did log in again and the system told me that I had chosen a new language and threatened to rename several of my directories. I selected to keep the existing Dutch names. I had definitely NOT chosen a new language (English). In fact, the only language support I had enabled was for Dutch. However, menu titles had all changed to English. The date format was still Dutch, but the names of day and month had changed to English.

When booting normally, the system stops with BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash). It also stops there when I remove the locale settings from the boot-up script.

When booting in recovery mode it stops at the infamous: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0.

After reading this forum I tried entering 'setkeycodes e059 120', which it seemed to accept, but nevertheless did not prompt any further booting action.

When checking the default settings from within initramfs, I found everything OK, except XKBLAYOUT="nl". (I also saw BOOTTIME_KMAP_MD5="aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa". This seems odd, but I don't know if it's wrong or not.)

From the Live CD I can access and read all my partitions without trouble, but permissioning issues do not allow me to make changes to files in my system directories. And I do not know how to do so from within initramfs, in case that is possible.

At the end of the day, I *could* again reinstall my system, because I have my /home directory on a different partition. Presumably, even my Virtual Disk files will save me from having to reinstall (activated) Windows XP in Virtual Box.

I used Partition Manager 8.5 from Paragon Software GmbH to check for any changes in disk ordering, etc. I found everything to be in order.

What else can I try to rescue my system? [/COLOR][/FONT]:confused:[FONT=Times New Roman][COLOR=Black] In case I need to edit files on my system partition, I need to know how to overcome the permissioning problem.
[/COLOR][/FONT]

---

### Post by AbdulRahiem on 2008-03-23
[FONT=Times New Roman]The culprit has been found. An essential program for me is Geneweb. But on the default repository [/FONT][FONT=Times New Roman]('Server for Kuwait') [/FONT][FONT=Times New Roman] only version 4.09 or 4.10 was available. The database in those versions is incompatible with databases created under version 5.

I searched the net and indeed found debian packages for version 5.01. However, the advice was that I should use Synaptic to download and install it by adding a new source. ([/FONT]deb [http://*ftp.de*.debian.org/debian](http://*ftp.de*.debian.org/debian)* sid main.) [FONT=Times New Roman] So far so good. However, after a little while I was getting a warning that upward of 600 updates were available. Downloading (> 4 hours) and installing those updates was, each time, breaking my system as it somehow mishandled the language settings.

Now, luckily, geneweb version 5.00 is available on my default repository. Everything is working well.

The only general problem that remains is that Synaptic always complains it cannot verify the sources as the public key is not available. I don't know the reason for that.

* there was the advice to replace 'de' by the code for my country, but 'kw' was not listed amongst the available mirrors. So, I tried 'nl' and 'de'.

Best regards


[/FONT]

---


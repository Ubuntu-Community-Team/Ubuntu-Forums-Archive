---
title: "[SOLVED] Epson DX7000F: I cannot chose USB CUPS backend adding my printer."
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by Norber_OK on 2008-07-15
I have an Epson Stylus DX7000F printer.

I have downloaded gutenprint-5.2.0-beta3 from sourceforge.net, and I have compiled it, then I have the Epson Stylus DX7000F printer driver option when adding the printer in cups web.

In cups web, when I try to add a new printer it asks me about the connection and it gives me a list in which I cannot chose USB backend (because it doesn't appear in the list).

I had an (not working) idea to add the printer in cups web: I was choosing AppSocket (for example) and in the next step, when it was asking me the connection uri I was deleting the word "sockect" and I was writing: "usb://epson/Stylus%20DX7000F" then it allowed me to continue till the end where it stopped with the uri error: Bad device-uri "USB://EPSON/Stylus%20DX7000F"!

Now I have tried to write "epson:/Stylus_DX7000F" then it allows me to continue till the end without an error, but when I try to print a test page it shows me the error message:

"Unable to open parallel port device file: No such file or directory"

I have not been able to add the printer and make it work.
What shoul I try? Any idea, workaround, etc ...?

---

### Post by wpshooter on 2008-07-15
I have a USB printer at home that I am not using.

When I get home I will try to see how/if I can go about getting the USB device to come up on the listing.

Check back in about 8 hours.

---

### Post by wpshooter on 2008-07-15
I plugged the USB cable of a Lexmark USB model Z611 into a up and running version of Hardy 8.04.1 and it immediately detected the the printer and assigned it a USB device name string.

The only problem I have with this one is that once it is detected, I can not get it to work because you have to read thru and run a book full of commands to get the driver installed and "PERHAPS" working.

But like I say it detects it just fine.

---

### Post by Norber_OK on 2008-07-16
Thank you for your reply wpshooter, it is difficult to get any answer from anyone by today.

I have tried to unplug the usb cable, reboot and plug it, but nothing happens.

When I run the terminal command lpinfo -v it does not show any usb:

lpinfo -v

network socket
network beh
direct hal
direct hpfax
direct hp
network http
network ipp
network lpd
file cups-pdf:/
direct scsi
network smb

So I think (without any more knowledge) that it may be a CUPS backend problem.

I would like to try any more but I dont know what.

Any idea, workaround, etc ...?

---

### Post by Norber_OK on 2008-11-03
SOLVED: See [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=940149](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=940149)

---


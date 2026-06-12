---
title: "HP 940c not connected"
date: 2009-03-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rv65 on 2009-03-15
Jaunty doesn't seem to work with my HP 940c. I'm using USB of course. It works in Intrepid and XP so why doesn't it work on Jaunty? Any reponse would be great.

---

### Post by rv65 on 2009-03-20
Any suggestions. It won't print for some reason. It will detect it but then it says it's not connected. It's connected to the USB port on both the printer and the Computer.

---

### Post by rv65 on 2009-03-22
Still waiting for why it's having problems. Is my printer not compatible or are there settings that I need to reconfigure.

---

### Post by DougieFresh4U on 2009-03-22
I have had the messege telling me 'printer may not be connected'.
It was happening after updates a couple of times, so I went into 'Synaptic' and checked to make sure things pertaining to printer were installed and I even re-installed some. I think one package was 'foomatic'. I shall look and see in a few

---

### Post by Nullack on 2009-03-22
Im having the same problem with my samsung laser printer on usb.

Im looking into it.

As usual the wiki has info:

[https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

---

### Post by Nullack on 2009-03-22
Seems to be detecting ok:
```

nullack@PPP:~$ lsmod | grep usb
usblp                  22656  0 
usbhid                 47040  0 
nullack@PPP:~$ tail -f /var/log/messages
Mar 22 17:28:54 PPP g15daemon[2551]: Booting plugin "Clock"
Mar 22 17:28:54 PPP g15daemon[2551]: Booting plugin "Linux UINPUT Keyboard Output"
Mar 22 17:28:54 PPP g15daemon[2551]: Booting plugin "LCDServer"
Mar 22 17:28:56 PPP kernel: [   17.805517] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Mar 22 17:28:56 PPP kernel: [   17.805520] Bluetooth: BNEP filters: protocol multicast
Mar 22 17:28:56 PPP kernel: [   17.845484] Bridge firewalling registered
Mar 22 17:28:58 PPP kernel: [   19.392653] ppdev: user-space parallel port driver
Mar 22 17:29:02 PPP kernel: [   23.252745] eth0: link up, 100Mbps, full-duplex, lpa 0xC1E1
Mar 22 17:29:13 PPP pulseaudio[3485]: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
Mar 22 17:48:52 PPP -- MARK --
Mar 22 17:49:29 PPP kernel: [ 1250.816170] usb 3-2: USB disconnect, address 3
Mar 22 17:49:29 PPP kernel: [ 1250.818087] usblp0: removed
Mar 22 17:49:41 PPP kernel: [ 1263.456023] usb 3-2: new full speed USB device using uhci_hcd and address 6
Mar 22 17:49:42 PPP kernel: [ 1263.652117] usb 3-2: configuration #1 chosen from 1 choice
Mar 22 17:49:42 PPP kernel: [ 1263.680120] usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x04E8 pid 0x327E
^C
nullack@PPP:~$ lpinfo -v
network socket
network beh
direct hpfax
direct hp
network http
network ipp
network lpd
direct hal:///org/freedesktop/Hal/devices/usb_device_4e8_327e_3V54BKEL510850E__if0_printer_noserial
direct usb://Samsung/ML-2510%20Series
direct scsi
network smb
```

Turned on apparmor complain:

```
nullack@PPP:~$ sudo aa-complain cupsd
[sudo] password for nullack: 
Setting /etc/apparmor.d/usr.sbin.cupsd to complain mode.

```

Got this in the log:

```
Mar 22 17:52:35 PPP kernel: [ 1437.009253] type=1505 audit(1237704755.463:10): operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=5029
Mar 22 17:52:35 PPP kernel: [ 1437.009672] type=1505 audit(1237704755.463:11): operation="profile_replace" name="/usr/sbin/cupsd" name2="default" pid=5029
```

Ill run the printing problems report script.

---

### Post by Nullack on 2009-03-22
Ive found this bug and confirmed it:

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/314106](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/314106)

Effected users can use the "effects me" button on LP or subscribe to the bug to follow it.

---

### Post by DougieFresh4U on 2009-03-22
I didn't report bug when it happened to me, I should have, but I didn't think any thing of it. As I said I just went and reinstalled a couple of packages pertaining to printer, foomatic being one as I remember updates for it last week. I also reinstalled a couple of the cups packages and I was up and running. 
couldn't understand why my printer was detected and saying 'ready' but when I click print, got messege after a few minutes 'may not be connected.
working fine at the moment

---

### Post by Nullack on 2009-03-22
Can you please go through your logs and list the packages you installed that got this working

---

### Post by DougieFresh4U on 2009-03-22
> **Nullack said:**
> Can you please go through your logs and list the packages you installed that got this working

Please let me know which logs I should be looking in and I will help best as I can.
Sorry for lack of knowledge.

---

### Post by Nullack on 2009-03-22
Thanks, its dpkg.log in /var/log also note the time and date to help you sort through it.

---

### Post by Nullack on 2009-03-25
Is anyone else able to get printing to work over USB on jaunty currently?

---

### Post by DougieFresh4U on 2009-03-25
> **Nullack said:**
> Thanks, its dpkg.log in /var/log also note the time and date to help you sort through it.

Went through several days  of logs and not a thing in there.
did you try going into Synaptic and reinstalling foomatic and cups , then reboot? Thats what got my 'hp5550 deskjet' to work again.

---

### Post by Nullack on 2009-03-25
Thanks Dougie but no such luck for me - re-installed all foomatic and cups packages that were already installed through synaptic search and rebooted - same ol printer is not connected message.

---

### Post by cabernet54 on 2009-03-25
I have the same problem with my HP 930C.

This evening I'll test reinstalling the cups and foomatic packages with synaptic too.

:(

---

### Post by Nullack on 2009-03-25
Upon Steve Langaseks request, Ive created a new bug to deal with these USB printer not connected issues. Can someone please confirm the status of the bug and feel free folks to subscribe and or check the effects me too button.

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/348316](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/348316)

---

### Post by Nullack on 2009-03-26
Folks if someone could kindly confirm the bug status in the above post that would be great thanks :)

---

### Post by cabernet54 on 2009-03-26
Tested reinstall cups and foomatic... but issue still here! :(

HP 930C and Canon IP4200 - same problem (with Intrepid all is perfect working)

---

### Post by cabernet54 on 2009-03-26
Mystery..... with XP in Virtualbox I have printed fine with the same HP 930C!!! :roll::-k:shock:

[[img]http://pixdiff.com/uploads/files/thumbs/thumb_-schermata-7f.png[/img]](http://pixdiff.com/uploads/imagehost/showimage/imageId/1e8112c3e7ca5eb82daf2e475fd4b155)

---

### Post by Nullack on 2009-03-27
The bug is still in a new status, can someone please confirm the bug by changing the status to confirmed. Confirming means a status change not saying confirmed in a bug comment.

---

### Post by cabernet54 on 2009-03-28
After the upgrade to beta version (with the last update) the problem is solved :guitar::popcorn:

---

### Post by rv65 on 2009-03-28
I fixed it. I played with the settings.

---

### Post by Nullack on 2009-03-28
Obviously, what does played with the settings mean?

Testing isnt about fixing it for yourself - users are encouraged to report fixes in the bug reports on launchpad so that Ubuntu itself may benefit from the results :)

---

### Post by Till Kamppeter on 2009-03-29
rv65, can you please tell HOW you fixed the problem? Which settings did you change? We could make your settings the default in Ubuntu, so that the printers work out-of-the-box for everyone.

Thanks in advance.

   Till

---

### Post by canabal on 2009-03-29
I am having the same problems with a Dell Latitude D630 and an epson stylus CX4800.

I reported all I could to launchpad.

---

### Post by canabal on 2009-03-29
Strange, after re-installing everything and restarting it did not work.

I opened up the foomatic control panel (in applications>system tools) and installed it from there using the "simple" driver and it worked.

---

### Post by rv65 on 2009-04-02
How I fixed it is the $64,000 question.

I just went into System>Preferences>Printer and went into some menu. I just selected it as the default printer and it went away. It's the detailed menu with all the settings.

---

### Post by Till Kamppeter on 2009-04-06
I have solved the problem now. It was a bug in hal-cups-utils assigning wrong CUPS URIs to USB printers when they were automatically set up on hot-plugging (Plug'n'Print). Please update your Jaunty system, REMOVE the queue(s) for your USB printer(s), power-cycle the printer(s) and you should get working print queue(s).

---

### Post by Nullack on 2009-04-06
L E G E N D :popcorn::guitar::p;):KS

---

### Post by rv65 on 2009-04-15
Mine still is having problems. It's not responding. I have no idea how to fix it. I deleted it, unplugged it, cleared the print queue and it still will say that error.

---

### Post by DougieFresh4U on 2009-04-15
Have you tried reinstalling 'foomatic' and other related packages?

---


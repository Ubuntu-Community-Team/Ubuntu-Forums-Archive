---
title: "USB-util"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by teja483 on 2011-05-19
testuser@testuser:~$ tail -f /var/log/messages 
May 20 14:16:00 testuser kernel: [72230.000649] usb 2-6: USB disconnect, address 10
May 20 15:15:38 testuser kernel: [75808.543322] vboxdrv: disagrees about version of symbol module_layout
May 20 15:16:57 testuser kernel: [75887.244794] vboxdrv: disagrees about version of symbol module_layout
May 20 15:18:17 testuser kernel: [75967.108318] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
May 20 15:52:33 testuser kernel: [78023.700084] usb 2-6: new high speed USB device using ehci_hcd and address 11
May 20 15:53:01 testuser kernel: [78051.314352] usb 2-6: USB disconnect, address 11
May 20 15:53:03 testuser kernel: [78053.264084] usb 2-6: new high speed USB device using ehci_hcd and address 12
May 20 15:53:11 testuser kernel: [78061.679975] usb 2-6: USB disconnect, address 12
May 20 17:21:23 testuser kernel: [83353.651032] vboxdrv: disagrees about version of symbol module_layout
May 20 17:21:24 testuser kernel: [83354.648202] vboxdrv: disagrees about version of symbol module_layout
May 20 17:47:55 testuser kernel: [84945.556083] usb 2-6: new high speed USB device using ehci_hcd and address 13

---

### Post by chellrose on 2011-05-19
Have you ever plugged in your USB drive to a Windows box?  If so, try putting it into a Windows box (7 or Vista, as I've heard that XP doesn't do this correctly), click the icon in the taskbar for removing external media, and click "Eject Kingston USB" (or some similar message that should appear), then wait for the "Safe to remove" message before unplugging it.
Sometimes Windows will put a hidden "lock" file on a USB drive if it isn't removed "properly" and that can cause it to not show up in Linux.

If that doesn't work, try reformatting the drive using Windows.  Try both NTFS and FAT32 (I think FAT32 is most common) and see which, if either, is recognized by Ubuntu,

---

### Post by prshah on 2011-05-19
> **teja483 said:**
> i inserted my USB(kingston) in the USB drive and its not detected.
what utility to use for the purpose.


You should not have to install any "utilities" or "drivers" to use USB pen drives in Linux.

However, if you have used Kingston's "secure" drive software (which encrypts contents on a USB drive) then it will not show up. Are you using a software or hardware based "secure" or encrypted USB pendrive?

If not, then please do the following diagnostic actions to check:
[indent]a) Unplug your USB drive
b) Open a terminal (Applications-Accessories-Terminal)
c) give the command ```
tail -f /var/log/messages
```
d) Plug in your USB pendrive; a whole bunch of diagnostic text will appear. Please copy and paste that text here.[/indent]

This text is diagnostic only and will give us more information. It will not "solve" your problem; nor will it deepen the problem. This information can be used to check why your pen drive is not showing up.

---

### Post by teja483 on 2011-05-20
testuser@testuser:~$ tail -f /var/log/messages 
May 20 14:16:00 testuser kernel: [72230.000649] usb 2-6: USB disconnect, address 10
May 20 15:15:38 testuser kernel: [75808.543322] vboxdrv: disagrees about version of symbol module_layout
May 20 15:16:57 testuser kernel: [75887.244794] vboxdrv: disagrees about version of symbol module_layout
May 20 15:18:17 testuser kernel: [75967.108318] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
May 20 15:52:33 testuser kernel: [78023.700084] usb 2-6: new high speed USB device using ehci_hcd and address 11
May 20 15:53:01 testuser kernel: [78051.314352] usb 2-6: USB disconnect, address 11
May 20 15:53:03 testuser kernel: [78053.264084] usb 2-6: new high speed USB device using ehci_hcd and address 12
May 20 15:53:11 testuser kernel: [78061.679975] usb 2-6: USB disconnect, address 12
May 20 17:21:23 testuser kernel: [83353.651032] vboxdrv: disagrees about version of symbol module_layout
May 20 17:21:24 testuser kernel: [83354.648202] vboxdrv: disagrees about version of symbol module_layout
May 20 17:47:55 testuser kernel: [84945.556083] usb 2-6: new high speed USB device using ehci_hcd and address 13
  
this is the result after what u said................

---

### Post by prshah on 2011-05-23
> **teja483 said:**
> testuser@testuser:~$ tail -f /var/log/messages 
May 20 14:16:00 testuser kernel: [72230.000649] usb 2-6: USB disconnect, address 10
May 20 15:52:33 testuser kernel: [78023.700084] usb 2-6: new high speed USB device using ehci_hcd and address 11
May 20 15:53:01 testuser kernel: [78051.314352] usb 2-6: USB disconnect, address 11
May 20 15:53:03 testuser kernel: [78053.264084] usb 2-6: new high speed USB device using ehci_hcd and address 12
May 20 15:53:11 testuser kernel: [78061.679975] usb 2-6: USB disconnect, address 12
May 20 17:47:55 testuser kernel: [84945.556083] usb 2-6: new high speed USB device using ehci_hcd and address 13
  

I'm sorry, I can't understand why there are so many connects and disconnects. Is the drive not plugged in properly?

---

### Post by linuxinstalledfromhdd on 2011-05-23
I just use Smart Disk Creator to format my usb drives when I purchase them new. Never have a problem using them in MAC, Win, or anything else again.  Works like charm.

---

### Post by Plumtreed on 2011-05-23
Wot, exactly, is 'Smart Disk Creator'?..........doesn't Google:(

---

### Post by nuffink666 on 2011-05-23
Smart Disk creator is a Ubuntu app off the system --- Admin menu and uis used for creating as it suggests a "bootable" device (normally USB but any hard disk format) that you then also choose your "loadable" CD or disk image, thus creating a bootable device with incorporated iso for instance....
 
from your log its your VirtualBox usb that is having the issue loading and unl;aoding by the looks, what version of VB are you using and have you ensured that you are running the right extensions as this stuff AFAIK contains all the USB bits and is relevant "apparently" tot the version of VB that you are running

---

### Post by Plumtreed on 2011-05-23
> **linuxinstalledfromhdd said:**
> I just use Smart Disk Creator to format my usb drives when I purchase them new. Never have a problem using them in MAC, Win, or anything else again.  Works like charm.

Is the Smart Disk Creator another name for the 'thing' that appears in 10.10's....System>Administration as Startup Disk Creator????????

....cos, if it is, I question it's ability to format over soft disk protection on USB drives!

OP may have a USB with so-called 'Lock Software' which is OK on Windows but is next impossible to remove once a reformat has been attempted.....some imation flash drives have this 'feature'.

---

### Post by teja483 on 2011-05-24
hii Mr.prshah...

thank you for ur support.....

i found that errors of USB is basically my kernel problem....

so i reinstalled ubuntu 10.10 .now its working fine.

i know this is not the propper solution..... but time facor made me to do that...


thank you again. for replying.

---


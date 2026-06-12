---
title: "Ubuntu does not boot up. Hung at purple screen five dots."
date: 2014-02-23
forum: Installation &amp; Upgrades
---

### Post by morningsunshine on 2014-02-23
Hi folks,

I am using Ubuntu 12.04 on MACbook Pro 5.3 hardware. It was working all fine but then the screen turned black and I waited and it wont turn back on. So I hard shut it down and started it again. Now it started the boot and purple screen with five dots came up. And it has been sitting there for a long time now.

I haven't installed any new software and OS updates either. There should be more than enough disk space available too.

Can someone please give pointers? help!

---

### Post by ubfan1 on 2014-02-23
Try typing Esc to switch to a text screen with progress/errors and  see where things stopped working.

---

### Post by morningsunshine on 2014-02-23
pressing Esc shows the boot screen with option to select from
Ubuntu, with Linux 3.5.0-45-generic
Ubuntu, with Linux 3.5.0-45-generic (recovery mode)
previous linux versions
memory test (memtest86+)
memory test (memtest86+, serial console 115200)

---

### Post by morningsunshine on 2014-02-23
Choosing any option does not go through and remains stuck on boot screen. I have tried using the option 'nomodeset' also but no use.

Any ideas please...

---

### Post by ubfan1 on 2014-02-23
Did you try the "previous linux versions" and select one of those?   Another thing to try is to edit the grub selection (type "e", instruction on screen), and type in a new line: set debug=1 then type Ctrl-x or F10 (whichever works) to boot and see if you get any more error messages. I'm not familiar with Macs, but I've never seen the boot process hang up after getting the grub menu up.

---

### Post by morningsunshine on 2014-02-23
Thanks for the reply. I did try booting previous versions. It still has no change.

I also triedsetting debug=1 n it does not show any messages. It just goes to the same purple boot screen with 5 dots all lit up.

---

### Post by morningsunshine on 2014-02-23
I tried another thing meanwhile.

I took out the disk and connected it as external disk. Booted via live cd and took the back up of data n home dir. Couldnt take back up of db though.

Is there anything I should check and update in this way to troubleshoot this problem?

---

### Post by ubfan1 on 2014-02-23
Maybe while running from the live CD, run a disk check on your root partition, and a memory check to see if that could be a problem.

---

### Post by morningsunshine on 2014-02-23
Thanks. I plugged the disk back in and ctrl alt + t jumped in to a terminal. I am looking at it showing startup boot messages now. 

It starts a few services
Apparmour
Lightdm
Bluetooth
Mdns
Network connection manager
Cups
Userspace bootsplash
Mysql server

All ok. Nothing after mysql server. And is just sitting there. The disk is running n no other message..

---

### Post by morningsunshine on 2014-02-23
Little correction:
Userspace bootsplash is STOPPING - [Ok]

---

### Post by morningsunshine on 2014-02-23
I now set debug=1 and booted the box. Pressed ctrl alt t. It shows 2 messgaes:

Plymouthd  Ok
Starting Postgresql 9.1 database server -> this is hung

---


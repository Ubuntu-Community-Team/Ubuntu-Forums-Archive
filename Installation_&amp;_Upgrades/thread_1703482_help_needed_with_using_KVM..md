---
title: "help needed with using KVM."
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by paulclark87 on 2011-03-09
Basically i have KVM up and running in ubuntu which the whole thing is running in vmware. However im trying to deploy virtual machines through virt-manager with KVM which is successfully running etc but when i actually go into the vm it gets stuck on booting up with error message,

Starting SeaBIOS (version 0.5.1-20100120_01601-rothera)

Booting from CD-Rom...
0MB medium detected
Boot failed:Could not read from CDROM (code 0007)
No bootable device.

Is this because the main vm that has KVM installed is also in a virtual machine and it cant see the CD Rom etc. It is virtual machines being hosted by a bigger virtual machine.

Any help appreciated

---

### Post by Kirboosy on 2011-03-09
Welcome to the Forums! :)


Are you sure that it is sharing the image with the VM that is trying to boot? 

> Booting from CD-Rom...
**0MB medium detected** [COLOR=Red]<--This concerns me[/COLOR]
Boot failed:Could not read from CDROM (code 0007)
No bootable device.


~Caboose

---

### Post by paulclark87 on 2011-03-09
in virt-manager im clicking new to deploy a new virtual machine. im picking the location of the iso of the os that im going to install. Also ubuntu just to make it easy. Gets through all the options about hard disk and ram space etc. It even deploys successfully.

However, when i open the deployed image it comes up the error message above.

---

### Post by Kirboosy on 2011-03-09
How do you have the HOST VM network settings configured?

---

### Post by paulclark87 on 2011-03-09
well i installed KVM and virt-manager without needing to specify anything. Virtual Manager then runs straight away. 

[IMG]file:///C:/Users/Paul/AppData/Local/Temp/moz-screenshot.png[/IMG][IMG]file:///C:/Users/Paul/AppData/Local/Temp/moz-screenshot-1.png[/IMG]I then have to areas 

localhost (QEMU Usermode)
localhost (Qemu)

---

### Post by Kirboosy on 2011-03-09
> **paulclark87 said:**
> well i installed KVM and virt-manager without needing to specify anything. Virtual Manager then runs straight away. 

[IMG]file:///C:/Users/Paul/AppData/Local/Temp/moz-screenshot.png[/IMG][IMG]file:///C:/Users/Paul/AppData/Local/Temp/moz-screenshot-1.png[/IMG]I then have to areas 

localhost (QEMU Usermode)
localhost (Qemu)

Try uploading your screenshots with the paperclip button.


I guess it is possible that it isn't working properly since its a VM in a VM. I've never tried that way so I can't say for sure.

---

### Post by paulclark87 on 2011-03-09
here are some screenshots

---

### Post by paulclark87 on 2011-03-09
Im definately thinking that my problem is based on trying to doing nested vms and its just not liking it reagrdless if i have it working or not.

Going to try doing it another way fingers crossed it works.

Watch this space

---

### Post by Kirboosy on 2011-03-09
Ok! Let me know how that goes for you. :)

---

### Post by paulclark87 on 2011-03-09
dont know if im having one of those days but ive just tried to install ubuntu as a dual boot and after a while the screen goes black and does nothing even teh disc stops spinning. 
 
So it picks up the disc, information comes up on the screen that ubuntu is going to install and when it hits the purple screen with ubuntu, thats when it goes black.
 
Anyone know whats causing this at all?
 
specs
intel core 2 duo P7450 @2.13Ghz 64bit
4Gb Ram
Nvidia GeForce GT 230M

---

### Post by Kirboosy on 2011-03-09
Do you have a thumbdrive handy? You could make a startup disk using [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/"). It will install faster this way too.

---


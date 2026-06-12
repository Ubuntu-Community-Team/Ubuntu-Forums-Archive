---
title: "Can't boot to live / installation (9.10 and 10.4)"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by nullkuhl on 2010-04-09
My notebook is an HP Envy 15 (Core i7 720QM, Intel DMI Host Bridge, PM55)

I have 2 ISO files, Ubuntu Karmic 9.10 and Ubuntu lucid lynx 10.04, both have correct md5sums, i burned each on cd's and flash usb disks ( using unetbootin and lili usb tool ).

However i never had a successful boot, i always reach : 
** (initramfs) :  Unable to find a medium containing a live file system.**

Bios of notebook has no settings to tweak regarding HDD

Could this be a sata issue anyway ?  I tried searching for this issue on the forums but all the posts were having burn problems, I also tried the flash usb disks on a desktop machine and they boot properly with no problem.

Please Help ! i cant install ubuntu :(

---

### Post by ssulaco on 2010-04-09
> **nullkuhl said:**
> Bios of notebook has no settings to tweak regarding HDD([COLOR="Red"][COLOR="Red"]you talking about boot sequence[/COLOR][/COLOR])

I also tried the flash usb disks on a desktop machine and they boot properly with no problem.
Please Help ! i cant install ubuntu :(
Could be boot sequence issue,bad rom drive,and/or bad burn...Ive never done a usb install,here is some info
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by nullkuhl on 2010-04-09
i have the same problem when booting from cd, its not a USB issue. :'(

---

### Post by ssulaco on 2010-04-09
You said usb boots properly?try the usb install

---

### Post by nullkuhl on 2010-04-09
> **ssulaco said:**
> You said usb boots properly?

usb and cd boots properly on a different machine, however on my notebook hp envy 15, both fails, ending up with the message i wrote above ^^ :(

---

### Post by ssulaco on 2010-04-09
sorry....Have you checked boot sequence

---

### Post by nullkuhl on 2010-04-09
> **ssulaco said:**
> sorry....Have you checked boot sequence

boot sequence ? what do you mean and also how to check it ?

---

### Post by ssulaco on 2010-04-09
read this.........[http://www.hiren.info/pages/bios-boot-cdrom](http://www.hiren.info/pages/bios-boot-cdrom)
and......[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

---

### Post by nullkuhl on 2010-04-09
> **ssulaco said:**
> read this.........[http://www.hiren.info/pages/bios-boot-cdrom](http://www.hiren.info/pages/bios-boot-cdrom)

yes yes sorry didnt get what you meant :), use i checked boot sequence and its booting from the usb/cd fine but an error happens, the one i wrote above ^^ !

---

### Post by ssulaco on 2010-04-09
Have you tried the Live (CD) on your desktop?

---

### Post by nullkuhl on 2010-04-09
> **ssulaco said:**
> Have you tried the Live (CD) on your desktop?

yes i tried cd and usb on desktop, both works fine !

---

### Post by ssulaco on 2010-04-09
do you have music cd to check to see if the rom drive is being seen?

---

### Post by nullkuhl on 2010-04-09
> **ssulaco said:**
> do you have music cd to check to see if the rom drive is being seen?

the rom drive is being seens because i can see the ubuntu boot menu list, however when i select try ubuntu without changes or install ubuntu it keeps booting but then i end up with the message i posted earlier !

---

### Post by ssulaco on 2010-04-09
same issue....
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/454158](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/454158)

Try burning Hardy......see what happens
[http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)

---

### Post by nullkuhl on 2010-04-09
> **ssulaco said:**
> same issue....
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/454158](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/454158)

Try burning Hardy......see what happens
[http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)

it's worse with hardy , i get a soft bug : cpu 7 stuck for 11s error, i think hardy do not support my core i7 processor

---

### Post by ssulaco on 2010-04-09
Try Jaunty.[http://releases.ubuntu.com/jaunty/](http://releases.ubuntu.com/jaunty/)
if that fails hopefully someone who has seen this will chime in.....goodluck.

Just for the heck of it did you try Hardy in your desktop?

---


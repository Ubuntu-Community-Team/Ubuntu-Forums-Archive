---
title: "Boot problem"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by spiRos21r on 2010-03-10
Hello,

I have a dual-boot partition on my HP Pavilion dv5 (Windows Vista and Ubuntu) for quite some time with no problems..

Yesterday I decided that it was a good time to upgrade Ubuntu to 9.10 and Grub to Grub2.. Everything went fine with the Ubuntu upgrade and grub seemed to be ok.. So I booted my Ubuntu partition and installed grub2 with "sudo apt-get install grub2" rebooted to my Ubuntu partition again and as everything seemed ok I did "sudo upgrade-from-grub-legacy".. Didn't notice this warning on the grub2 update instructions "NB! You have to use the spacebar to mark the choice here. DO NOT go on without doing this. It WILL result in your system showing error 15 and being unable to even show a boot menu. If you are running a dual boot system with WindowsXP or Vista, you might have to do additional fixes after upgrading to get it to work." so I get Grub Error 15 when i try to boot my laptop..

My problem is that I don't have a livecd and I only have access to my acer netbook(Windows XP) and my Lacie external HD.. So I tried to boot from my usb hd, downloaded unetbootin, installed the Ubuntu livecd on the usb hd, changed the bios setup to boot from usb but nothing happens.. Still Grub Error 15..

I wanted to see if the problem is on the HD or the laptop so I tried to boot from the external HD on my acer netbook.. That didn't work either so I suppose the problem is on my external HD(?) but that's just my guess.. Any help?

---

### Post by spiRos21r on 2010-03-10
Can anyone help? I really need my laptop today for a work project..

---

### Post by TeDiouS on 2010-03-11
Those are terrible.

Try downloading another iso, and if you have a usb thumb drive, try that instead, just in case.

If not, use your External HDD again, w/ the new iso.

I know someone knows a detailed solution.. yet no post.. :-k
[SIZE=1]*Maybe the list is too long and these get pushed down.. maybe.*[/SIZE]

As for the bios, I usually tell it to boot first from an "add-on card" so mine says. And if the external HD is turned on, plugged in. It will recognize it as one, and select it.
Also, make sure the system is to boot from USB first.

Hope that helps.

---


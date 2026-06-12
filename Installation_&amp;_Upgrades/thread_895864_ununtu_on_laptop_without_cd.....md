---
title: "ununtu on laptop without cd...."
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by Naytobe on 2008-08-20
hello all !

I have an old laptop toshiba satellite p4...or maybe p3..anywayz..the cd is busted. I have winXP installed on it and would like to load ubuntu into it...I have a 1go usb key...network..etc..

Is there a way for a newbie to achieve that ?? 

thanx

nay

---

### Post by nc_jed on 2008-08-20
Give this a try:  [http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/](http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/)

---

### Post by nc_jed on 2008-08-20
And welcome to Ubuntuville (notice that was your first post).

---

### Post by Naytobe on 2008-08-20
Wow Thanx for the fast reply !!!

Thnx for the link but if i understood properly, it will not install the os on my HD ? If thats the case, is there another way ? I would like to install it and erease XP !!! fedup with it !

thnx

Nay

---

### Post by tangibleorange on 2008-08-20
> **Naytobe said:**
> Wow Thanx for the fast reply !!!

Thnx for the link but if i understood properly, it will not install the os on my HD ? If thats the case, is there another way ? I would like to install it and erease XP !!! fedup with it !

thnx

Nay

as far as i understood the link, it will image your flash drive from the liveCD, so you can still use the install funciton as you would be able to from a proper CD. before you start, however, you should probably check that your BIOS supports boot from USB.

---

### Post by nc_jed on 2008-08-20
> **tangibleorange said:**
> as far as i understood the link, it will image your flash drive from the liveCD, so you can still use the install funciton as you would be able to from a proper CD. before you start, however, you should probably check that your BIOS supports boot from USB.

Yes, that was my intention (use the 'Install' facility once Ubuntu starts).  Sorry for my less than clear point on that, and thanks Tan for clearing that up.

Jed

---

### Post by Naytobe on 2008-08-21
Great !  I wanted to try that last night....lol my laptop gives me '' the blue screen of death '' lol can't boot from usb flash either...

any Ideas ? netinstall ?

nay

---

### Post by tangibleorange on 2008-08-21
> **Naytobe said:**
> Great !  I wanted to try that last night....lol my laptop gives me '' the blue screen of death '' lol can't boot from usb flash either...

any Ideas ? netinstall ?

nay

hmm i think you're struggling if you cant boot from HDD, USB or CD. There probably is a way to do it from a network, but its probably very complicated...

---

### Post by nc_jed on 2008-08-21
Bummer to hear about the no USB boot option.  There is (sort of) a network install option, but it is a little fringe ([http://mywheel.net/blog/index.php/ubuntu-network-install/](http://mywheel.net/blog/index.php/ubuntu-network-install/)).  

I was trying to cook up a way that Wubi (the Windows installer) could help, just I just don't think so.  Another thought for getting close, do you have a second (desktop/laptop) computer at home?  You could buy a 3.5" -> 2.5" IDE connector/converter for a few bucks.  Plug that into the desktop, plug the laptop drive into that, boot up with the Live CD, install from there.  after install, remove the laptop drive, reinsert into the laptop and boot it.  Obviously, there is different hardware in the 2 machines, so expect some reconfig.

---

### Post by DavidTangye on 2008-08-21
> **Naytobe said:**
> any Ideas ? netinstall ?The first section of [https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet) tells how to set up a netboot server first, then be able to install onto devices that have just a hard disk and network card that can be set to 'net'boot off.

---

### Post by Mister.Vash on 2008-08-22
You may want to take a look at this - 
[https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD](https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD)

and see if any of those option might do the trick

---

### Post by chris062689 on 2008-08-22
Use Ubuntu Eee's USB Creation Software.
You don't need to use an Ubuntu Eee ISO, any Linux-based ISO will do (tested with Ubuntu!)

Windows: [http://downloads.sourceforge.net/unetbootin/unetbootin-eeeubuntu-windows-238.exe?modtime=1214975248&big_mirror=0](http://downloads.sourceforge.net/unetbootin/unetbootin-eeeubuntu-windows-238.exe?modtime=1214975248&big_mirror=0)

Linux:  [http://downloads.sourceforge.net/unetbootin/unetbootin-eeeubuntu-linux-238?modtime=1214975255&big_mirror=0](http://downloads.sourceforge.net/unetbootin/unetbootin-eeeubuntu-linux-238?modtime=1214975255&big_mirror=0)

---


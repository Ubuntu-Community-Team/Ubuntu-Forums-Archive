---
title: "new install freezes when rebooting after first update"
date: 2017-08-31
forum: Installation &amp; Upgrades
---

### Post by kg0012 on 2017-08-31
I am trying to resurrect a Dell mini-1012 net book (useless running windows).
 I have loaded Lubuntu 17.04 & the live CD worked flawlessly except for the lack of WIFI drivers. & so did the installed version. All went well until I decided to check for updates. There was a huge backlog of updates > 50 MB. which I installed. Only to find that the computer would not boot after that. It was hanging as soon as it tried to load Lubunu. 
A new core core version came with the update so I tried booting with the old core version... & it still hung. Next I reinstalled lubuntu 17.04 & only loaded the security updates & a few others that looked necessary. Once more the updates killed the machine. 
Investigating further I found it was throwing up three error messages about the lack of firmware for the Wireless adapter but figured that should not have caused the hang. Next step was to try and boot with "nomodeset" in grub. Now able to see the startup splash I found the hang took place immediately after the message "*Listening on Load/Save RF Kill Switch Status /dev/rfkill/watch. Starting Load/Save RFKill Switch Status*". I then disabled WiFi & Bluetooth in the Bios. The boot process now went 3 lines further & ended with "*Created slice system-systemd\x2 backlight slice Starting Load/Save Backlight..es of leds:dell::kbd_backlight..*." at this stage I decided to drop back to the 16.04.2 LTS version as a safer option. 
It was the wrong move as nothing changed .... Live DVD excellent Freshly installed version also Excellent. after updating black screen of death same place same errors. #-o

I've given it my best shot.. has any one any ideas please? 
Lubuntu runs like a charm unupdated & I would like to keep it, and while there are other light distros out there The family is used to LDXE from the fleet of raspberry pi's around the house so lubuntu is a very good fit.

---

### Post by ajgreeny on 2017-08-31
It sounds as if this might be a kernel problem so I wonder if it's worth trying to install Lubuntu-16.04.1 which will run the 4.4.0-## series of kernels.

I am not sure what you mean by > A new core core version came with the update so I tried booting with the old core version... & it still hung.unless you are talking of a new kernel version in which case you can try booting from the old version by holding Shift at boot to get to the grub menu then choosing Advanced and try the old kernel version from that.

You can get the 16.04.1 iso file from [http://cdimages.ubuntu.com/lubuntu/releases/16.04.1/release/](http://cdimages.ubuntu.com/lubuntu/releases/16.04.1/release/)
Scroll down to the i386 or amd64 desktop version you need and give it a try.

---

### Post by kg0012 on 2017-09-01
Hi Thanks for the reply. 
Doesn't appear to be the Kernel version for two reasons. 
First, as long as I don't do the updates the machine will run like a dream for days on end.
Second, one of the first things I tried was to boot from the old kernel as you described, and absolutely nothing changed. Something in that huge wad of updates (83MB when I checked). Breaks Ubuntu on that machine. I reloaded 16.04.2 last night, did no updates, and it went through 8 reboots with out an issue then has run overnight under high load with no issues. However not loading security updates is too big a risk to my network. 
My Gut feeling is a system-d issue but that is probably because the change to system-d on the raspberry pi (Rasbian) caused me so much grief.

---

### Post by ajgreeny on 2017-09-01
I would still suggest you try the 16.04.1 point version as it is not only the kernel that was upgraded in the 16.04.2 version but also the xorg versions.

You do not say what the hardware actually is but I assume, being a Dell Mini netbook that it's probably a low powered Intel CPU (Atom?) using integrated Intel graphics.  I have an old re-badged MSI netbook of similar type which runs Lubuntu 16.04 installed from the original ISO, before even 16.04.1 appeared, and that runs very well for such an old low powered machine.

---

### Post by kg0012 on 2017-09-02
Hi thanks again for the reply. 
I will give 16.04.01 a go. It will be interesting to see what happens. 
You are right it is a typical Intel dual core Intel atom NM450 and NM110 chipset. One of three similar netbooks. I have been given after the owners discarded them because they ran so slowly,that they were next to useless. The other two were both HP's & have been happily running mint-mate for years now. with no issues including updates & upgrades. Although the lower spec one was a little slow with the mate desktop. Being almost identically spec'ed I expect this one would also struggle with the mate desktop. 

Cheers & I will let you know how it goes.

---

### Post by Boozin on 2018-01-28
Just wanted to say that the backlight disable bug workaround got my install to work on a dell mini 1012 as well.  


sudo systemctl mask [email]systemd-backlight@leds\:dell\:\:kbd_backlight.servic[/email]e

used this line and it booted fine.  Laptop works great again after a dist updated hosed it up for no reason.  did a fresh install and ran into the "second boot" hang up problem.  disabling the service fixed it.

---

### Post by predo86 on 2018-07-22
> **Boozin said:**
> Just wanted to say that the backlight disable bug workaround got my install to work on a dell mini 1012 as well.  


sudo systemctl mask [EMAIL="systemd-backlight@leds\:dell\:\:kbd_backlight.servic"]systemd-backlight@leds\:dell\:\:kbd_backlight.servic[/EMAIL]e

used this line and it booted fine.  Laptop works great again after a dist updated hosed it up for no reason.  did a fresh install and ran into the "second boot" hang up problem.  disabling the service fixed it.

I have the same problem with booting, but after entering the line in recovery root mod and restart the computer it's worked again!

Thanks Boozin!

---


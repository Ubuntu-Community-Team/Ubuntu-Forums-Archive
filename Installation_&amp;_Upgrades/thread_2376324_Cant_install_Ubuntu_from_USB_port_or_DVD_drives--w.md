---
title: "Cant install Ubuntu from USB port or DVD drives--whats next?"
date: 2017-11-01
forum: Installation &amp; Upgrades
---

### Post by inquiring2017 on 2017-11-01
I have a low end laptop with (2) USB ports and NO DVD drive. The laptop is pre-installed with WIN 10 (Yuck!). I want to remove WIN 10 and install Ubuntu desktop instead. The BIOS doesn't show any USB port to point to and there is no DVD drive from which to install a bootable Ubuntu version.

What other choices exist that will allow me to install Ubuntu onto the laptops's SSD 32 GB internal drive?

Thank you.

Jay

---

### Post by sudodus on 2017-11-01
Welcome to the Ubuntu Forums :-)

Please tell us more about what you have, what you have done and what you want.

Please specify your computer hardware

- Brand name and model
- CPU
- RAM (size)
- internal drive (size)
- graphics chip/card
- wifi chip/card
- CD drive (you have no DVD, but maybe a CD)

Software:

- Which version of Ubuntu are you trying to install?
- What is the name of the iso file, that you have downloaded?
- Have you checked with md5sum, that the download was successful? Or did you use the torrent method, that has a built-in check?

- Have you created a USB boot drive yet? In that case, how did you create it (which tool)?

---

### Post by oldfred on 2017-11-02
What brand/model laptop?
Some of these very lightweight systems were 64 bit, but used 32bit UEFI to make it Windows only like a iPad is Apple only.
And Linux did not have a 32 bit UEFI when those systems were designed. But it does now, but not in Ubuntu's standard configuration.
There are instructions on adding the 32 bit UEFI to Ubuntu.

Some also had the now obsolete Windows RT - Locked UEFI which is only Windows.

Often you have to turn off UEFI Secure Boot and turn on allow UEFI boot from USB ports. 
Have you updated UEFI. Some systems need updates.

---

### Post by ulysses77 on 2017-11-02
Take an Ubuntu bootable installation medium, make a blood sacrifice of whatever animal is the current version name, and place it in the middle of a giant Ubuntu circle with the laptop also within the circle, and chant:
"Sudo apt-get purge Windows 10!" (or whatever the overwritten OS would be) and "Sudo apt-get install Ubuntu!" It's thought that dancing around the circle whilst doing this speeds installation. After about 30 minutes (depending on your connection to the spirit world and how persistent you are, along with the make and model of the computer and the CPU speeds), lightning will flash or the lights will flicker and you'll hear the Ubuntu startup sound from 8.04 echo from all around you and the laptop will suddenly switch on with a complete installation of Ubuntu and a cup of coffee and a fresh chocolate chip cookie. 

...

Ok not really, but in Windows 10 if you have this issue, there are relevant settings under Windows 10's settings for "Advanced Startup Options". Look in your settings to see if it's there. If it is, there will be an option saying to reboot into a bootable medium such as a USB drive or CD drive (USB in this case). Whenever I couldn't find any other way of getting a system to boot off of another medium, I found that this is the way. Especially with HP Streams and the lower end Dells whose components are non-upgradeable. Try this method (not the first) and let me know how it turns out. If the Advanced Startup Options isn't in the settings, then typically you can find a way to do it from BIOS (in my experience).

---


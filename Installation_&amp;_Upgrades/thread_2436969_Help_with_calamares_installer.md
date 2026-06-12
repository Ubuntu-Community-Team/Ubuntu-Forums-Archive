---
title: "Help with calamares installer"
date: 2020-02-16
forum: Installation &amp; Upgrades
---

### Post by coley9225 on 2020-02-16
Let me start by saying  that I'm a noob. OK, a brief history of my situation. I fought with my computer since mid 2018 to install lubuntu 18.04. I finally got it in at the beginning of Feb this year(couple of weeks ago.The way I accomplished this was to run ubiquity -b from terminal to install without bootloader, then run bootrepair, After that I had to boot into os and purge and reinstall grub. Now, with that said, I'm having trouble installing lubuntu19.10 into my computer alongside lubuntu 18.04 and windows 10. I fear I my have to do like before. My question at this point is, can I make calamares install without boot loader like I did with ubiquity? I don't want to just upgrade my current install because I want to "test drive" the lxqt desktop before committing totally. My other thought is to do a new install of 18.04 where I want 19.10, then just upgrade that one, and I'll have all three os available. As always, any thoughts or tips will be greatly appreciated. As an off topic question, I see a lot of people with little quotes at the end of their posts. How do you do that? Is it something you have set to do automatically or do you type that in every time? Lol...just curious. Thanks

---

### Post by vidtek on 2020-02-16
> **coley9225 said:**
> Let me start by saying  that I'm a noob. OK, a brief history of my situation. I fought with my computer since mid 2018 to install lubuntu 18.04. I finally got it in at the beginning of Feb this year(couple of weeks ago.The way I accomplished this was to run ubiquity -b from terminal to install without bootloader, then run bootrepair, After that I had to boot into os and purge and reinstall grub. Now, with that said, I'm having trouble installing lubuntu19.10 into my computer alongside lubuntu 18.04 and windows 10. I fear I my have to do like before. My question at this point is, can I make calamares install without boot loader like I did with ubiquity? I don't want to just upgrade my current install because I want to "test drive" the lxqt desktop before committing totally. My other thought is to do a new install of 18.04 where I want 19.10, then just upgrade that one, and I'll have all three os available. As always, any thoughts or tips will be greatly appreciated. As an off topic question, I see a lot of people with little quotes at the end of their posts. How do you do that? Is it something you have set to do automatically or do you type that in every time? Lol...just curious. Thanks

Coley- Get yourself another SDD drive for your O/S.   I use 3 x 250gb, enough for Windows 10 Ubuntu and a decent sized /home

One is for day to day use as my main system, one is a clone of that for when I mess up, and one is for experimentation.  That way I don't have to worry about the WAF  (wife approval factor) of my HPTC.  The lovely Jane gets rather upset if she can't watch her films and tv shows.
 
Edit your signature for quotes, but instead of smart-a**s** quips, it's much more helpful to put your system's details in it and set the profile to show it in posts. see mine at the bottom.

Tony.

---

### Post by Dennis N on 2020-02-16
> My question at this point is, can I make calamares install without boot loader like I did with ubiquity?
Yes. There is a 'no bootloader' option at bottom of 'Partitions' screen. See the attached screenshot.

---

### Post by coley9225 on 2020-02-16
Thanks. I didn't notice the no bootloader option before. I was considering installing to external 250GB drive, but will bootrepair add a listing in my grub menu on internal  drive. I would like to boot as I do now, just with the third choice for 19.10. The problem with my computer is it chokes during grub install, hence the need to install without bootloader, and boot repair after. Can I install grub to external drive, and still have grub entry on internal drive? My end game is to find a distro I'm comfy with, and kick windows to the curb. If the grub is on the external drive, when I get to that point, a simple hdd swap and I have full linux install without the hassle of fresh install and reinstallinf all myy apps.
 And thanks for the tip on the quotes, I think I'll take your advice and put system specs there, so when I ask for help people know what I'm working with.

---

### Post by Dennis N on 2020-02-16
> I'm having trouble installing lubuntu19.10 into my computer alongside lubuntu 18.04 and windows 10.
In this case, you can use the 'no bootloader' option when installing Lubuntu 19.10, and then when finished, boot into Lubuntu 18.04 and run the command:
```
sudo update-grub
``` in the Lubuntu 18.04 terminal. That will scan the disk for other operating systems, find the new Lubuntu 19.10, and add a boot entry for Lubuntu 19.10 in the Lubuntu 18.04 grub menu. Using boot repair should not be necessary. I would stick with installing to the internal disk drive. 
 
FWIW, I had problems with Calamares installing grub in a UEFI system for Lubuntu back when they started using Calamares for Lubuntu 18.10. After several tries, I ended up installing on a BIOS-only computer instead. I do have a Lubuntu 19.10 currently installed, but it's in a virtual machine and is a BIOS install.

---

### Post by coley9225 on 2020-02-16
Thank you for the help, I now have 3 os to choose from. I still didn't find the no bootloader option, but got an error message about no partition flagged as efi/boot. It loaded without bootloadeer, and, as advised, I ran update-grub, and I am now in lubuntu 19.10. Learning lxqt over lxde is gonna take a while, but so did moving away from windows. Thanks again for the help, now I can mark this one solved.

---

### Post by guiverc on 2020-02-16
Just an FYI:

Are you aware of the lubuntu manual - [http://manual.lubuntu.me/](http://manual.lubuntu.me/)
(It's really good in my opinion, being started for the LXQt desktop)

You'll find other Lubuntu resources at the Lubuntu web site too - [https://lubuntu.me/](https://lubuntu.me/)

(be aware there are other unofficial sites that advertise Lubuntu, if unsure stick to ubuntu.com for direction, ie. go through [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours) )

---

### Post by Dennis N on 2020-02-16
> I still didn't find the no bootloader option, but got an error message about no partition flagged as efi/boot
You probably need to manually set the boot flag somewhere in the Calamares installer screens. I'm not sure where that is though. Fortunately, it completed the OS install, but did not install grub bootloader, which was the goal anyway. If it had installed the bootloader, it would have replaced your 18.04 boot loader.

The option to not install a bootloader might not be available for UEFI. My image is from the old BIOS install.

---


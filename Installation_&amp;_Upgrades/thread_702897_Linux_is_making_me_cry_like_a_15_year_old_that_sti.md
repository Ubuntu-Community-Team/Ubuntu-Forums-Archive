---
title: "Linux is making me cry like a 15 year old that still loses with hackmods"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by Gimpojones on 2008-02-20
I have a ASUS F3 Series F3SV-X4 NoteBook Intel Core 2 Duo T7500(2.20GHz) 15.4" Wide XGA 1GB 160GB DVD Super Multi NVIDIA GeForce 8600M GS - Retail

I've tried the alternate CD and i can get to a corrupted screen, with the asus logo as well as the ubuntu and a speckled box that i can move around the screen.

I downloaded some nvida drivers and 'attempted' to install them, but somehow i guess the internet isn't active in terminal?  I tried to use the ethernet, and well same problem.

Are there any know issues with this laptop and 7.10?  I'm tired of using vista and the ghetto version of beryl.

I've upgraded this machine to a 350g drive and 3gigs of ram.

it has
Intel Pro/wireless 3945abg
Attanr L1 gigabit ethernet

any ideas on getting this to work?  I've been reading that 7.10 apparently has some issues, would it be better for me to try another version?

thanks for the assistance in advance.

---

### Post by Pumalite on 2008-02-20
Download the 64 bit version from here and give it a try:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by overdrank on 2008-02-20
> **Gimpojones said:**
> I have a ASUS F3 Series F3SV-X4 NoteBook Intel Core 2 Duo T7500(2.20GHz) 15.4" Wide XGA 1GB 160GB DVD Super Multi NVIDIA GeForce 8600M GS - Retail

I've tried the alternate CD and i can get to a corrupted screen, with the asus logo as well as the ubuntu and a speckled box that i can move around the screen.

I downloaded some nvida drivers and 'attempted' to install them, but somehow i guess the internet isn't active in terminal?  I tried to use the ethernet, and well same problem.

Are there any know issues with this laptop and 7.10?  I'm tired of using vista and the ghetto version of beryl.

I've upgraded this machine to a 350g drive and 3gigs of ram.

it has
Intel Pro/wireless 3945abg
Attanr L1 gigabit ethernet

any ideas on getting this to work?  I've been reading that 7.10 apparently has some issues, would it be better for me to try another version?

thanks for the assistance in advance.

Hi and you have it installed with the alternate cd? If not, then try booting the alternate cd and You can try and reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash and and add vga=771  or 775 and then hit enter and then  b to boot. Hope this helps. Good luck!

---

### Post by Gimpojones on 2008-02-20
It's technically installed, Grub will let me choose vista or the 3 linux options.  when i choose the first linux option, the system takes a crap.  When i select the recovery mode, i can get to the terminal, but i cannot seem to connect to the internet when i'm trying to install the nvidia driver

---

### Post by overdrank on 2008-02-20
> **Gimpojones said:**
> It's technically installed, Grub will let me choose vista or the 3 linux options.  when i choose the first linux option, the system takes a crap.  When i select the recovery mode, i can get to the terminal, but i cannot seem to connect to the internet when i'm trying to install the nvidia driver

Ok in the recovery mode have you tried to reconfigure your xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then reboot with this command reboot. If this fails then use the configure command except without the -phigh tag and then choose the driver vesa

---


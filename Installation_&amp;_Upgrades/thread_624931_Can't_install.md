---
title: "Can't install"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by Cloaked on 2007-11-27
First off my apology's if this thread is a duplicate. I ran a couple searches and didn't come up with any answers.


Downloaded the ubuntu-7.10-desktop-amd64.iso file and burned to CD.
Popped it in and got up to the gui type screen. Hit enter on the default option (install).
Went to the loading screen and watched that for awhile, then a black screen with a cursor (little blinking flat line) at the upper right corner. After a min or two of that the following text appeared.

"[ 183.239166] hda: timeout waiting for DMA
[ 188.233102] hda: drive not ready for command"

15 secs later it came again..
"[ 249.400922] hda: timeout waiting for DMA  ect..."

It just keeps on repeating like that. The numbers change but it looks like they do so randomly. My best guess is they are HDD sectors.


Hardware:
CPU: Intel Core 2 Duo 2.4ghz
Mobo: ASUS P5N32-SLI SE Deluxe
Optical: HP|dvd840i
HDD: Two SATA (3gbs) 7200rpm 250gb Seagate Barracudas
RAM: 2gb 240pin Corsair XMS2 DDR2 (2x 1gb sticks)
Gphix Card: XFX Nvidia Geforce 7600GT :(My second one went bad a week ago)

One Hdd is ready to be formatted and have Ubuntu installed while the other has my XP Pro 64bit edition install on it as well as my data.


P.S.

I haven't been able to get any linux install to work yet on my 64bit intel >_<

---

### Post by leosan on 2007-11-27
hey hello, and also help

Got a sort of same problem here
downloaded the amd 64 ubuntu 7.10 iso, burnt it

With install and even in safe mode get a black screen.
and stays black

can it be that my graphics card is causing the problem?
got a nvidia 8800gts

thanks

---

### Post by BrianElliott0218 on 2007-11-27
Did you try booting to the live CD first instead of full install?
If so, and you are getting the errors, try booting to the Safe Graphics mode.  That may tell you the answer to your problem, or at least get you started in the right direction.

Nice system componants!  :-)

Good luck!
~BE:popcorn:

---

### Post by leosan on 2007-11-27
no thats the strange problem i got no errors
and safe goes also to a black screen and nothing else happens

will try tomorrow a other live cd of ubuntu

---

### Post by ghstwalker on 2007-11-28
I'm having the same problem with my p5n32-sli deluxe... 
i used the 7.10 64bit live-cd and 7.10 x86 live cd and get a blank screen continuously... 
used a 6.06 standard live-cd and got an error message about APIC...
with some help from the forums and searching i got the 6.06 live cd to boot, but with no hardware dectection and the screen was offcenter...
this is how i got it to boot:

at the boot option screen press F6
at the end of the line type
> noapic nolapic

If you can get this to work with 7.10 on either live-cd let me know
heres the links that helped me out 
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html]("http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html")
[URL="https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html"]
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html]("http://en.wikipedia.org/wiki/Intel_APIC_Architecture")[/URL]

---


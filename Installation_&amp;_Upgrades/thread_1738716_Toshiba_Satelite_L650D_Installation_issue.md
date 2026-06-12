---
title: "Toshiba Satelite L650D Installation issue"
date: 2011-04-25
forum: Installation &amp; Upgrades
---

### Post by borisagrees on 2011-04-25
Hi there these are my computer specs

AMD Turion II p520 Dual-Core Processor
RAM 4Gig
Motherboard Toshiba defult
Video ATI mobility radeon HD 5650

Currently i am trying to install ubuntu, i hyave tried with wubi and a live disc, i downloaded ubuntu 64BIT 10.10 as i am running windows seven 64 bit, When i go to install either way, or try ubuntu by the CD it just comes up with a blinking _ and doesnt do anything, i have tried all the options in the GRUB menu and the nomodest(i think) command line, nothing seems to work at all

What can i do, i want to swich from windows seven to ubuntu so bad, as i have used it as a part, but because i havent used linux a lot before can you please keep it simple

Cheers and thank you in advance :popcorn:

---

### Post by borisagrees on 2011-04-25
Update, Ok so i edited the normal mode of instalation by pressing shitft for grub and erasing the quiet splash command line and replacing it with nomodeset with the windows installed ubuntu, i had no graphical interphace just the flashing cursour, and it took around a half an hour to install, i only knew it was by my HDD light flashing the rest of the computer was inoperatable,

Now that it is installed it is doing the same thing, but no loading at all even with the same code that worked for the install, i am completely lost, i cant even test ubuntu off the live CD as it does the same as i would have tried to get a bootinfoscrit

it seems to hang on a PCI screen with SOMETHING like

pic connection (??)  [0000bfxx.******** stuff that i dont understand]

please i really want to fix this and use ubuntu any help is appreciated

---

### Post by dino99 on 2011-04-25
several things to test while booting:

- remove: quiet splash from boot line
- add either: noacpi, nolapic, noapic, irqpoll, nomodeset

as you dont say if its a fresh install or not, the blinking cursor cant be a weird xorg.conf issue:

sudo rm /etc/X11/xorg.conf

you can boot also in recovery mode and try: repair

---

### Post by bcbc on 2011-04-25
I seem to recall toshiba needs the boot option: acpi=copy_dsdt 

[https://bugs.launchpad.net/bugs/647358](https://bugs.launchpad.net/bugs/647358)

---

### Post by borisagrees on 2011-04-25
> **dino99 said:**
> several things to test while booting:

- remove: quiet splash from boot line
- add either: noacpi, nolapic, noapic, irqpoll, nomodeset

as you dont say if its a fresh install or not, the blinking cursor cant be a weird xorg.conf issue:

sudo rm /etc/X11/xorg.conf

you can boot also in recovery mode and try: repair

it is a fresh install, i have tried removing quiet splash and adding noacpi and nomodeset, anything else i could try?

it is a fresh install

what is the sudo command for?

how do i get into recoverymode?

it seems to be happening on the live version running straight off the linux disc to try ubuntu without anychanges to your computer

---

### Post by borisagrees on 2011-04-25
with the nomodeset command it seems to stop at

pci_root pnp0A08 :00: host bridge window [mcm 0xfed55000xffffffffffffff]

---

### Post by borisagrees on 2011-04-25
ok i tried the toshiba fix now it stops at

[0.173293] PCI : probing pci hardware

I cant get into ubuntu at all, ever since i have had the bloody thing it just keeps going with this damn cursor its driving me up the wall, and totally turning off ubuntu, why cant it just work??

---

### Post by bcbc on 2011-04-25
Make sure you update the BIOS as well if you don't have the latest version.

Also check the md5sum on your install medium.

---

### Post by borisagrees on 2011-04-25
Ok i shall update my bios, i might also wait for the new ubuntu to come out in two days then try again, as it may support my laptop better, your thoughts?

---

### Post by borisagrees on 2011-04-25
> **bcbc said:**
> Make sure you update the BIOS as well if you don't have the latest version.

Also check the md5sum on your install medium.

if it were the md5sum, then the ubuntu off the live disc would work wouldnt it?

---

### Post by Bucky Ball on 2011-04-25
Toshiba don't play nice with Linux but it can be done. You might get some clues here:

[http://ubuntuforums.org/showthread.php?t=1612648](http://ubuntuforums.org/showthread.php?t=1612648)

Mine is a different model but you might get some ideas. Good luck.

---

### Post by borisagrees on 2011-04-26
> **bcbc said:**
> Make sure you update the BIOS as well if you don't have the latest version.

Also check the md5sum on your install medium.

ok i have the latest bios and still no luck i am looking up how to check a md5sum on a install

---

### Post by batina on 2011-05-02
hi

i also have toshiba l650d and i'm stuck at the same flashing cursor/line... cant get it to work.:(

so, i tried 9.10 and it worked! i used noapic. didnt installed it, just tried from cd.

now, im gonna install 9.10, and try updating to 11.4... ill post how it went

---

### Post by batina on 2011-05-02
> **batina said:**
> hi

i also have toshiba l650d and i'm stuck at the same flashing cursor/line... cant get it to work.:(

so, i tried 9.10 and it worked! i used noapic. didnt installed it, just tried from cd.

now, im gonna install 9.10, and try updating to 11.4... ill post how it went

yeah, so 10.4 (lts) is the latest working edition on toshiba l650d... just tested it, and it works

---

### Post by Bucky Ball on 2011-05-02
> **batina said:**
> yeah, so 10.4 (lts) is the latest working edition on toshiba l650d... 

And the most stable. I'd stick with it. ;)

---

### Post by texas.chef94 on 2011-05-02
as an aside not related to this model, I have L675D that would not install 10.19 under any circumstances but did allow 10.04. I also wanted SUSE 11.3 and only way I discovered install would work was aspc=off
Had I know Toshiba's Linux limitations I would have stuck with HP
Cheers

---

### Post by Bozox on 2011-07-06
I have been able to install Ubuntu on my Toasiba satellite L650D*

Ubuntu 10.04  10.10 and 11.04
On the purple screen press any key
Press F6
Press escape
now press Tab and add
pcie_aspm=off
Hit enter and be patient
 
Run live cd, then install from the desktop.
But before you reboot:
Open terminal window and type:
sudo gedit 
Edit the file /etc/default/grub    insert pcie_aspm=off      as boot option like this:

GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash pcie_aspm=off&#8221;

save and recompile grub.cfg with the command:

sudo update-grub

Good luck.

This works on openSuse 11.4 also

---


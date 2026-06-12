---
title: "installation saga"
date: 2014-11-10
forum: Installation &amp; Upgrades
---

### Post by bjh6 on 2014-11-10
I have an old Sony Vaio VGN-FJ1S (Pentium M740 1.73GHz, 1GB Ram) running Windows XP. I decided to install Ubuntu on it. First I created a 25G of space by contracting the existing XP partition. I then began to install Ubuntu 14.04.

First problem - the installation process simply hanged. I found that it was necessary to specify ACPI=off; then when installation was complete, 
there was no wireless network; I found that IRQPOLL would fix this.

Once the system was up and running it was exceedingly slow because the latest Unity insists (apparently) on expanding/contracting windows, 
rather than simply opening them. Problem solved with Gnome!

However, the system would not power down - I was forced to use the brute force hold-down-power-key-for-6-seconds.

So I decided to scrap the install, start from scratch, and install 12.04 instead.

BUT 12.04 would not install at all - the install process crashed with an error message just after it offered to take a photo or allow selection 
of an image to represent the user!

SO, I thought, perhaps 10.04 would be better and I again removed the installation, downloaded 10.04 and, to my delight, the installation 
process went smoothly, wireless and power-off worked without any need for special settings.The one hiccough was that during the installation a
 dialog box appeared - it looked like some sort of error message, but the text seemed to have been presented in some unsupported language - 
each character appeared as a small empty box. This seemed to make no difference to the overall performance of the system.

My next thought was 'WIll it upgrade to 12.04?'; this was offered by Update Manager, so I took up the offer. All went well and 12.04 now 
worked fine.

Update Manager now offered upgrade to 14.04, so I took up the offer, and the upgrade process succeeded, BUT the system would not then reboot!

I then repeated the 10.04 installation, upgraded to 12.04 and do not plan to upgrade to 14.04 unless i can find out exactly what changed 
between 12.04 and 14.04 to make for this unfortunate state of affairs!

---

### Post by sammiev on 2014-11-10
On a computer like yours I would have tried 12.04 with Lubuntu or Xubuntu with xfce. They require less resources than Gnome or Unity. Glad you have it working. :)

---

### Post by bapoumba on 2014-11-10
I have a vaio VGN-C2S, Intel Core 2 Duo 1.66GHz, 1GB ram from 2006 or something and I know I can forget running Ubuntu with unity on it. lubuntu works very well. 14.10 currently.

---

### Post by ian-weisser on 2014-11-10
Your description "it would not reboot" is unclear. It could mean a lot of symptoms.

12.04 wouldn't halt?
BIOS couldn't find the GRUB bootloader?
GRUB couldn't load the system?
The disk wouldn't remount rw?
The login screen froze?

We can probably help you with a bit more detail...

---

### Post by bjh6 on 2014-11-11
Sorry, ian-weisser, I was unclear! After installing 14.04, the machine shutdown, then restarted, but froze part way through - well before any login screen! My guess was that the same settings were needed (viz ACPI=off and IRQPOLL), but by that stage I wasn't prepared to spend more time playing with those settings only to find that brute force power-off was again required!

---

### Post by ian-weisser on 2014-11-11
Froze before seeing the manufacturer logo / POST screen? (BIOS problem)
Froze after the manufacturer logo, but before the GRUB screen?
Froze during the GRUB screen?
Froze after the GRUB screen but before the Ubuntu splash screen?
Froze during the Ubuntu splash screen?

---

### Post by bjh6 on 2014-11-14
Thanks, ian-weisser, for continued interest.

The freeze takes place during the Ubuntu splash screen; I have tried again and discovered (a) that acpi=off and irqpoll are needed when upgrading as well as on clean install. It sems that something changes betwee 12.04 and 14.04 which causes this machine to work less well than previously. I also tried booting on the second item on the grub screen - diagnostic boot or similar. This froze after a  reference to jog dial. This particular machine never had a jog dial - a feature of somewhat older Sony's!

---

### Post by ian-weisser on 2014-11-14
Can you boot from a LiveUSB or LiveCD?
Is your goal still to restore a working 12.04 install?

---

### Post by bjh6 on 2014-11-19
LiveCD has the same problem - will freeze unless I specify acpi=off, will not recognise wireless unless i also specify irqpoll. 10.04 had none of these problems and 12.04 is fine if I upgrade from 10.04.

I have a working 12.04 system because I re-installed from 10.04, then upgraded to 12.04.

Thanks for the interest - it seems that out-of-the-box 14.04 is not compatible with my hardware; as it is old, I can understand that things have moved on!

---

### Post by mastablasta on 2014-11-19
because acpi= off you have the shutdown issue I believe. you can try shutting it down via terminal and see if there are any errors.

for example

```
sudo shutdown -h now
```

if this works you could change the shutwodn command to do just that.

otherwise the 12.04 had unity 2D, while all later version 3D only. in simpler terms computer needs good GPU in order to have these new desktops (Unity, Gnome3, KDE) run fast and fluent.

For older computer it is best to use desktops that do not need graphics acceleration to draw windows. such are XFCE (found in Xubuntu) and LXDE or LXQT (found in Lubuntu) another one that is preety fast and based on old Gnome 2 is Mate desktop (found in Linux Mint Mate or Ubuntu mate). it would look like 10.04 version. there are also only windows managers which are even less resource consuming. 

I can't say what causes the other issues. but just so you know the install is possible using textmode. might not look so well but gives a lot more data on what went wrong if anything goes wrong.

---


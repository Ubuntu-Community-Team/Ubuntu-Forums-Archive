---
title: "GRUB RESCUE Problem"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by dayobiz on 2010-03-19
I can't boot from USB or CD (checked the BIOS settings, checked the [URL="http://www.linuxquestions.org/questions/#"][COLOR=blue][COLOR=blue! important][FONT=Verdana][COLOR=blue! important][FONT=Verdana]hardware[/FONT][/COLOR][/FONT][/COLOR][/COLOR] [IMG]http://kona.kontera.com/javascript/lib/imgs/grey_loader.gif[/IMG]
[/URL]connections, tried multiple CD's and [URL="http://www.linuxquestions.org/questions/#"][COLOR=blue][COLOR=blue! important][FONT=Verdana][COLOR=blue! important][FONT=Verdana]flash [/FONT][/COLOR][COLOR=blue! important][FONT=Verdana]drives[/FONT][/COLOR][/FONT][/COLOR][/COLOR] [IMG]http://kona.kontera.com/javascript/lib/imgs/grey_loader.gif[/IMG]
[/URL]), and my linux box is stuck on GRUB Rescue mode because I deleted the partition with the boot program on it. Is there any way I can wipe out my [URL="http://www.linuxquestions.org/questions/#"][COLOR=blue][COLOR=blue! important][FONT=Verdana][COLOR=blue! important][FONT=Verdana]hard [/FONT][/COLOR][COLOR=blue! important][FONT=Verdana]drive[/FONT][/COLOR][/FONT][/COLOR][/COLOR] [IMG]http://kona.kontera.com/javascript/lib/imgs/grey_loader.gif[/IMG]
[/URL]so I can boot fresh off a CD or USB? I've posted this before but I'm posting again with different wording with hopes of coming up with a solution.

---

### Post by phillw on 2010-03-19
If your BIOS settings are correct, and set to look at CD and USB before your hard-drive, I think you have a problem with the way you are burning either the CD or making a boot usb stick.

As I don't know which OS you're using to burn the CD's, I've summarised the iso-burning community document and split it by OS. You can access it via my Signature, or directly here --> [http://forum.phillw.net/viewtopic.php?f=4&t=36](http://forum.phillw.net/viewtopic.php?f=4&t=36)

If you follow that, you will have a working LiveCD. Just an additional note, some CD-R drives are not too good at burning for other machines, you may want to try a friends computer for burning a CD if you are still not having any success.

For USB sticks, from the LiveCD you can create a usb startup disk.

Either way, you want to test your boot media on another computer to ensure it is working, that way you will know it is a problem on your computer. Rescuing Grub requires the use of a startup disk, once you can boot via CD or USB putting on a kernel can be done via this 'How-To' --> [http://forum.phillw.net/viewtopic.php?f=4&t=35](http://forum.phillw.net/viewtopic.php?f=4&t=35)

Regards,

Phill.

---


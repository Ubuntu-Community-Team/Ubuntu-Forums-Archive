---
title: "Ubutnu Server 6.06 install wireless"
date: 2007-07-10
forum: Installation &amp; Upgrades
---

### Post by Stegga on 2007-07-10
I have formatted a computer and installed Ubuntu 6.06 server WITH THE WIRELESS CARD in the machine, as well as a USRobotics external fax modem (for fax server) and during install it said that it had found 2 interface thingy's ,and I chose the wireless (ath0 - I think it was) connection and it seemed to take all the ESSID, Wireless Network name and WEP key in but I know have a cursor blinkign at me and no wireless connection!

Where do I start it trying to see if the wireless card has been installed correctly. I typed in ping 196.7.0.132 to see if I had a connection with the wrieless entwrok, and it came back with some error (You may have guessed it that I am not at that computer anymore)

Please help if you can.

Thanks,
Andrew

---

### Post by az on 2007-07-10
Depending on what wireless device it is, you may need to use the generic (desktop) kernel.  The server kernel is not built for a lot of desktop hardware.

If you can connect to the net in some other way, run

sudo apt-get install linux-generic

The installer boots the generic kernel, but will put the server kernel on your system, which may be why the wireless device was detected while installing but not now, after you have rebooted into the server kernel.

---


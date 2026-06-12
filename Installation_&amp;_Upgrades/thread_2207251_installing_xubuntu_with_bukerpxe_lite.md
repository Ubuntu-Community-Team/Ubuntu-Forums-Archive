---
title: "installing xubuntu with bukerpxe lite"
date: 2014-02-22
forum: Installation &amp; Upgrades
---

### Post by xforxprefectx on 2014-02-22
hello world.

i am in a bit self inflicted trouble. i crashed my xubuntu system during an update and now i only have a smartfone with android and my broken samsung ultrabook to work with. i live in the jungle and the computer refuses to boot from any usb drive so there are really no other option than to use whats availible out here.
i am just a happy and little experienced ubuntu user and i dont know what to do now. research is pretty much impossible out here since a 14.4 analog modem would be a huge improvement to the availible intsrnet bandwidth.
this is what i have:
android smartfone
xubuntu 13.10 64 bit iso file on a micro sd card
samsung series  9 ultrabook
tp link router that connects fone and computer through wifi.
buker pxe liteand servers ultimate installed  on the fone.

i can download additional software if needed. its just a few hours by boat to get to the next 1 mbit wifi hotspot.

please held me if you can the laptop is my only big piece of civilisation comfort out here.

thx alot yas

---

### Post by erind on 2014-02-24
Can you boot directly into the UEFI bios ? If so:

 - does it detect the Micro SD card ?
 - can you change the boot order while in Bios, so the SD card is the first to boot ?

If none of the above is possible, given your location, there's really not much that you can do, short of finding/ borrowing just a plain old USB thumb drive with any Live OS on it ... There's also the 'install over network' option, but I'm not familiar with that one and it could have its own set of requirements/issues as well, so IMHO your best bet is to find/use any bootable USB device. 
Best of luck !!

---

### Post by xforxprefectx on 2014-02-25
hi there.
thanks for the reply but there is a missunderstanding. this computer WILL NOT boot from any usb flash device, sd card or whatever you can think of. booting any os is only possible though the network via pxe. the micro sd card is in the smartfone the bios itself looks like a classic bios. it says on top of the screen  phoenix securecore tiano setup. in the boot section the uefi bios support is activated, but i dont know if this is only a simulation for some uefi features or if it acually means its a uefi bios.so its still the only option to figure out how to configure my fone as a pxe server.

cheers

---

### Post by erind on 2014-02-25
OK thanks for clearing that up. Now, as I said above I have zero experience with the network install, or how to configure your phone as PXE server for that matter. 

A quick look of phoenix securecore tiano setup shows that it is UEFI. From:

[https://www.phoenix.com/pages/phoenix-securecore-tiano-tm](https://www.phoenix.com/pages/phoenix-securecore-tiano-tm)
> Phoenix SecureCore Technology 2.x or SecureCore Technology Enhanced is our flagship UEFI product. SecureCore Technology 2.x is fully compliant with UEFI 2.0 and rigidly adheres to requirements set by Intel MPG (EDK1117 with patches and successors).

Even though you had Xubuntu in this laptop, I'd make sure that "Legacy Mode" is enabled in your laptop's UEFI ("Secure Boot" disabled), before trying  any kind of install. Different manufacturers use slightly different terms for their UEFI "Legacy Mode", so you got to dig in your UEFI to find the respective terms used. From this thread (contains two big JPEG images):
[URL="https://forum.ts.fujitsu.com/forum/viewtopic.php?f=95&t=46061"]
https://forum.ts.fujitsu.com/forum/viewtopic.php?f=95&t=46061[/URL]

> 
- Advanced &#8211; Boot Configurations &#8211; Fast Boot : [Disabled]
- Advanced &#8211; Boot Configurations &#8211; CSM : [Enabled]
- Security &#8211; Secure Boot Configuration &#8211; Secure Boot Option : [Disabled]

You can only make changes to the secure boot settings once a supervisor has been configured.

Having this UEFI thing in the middle, makes installing other OSs that more complex/ difficult. In the meantime take a look at this (low bandwidth/ text only) site on how to set up the PXE server, and wait for somebody more knowledgeable than me to guide you further.

[http://www.debian-administration.org/articles/478](http://www.debian-administration.org/articles/478)

---


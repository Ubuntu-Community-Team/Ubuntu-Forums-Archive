---
title: "Booting from flash drive or SD card"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by RastaCalavera on 2010-03-01
Hey guys,

So I am at my wits end trying to figure out why this won't work. I am trying to install ubuntu 9.10 on my netbook (I hear it runs better than remix) but an running into a wall. I am already using Jolicloud as my main os on my main partition. I have used Unetbootin to get the 9.10 iso on my re-movable media. I have gone into the bios and chose to have it look at the re-movable first, then my 1st partition on the HD. For some reason it never looks at the USB drive. I have disabled everything on boot except for the media and i get a screen that says "insert bootable media or restart" then i have to go back into bios and enable the HD again. 

Side note, the media I am using might not be in fat 32 because I haven't figured out how to format in linux but, I have formatted in windows so that it is fat 32 and got the same problem. Ideas? THANKS!!!

---

### Post by masteross on 2010-03-01
All you need is Universal usb installer
at [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
and ask your computer to boot from usb flash

you don't need any cd/dvd drive

i hope i help you

---

### Post by C.S.Cameron on 2010-03-01
You did not say what make of netbook you have however you might try selecting your flash drive as first hard drive in BIOS and see if that works.

---

### Post by efflandt on 2010-03-02
If you have a computer you can access with CD drive, you can use the USB Startup Disk Creator from the Ubuntu live/install CD to create a bootable USB.  That works with SD, but it has to be in a USB card reader.  I even installed that on 2 GB bootable microSD (a complete OS the size of your little fingernail).

But if you are trying to boot from an SD slot in the computer, that might or might not work depending upon how that is tied to the computer.  That works on my desktop where the card reader is internally connected to USB.  But it does not work for the SD slot in my laptop, because that is a different type of block device that it will not boot from (even the same SD card that works in an external USB card reader)

---

### Post by RastaCalavera on 2010-03-02
I have changed the options in my bios menu to look at an external drive first before booting off the HD. I created a bootable USB drive with live 9.10 on it and tested it on my other computer. It worked fine. I am using an  Eee PC 1005HA. I have located other people who encountered this problem but all of them were able to make it work after using either the left port USB drive or changed their bios (BOTH OF WHICH I HAVE DONE). I have even disabled booting from the HD all together and just had it look for a USB device but i get a screen that says insert bootable media and press any key or restart to reconfigure.

---

### Post by RastaCalavera on 2010-03-02
So i just found this on the Ubuntu website:

Some BIOS's (eg., Eee PC) have trouble recognizing that the USB is bootable. You may have to trick it into booting using the following method. At boot, enter the BIOS. Then, right as you exit the BIOS, hit the Esc key. For some systems, this will bring up the boot menu. 
 
[B][SIZE=2][FONT=Arial] this applies to me so I will give it a try. (my font changed for some reason after pasting paragraph and I couldn't change it back lol)[/FONT][/SIZE]
[/B]

---

### Post by RastaCalavera on 2010-03-02
> **RastaCalavera said:**
> So i just found this on the Ubuntu website:

Some BIOS's (eg., Eee PC) have trouble recognizing that the USB is bootable. You may have to trick it into booting using the following method. At boot, enter the BIOS. Then, right as you exit the BIOS, hit the Esc key. For some systems, this will bring up the boot menu. 
 
[B][SIZE=2][FONT=Arial] this applies to me so I will give it a try. (my font changed for some reason after pasting paragraph and I couldn't change it back lol)[/FONT][/SIZE]
[/B]


Hitting esc worked!! I am now typing this using the live 9.10 on my flash drive. Big note for anyone using Eee PC, HIT ESC after exiting boot menu. Thanks for you thoughts and advice everyone!!! :)

---


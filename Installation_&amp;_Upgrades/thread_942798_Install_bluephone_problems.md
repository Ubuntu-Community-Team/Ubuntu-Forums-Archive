---
title: "Install bluephone problems"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by gh0ti on 2008-10-09
hi I am trying to install [COLOR="Blue"]_[bluephone]("http://www.linuxsoft.cz/en/sw_detail.php?id_item=7156")_[/COLOR]

but when i try to make I get the following error.

> main.c:27:27: error: openobex/obex.h: No such file or directory
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/martin/Desktop/bluephone-0.2/bluephone-0.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/martin/Desktop/bluephone-0.2/bluephone-0.2'
make: *** [all] Error 2


---

### Post by nymusicman on 2009-01-21
I have good news and bad news. The good news is the package you need is libopenobex1-dev

The bad news is when I was done, I got a segmentation fault. Good luck.

---

### Post by Stashell on 2010-07-02
I know is a very late reply but I just got into this issue today triying to find a bluetooth program to manage my cellpone so if anywone as this problem don't give up on the segmentation error message, it actually happens because the application is not run correctly

Do the following 

Before running BluePhone make your phone discoverable 

open a terminal window and type

    $ hcitool scan

 write down the Bluetooth address of your phone it should be in the form 00:00:00:00:00:00 then type

    $ sdptool browse 00:00:00:00:00:00

where 00:00:00:00:00:00 is the Bluetooth address you just obtained for your
phone. Look for the entry of the form below and note down the channel
number.

    Service Name: Serial Port 1
    Service RecHandle: 0x10003
    Service Class ID List:
      "Serial Port" (0x1101)
      Protocol Descriptor List:
        "L2CAP" (0x0100)
          "RFCOMM" (0x0003)
              Channel: 4

The first time that you run BluePhone you need to specify the device
address and RFCOMM channel at the command line.

    $ bluephone --address=00:00:00:00:00:00 --rfcomm=4

you will then see the bluephone icon appear on the system tray
hope it helps

---


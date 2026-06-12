---
title: "USB ADSL Modem Manager not working"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by FreewheelinFrank on 2007-10-18
Steven Harper's USB ADSL Modem manager is not working after upgrading to 7.10.

This was the only way I could connect to the internet in Ubuntu.

The thread in the Dev Link Forum is now closed.

Does anybody have any advice about how to get a connection back?

---

### Post by Bumblebum on 2007-10-18
I have exactly the same problem as you, so if anyone gets it working please post how in this post :-)

I have also tried using a program called UbuDsl which seems to do the same sort of thing but it didn't work for me, but you can try it from [http://ubudsl.ubuntu.pl/index_en.html](http://ubudsl.ubuntu.pl/index_en.html)

Looks like i'm going back to feisty until USB ADSL Modem Manager works.

---

### Post by redwinder on 2007-10-19
> **FreewheelinFrank said:**
> Steven Harper's USB ADSL Modem manager is not working after upgrading to 7.10.

This was the only way I could connect to the internet in Ubuntu.

The thread in the Dev Link Forum is now closed.

Does anybody have any advice about how to get a connection back?

damn is the same for me, it doesn`t even start to authenticate,come on steve harper fix it please! :(

---

### Post by FreewheelinFrank on 2007-10-20
Bump.

Second day of Ubuntu 7.10.

And second day of no choice but to boot into Windows.

---

### Post by Glugglug on 2007-10-21
I have tried both of these and can't get them to work there is a Ubuntu help page that gives instructions on how to download the firmware and split it in to 2 bins and how to set up a working folder  but  I didn't get very far with it .  would I be right in thinking that the two programs USB modem manager  and ubudsl are based on the same set of instructions so if I did continue with the help page that probably wouldn't work either.

---

### Post by StevenHarper on 2007-10-21
Hi, I have just found this thread.

I have fixed the Modem Manager, the problem is in the Detection code to find the modem, a change in USB handling has broken is : Have no fear I have fixed it and made and Tested the build.

I also Have switched to a nicer TrayIcon (the standard GTK one) this positions the Drop down menu better.

so....

**0.5.5 is now ready for 32bit Ubuntu**

New Features are

    * New Tray Icon
    * Fixed Modem Detection bug : was a show stopper in Gutsy 

Download Location is
[http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/](http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/)

Please send me feedback : including if it works (I have tested it) 

Steve

---

### Post by pathum on 2008-01-01
Bro I've tried ur app n it didn't work for me.... i have a ZTE ZXDSL 852 USB Modem which i guess is the reason for it to not work for me...I use Feisty 7.04 and is totally cut off from the net... I'd be grateful if u could include support for my kinda modems as almost all of us in my country use the same type of modems...

Tnks

---

### Post by adrian5632 on 2008-01-21
Try the new version of UbuDSL (download the 0.9.4 version) from ttp://sourceforge.net/projects/ubudsl - it has improved support for ZXDSL.

---

### Post by pathum on 2008-05-18
> **StevenHarper said:**
> Hi, I have just found this thread.

I have fixed the Modem Manager, the problem is in the Detection code to find the modem, a change in USB handling has broken is : Have no fear I have fixed it and made and Tested the build.

I also Have switched to a nicer TrayIcon (the standard GTK one) this positions the Drop down menu better.

so....

**0.5.5 is now ready for 32bit Ubuntu**

New Features are

    * New Tray Icon
    * Fixed Modem Detection bug : was a show stopper in Gutsy 

Download Location is
[http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/](http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/)

Please send me feedback : including if it works (I have tested it) 

Steve

Steve, will your new version work for ZTE ZXDSL852 USB modem?

And Adrian, i tried the Alpha 2 version of UBUDSL....the modem GETS DETECTED but FAILS to CONNECT...SAYS "Connection Timed out, Service Provider Not Responding"

Any Idea why?

---


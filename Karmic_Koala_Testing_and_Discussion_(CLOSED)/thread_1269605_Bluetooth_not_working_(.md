---
title: "Bluetooth not working :("
date: 2009-09-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tretle on 2009-09-18
My bluetooth adapter doesn't seem to be recognized anymore, anyone else having this issue?

---

### Post by hapee on 2009-09-18
I had this a first time after I rebooted the system, than I plugged the devices in again, rebooted the system en since than all back to normal.

---

### Post by Diggs808 on 2009-09-18
Internal Bluetooth card here.  So I cannot easily plug and unplug the adapter.  It does not detect my card.

---

### Post by tretle on 2009-09-18
thank god its not just me :)

---

### Post by Vanishing on 2009-09-18
> **tretle said:**
> thank god its not just me :)

offtopic:
as the alpha testing note indicates:
when something bad happened, it most likely did not just happen to you...
though i dont use bluetooth.:)

---

### Post by tretle on 2009-09-18
It happened at the worst time, wanted to check to see if I could use my bluetooth headset with empathy :(

---

### Post by theo2881 on 2009-09-18
My adapter also is not being shown in bluetooth settings, however it shows up in the terminal under lsusb command.

---

### Post by jwssr on 2009-09-18
There is a better alternative to gnome bt...

It is blueman.

To Install Blueman in Ubuntu......

Go to System—>Administration—>Software—>Sources.Now click on Third-Party Software tab, Click on add one of the following sourcelist which is suitable for you

For Ubuntu Jaunty (9.04) Users..change the word jaunty to karmic..but not necessary.

OR

just add this entry at the end of   /etc/apt/sources.list.

    deb [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) jaunty main 

here is link to key..
[http://keyserver.ubuntu.com:11371/pks/lookup?search=0x947C4F7371932C794B153F0F6B15AB91951DC1E2&op=index](http://keyserver.ubuntu.com:11371/pks/lookup?search=0x947C4F7371932C794B153F0F6B15AB91951DC1E2&op=index)

apt-get update
apt-get install blueman

I have used bt on ubuntu for 4 cycles now...and have used bluez..up until recently..when it was dropped for gnome bt and blueman.  at present, you can have both installed at same time and use at same time also.

I have 2 usb bt adapters plugged in and blueman sees both and lets me use both.  I have a mot s305 stereo headset and only blueman lets me use a2dp services..not avail in gnome bt.

there is alot of info on the forums about blueman vs gnome bt...just  google ubuntu blueman..

here is a link of good info
[http://www.ubuntugeek.com/blueman-bluetooth-manager-for-ubuntu.html#more-960](http://www.ubuntugeek.com/blueman-bluetooth-manager-for-ubuntu.html#more-960)

good luck

---


---
title: "Bluetooth missing in Intrepid?"
date: 2008-10-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by isecore on 2008-10-29
After upgrading to Intrepid from Hardy bluetooth no longer works. If I tickle it with a sudo /etc/init.d/bluetooth restart the icon appears but is non-functional. Cannot set the name of my device, can't send files, can't receive files. Nada.

Anyone know anything about this? I filed [a bugreport on Launchpad]("https://bugs.launchpad.net/ubuntu/+bug/289836")but it's seen very little action or response. There's also [another thread]("http://ubuntuforums.org/showthread.php?t=858463") on the forums about this, but there's been no responses for four days and we're getting close to launch soon.

I'm running Intrepid x64, all patched up as of the 29th.

---

### Post by fabertawe on 2008-10-29
I had to install 'gnome-bluetooth' to get 'gnome-obex-server'. Here are the contents of a little script I run when I want to use bluetooth...
```
#!/bin/sh
sudo /etc/init.d/bluetooth restart
wait 5
bluetooth-applet&
gnome-obex-server
sudo /etc/init.d/bluetooth stop
```
I can't remember why I put the 'wait' in, it's probably not necessary.

---

### Post by oniichan on 2008-10-29
An Intrepid update a few days ago broke bluetooth completely. I fixed it by completely removing bluetooth and bluez. After a clean re-install everything worked fine. Even after today's incremental Intrepid updates.

---

### Post by _oOMOo_ on 2008-10-29
The bluetooth adapter I used to use no longer works in Intrepid. I filed a bug - [https://bugs.launchpad.net/bugs/268502]("https://bugs.launchpad.net/bugs/268502")

I bought a new adapter and it works. Still no "services" tab under bluetooth preferences - and my phone only reports a network service available. Is there a quick way to enable the other services?

Cheers

---

### Post by isecore on 2008-10-29
I tried purging everything related to bluetooth and then reinstall it. No dice. Same thing - I get a bluetooth-icon in the tray but it's a dud and non-functional.

---

### Post by aka_butters on 2008-10-29
I have been experiencing the same issues.  With 8.04 I was able to send and receive files between my phone and laptop.  It seems as if my bluetooth adapter is still fully supported because i was able to receive a file after installing the gnome-obex-server, but I never needed that before.  Also I can no longer push to my phone because it says that OBEX Push is not supported.  This seems very backwards for ubuntu especially after saying that there would be increased bluetooth support (for Tethering etc).  And I also can not set the services my laptop supports anymore.

---

### Post by mihai.ile on 2008-10-29
well they say that it upgrated the bluetooth stack, for me, I call it downgrade

---

### Post by igknighted on 2008-10-29
FWIW, it works fine for me in intrepid with all the latest updates.

---

### Post by mihai.ile on 2008-10-30
> **igknighted said:**
> FWIW, it works fine for me in intrepid with all the latest updates.

So you can send photos from the phone to pc or you are using the browse device button from the applet?

---


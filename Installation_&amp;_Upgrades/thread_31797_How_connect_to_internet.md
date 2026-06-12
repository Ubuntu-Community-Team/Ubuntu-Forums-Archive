---
title: "How connect to internet?"
date: 2005-05-04
forum: Installation &amp; Upgrades
---

### Post by Robi1 on 2005-05-04
I installed ubuntu 5.04 on my computer, but can't figure out how to connect to the internet. I have always used KPPP before, in KDE or "Internet Configuration Wizard" in Gnome, but I find niether of these in ubuntu. 

I am using a US Robotics 5610 (hardware based) PCI modem which likes to be ttyS4 or ttyS14 (com 5). Computer's an old Pentium 4 1.5 Ghz. on a VIA MB., dual-boot with Windows XP. 

Is there an instruction or reference somewhere that I have missed? Thanks for any help.

---

### Post by wwwolf on 2005-05-04
I have that same modem but I have Kubuntu which is Ubuntu with KDE so it has KPPP. I never could get KPPP to work for me but I do this indtead:

sudo wvdialconf ISP-Provider

let it detect your modem, then run:

pon ISP-Provider

You'll her the modem dial up and your on the internet. You can check to see if your still on by running:

ifconfig

Although I think Gnome has some type of modem lights application that sits on your task bar telling you your on-line

HTH,

wwwolf

---

### Post by Robi1 on 2005-05-09
Ok I did the "sudo wvdialconf ISP-Provider" command and That confirmed that ubuntu sees my modem at ttyS14. That's the same as in SuSE 9.1.  But the pon command didn't work. I'm pretty sure there must be a way to configure the ISP (name, user ID, password and phone number), and set up a dialer, but I surely can't find it. Is there a reference source for these programs somewhere? 

Thanks for any suggestions. :-|

---

### Post by Professor X on 2005-05-09
Here's how I set up wvdial:

```
sudo wvdialconf
sudo gedit /etc/wvdial.conf

```

Insert your phone number, username, and password.

Then connect using

```
sudo wvdial
```

You can also set it up so that you can run it without using sudo.  I think you just chmod a+s /usr/bin/wvdial

---

### Post by Robi1 on 2005-05-10
Ok I finally got my connection established, but it took some serious tinkering. So for the benefit of anyone having the same trouble, here are the steps:

first: "sudo wvdialconf (ISPname)"

this command gave me the location of my modem as ttyS14

next: "sudo gedit /etc/wvdial.conf" then enter: 
phone = (number), 
username = (me@ISPname),
password = (whatever)

save and exit gedit

next   link ttyS14 to /dev/modem using the command:
ln -s /dev/ttyS14 /dev/modem
(change the ttySXX to the result obtained in the first step above)

last sudo wvdial, and open browser when connected

That's it. Thanks to all who helped me.
Robi :grin:

---


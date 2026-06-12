---
title: "Edgy live; no usb mouse detection"
date: 2006-12-19
forum: Installation &amp; Upgrades
---

### Post by Ric95 on 2006-12-19
I have Dapper, but I want a fresh install of Edgy ( upgrade didn't work. Mabey a 64 bit prob.)
So I burnt the CD. ( sumchecks ok)
When I start it live I get the desktop, but the mouse is dead. ( Logiteck USB ) 
I have done Cont+Alt+F1 then reconfigure xserver-xorg, I went through the configuration but that didn't help. ( probably because I'll still in live CD mode...)
     How can I start the mouse in live CD so I can run the install?
     And if I install this way, will reconfiguring fix the mouse? 
   ( and hey! why can Dapper64 find it but Edgy 32 can't???  ;)  )

---

### Post by evilc on 2006-12-20
Not sure if this will help but when I used to work on XP machines (troubleshooting) if the mouse or keyboard was USB and sometimes got loaded last, this caused them not to work as other USB's were seen and the operating system ignored the additions. I recommend you use a USB-PS2/serial adapter it will clear the problem, I have USB-PS2 on both keyboard & mouse and no problems running or being seen by live CD's.

---

### Post by holdinout on 2006-12-20
Maybe you'll have to do it old school with the keyboard... After the install, saving xorg.conf should be possible.

---

### Post by Ric95 on 2006-12-20
>  I recommend you use a USB-PS2/serial adapter it will clear the problem,
Ok, I'll try that first. ( I happen to have an adapter too.)
> Maybe you'll have to do it old school with the keyboard
I'd be happy to, but I couldn't find how to run anything 'Keyboard only".
          thanks guys :)

---

### Post by YaseenKriel on 2006-12-20
u not the only one with usb mouse issues, did a edgy installation on my notebook, a toshiba, and still trying to get mouse to work! some threads say its the fglrx driver but was having the issue before i installed the driver. getting a usb mouse to work and carry on working should be a simple thing to do.

---


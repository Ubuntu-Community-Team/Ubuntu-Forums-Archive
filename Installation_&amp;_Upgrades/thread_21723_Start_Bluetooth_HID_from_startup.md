---
title: "Start Bluetooth HID from startup"
date: 2005-03-23
forum: Installation &amp; Upgrades
---

### Post by wbeck85 on 2005-03-23
I have a Logitec mx900 bluetooth mouse, which to my surprise, worked nearly out of the box with ubuntu with my internal bluetooth module in my laptop. I worked for hours to get it to work with SuSe, yoper, fc3, vidalinux.... All i did was apt-get the bluetooth packages and type in a console:

$sudo modprobe hidp
$sudo hcid
$sudo hidd --connect aa:bb:cc:dd:ee:ff  (where that string is the bluetooth address fo the mouse)
$sudo hidd --server

And my cursor came alive.

However, I have to type that stuff in everytime that I boot up. That can be bothersome. How do I get it to work automatically when I boot the computer? Could I have the bluetooth mouse working at the GDM. (it does if I logout or kill X and return to the gdm after entering the above commands, so I believe it is possible to get it working as soon as the computer boots up.)

I am new and do not know the directory setup much yet (so when you tell me edit your soandso.conf file, please include the path as well)


Thanks

---

### Post by MaX on 2005-03-24
[QUOTE=wbeck85]I have a Logitec mx900 bluetooth mouse, which to my surprise, worked nearly out of the box with ubuntu with my internal bluetooth module in my laptop. I worked for hours to get it to work with SuSe, yoper, fc3, vidalinux.... All i did was apt-get the bluetooth packages and type in a console:

$sudo modprobe hidp
$sudo hcid
$sudo hidd --connect aa:bb:cc:dd:ee:ff  (where that string is the bluetooth address fo the mouse)
$sudo hidd --server

And my cursor came alive.

However, I have to type that stuff in everytime that I boot up. That can be bothersome. How do I get it to work automatically when I boot the computer? Could I have the bluetooth mouse working at the GDM. (it does if I logout or kill X and return to the gdm after entering the above commands, so I believe it is possible to get it working as soon as the computer boots up.)

I am new and do not know the directory setup much yet (so when you tell me edit your soandso.conf file, please include the path as well)


Thanks[/QUOTE]
 Check the (typing from memory) /etc/bluetooth/bluez.conf (or some conf there) there you can set it to connect to different types etc, works for my T68i at least.

---

### Post by wbeck85 on 2005-03-24
Well, no, that doesnt really help me. I've looked at that file (i think you mean /etc/bluetooth/hcid.conf, on my computer, bluez.conf doesnt exist)

Anyway, what I am really looking for is an autexec type of thing that wil just enter the above commands for me when X boots up.

Thanks though

---

### Post by RCook on 2005-04-19
[QUOTE=wbeck85]Well, no, that doesnt really help me. I've looked at that file (i think you mean /etc/bluetooth/hcid.conf, on my computer, bluez.conf doesnt exist)

Anyway, what I am really looking for is an autexec type of thing that wil just enter the above commands for me when X boots up.

Thanks though[/QUOTE]

If your still looking for an answer to your question I suggest you look here: [MX900 in Ubuntu](http://episteme.arstechnica.com/eve/ubb.x/a/tpc/f/96509133/m/236003972731)  I used your information to get my MX900 working, this should help you get yours to work at boot. 

RCook

---

### Post by Kareema on 2005-04-20
There's a much easier way to start a HID device on startup. I just tried to install my Anycom laptop mouse, followed this thread and the link from RCook and was not satisfied with the answers given. Looking at the bluez-utils package I found that there's a startup script /etc/init.d/bluez-utils that uses a configuration file /etc/default/bluez-utils.

Take /etc/default/bluez-utils and add/change the following entries in the HIDD section:
```
HIDD_ENABLED=1
HIDD_OPTIONS="--connect AA:BB:CC:DD:EE:FF --server"
```

and replace the bdaddr with the one of your device.

It works perfect for me (at startup) and I hope it will for you, too.

EDIT: Oh, I forgot that you have to put "hidp" in your /etc/modules, too...

---


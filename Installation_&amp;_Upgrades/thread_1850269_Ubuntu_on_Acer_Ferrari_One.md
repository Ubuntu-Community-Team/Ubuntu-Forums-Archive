---
title: "Ubuntu on Acer Ferrari One"
date: 2011-09-26
forum: Installation &amp; Upgrades
---

### Post by alikaytan on 2011-09-26
[B][FONT=Palatino Linotype][SIZE=4]Hi,
I' m using Acer Ferrari One with 3gb ram and 320gb hdd running win7(64bit) home edition or sth like.
I wanted to remove all windows and install ubuntu 10.10.04 but unfortunately i couldn't boot it form usb. So then i tried to intalls ubuntu via wubi using a usb driver to run ubuntu alongside win7 but this time ubuntu give "chkdsk /r" error. I have tried several times and did everything what is said on some forums.
NOW what i want to do is install ubuntu 10.04 on my pc. I can't use a cd driver and i couldn't reboot via usb.
Advice needed immediately...I'll be grateful for any help.[/SIZE][/FONT][/B]

---

### Post by westie457 on 2011-09-26
> **alikaytan said:**
> [B][FONT=Palatino Linotype][SIZE=4]Hi,
I' m using Acer Ferrari One with 3gb ram and 320gb hdd running win7(64bit) home edition or sth like.
I wanted to remove all windows and install ubuntu 10.10.04 but unfortunately i couldn't boot it form usb. So then i tried to intalls ubuntu via wubi using a usb driver to run ubuntu alongside win7 but this time ubuntu give "chkdsk /r" error. I have tried several times and did everything what is said on some forums.
NOW what i want to do is install ubuntu 10.04 on my pc. I can't use a cd driver and i couldn't reboot via usb.
Advice needed immediately...I'll be grateful for any help.[/SIZE][/FONT][/B]

Hi alikaytan, welcome to the forum.
When you created the USB did you just copy the ISO or use a program like unetbootin?

Just copying does not make it bootable.

I use an Acer laptop with less specs than yours and it boots from USB. You have to change settings in the BIOS for permanent changes to boot order (press F2 during POST) or one-time change to boot order (press F12) and pick the one you want.

---

### Post by alikaytan on 2011-09-26
thanks for reply...i did it at last gratefull for your help, but unfortunately i have one more problem..
ican't connect to a wireless internet connection..
pc sees the coneection, but i simply cannot connect ...i write the pass and it keeps trying to connect but then asks me the pass again then it tries on and on it goes like that...the pass definitely correct cause i can coonet with my mobile phone and other laptop with the same pass...
is there anything i can do?

---

### Post by westie457 on 2011-09-26
> **alikaytan said:**
> thanks for reply...i did it at last gratefull for your help, but unfortunately i have one more problem..
ican't connect to a wireless internet connection..
pc sees the coneection, but i simply cannot connect ...i write the pass and it keeps trying to connect but then asks me the pass again then it tries on and on it goes like that...the pass definitely correct cause i can coonet with my mobile phone and other laptop with the same pass...
is there anything i can do?

A quick dirty fix for this needs a wired connection and physical access to the router.

Plug the cable in then reset the router to factory default settings.
Log in to the routers home page via your web browser. the address should be 192.168.0.1 (increase the last block by each time you cannot log in). manually set up your wireless connection with no security.
You might get some people piggy backing off your signal depending on how many people live near you.
Connect all your machines to the new connection and in the routers home page go to the Advanced tab and look for MAC Filter.

For each machine connected to the router run ```
ifconfig
``` to find the HW address.
The command in Windows is ```
ipconfig /all
```.
Every time you get a match add it to the list. Turn on MAC Filtering to allow only those listed to connect and SAVE the settings.

Finally change the log in details for the router so outsiders cannot change these settings.

---

### Post by alikaytan on 2011-09-26
thanks but sorry i think i couln't exactly tell my problem...
i don't have a problem with installing or sth with router or modem...
My neighbours have a wireless connection already set up and i want to connect to this wireless lan..
Although i write the pass correctly i cannot connect to this lan...

---


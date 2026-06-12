---
title: "Bluetooth - Logitech MX900"
date: 2005-08-20
forum: Installation &amp; Upgrades
---

### Post by D-Vine on 2005-08-20
OK i have the MX900 mouse, it worked perfectly untill yesterday when i got the bluetooth proggies, once they were installed it didn't work anymore because there was no bluetooth connection made, i read some stuff about how to configure it but it's a bit to complicated :-| so now i've uninstalled them and the mouse still won't work.
Can somebody help me? Or explain in newbie language how to configure the bluetooth connection for the MX900?

---

### Post by D-Vine on 2005-08-21
Plz can't anyone help me?:s It's really urgent... :-?  now i have to work with some bad optical mouse that hangs all the time ](*,) , so i'd really want my mouse to work again :|

---

### Post by wbeck85 on 2005-08-22
Hey, sorry i didnt see this post until earlier.

Here's what I did. in synaptic, install bluez-utils, bluez-pin and libbluetooth1 and whatever else they depend on. once those are installed, type in a terminal```
sudo modprobe hidp
``` then ```
sudo hcid
``` and then ```
sudo hidd --server --search
``` while the terminal says "searching..." press the connect button on the bottom of the mouse. Hopefully, the next thing you read says something like "Connecting to xx:xx:xx:xx:xx:xx" Then you should be able to use the mouse.

Thats all i had to do to get mine to work. Good luck to you!

---

### Post by wbeck85 on 2005-08-22
haha!
those angry faces should be a mac address :)

---

### Post by D-Vine on 2005-08-29
Tnx, worked perfectly \\:D/

---

### Post by D-Vine on 2005-08-29
allright, somethings wrong, after my screensaver started the mouse didn't work anymore...
do or did you have the same problem? how can i fix it?

---

### Post by damien82 on 2005-12-27
ok, i know this is an old thread, but just can't get my logitech mx900 to work.

this is what i get when i type "sudo hidd --server --search"

Searching ...
        Connecting to device 00:07:61:16:7E:E0
Can't get device information: File descriptor in bad state

anyone have any ideas what to do?

---

### Post by greenwom on 2006-03-12
I did see an answer to your question.  If the mouse or keyboard isn't picked up by the command 
hidd --search

try to puch the connect button on the bottom of the mouse.  and run the search again.  If you do that it'll either connect it or give you the mac address. if you get the address just run

hidd --connect (and the address)

read through the forums about the config files and how to get it to go at start up

hope this helps

---

### Post by edifuzzy on 2006-04-24
Thanks for the info......this method  works great....mx900 works brilliantly now.

Thanks again

---


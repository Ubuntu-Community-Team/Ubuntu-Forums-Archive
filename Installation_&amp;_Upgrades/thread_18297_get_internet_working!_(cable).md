---
title: "get internet working! (cable)"
date: 2005-03-05
forum: Installation &amp; Upgrades
---

### Post by zuccs on 2005-03-05
hey,

I have a Motorola SB5100 SURFboard Cable Modem and my ISP is optusnet (australia). I have completely no idea where to start with the installation to get my internet working!

in the device manager, the cable modem IS recognised and listed as USB Cable Modem.....now how do i connect it to the internet..?

*edit* the modem is currently running thru USB but i can change that to ethernet if that is better? *edit*

i have a fresh install of ubuntu and have never used it before and i have searched a few forums and guides but nothing too helpful that i have found..

any advice would be awesome, thanks guys,
-zuccs

---

### Post by Jesus Franco on 2005-03-05
Use ethernet and try calling your isp and ask them for thier DNS servers. Fill that info in the "networking" window. Also ask for thier host name. I have comcast and the hostname is comcast.net, also For thier DNS search path its hsd1.ma.comcast.net

You wont need to do much just fill in the info. and activate the card.  :mrgreen:

---

### Post by KiwiNZ on 2005-03-05
Yes use ethernet , I tried to get one of those working on USB inLinux ( several Distros ) it was hopeless.

---

### Post by zuccs on 2005-03-06
I have connected the cable modem thru ethernet and when I rang my ISP they wouldnt give me any of the details, (DNS, hostname). They said its already built into the modem and all I have to do is pull the power out of it for 5-10 seconds and it should connect automatically....

when i logon to ubuntu i get an error saying no internet connection or something, and more obviously, i cannot visit any websites....

if i am connected to the internet thru XP, is there a way to find the hostname and DNS servers? that way i can fill it into the networking window like you suggested Jesus Franco.

this sounding right...? where to now? thanks again for your quick replies guys

---

### Post by alastair on 2005-03-06
"if i am connected to the internet thru XP, is there a way to find the hostname and DNS servers?"

Yes - should be OK.

a) See if you are using DHCP for IP address (control panel / network / ...)
b) list details in a DOS shell :

ipconfig /all

---

### Post by zuccs on 2005-03-06
ok...i got cable running thru ethernet on XP fine.. and i now have details for DNS servers, DHCP server (enabled: yes), default gateway IP and all that other stuff...

now, the next problem lol....the networking window on ubuntu just stalls when i try to open it.. now what?  #-o 

is it spose to be this hard? or should cable internet just run itself thru linux?

---

### Post by alastair on 2005-03-06
Linux/unix still requires some thought/work often I'm afraid - although it is getting very close to "just works" for most people.

If the "networking GUI" "stalls", this probably means that something is 'wrong' in the networking configuration i.e. wrong interfaces up, routes, DHCP stalls etc.

Post :

output of :

ifconfig -a
route -n
cat /etc/network/interfaces

and explain your network a little again i.e.

PC (IP?) <--- e/net ---> modem (IP?)  ..... ?

---

### Post by nolan on 2005-03-23
Hello :)

If you are using dual boot, try this :

-boot in ubuntu
-select your eth device and delete every settings you might have tried. Just set up "automatic dhcp" and "connection at start-up"

then reboot in windows (xp here)
open a console (run > cmd)
ipconfig /release
reboot in ubuntu

It *should* work (at lease it did for me and trust me.. i had been trying to get internet on my linux boxes for a very long time)

---


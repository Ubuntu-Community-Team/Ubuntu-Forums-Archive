---
title: "Please help with ubuntu installation"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by opaquemafia on 2008-08-23
I have been trying to get Ubuntu installed on my working dell cpx laptop

it has a 

p3
30gig hd
256 ram


I burned my own live cd and i cant get it to install all the way... after answering all the questions it will beginning installing the system and it will fly through everything else but once it hits 15% it does nothing it just sits there... any help please

---

### Post by Shazaam on 2008-08-23
You might want to try the Alternate Install Ubuntu cd from one of the mirrors here...
[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

---

### Post by opaquemafia on 2008-08-23
> **Shazaam said:**
> You might want to try the Alternate Install Ubuntu cd from one of the mirrors here...
[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)


yeah i am currently downloading it right now... imma cross my fingers and hope it works because xp is already off my lappy and if i have to install anything i want it to be ubuntu

---

### Post by Shazaam on 2008-08-23
If you find that Ubuntu runs a little slow for you try out Xubuntu. It is lighter on resources which is great for older machines.

---

### Post by opaquemafia on 2008-08-23
> **Shazaam said:**
> If you find that Ubuntu runs a little slow for you try out Xubuntu. It is lighter on resources which is great for older machines.


that text based disk is working wonders... it is installing just fine...


if you happen to have the time would you mind hitting me up on aim i just wanna figure out the driver situation for the wireless card and for the lan card

omfgitsashark

---

### Post by manishtech on 2008-08-23
> **opaquemafia said:**
> that text based disk is working wonders... it is installing just fine...


if you happen to have the time would you mind hitting me up on aim i just wanna figure out the driver situation for the wireless card and for the lan card

omfgitsashark
LAN Cards are supported out of box.

Can you tell your wireless chipset? Broadcom, atheros or Intel?
Intel ones have their drivers inbuilt as I have (iwl3945). Broadcom and atheros required ndiswrapper

---

### Post by opaquemafia on 2008-08-23
> **manishtech said:**
> LAN Cards are supported out of box.

Can you tell your wireless chipset? Broadcom, atheros or Intel?
Intel ones have their drivers inbuilt as I have (iwl3945). Broadcom and atheros required ndiswrapper


the wireless card that i have is a 

d-link air
IEEE 802.11b wireless lan adaptor
dwl-650

also what about activesynce drivers for a windows 6.1 phone



all i gotta say is holy crap i am loving ubuntu right now... gunna be fun rocking this thing at school

---

### Post by opaquemafia on 2008-08-23
i was able to figure out the drivers... i just want to thank every who helped me get this going i am in love thats all i gota say

---

### Post by manishtech on 2008-08-23
> **opaquemafia said:**
> i was able to figure out the drivers... i just want to thank every who helped me get this going i am in love thats all i gota say
Type this command in terminal and post here what you get

```
lspci | grep -i network
```

---

### Post by opaquemafia on 2008-08-23
> **manishtech said:**
> Type this command in terminal and post here what you get

```
lspci | grep -i network
```


im not home right but i will check it as soon as i can

---


---
title: "have you got 3g / umts modem problems with karmic too?"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by karlrt on 2009-10-04
I post this because my huawei e230 is really unstable on karmic. If suspended or plugged in after system start, the network manager doesnt even find any connected modem, so i have to reboot to get connected.

the 2nd thing is that if the modem is found by nm, get it connected is like playing roulette, sometimes it works from the beginning, sometimes it connects but there is no real connection established, sometimes it stops while connecting, any attempt of reconnection is useless then, it instantly stops working, then i have to reboot :(

Do you experience same things? or do your 3g modems work with karmic? 

btw, here my bug-report: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/435267]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/435267")

---

### Post by GeorgeVita on 2009-10-04
> **karlrt said:**
> I post this because my huawei e230 is really unstable on karmic. If suspended or plugged in after system start, the network manager doesnt even find any connected modem, so i have to reboot to get connected.

Sometimes (randomly, 5%) network manager cannot find my Huawei E169 and I can resume from this problem without reboot, just by 'removing' and 'running again' option driver: ```
sudo modprobe -r option
sudo modprobe option
```
Please test if above has the same result to you. If so this could be a time-lug between driver load and modem switching (or internal modem reset). Possibly we have the same problem.

Regards,
George

---

### Post by karlrt on 2009-10-04
hi george!

didnt help for me

```
# modprobe -r option 
FATAL: Module option is in use.

```

and i dont have it 5 % of the time, but ALLWAYS if i suspended before and sometimes if i do a reboot

thanks for your suggestion!

karl

---

### Post by GeorgeVita on 2009-10-04
Hi Karl,
> **karlrt said:**
> hi george!
didnt help for me```
# modprobe -r option 
FATAL: Module option is in use.

```and i dont have it 5 % of the time, but ALLWAYS if i suspended before and sometimes if i do a reboot
thanks for your suggestion!
karl

Suspended while connected or after manually disconnected  from network manager icon?
Also what **version** of Ubuntu? (to test it)

> or do your 3g modems work with karmic? My ZTE MF636 is NOT working!
[http://ubuntuforums.org/showthread.php?t=1202430](http://ubuntuforums.org/showthread.php?t=1202430)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408555](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408555)

Regards,
George

---

### Post by karlrt on 2009-10-04
wow, first time it worked after suspend. i had to 

1.) disconnect connection
2.) suspend/resume
3.) modem was not seen
4.) modeprobe -r option: FATAL: Module option is in use.
5.) tried modeprobe -r a 2nd time, then worked
6.) still no modem seen in nm ->
7.) i removed my 3g connection from connection manager
8.) modem was seen and connected

i use karmic koala amd64, all updates installed

---

### Post by GeorgeVita on 2009-10-04
[SIZE="4"]![/SIZE]
I managed to ... get it stucked (!) doing a suspend while connected.
After resume, the modem turned to a 'non usable' state with green led blinking twice (GPRS network, not my provider). Many tries did not work till a reboot! My modem was always powered as I have the PSU to the power outlet (my PC is EeePC 1000H).

Another trick for you to test:```
sudo killall modem-manager
``` this will 'kill' modem-manager but run again (new process) as it is triggered always.

I am running Ubuntu 9.10 (32bit) fully updated, now testing suspend after normal disconnection...

**EDIT:** ... Tested and it is OK!
I will try to 'investigate' previous problem and let you know.

**New edit:** Suspended again without manually disconnecting, problem appears (modem NOT at nm), connected fine after: **sudo killall modem-manager**

I am going to add a comment to your above mentioned [bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/435267")

Regards,
George

---


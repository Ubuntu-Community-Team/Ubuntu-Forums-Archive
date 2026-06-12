---
title: "My 7.04 install went OK, few minor issues"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by derek45 on 2007-04-26
I installed ubuntu 7.04 on my Toshiba M45-S165 laptop. Let it partition the HD and dual boot with Win XP.


:guitar: 

Everything seemed to install OK,  except I'm still having trouble figuring out WEP Wi-Fi

I can connect fine with CAT-5,  but can't seem to get logged into my D-Link WEP router.


I briefly connected to an open wi-fi  network and it worked.

I'm also having trouble with My USB mouse.  it freezes after about 10 mins. use.

I tried my wife's Microsoft wireless mouse, same trouble.


I've been running 6.10 on my desktop since March with no trouble. Really liking it.

...but these mouse and Wi-Fi issues have prompted me to set up GRUB to boot into XP by default.
:(

---

### Post by pitt0071 on 2007-04-26
hi derek

do you use the network manager applet to enter you wep key?

if yes, i would suggest you to try setting up your wifi with the iwconfig command

you should be able to set up the wep key with it but i think you have to enter it as hexadecimal, it will probably not work if you enter it as ascii...

```
$ man iwconfig
``` 

that manual should help you out

pitt

---

### Post by derek45 on 2007-04-26
> **pitt0071 said:**
> hi derek

do you use the network manager applet to enter you wep key?

if yes, i would suggest you to try setting up your wifi with the iwconfig command

you should be able to set up the wep key with it but i think you have to enter it as hexadecimal, it will probably not work if you enter it as ascii...

```
$ man iwconfig
``` 

that manual should help you out

pitt

I just clicked on the network icon by the clock and sound...

Never did the iwconfig thing before,  I"m trying to figure it out now.

THANKS !

---

### Post by derek45 on 2007-04-26
Ok,  I went into iwconfig,  but every time I try to change a setting it says

"SET failed on device ath0 ; Operation not permitted"

:confused:

---

### Post by pitt0071 on 2007-04-27
are you running the command as root?

sudo iwconfig <parameters>

pitt

---

### Post by derek45 on 2007-04-27
> **pitt0071 said:**
> are you running the command as root?

sudo iwconfig <parameters>

pitt


Um,  I don't know,  I don't think so.

I don't know what "root" means?

**This is all new to me.**

I was typing iwconfig in the terminal.

I didn't do "sudo" anything.

---

### Post by pitt0071 on 2007-04-28
ok then type in:

```
$ sudo iwconfig <your interface> <parameters>
```

where your interface will probably be something like eth1

and parameters may vary, check with the manual

example parameters may be essid or key etc


good luck
pitt

---

### Post by Loki-uk on 2007-04-28
There seems to be a bug in the mouse code in the latest kernel I have been suffering mouse freezes but if I use ALT + TAB to cycle apps the mouse comes back. I have no idea why but it works almost every time.

Loki

---

### Post by derek45 on 2007-05-02
Thanks for the replies.

I"ve been out of town and away from my wi-fi.

I"ll check this out when I get time.

---

### Post by derek45 on 2007-05-02
OK,  using the sudo iwconfig commands,  I've been able to make some changes,    I can change the ESSID, and then do an iwconfig,  and see the changes.......but other things,  like retry,  I can't seem to figure out.  I'm using the manual,  but it doesn't accept the commands that the manual uses as examples.

---

### Post by derek45 on 2007-05-11
What I thought was the USB mouse locking up,  now seems to be any USB device locking up.

I had my thumb drive in yesterday,  and right after my mouse locked up,  I got notified to eject my UBS device before taking it out.  I hadn't touched it.

Any idea why UBS would die after about 15mins?????????????

---

### Post by derek45 on 2007-06-02
I bought a new WPA teltrend router,  and can connect to it fine.

:D


For some reason,  it likes WPA a lot more than WEP.

COOL.

---


---
title: "GUI mode with server edition"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by bdavide on 2008-10-19
Hello,

Ive downloaded and installed Ubuntu 8.04 server edition on a dell computer.
After boot I discovered I can only use it in command mode.
I am not comfortable with it, I would prefer the GUI mode as for the "desktop edition".

Is it possible to have the same GUI interface?

---

### Post by steveneddy on 2008-10-19
Yes.

Just install ubuntu-desktop

```
sudo apt-get install ubuntu-desktop
```then go make a sandwich.

You can start and stop the GUI by typing in terminal - or preferably a tty

```
sudo /etc/init.d/gdm stop
```or 

```
sudo /etc/init.d/gdm start
```While in GUI mode, hit the 

**CTRL+ALT+F1**

keys to get to a tty terminal, login, then type inthe commands to start and stop the GUI.

The gui is at 

[B]CTRL+ALT+F7

[/B]and [B]

CTRL+ALT+F8

[/B]is a system monitor.You should have a tty terminal for F1 through at least F4 and maybe even F6.

---

### Post by bdavide on 2008-10-19
Thanks for your reply.

This is the answer I get when I type:

sudo apt-get install ubuntu-desktop

E: Couldn`t find package ubuntu-desktop

---

### Post by oldos2er on 2008-10-19
Do you have a working internet connection? Try the command "sudo aptitude update && sudo aptitude install ubuntu-desktop".

---

### Post by bdavide on 2008-10-20
Exactly, this is the problem. I think I have no connection to internet, even though the cable is connected to netcard.
In fact using this command:

```
sudo aptitude update
```

release an error, I guess connection error.

Im trying to setup the network with this command I found in internet:

```
edit /etc/sysconfig/network-scripts/ifconfig-eth0

```
but I receive a write permission problem (even though I gave root password)

Any help?

---

### Post by bdavide on 2008-10-21
Some updates:

I used these 2 lines to find out the IP configuration.

nano /etc/network/interfaces
nano /etc/resolv.conf

and it all looks correct to me.
I am 100% sure internet is up and running and the cable works properly (checked with another PC)

I am not sure about Netcard and driver, I can only see the led of the Netcard blinking.

What do I do? Thanks

---


---
title: "network ethernet or wireless gone"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by tonyuk123 on 2010-08-01
Hi
i'm running ubuntu 9.04
today i was cleaning out a desktop pc of dust ! and decided to add a wireless network card i have to it
the ethernet connection was working fine before and after fitting
but the wireless card does not work atall
it is recorgnised but unable to work 
i was following a thread in a forum here and it seemed to be going well (at least ethernet connection and internet were working until the last stage) it suggested using wicd for the network
so i did the install for it
which worked
since though i have no internet or ethernet connection anymore

the wireless card reports as Atheros which seems to be notoriously difficult to get going judging by the forums here
difficult to post any info big time here as the pc i am talking about wont talk to anything now

any ideas how to get it back owrking without having any network/internet connection atall??????

if i do
sudo iwlist ath0 scanning 
interface doesn't support scanning : network is down

if i do
sudo dhclient aht0
i get back
wifi0: unknown hardware address type 801
execve (/sbin/dhclient-script, ...): permission denied
wifi0: unknown hardware address type 801
bind socket to interface: no such device

any ideas or advice?????

---

### Post by dino99 on 2010-08-01
which model is this wireless card ?

---

### Post by tonyuk123 on 2010-08-02
i am at work so cant check
pretty sure it is atheros ar5100+ or something very similar to that, is sold as a 'TP Link' and is the 108Mbps version
anyway thats not the main problem even though i obviously want to get it working
would be happy to get the ethernet internet connection back at least, how do i change back to the fefault ubuntu network tool, from wicd? (remebering i dont have the cd as i upgraded, and no internet connection, although i assume it hasnt removed the old tool, just made wicd the default now) as it doesn't have the options the other one did, and for some reason doesn't work atall, even when i enter what it needs normally
btw, the card has a light, but doesn't come on
the ehthernet card has a stable light and flashes the other when it attempts to work. but i cannto even access the modem setup on ip 192.168.1.1, which i know it is

will confirm the card version later when home

---

### Post by tonyuk123 on 2010-08-02
ok
if i do lspci in terminal
besides a lot of other bits
i get

02:0a.0 ethernet controller: realtek rtl 8139/8139c/8193c+
02:0b.0 ethernet controller: atheros communication inc. Atheros AR5001+ wireless network adapter (rev 01)

the realtek card has worked fine until i installed wicd
the atheros card has only just been put in this pc, but worked on ubuntu 8.04 without anything being changed and on a much older pc

any ideas welcomed please

---


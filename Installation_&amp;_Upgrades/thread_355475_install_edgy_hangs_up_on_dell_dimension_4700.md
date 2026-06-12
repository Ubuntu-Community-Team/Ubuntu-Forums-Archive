---
title: "install edgy hangs up on dell dimension 4700"
date: 2007-02-07
forum: Installation &amp; Upgrades
---

### Post by klein de usa on 2007-02-07
hi
i'm haveing a problem installing edgy 6.10 i386 offen the alternate install cd .
i have a dell dimension dim 4700 pen.4 3.40ghz , one sata drive , 2 cd-drives that are ide.
if i boot offen the live cd edgy runs but i don't think it see's my sata hard drive but it runs.
when i try to install edgy from  the alternate install cd the main screen comes up and i click on the first choice and it starts this is what it puts on the screen:

[17179573.608000] ata2:disabling port
[17179573.632000] usb 3-1.1: can't set config#1, error -71
[17179573.632000]hub 3-1:1.0:hub_port_status (err-71)
[17179573.636000]hub 3-1:1.0:hub_port_status (err-71)
[17179573.636000]hub 3-1:1.0:hub_port_status (err-71)
[17179573.616000]acpi:getting cpuindex for acpi id ox2
start system log daemon: syslogd, klogd 
_  


after it puts all that on the screen it just sits there at a blinking curser , does anyone have any ideas?
i have installed edgy 6.10 numerious times on a couple dells and haven't had any problem before.
my cd's are set :
	controller=parallel ata
	port=pata-0

---

### Post by klein de usa on 2007-02-19
ok 
edgy is on my dell 4700 finely ,
i had to use the desktop cd and install it that way for some reason the alternate cd just wouldn't install no mater what i did, also i found out that  the desktop cd will install grub where you tell it to, i had read post in here that said it wouldn't, but it will it is the sixth screen in the install,

---


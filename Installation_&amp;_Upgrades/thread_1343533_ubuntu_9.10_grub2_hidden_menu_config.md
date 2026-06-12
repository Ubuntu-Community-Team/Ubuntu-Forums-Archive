---
title: "ubuntu 9.10 grub2 hidden menu config"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by gopher2x on 2009-12-01
how do i make my grub menu hidden or only display for 1 second? heres my current settings... cant seem to get it working

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=1
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=1
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
\GRUB_CMDLINE_LINUX=""

---

### Post by u.b.u.n.t.u on 2009-12-02
Within Ubuntu 9.10, start up manager, there is an option to set the default boot and time delay.

---

### Post by gopher2x on 2009-12-02
sorry whats the name of the executable you are referring to?

---

### Post by TransitMan on 2009-12-02
It is called "START UP MANAGER" whereby you can change the settings of GRUB to what you wish.
If you do not have this installed, open Synaptic and searh for it, click to install and install it.
When it is installed, it will be located SYSTEM -> ADMINISTRATION -> STARTUP-MANAGER.

---

### Post by garvinrick4 on 2009-12-02
sudo apt-get install startupmanager




It is a setting in Startup-manager as well as boot order.

Just set to 10 seconds- you can always hit enter if you want to go like now.

If I put at 5 seconds I seem to day dream and miss my chance to boot in another partition alot.

---

### Post by ConstintineVamp on 2009-12-02
Im still using Jaunty cause i never could get Grub 2 to Update after a kernel upgrade

---

### Post by u.b.u.n.t.u on 2009-12-02
> **gopher2x said:**
> sorry whats the name of the executable you are referring to?

Yeah sorry about the lack of details. I am writing this from a non Ubuntu 9.10 operating system so I couldn't check.

Cheers to those who came to the rescue!

---

### Post by gopher2x on 2009-12-02
ok i got the config program installed however it has no option to hide the grub2 menu... i set my timeout to 1 so it only briefly shows... however i would like it to stay hidden unless i hold down shift. this is a feature of grub2 i just dont know how to turn it on. any grub experts ?

---

### Post by darkod on 2009-12-02
Do you have another OS present? It's a silly question because why would you like hidden menu with another OS present but I just found this:
*[COLOR=Navy][COLOR=DarkRed]According to some of the GRUB 2 developers, in Ubuntu the menu will [I]**not*** be hidden any time there are other OSs found by os-prober, regardless of this setting. This is in keeping with the Ubuntu Team's goal towards booting: [https://wiki.ubuntu.com/DesktopExper...pec#Bootloader]("https://wiki.ubuntu.com/DesktopExperienceTeam/KarmicBootExperienceDesignSpec#Bootloader")

[/COLOR][/COLOR][/I][COLOR=Navy][COLOR=DarkRed][COLOR=Black]Otherwise uncommenting the line GRUB_HIDDEN_TIMEOUT should make it hidden.[/COLOR][/COLOR][/COLOR][I][COLOR=Navy][COLOR=DarkRed]
[/COLOR][/COLOR][/I]

---


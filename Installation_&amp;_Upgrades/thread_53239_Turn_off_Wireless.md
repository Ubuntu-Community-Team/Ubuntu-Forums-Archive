---
title: "Turn off Wireless"
date: 2005-07-30
forum: Installation &amp; Upgrades
---

### Post by jemt on 2005-07-30
Hi experts.

How do I turn off my wireless network card? I don't use it very often so it's a waste of battery having it turned on :)

Unfortunately the keyboard's wireless on/off dosn't work in Ubuntu. It is a brand new IBM X31.

---

### Post by amohanty on 2005-07-30
>> ifconfig eth0 down

replace eth0 with your interface name. To get that just do:

>> ifconfig

ALso I dont think this will shut it down simply be the same as _Disable_ in WinXXX for the network connection. But on the up side once you do this, you can eject it.

AM

Edit: PS: to turn it on do :
>> ifconfig eth0 up

AM

---

### Post by jemt on 2005-07-31
I don't want to just disable it. I want to turn it of. It's a Centrino based computer so I can't eject it.

---

### Post by jemt on 2005-07-31
I think I cracked it. It seems that /etc/acpi/wireless.sh does not work proberly. I replaced the script with one I made myself :

-----------------------------------------------------------------------------------------------------------------

#!/bin/bash
# Enable/Disable Wireless

# Specify your network device state file
dev_state="/sys/class/net/eth1/device/power/state"

echo

if [ -f $dev_state ] # Checking that file exists
	then
		if [ -G $dev_state ] # Checking that the user has permission to read from the file
			then
				if [ `cat $dev_state` = 0 ] # If true, wireless is turned on
					then
						echo -n 3 > $dev_state # Wireless switched off
						echo "Wireless switched off [\"ok\"]"
					else
						echo -n 0 > $dev_state # Wireless switched on
						echo "Wireless switched on [\"ok\"]"
				fi
		else
			echo "Permission denied - try as root [\"fail\"]"
		fi
	else
		echo "Device state does not exist! [\"fail\"]"
fi

echo

-----------------------------------------------------------------------------------------------------------------

Of cause it is not that generic as you haft to specify the path to a state file. But it works for me :)

---

### Post by royg1234 on 2005-07-31
Try this:
[list=1]
[*]add "Network Manager" to your panel.
[*]click on your connection
[*]hit "Configure"
[*]find your connection and hit "Deactivate"
[/list]

That's usually what I do, but I'm not sure if it actually does anything to save the battery.

---

### Post by jemt on 2005-07-31
Hi.

I don't have that applet available. But nevermind. My fn+f5 works great with my new shell script :)

 - Thanks anyway

---


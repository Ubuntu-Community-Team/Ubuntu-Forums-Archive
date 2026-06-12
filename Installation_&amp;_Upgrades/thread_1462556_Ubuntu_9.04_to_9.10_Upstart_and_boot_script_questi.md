---
title: "Ubuntu 9.04 to 9.10 Upstart and boot script question."
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by Dave_Connor on 2010-04-25
Hey everyone. I just updated my netbook and laptop to 9.10 and if 10.04 is a positive upgrade I will do aswell with my server that is running 9.04. But with updating my network script that runs at boot. I know it is working but is not showing output to console before I log into tty1. I have tried modifying it with lsb_action_msg() {} function around my script and placing ". /lib/lsb/init-functions" at the top of a copy of the original script but this did not work. I will mostly need the output for my netbook since I roam alot on my campus. 

Here is the script for networking.

```

#!/bin/bash
mpc pause

sudo /etc/init.d/network-manager stop
sudo ifconfig ra0 up
sudo ifconfig eth0 up

NETWORK="network"

RUN=$(ps -A | grep wpa_supplicant | wc -l)/
if [ $RUN == 1 ]
then
	sudo killall wpa_supplicant
	sudo ifconfig eth0 up
	sudo ifconfig ra0 up
fi

if [ $RUN == 0 ] 
then
	sudo ifconfig ra0 up
	sudo ifconfig eth0 up
fi

echo "Scanning network, scanning for $NETWORK"
NET=$(sudo iwlist ra0 scan | grep "$NETWORK" | wc -l)

if [ $NET ==  1 ]
then
	CONFIG=$(sudo cat /etc/wpa_supplicant.conf.home | grep "$NETWORK" | grep "#" | wc -l)
	if [ $CONFIG == 1 ]
	then
		echo "incorrect config for /etc/wpa_supplicant.conf for network $NETWORK"
		exit
	fi

	if [ $CONFIG == 0 ]
	then
		echo "correct config found"
		echo ""
		echo "Connecting to network"
		echo ""
		sleep 1
		sudo wpa_supplicant -B -D wext -i ra0 -c /etc/wpa_supplicant.conf.home
		sleep 3
		echo "requesting ip address from ap"
		echo ""
		sudo dhclient ra0 > /dev/null;
		echo "ip recived, you now connected to network '$NETWORK'"
	
		# test connection
		echo "";
		echo "Testing network connection: ";

		PING=$(ping -c 1 -w 2 google.com | wc -l);

		if [ $PING == 5 ] 
		then
			echo "Error, network time out with google.com";
		fi

		if [ $PING == 6 ] 
		then
			echo "Test Successful, ping to host: google.com, got response";
		fi 

		MOUNT=$(mount | grep /media/NANO | wc -l)
		if [ $MOUNT == 1 ]
		then
			echo ""
			echo "Device /dev/sdc1 is already mounted to /media/NANO"
		fi

		if [ $MOUNT == 0 ]
		then
			echo ""
			echo "mounting /dev/sdc1 to mount point /media/NANO"
			sudo mount /dev/sdc1 /media/NANO -o uid=$USER,rw

		fi
		#sudo /etc/init.d/mpd restart
		#amixer set PCM 0%
		#mpc pause
	fi
fi

if [ $NET == 0 ]
then
	echo "Network '$NETWORK' is not in range"
	echo ""
	sleep 2
	echo "Trying to connect to wireless network 'network_2'"
	/home/arthur/./net-2.sh
	
	# after network completes, restart music
	MOUNT=$(mount | grep /media/NANO | wc -l)
	if [ $MOUNT == 1 ]
	then
		echo "Device /dev/sdc1 is already mounted to /media/NANO"
	fi

	if [ $MOUNT == 0 ]
	then
		sudo mount /dev/sdc1 /media/NANO -o uid=$USER,rw
	fi

	sudo /etc/init.d/mpd restart
	#amixer set  0%
fi


```

What tips are there for would just having the script run POST-login after tty1 since I have looked at ways for to do this as well. Any tips or suggestions would such be a great help.

Edit: 
if you include /lib/lsb/init-functions at the beginning of your script with ". /lib/lsb/init-functions" and replace "echo" with "log_action_msg" then your console will update with what you want your script to report back on text boot.

---


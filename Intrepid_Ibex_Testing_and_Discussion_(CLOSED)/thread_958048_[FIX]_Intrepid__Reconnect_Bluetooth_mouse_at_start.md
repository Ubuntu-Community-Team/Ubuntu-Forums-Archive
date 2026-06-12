---
title: "[FIX] Intrepid :: Reconnect Bluetooth mouse at startup"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by onemyndseye on 2008-10-25
This is a brutal hack to get your BT Mouse to reconnect on startup.. but in Kubuntu Intrepid Ibex I've found no other solution..

First install the "bluez-compat" package with ' sudo apt-get install bluez-compat '

Then create the following script in /usr/local/bin

script: bt-moused.sh
> 
#!/bin/bash


# MAC Adress for your BT Mouse
MAC_ADDRESS="00:07:61:6B:AB:75"

## Disable Touchpad on connect
## 1 = Yes
## 0 = No
#
TOGGLE_TOUCHPAD=1

bt_mouse_connect() {

MOUSE_CONNECTED=""
hidd --connect $MAC_ADDRESS >/dev/null 2>&1 && MOUSE_CONNECTED=YES || MOUSE_CONNECTED=""

if [ -n "$MOUSE_CONNECTED" ]; then
  echo "BT Mouse connection sucessfull!"
  [ "$TOGGLE_TOUCHPAD" = "1" ] && synclient TouchpadOff=1
  return 0
else
  echo "BT Mouse connection failed! Retrying ..."
  sleep 3
  bt_mouse_connect
fi

}


check_mouse_connected() {

echo -n "Checking BT Mouse connection .."
CHECK_CONNECTED="$(hidd |grep "$MAC_ADDRESS")"
if [ -z "$CHECK_CONNECTED" ]; then
  echo "BT Mouse no longer connected! Will keep trying to reconnect. "
  [ "$TOGGLE_TOUCHPAD" = "1" ] && synclient TouchpadOff=0
  bt_mouse_connect
else
  echo " BT Mouse still connected."
fi

sleep 3
check_mouse_connected


}





check_mouse_connected
bt_mouse_connect




Be sure to edit the MAC_ADRESS line at the top of the script to match the MAC address of your mouse..  shown by ` hcitool scan ' while your mouse is in pair mode.... Also, by default, the script toggles off your synaptics touchpad if one exists... If you dont want this to happen then edit the script as described in the comments.


Now edit the file /etc/rc.local: ' sudo pico /etc/rc.local '

Add the following line at the bottom
> 

/usr/local/bin/bt-moused.sh >/dev/null &






This script periodically checks to make sure the BT Mouse is connected and attempts to reconnect if the connection is lost.  Should the connection be lost.. by reboot.. sleep mode. .. etc etc .  It is still necessary to press the Connect button on your mouse for the script to re-establish  the connection but given that is taken care of by the user, the script SHOULD take care of the rest.

I hope this horrible hack helps someone until the bugs are worked out of the bluetooth system :)

Take care,
-onemyndseye

** I've attached the script if anyone would like to save a step **

---

### Post by onemyndseye on 2008-10-30
I've made serveral improvments to this script that I'll post should someone show interest.. although I've been testing this version for over 2 weeks with no problems

If anyone has a better solution please feel free to speak up :)

-onemyndseye

---


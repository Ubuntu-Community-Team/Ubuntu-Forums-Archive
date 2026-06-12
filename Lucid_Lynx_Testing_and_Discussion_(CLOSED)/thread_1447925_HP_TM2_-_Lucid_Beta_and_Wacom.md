---
title: "HP TM2 - Lucid Beta and Wacom"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by waka324 on 2010-04-06
Just wanted to share how to configure your TM2 upon login and how to get auto-rotation to work!

first
```

gedit wacom-configure.sh 
```

paste this into it...

!UPDATE! - ERASER=$(xinput --list | grep 'Wacom ISDv4 E3 eraser' | grep -o [0-9][0-9]) is now ERASER=$(xinput --list | grep 'Wacom ISDv4 E3 Pen eraser' | grep -o [0-9][0-9])

```
#!/bin/bash

ERASER=$(xinput --list | grep 'Wacom ISDv4 E3 Pen eraser' | grep -o [0-9][0-9])
STYLUS=$(($ERASER+1))
TOUCH=$(xinput --list | grep 'Wacom' | grep -o [0-9][0-9] | grep -v $ERASER | grep -v $STYLUS)

xsetwacom set $STYLUS rotate NONE 
xsetwacom set $ERASER rotate NONE
xsetwacom set $TOUCH rotate NONE

xsetwacom set $STYLUS TopX -100 
xsetwacom set $STYLUS TopY 12 
xsetwacom set $STYLUS BottomX 26170 
xsetwacom set $STYLUS BottomY 16475
xsetwacom set $STYLUS TPCButton 0
xsetwacom set $STYLUS Button2 3
xsetwacom set $STYLUS Button3 4


old="0"
	if [ -e /sys/devices/platform/hp-wmi/tablet ];	then
		new=`cat /sys/devices/platform/hp-wmi/tablet`
		if [[ $new != $old ]]; then

			if [[ $new == "0" ]]; then
				
				xrandr -o normal 
				xsetwacom set $STYLUS rotate NONE 
				xsetwacom set $ERASER rotate NONE
				xsetwacom set $TOUCH rotate NONE
				

			elif [[ $new == "1" ]]; then
				xrandr -o right 
				xsetwacom set $STYLUS rotate CW 
				xsetwacom set $ERASER rotate CW
				xsetwacom set $TOUCH rotate CW 


			fi 

		fi
	fi
```

save, and right click on the file (in your home directory)and go to permissions and make it executable.

now, we do something similar to make a rotating script, but first we have to make sure we can detect the rotating bezel...
so...
```
sudo gedit /etc/modules

```

then paste this into it...

```
hp-wmi
```

I had an issue with it not starting, until I added it between the two existing lines, so do that.

save and exit. 

now we make another script, 

```
gedit auto-rotate.sh
```

paste this into it...

```
#!/bin/bash


ERASER=$(xinput --list | grep 'Wacom ISDv4 E3 Pen eraser' | grep -o [0-9][0-9])
STYLUS=$(($ERASER+1))
TOUCH=$(xinput --list | grep 'Wacom' | grep -o [0-9][0-9] | grep -v $ERASER | grep -v $STYLUS)


old="0"

while true; do
	if [ -e /sys/devices/platform/hp-wmi/tablet ];	then
		new=`cat /sys/devices/platform/hp-wmi/tablet`
		if [[ $new != $old ]]; then

			if [[ $new == "0" ]]; then
				
				xrandr -o normal 
				sleep 1s
				xsetwacom set $STYLUS rotate NONE 
				xsetwacom set $ERASER rotate NONE
				xsetwacom set $TOUCH rotate NONE
			elif [[ $new == "1" ]]; then
				
				xrandr -o left 
				sleep 1s
				xsetwacom set $STYLUS rotate CCW 
				xsetwacom set $ERASER rotate CCW
				xsetwacom set $TOUCH rotate CCW 
			fi 

		fi
		old=$new
		sleep 1s
	fi
done
```

you can even add 

```
		gconftool-2 -t string -s /desktop/gnome/background/picture_filename /home/your-username/wallpaper-landscape.jpg
```

and

```
gconftool-2 -t string -s /desktop/gnome/background/picture_filename /home/your-username/wallpaper-portrait.png
```

into the rotation parts to change your background to different images, in my case, I have two versions of the same image, but one is rotated so it never stretches it. (obviously, you need to chant 'your-username' and the image file name for it to work.)

then, we save, make it executable, now we just go to menu, preferences, and select startup applications and add them to the startup applications with the startup command of 

bash 'the-script-you-made.sh'

so that when you login, it runs the scripts and configures your tablet, and allows it to auto rotate!

---


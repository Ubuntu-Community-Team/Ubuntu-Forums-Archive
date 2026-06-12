---
title: "pulse audio controller for xfce for keyboards w audio keys"
date: 2012-03-19
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2012-03-19
this is broken for the moment but does have steps in the right direction....  plz someone fix this better than me.....

a good majority of this code is from this thread....

[http://crunchbanglinux.org/forums/topic/11392/pulseaudio-volume-control-with-media-keys/](http://crunchbanglinux.org/forums/topic/11392/pulseaudio-volume-control-with-media-keys/)

alt + f2

gnome terminal

run

go god mode

```

sudo su
gedit  /usr/bin/paremote

```

then give gedit this script

```

#!/bin/bash
declare -i CURVOL=`cat ~/.volume` #Reads in the current volume
if [[ $1 == "increase" ]]
then
CURVOL=$(($CURVOL + 6554)) #3277 is 5% of the total volume, you can change this to suit your needs.
fi
if [[ $1 == "decrease" ]]
then
CURVOL=$(($CURVOL - 6554))
fi
if [[ $1 == "mute" ]]
then
pactl set-sink-mute 0 1
amixer -c 0 set Master unmute
exit
fi
if [[ $1 == "unmute" ]]
then
pactl set-sink-mute 0 0
amixer -c 0 set Master mute
exit
fi
if [[ $CURVOL -le 65540 && $CURVOL -ge 0 ]] # Check to see if the volume is a valid number (65540 was needed in this case because of how I rounded the increment)
then
pactl set-sink-volume 0 $CURVOL
echo $CURVOL > .volume # Write the new volume to disk to be read the next time the script is run.
exit
fi

```

save

in terminal 

```

chmod +x /usr/bin/paremote
exit

```

youve installed

```

paremote increase && paremote decrease && paremote mute && paremote unmute

```

for terminal....

now to script it to work with keys...

(unfinished) be back in 5

i think ill script unmute for + and - keys...  im gonna have to do something about the mute unmute toggle for alsa though....

for the + and - keys we will make bash scripts that run several commands at once.

we will name the bash scripts what the keys are named for simplicity.

again god mode

```

sudo su

```

```

cat > /usr/bin/XF86AudioLowerVolume << EOF
amixer -c 0 set Master 1dB-;
paremote decrease;
paremote unmute;
EOF
cat > /usr/bin/XF86AudioRaiseVolume << EOF
amixer -c 0 set Master 1dB+;
paremote increase;
paremote unmute;
EOF
chmod +x /usr/bin/XF86AudioLowerVolume
chmod +x /usr/bin/XF86AudioRaiseVolume

```

```

gedit /usr/bin/mute
[code]

and feed it this

[code]
#!/bin/bash
MUTE=`cat $HOME/.mute`;
test "$MUTE" = "1";
RETURN=$?;
if [[ $RETURN -eq 0 ]];
then
amixer -c 0 set Master unmute;
paremote unmute;
echo "0" > $HOME/.mute;
exit
fi
if [[ $RETURN -eq 1 ]];
then
amixer -c 0 set Master mute;
paremote mute;
echo "1" > $HOME/.mute;
exit
fi

```

and finally

```

chmod +x /usr/bin/mute
exit

```

almost have it!!!!  im probably going to use this scripts syntax for running its mute / unmute functions on alsa also, build the alsa commands to mute / unmute so both do so at the same time

```

cat > /usr/bin/XF86AudioMute <<EOF
mute;
EOF
chmod +x /usr/bin/XF86AudioMute

```

amixer -c 0 set Master unmute
amixer -c 0 set Master mute

are the alsa commands.....

this should be working 100% now i gotta re think this whole thing

#!/bin/sh
amixer -D pulse sset Master toggle;
(previous mute file note)

as of right now the volume up and down unmute, but the actual mute doesnt.  still same problem i was intending to fix, but at least i have a temp work around until then

amixer -D pulse set Master unmute

this might come in handy

still strange problems

---


---
title: "LIRC not working after upgrade to 12.04"
date: 2012-06-10
forum: Installation &amp; Upgrades
---

### Post by ExpressTrain on 2012-06-10
I just upgraded from 11.04 to 12.04 (stopping at 11.10 for about 5 minutes).  Primarily use this machine for MythTv (frontend and backend).  I have 2 Hauppauge 350 capture cards, one of them has the IR receiver cable plugged in.  After the upgrade everything seems to be working except the IR remote control.  I tried running "$sudo dpkg-reconfigure lirc" and it gave me this output:
 * Stopping remote control daemon(s): LIRC                               [fail] 
ls: cannot access /lib/modules/3.2.0-24-generic-pae/kernel/drivers/staging/lirc: No such file or directory
 * Loading LIRC modules                                                  [ OK ] 
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

I also looked in the /dev folder (because the mythtv frontend configuration menus referenced something in /dev/lirc), and there is nothing there beginning with "lirc".  

Can anyone point me in the right direction?

---

### Post by matthys on 2012-06-10
Got the same issue. But I did a new installation and try to get a Hauppauge PVR-150 working.

Anyone else any ideas?

---

### Post by danieleverywhere on 2012-06-25
Every update the same problem :( Got the same problem, too

---

### Post by danieleverywhere on 2012-06-25
At the moment it is working again! I did several things so I don't know what exactly helped :p

I try to list everything for you:

/etc/modprobe.d/lirc-blacklist.conf (or without .conf but that is deprecated)
```
#blacklist ati_remote                                                                                                        
#blacklist ati_remote                                                                                                        
blacklist lirc_atiusb                                                                                                        
blacklist ati_remote
```/etc/modprobe.d/rc_hauppauge_new-blacklist.conf
```
blacklist rc_hauppauge_new
```/etc/lirc/lircd/hardware.conf (maybe it doesn't like the START_LIRCD="true")
```

REMOTE="ATI/NVidia/X10 RF Remote (userspace)"
REMOTE_MODULES=""
REMOTE_DRIVER="atilibusb"
REMOTE_DEVICE=""
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="atiusb/lircd.conf.atilibusb"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="false"
START_LIRCMD=""
LOAD_MODULES="true"
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
```/usr/bin/once
```
#!/bin/sh
if [ $1 ]
then
  if [ "$(pidof $1)" ] 
  then
    echo "$1 bereits gestartet"
  else
    echo "$1 gestartet ($@)"
    $@
  fi
fi
exit 0
```/etc/rc.local
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

if [ -d /var/run/lirc ]; then
        echo "/var/run/lirc existiert bereits" || true
else
        mkdir /var/run/lirc || true
fi
/usr/bin/once /usr/sbin/lircd --output=/var/run/lirc/lircd --driver=atilibusb || true
exit 0
```~/.kde/Autostart/irexec-start.sh
```
#!/bin/sh
sleep 10
/usr/bin/once /usr/bin/irexec -d

exit 0
```Just informational or for comparison:
/etc/lirc/lircd.conf
```
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
begin remote

  name  /home/daniel/lircd.conf
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x0
  gap          139995
  min_repeat      5
  toggle_bit_mask 0x80800000

      begin codes
          Next                     0xF823
          Prev                     0x76A1
          Record                   0x7CA7
          Power                    0xD702
          Pause                    0x7EA9
          Stop                     0xFD28
          FastRewind               0x79A4
          Play                     0xFA25
          FastForward              0x7BA6
          Back                     0xF520
          Info                     0x84AF
          TVRecord                 0xED18
          TVEye                    0x5984
          TVSettings               0x0631
          TVWatch                  0x719C
          VolumeUp                 0xDE09
          VolumeDown               0x5D88
          VolumeMute               0xD500
          ChannelUp                0x608B
          ChannelDown              0xE10C
          WinMediaKey              0x709B
          CrossOK                  0xF31E
          CrossLeft                0x729D
          CrossRight               0xF41F
          CrossDown                0x77A2
          CrossUp                  0xEF1A
          VTRRed                   0x87B2
          VTRGreen                 0x0833
          VTRYellow                0x89B4
          VTRBlue                  0x0A35
          VTRText                  0x6B96
          Pad1                     0xE20D
          Pad2                     0x638E
          Pad3                     0xE40F
          Pad4                     0x6590
          Pad5                     0xE611
          Pad6                     0x6792
          Pad7                     0xE813
          Pad8                     0x6994
          Pad9                     0xEA15
          Pad0                     0x6C97
          PadStar                  0x0C37
          Pad#                     0x8DB8
          PadEnter                 0x0B36
          PadClear                 0x85B0
      end codes

end remote
```It would be nice to read a positive report from you ):P

---


---
title: "How get messaging for APCUPSD"
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by billydv on 2007-02-19
Well, since wall messaging doesnt work in Debian based distros for apcupsd (it doesn't send messaging to the desktop in kwrited), which really stinks so here is how to set it up to work with xmessaging instead.

First we need to change the /etc/apcupsd/apccontrol
make a copy and rename it original in case you ever want to go back and replace the contents with the following:

#!/bin/sh
#
# Copyright (C) 1999-2002 Riccardo Facchetti <riccardo@master.oasi.gpa.it>
#
# for apcupsd release 3.12.4 (19 August 2006) - debian
#
# platforms/apccontrol. Generated from apccontrol.in by configure.
#
# Note, this is a generic file that can be used by most
# systems. If a particular system needs to have something
# special, start with this file, and put a copy in the
# platform subdirectory.
#

#
# These variables are needed for set up the autoconf other variables.
#
prefix=/usr
exec_prefix=${prefix}

APCPID=/var/run/apcupsd.pid
APCUPSD=/sbin/apcupsd
SHUTDOWN=/sbin/shutdown
SCRIPTSHELL=/bin/sh
SCRIPTDIR=/etc/apcupsd
WALL=wall

#
# Concatenate all output from this script to the events file
# Note, the following kills the script in a power fail situation
# where the disks are mounted read-only.
# exec >>/var/log/apcupsd.events 2>&1

#
# This piece is to substitute the default behaviour with your own script,
# perl, or C program.
# You can customize every single command creating an executable file (may be a
# script or a compiled program) and calling it the same as the $1 parameter
# passed by apcupsd to this script.
#
# After executing your script, apccontrol continues with the default action.
# If you do not want apccontrol to continue, exit your script with exit
# code 99. E.g. "exit 99".
#
# WARNING: the apccontrol file will be overwritten every time you update your
# apcupsd, doing `make install'. Your own customized scripts will _not_ be
# overwritten. If you wish to make changes to this file (discouraged), you
# should change apccontrol.sh.in and then rerun the configure process.
#
if [ -f ${SCRIPTDIR}/${1} -a -x ${SCRIPTDIR}/${1} ]
then
${SCRIPTDIR}/${1} ${2} ${3} ${4}
# exit code 99 means he does not want us to do default action
if [ $? = 99 ] ; then
exit 0
fi
fi

case "$1" in
killpower)
echo "Apccontrol doing: ${APCUPSD} --killpower on UPS ${2}"
sleep 10
${APCUPSD} --killpower
xmessage -center "Apccontrol has done: ${APCUPSD} --killpower on UPS ${2}" &
;;
commfailure)
xmessage -center "Warning communications lost with UPS ${2}" &
;;
commok)
xmessage -center "Communications restored with UPS ${2}" &
;;
#
# powerout, onbattery, offbattery, mainsback events occur
# in that order.
#
powerout)
xmessage -center "Warning power loss detected on UPS ${2}" &
;;
onbattery)
xmessage -center "Power failure on UPS ${2}. Running on batteries." &
;;
offbattery)
;;
mainsback)
xmessage -center "Power has returned on UPS ${2}..." &
if [ -f /etc/apcupsd/powerfail ] ; then
printf "Continuing with shutdown." | ${WALL}
fi
;;
failing)
xmessage -center "Battery power exhaused on UPS ${2}. Doing shutdown." &
;;
timeout)
xmessage -center "Battery time limit exceeded on UPS ${2}. Doing shutdown." &
;;
loadlimit)
xmessage -center "Remaining battery charge below limit on UPS ${2}. Doing shutdown." &
;;
runlimit)
xmessage -center "Remaining battery runtime below limit on UPS ${2}. Doing shutdown." &
;;
doreboot)
xmessage -center "UPS ${2} initiating Reboot Sequence" &
${SHUTDOWN} -r now "apcupsd UPS ${2} initiated reboot"
;;
doshutdown)
xmessage -center "UPS ${2} initiated Shutdown Sequence" &
${SHUTDOWN} -h now "apcupsd UPS ${2} initiated shutdown"
;;
annoyme)
xmessage -center "Power problems with UPS ${2}. Please logoff." &
;;
emergency)
xmessage -center "Emergency Shutdown. Possible battery failure on UPS ${2}." &
${SHUTDOWN} -h now "apcupsd emergency shutdown"
;;
changeme)
xmessage -center "Emergency! Batteries have failed on UPS ${2}. Change them NOW" &
;;
remotedown)
xmessage -center "Remote Shutdown. Beginning Shutdown Sequence." &
${SHUTDOWN} -h now "apcupsd remote shutdown"
;;
restartme)
echo -n "Restarting APCUPSD Power Management: "
THEPID=`cat ${APCPID}`
kill ${THEPID}
rm -f ${APCPID}
rm -f /etc/apcupsd/powerfail
rm -f /etc/nologin
sleep 5
`${APCUPSD}`
echo "apcupsd"
;;
startselftest)
;;
endselftest)
;;
mastertimeout)
xmessage -center "Warning connection from master lost." &
;;
masterconnect)
xmessage -center "Connection from master established." &
;;
battdetach)
;;
battattach)
;;
*) echo "Usage: ${0##*/} command"
echo " warning: this script is intended to be launched by"
echo " apcupsd and should never be launched by users."
exit 1
;;
esac
##############################################


Now, the next thing we need to do is setup apcupsd to restart when we login or xmessaging wont work
Got to /home/(your user name)/.kde/Autostart and create a file called apcupsd-restart.desktop and insert the following text:


[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=
Comment=
Comment[en_US]=
Exec=sudo /etc/init.d/apcupsd restart
GenericName=
GenericName[en_US]=
Icon=
MimeType=;
Name[en_US]=
Path=
StartupNotify=false
Terminal=false
TerminalOptions=
Type=Application
X-DCOP-ServiceType=
X-KDE-SubstituteUID=false
X-KDE-Username=
X-KDE-autostart-after=kdesktop

#########################################

Save the file and right click, properties and change the file to make it execautable.

Next step requires a change in your sudoers file, in order for you to execute service starts change the following in your /etc/sudoers file:

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root ALL=(ALL) ALL
billydv ALL=(ALL) NOPASSWD: ALL

#################################
Sustitute billydv with your user name. If you are concerned about security you can read the documentation for sudo and actually set the sudo file to only allow you to restart apcupsd without a password but for me it doesnt matter, I prefer the skipped password.

Reboot your computer and unplug the cord to you UPS to test, you should then see xmessages on your desktop.

This will work with Ubuntu and Mepis or any other Debian or Ubuntu based Distro.

Good Luck

---


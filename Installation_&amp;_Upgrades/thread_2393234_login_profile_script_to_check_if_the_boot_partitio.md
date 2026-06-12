---
title: "login profile script to check if the boot partition has enough remaining space"
date: 2018-05-31
forum: Installation &amp; Upgrades
---

### Post by photonxp on 2018-05-31
The "Software Updater" in Ubuntu could check if the boot partition is full, but its default alert space is probably too low (several dozens of Mb) for some users. So I found this script that happened to work at ease only if with a few modifications. It puts a background job in your login profile file.

The script can report the space available of the boot partition to the login user when it's low, via notification. 
It can also be customized on the alert space of boot partition. Just change the **THRESHOLD** value.
The boot partition should be mounted as **/boot **(Run **df -h** to check), otherwise you should change the part **grep [[:blank:]]/boot$** in the script yourself.

------------------------------------ Below is content of **notify_when_boot_full.sh** -----------------------------------------------------------
```

#!/bin/bash 

# The scripts may or may not work, depending on your environment.
# The boot partition should be mounted as /boot (Run df -h to check), otherwise 
#     you should change the part `grep /boot$` in the script yourself.

# You need to move the script files to the /path/to/your_notify_dir, with proper permissions:
# notify_when_boot_full.sh
# notify_boot_in_profile.sh (See the other script below this one)

# INSTRUCTIONS ON LOGIN USAGE with .profile
# gedit ~/.profile 
# add the following line at the bottom of the profile file:
# /path/to/your_notify_dir/notify_boot_in_profile.sh & 
# (the & above is required, and also change the path to your script)
# The script will wait 10 minutes after you login by default
# If the script couldn't work in ~/.profile as background job &, check permissions and the log.

# You can also try cron job.
# Just change the file name notify_boot_in_profile.sh to notify_boot_in_cron.sh, as well as its content accordingly.


set -e

# sleep 600

# Change the THRESHOLD to the minimal boot space you alert
THRESHOLD=400
TARGET_USER=$USER

# Uncomment the next line if you try to use cron jobs. Use your login name to replace your_login_user_name 
#TARGET_USER=your_login_user_name

# YearMonthDay.HourMinute
datef=`date '+%Y%m%d.%H%M'`
echo 
echo $datef $0

# Get available boot memory in mega bytes, e.g., 100M
avail_m=$(df -h | grep [[:blank:]]/boot$ | awk '{ print $4 }')
echo $avail_m

# Change available boot memory to pure number without units, e.g., 100
avail_basic=${avail_m::-1}

# Notify the $TARGET_USER if available memory is below the $THRESHOLD
if [ $avail_basic -le $THRESHOLD ]
    then
    # adjust the environment value
    eval "export $(egrep -z DBUS_SESSION_BUS_ADDRESS /proc/$(pgrep -u $TARGET_USER gnome-session)/environ)"
    #export DISPLAY=:0
    /usr/bin/notify-send "Boot disk is low: $avail_m"
fi

exit 0

```

------------------------------------ Below is content of **notify_boot_in_profile.sh** -----------------------------------------------------------
```
#!/bin/bash 
# call this file in your profile as background job

set -e

# Adjust this value if it's too long or too short to wait
sleep 600

# You need to change this path for your own directory
BASE_DIR=/path/to/your_notify_dir
cd $BASE_DIR
SCRIPT=./notify_when_boot_full.sh
LOG_FILE=./notify_boot_in_profile.log
touch $LOG_FILE

$SCRIPT 2>&1 >>$LOG_FILE &

exit 0


```

:P

[A script to purge Ubuntu kernel files with user reservations]("https://ubuntuforums.org/showthread.php?t=2394104")

---

### Post by TheFu on 2018-05-31
**Logwatch** ?
[http://www.admin-magazine.com/Archive/2015/25/Lean-on-Logwatch](http://www.admin-magazine.com/Archive/2015/25/Lean-on-Logwatch)

---


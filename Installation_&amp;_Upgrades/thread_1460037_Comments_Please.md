---
title: "Comments Please"
date: 2010-04-22
forum: Installation &amp; Upgrades
---

### Post by Neill_R on 2010-04-22
How can I get a request to developers  or what is the best way to send suggestions?

My current concern is with shell scripts. They are not authored and are badly commented. I would like to see more explanation of what the script is doing and who wrote it. 

Also I am new to ubuntu and am unaware of how these scripts are updated as new releases of the kernel are applied. 

In particular if I make a change to a script is this there a requirement to repeat the change?

where or what calls / invokes the script could also be stated in the comments

---

### Post by nothingspecial on 2010-04-22
This is linux, modify whatever you like.

What script are you talking about.

---

### Post by Neill_R on 2010-04-22
The Modify what ever one likes approach if not coordinated with what the developers are doing is likely to lead to problems occurring in the future. This is a general point not a specific issue so I am talking about the scripts that exist or are provided by ubuntu / linux   for example

 this script /etc/rc.local

which as you will see i have changed on advise from 

[http://ubuntuforums.org/showthread.php?t=449319&page=3](http://ubuntuforums.org/showthread.php?t=449319&page=3)

This change has not as yet solved my problem but if it had I would want to be sure that this changes was  applied each and every time the system is updated or upgraded

For the moment I do clean installs and re apply my installs, removals and changes from a manual list of actions to be performed

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
# from [http://ubuntuforums.org/showthread.php?t=449319&page=3](http://ubuntuforums.org/showthread.php?t=449319&page=3)
sudo /usr/sbin/firestarter -s &
exit 0

---

### Post by oldos2er on 2010-04-22
Is there some particular reason you want to run firestarter at each boot? Maybe look into gufw, which is still being supported. [https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

---

### Post by nothingspecial on 2010-04-22
You would have to modify that file every time you reinstall.

I backup any modified config files in /etc then copy them all back.

---


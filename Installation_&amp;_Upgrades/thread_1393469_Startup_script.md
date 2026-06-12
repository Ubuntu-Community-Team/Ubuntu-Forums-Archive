---
title: "Startup script"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by allannk on 2010-01-29
Hello all, sorry if this isnt the right place to post. 

In order to access the internet, I have to login to a local firewall using pseudo-less TTY connection. 

ssh -T username@server

I do use a password aswell.
I made myself a script that works quite well, using EXPECT, but I really would like it to run by itself, silent, when my machine boots. 
The script have to keep running, as long as my computer is turned on

Script I made: (Name "/etc/init.d/knet")
--------------------------------------------
#!/usr/bin/expect -f
### BEGIN INIT INFO
# Provides:        knet
# Required-Start:     
# Required-Stop:    
# Default-Start:    2 3 4 5
# Default-Stop:        0 1 6
# Short-Description:    Starts ssh connection to firewall
### END INIT INFO

spawn ssh -T user@server
expect "Password:"
send "12345678 \n"
interact
---------------------------------------------

Im trying to add it to the init.d with the following command: 
"update-rc.d knet start 99 2 3 4 5 ."

Im not sure if its correct, but after quite a few tries, I still haven't had any luck. 

Can someone tell me, what im doing wrong? (Completely new to init.d)

Thanks in advance, 
-Allan

P.s. The script works just fine, aslong as I start it manually, when I boot my computer.

---

### Post by allannk on 2010-01-30
Noone? This shouldn't be a hard question for linux experts :-)

---

### Post by allannk on 2010-01-31
Bump

---

### Post by mrtomservo on 2010-01-31
I can't promise I can help, but this is what my init.d script looks like to run another script I made for an internet music server I created.  Your header looks a little short on info, you should really fill in the require-x info similar to this, and not leave it blank.  Generally init.d scripts aren't the actual script your running, it just manages it.  I'm not sure this adheres to standards, but it works just fine on my 9.10 server.  Hope this helps point you in the right direction! :)

#!/bin/sh
#/etc/init.d/start-lcdvc
#startup lcdvc at boot

### BEGIN INIT INFO
# Provides:          start-lcdvc
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start daemon at boot time
# Description:       Enable service provided by daemon.
### END INIT INFO

# Some things that run always
touch /var/lock/start-lcdvc

# Carry out specific functions when asked to by the system
case "$1" in
  start)
    echo -n "Starting Crow lcdvc daemon: start-lcdvc"
    /usr/bin/nice /usr/bin/lcdvc&
    echo "."
    ;;
  stop)
    echo "Stopping Crow lcdvc system daemon: start-lcdvc"
    /usr/bin/killall -9 lcdvc > /dev/null 2>&1
#    /usr/bin/killall -9 ledpulse > /dev/null 2>&1
#    /usr/bin/killall -9 mplayer > /dev/null 2>&1
    echo "."
    ;;
  restart)
    echo -n "Restarting Crow lcdvc system daemon: start-lcdvc"
    /usr/bin/killall -9 lcdvc > /dev/null 2>&1
    /bin/sleep 1
    /usr/bin/nice /usr/bin/lcdvc&
    echo "."
    ;;
  reload)
    echo -n "Reloading Crow lcdvc system daemon: start-lcdvc"
    /usr/bin/killall -9 lcdvc > /dev/null 2>&1
    /bin/sleep 1
    /usr/bin/nice /usr/bin/lcdvc&
    echo "."
    ;;
  force-reload)
    echo -n "Force Reloading Crow lcdvc system daemon: start-lcdvc"
    /usr/bin/killall -9 lcdvc > /dev/null 2>&1    /bin/sleep 1
    /usr/bin/nice /usr/bin/lcdvc&
    echo "."
    ;;
  *)
    echo "Usage: /etc/init.d/start-lcdvc {start|stop|restart|reload|force-reload}"
    exit 1
    ;;
esac

exit 0

---

### Post by mrtomservo on 2010-01-31
Actually what you'd want for the Required-x is probably:
$remote_fs $syslog $network

:)

---

### Post by allannk on 2010-01-31
Thanks for your reply, mrtomservo. 

I tried now to add the Require-Start, but it makes no difference. The script still isn't run. 

Im thinking it might be because, its never ending?
I need the ssh to be alive as long as my computer is powered on (or I cant access the internet), and maybe thats what prevents it from starting?

---

### Post by mrtomservo on 2010-01-31
Yeah, added the Required-x stuff won't make it work if it doesn't already, but it's still important. The fundamental problem is that you want to make an init.d script that calls the script you want to run.  So the init.d script should basically consist of the header and a case statement that handles the stop|start|etc stuff.  And then under the "start)" part of the init.d script, have it run another script that contains what you want it to do.  Having it run non stop is not a problem, just make sure you have it run in the background.  

I'm not sure if you need #!/usr/bin/expect -f , or if you should use #!/bin/sh or #!/bin/bash, does expect require this?

Anyway, for instance, make a new script file without the header info and stuff, just a plain sh/bash script that has the commands you want to run:

```
#!/bin/sh
#ssh connection to firewall

spawn ssh -T user@server
expect "Password:"
send "12345678 \n"
interact
```

Make it exececutable, place the above script where you like, and then call it from your init.d script like so:

```
#!/bin/sh
### BEGIN INIT INFO
# Provides: knet
# Required-Start: $remote_fs $syslog $network
# Required-Stop:  $remote_fs $syslog $network
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: Starts ssh connection to firewall
### END INIT INFO

case "$1" in
start)
echo -n "Starting ssh firewall connection"
/usr/bin/nice /script/you/just/saved &
echo "."
;;
stop)
echo "Stopping ssh firewall connection"
/usr/bin/killall -9 nameofscriptyoucreated > /dev/null 2>&1
echo "."
;;
restart)
echo -n "Restarting firewall connection"
/usr/bin/killall -9 nameofscriptyoucreated > /dev/null 2>&1
/bin/sleep 1
/usr/bin/nice /script/you/just/saved &
echo "."
;;
```

It's vital to make sure you add the "&" in the init.d script or your boot process might hang. :)  Hope this works!

---

### Post by allannk on 2010-01-31
Ah I see. This is much different than what I had tried. 

In an online meeting now, cant reboot, but hopefully this will work :-)
I will return once I have rebooted :-)

---

### Post by mrtomservo on 2010-01-31
Oh yeah, if done right you should be able to test if it works by doing something like:
```
/etc/init.d/script start
```

then

```
sudo pgrep script
```

To see if you get any process numbers, if not, it's not running.

Then try stopping it, check that it's NOT running.

That way you can check without having to reboot.  :)

---

### Post by allannk on 2010-01-31
Hey, I learned something there :-)

I think i've gotten a little further now. 

I could not manage to get expect to work, but I found something else, called sshpass. It works great, when I manually run it. 

$ /etc/init.d/script start

Then I can close the terminal again, and the internet keeps working (ssh still running), and pgrep also tell me the pid for it. 

But it still doesn't start by itself, when I turn on the computer.

I used the command from my top post, 
$ update-rc.d knet start 99 2 3 4 5 .
yet it doesnt by itself. pgrep doesn't find it either.

Also tried the startup application from System > Preferences > Startup Applications, still no luck

---

### Post by mrtomservo on 2010-02-01
Sorry, been crazy busy with a job interviews.  Whew! :)  Anyway, i'm glad I could help a little bit. :)  I think I might have reached the end of my usefulness though, as i'm not sure why it won't run automatically on boot.  From here, I think I would check the /var/log/syslog file and see if it is trying to tell you something or not. :)  I have this thread on watch though, so if you try something and get a little further, let me know and maybe I can help a bit more.

---


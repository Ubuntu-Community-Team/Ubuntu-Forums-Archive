---
title: "can't install sshd / openssh-server in ubuntu 11.10 from usb drive"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by alfonso78 on 2011-10-15
Hi,

I'm trying the new 11.10 and so I created a usb bootable stick with 512 MB persistent storage.

After I issue 
```
sudo apt-get install openssh-server
```

sshd is not running...

```
dpkg -l | grep ssh
```

correctly shows openssh-server installed.

So I tried to run 

```
sudo /usr/sbin/sshd -ddd
```

and there you go!

```
**Missing privilege separation directory: /var/run/sshd**
```

a simple 
```
sudo mkdir /var/run/sshd
```

did the trick!

Now I can run sshd using
```
sudo /usr/sbin/sshd
```

but the problem is still not solved...

If I try:

```
sudo service ssh status
```

I still get:

```
status: Unknown job: ssh
```

---

### Post by dalibor.klobucaric on 2011-11-09
Same problem here

solved it by adding 
```

sudo nano /etc/rc.local
```

adding this code above exit 0

```

if [ ! -d /var/run/sshd ]; then
   mkdir /var/run/sshd
   chmod 0755 /var/run/sshd
fi

```

now file looks like this

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
if [ ! -d /var/run/sshd ]; then
   mkdir /var/run/sshd
   chmod 0755 /var/run/sshd
fi


exit 0

```

and then adding run demon in cron

```

sudo crontab -e

```

so my cron file looks like this

```

# m h  dom mon dow   command
@reboot /usr/sbin/sshd

```
i know that this is not a solution but worked for me. If any one has the better one please i beg of you post it here.

I have Ubuntu 10.04
Best regards

---

### Post by narcisgarcia on 2012-08-20
Taken from [another forum thread]("http://ubuntuforums.org/showthread.php?t=1895174&page=2"):
```
sudo initctl reload-configuration
sudo service ssh start
```
(cleaner workaround without solving the bug)

---


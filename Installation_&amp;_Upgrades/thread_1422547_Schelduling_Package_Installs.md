---
title: "Schelduling Package Installs"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by Kelcin on 2010-03-05
This may not be the right forum, but for once in my life, I'm having trouble with which forum to put it in :).

First, I've got Ubuntu 8.04(Hardy Heron).
I've got the server and desktop version(though I think I lost my server CD).
I've got satellite internet, which only allows me to use a certain amount of bandwidth everyday. But I'm allowed to download all I want from 1-6 AM. But it takes on toll on my health for me to get up at 1 AM everyday.

I want to know if there is a way to schedule(with Synaptic or another package manager)package downloads.

Thanks in advance :).

---

### Post by Barriehie on 2010-03-05
> **Kelcin said:**
> This may not be the right forum, but for once in my life, I'm having trouble with which forum to put it in :).

First, I've got Ubuntu 8.04(Hardy Heron).
I've got the server and desktop version(though I think I lost my server CD).
I've got satellite internet, which only allows me to use a certain amount of bandwidth everyday. But I'm allowed to download all I want from 1-6 AM. But it takes on toll on my health for me to get up at 1 AM everyday.

I want to know if there is a way to schedule(with Synaptic or another package manager)package downloads.

Thanks in advance :).

There is, it's going to be a bit of a manual thing for you to install new packages but you can make the updates happen that way.  I would go into System > Administration > Software Sources and under the UpDates tab uncheck the boxes so that nothing will happen.  Now you'll have to make a crontab entry that will run the update whenever you like.  Let's say you want it to happen at 1:20 AM every Sunday, I'm picking 1:20 so you're provider has NO room to argue the clock...

Add this line to the end of your /etc/crontab file; you'll have to edit it as root user.

[color="green"]/etc/crontab[/color]
#
# Update my machine every Sunday at 01:20 Hours.
#
# m h dom mon dow user	command
```
20 1 * * 0 root apt-get update
```

Going to be just a bit of BASH scripting to install new packages; how are you with BASH?

I'm thinking have another crontab entry that will run a script to check for the instance of an install script; like this:

This will call check-install.sh
```
your crontab entry here.
```

This is **~/bin/check-install.sh**
```

#!/bin/bash
if [ -x /home/your_login_name/bin/do-install.sh ]; then
  /home/your_login_name/bin/do-install.sh &>/home/your_login_name/Desktop/Install_Log
else
  echo > /home/your_login_name/Desktop/No-Installs-Found
fi
exit 0

```

This is **~/bin/do-install.sh**, you'll have to make this one as you find packages to install.
```

#!/bin/bash
apt-get install package1 package2 package3 etc., etc., etc., &>/home/your_login_name/Desktop/Apt_Log
exit 0

```

Both of the above files will have to be executable, chmod +x, and your crontab entry will have to run as root.  If you don't have ~/bin directory then you'll have to make one and that's where I would put your scripts, kind of a standard thing...

HTH,
Barrie

---

### Post by Barriehie on 2010-03-14
Moving on!

---

### Post by Kelcin on 2010-03-15
I'm so sorry, every time I go to do what you posted, I end up having to do something else.

I'm OKish with BASH, though I haven't done much with it.

Thank you so much for posting!
I think I can do this, and it looks like it will work.

---

### Post by Barriehie on 2010-03-16
> **Kelcin said:**
> I'm so sorry, every time I go to do what you posted, I end up having to do something else.

I'm OKish with BASH, though I haven't done much with it.

Thank you so much for posting!
I think I can do this, and it looks like it will work.

:)  It was off the top of my head, sort of.  If you've any issues post back!  Mind I'm not a BASH expert but I'm having fun trying 8)

---


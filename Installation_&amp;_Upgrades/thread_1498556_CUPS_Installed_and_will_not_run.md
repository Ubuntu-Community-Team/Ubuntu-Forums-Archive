---
title: "CUPS Installed and will not run"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by steve32506 on 2010-05-31
I installed 10.04 today in Virtualbox. Everything seemed to go well until I tried to add a printer. I go into the System > Administration > Printing and the only option available is Connect. I try to connect to the localhost and get the following error:
CUPS Server Error: There was an error during the CUPS operation: 'failed to connect to server'.

I started CUPS and got an OK from the startup command.
I ran a ps -elf | less and cups is not listed. 

I tried removing and reinstalling CUPS and still it doesn't work.

Is there a way to get the startup items logged so I can find out what is going on? I checked all of the files in var/logs but the only things that's logged is in the auth.log and it's just the command I sent to start cups.

Thanks for your help.
Steve

---

### Post by steve32506 on 2010-06-02
I am still trying to figure this out. If anyone has any ideas about how to troubleshoot this or things I can try to make CUPS work, I'd appreciate it.

Thank you

---

### Post by bondo101 on 2010-06-02
Is it a network printer or a cable printer connected to your computer?
Go back into the installation dialogue box you should be able to search for the printer in the options they have.Theres a dialogue box with options click on the one that your situation requires.  If its network you will have to type the IP address in  to help find the printer. its almost an automatic setup.
     just trying to help

---

### Post by steve32506 on 2010-06-02
> **bondo101 said:**
> Is it a network printer or a cable printer connected to your computer?
Go back into the installation dialogue box you should be able to search for the printer in the options they have.Theres a dialogue box with options click on the one that your situation requires.  If its network you will have to type the IP address in  to help find the printer. its almost an automatic setup.
     just trying to help

I believe the CUPS service must be running in order to even get started with adding a printer. I am trying to install a network printer but the CUPS service will not start.

Thanks,
Steve

---

### Post by steve32506 on 2010-06-03
I was able to get it to work temporarily by opening a terminal and entering the command:
sudo /usr/sbin/cupsd

So, the problem has to do with the cups script in init.d. It is the one that comes with Ubuntu 10.04 and works on another one of my systems. There may be a permissions problems somewhere but I'm not Linux smart enough to figure it out. For now, I'll just manually enter the above command until I can figure it out.

Thanks,
Steve

---

### Post by mschap on 2010-06-27
> **steve32506 said:**
> I was able to get it to work temporarily by opening a terminal and entering the command:
sudo /usr/sbin/cupsd

So, the problem has to do with the cups script in init.d. It is the one that comes with Ubuntu 10.04 and works on another one of my systems. There may be a permissions problems somewhere but I'm not Linux smart enough to figure it out. For now, I'll just manually enter the above command until I can figure it out.

Thanks,
Steve

I am having the same problem now with two computers - this is getting annoying

---

### Post by Apostolique on 2010-06-30
I had the same problem as the OP and I fixed it the same way as the OP. I managed to make a bash script in order to do all the work for me:
```

#!/bin/bash
#
#Starts cups. (I guess)
#
echo "This will start cups in order to make the printer work. To continue, enter your password."
sudo /usr/sbin/cupsd
echo "Cups started successfully."

```

If you want to make a desktop shortcut, make a launcher, give it a name and in the command, type this: "_xterm -hold -e **FULL/PATH/TO/THE/SCRIPT.sh**_" without the quotes.

FULL/PATH/TO/THE/SCRIPT.sh = the path in order to get to your script.

I'm pretty sure there could be a way to make this auto run when the computer starts, but I don't know how yet.

---

### Post by mschap on 2010-07-01
I guess it raises the question however what in updates originally screwed this up and why is it not an easy fix.  We cannot be the only half dozen or so people experiencing this.

> **Apostolique said:**
> I had the same problem as the OP and I fixed it the same way as the OP. I managed to make a bash script in order to do all the work for me:
```

#!/bin/bash
#
#Starts cups. (I guess)
#
echo "This will start cups in order to make the printer work. To continue, enter your password."
sudo /usr/sbin/cupsd
echo "Cups started successfully."

```

If you want to make a desktop shortcut, make a launcher, give it a name and in the command, type this: "_xterm -hold -e **FULL/PATH/TO/THE/SCRIPT.sh**_" without the quotes.

FULL/PATH/TO/THE/SCRIPT.sh = the path in order to get to your script.

I'm pretty sure there could be a way to make this auto run when the computer starts, but I don't know how yet.

---

### Post by Cope57 on 2010-07-01
[http://localhost:631](http://localhost:631)

---

### Post by Apostolique on 2010-08-18
> **Cope57 said:**
> [http://localhost:631](http://localhost:631)

That will only work when CUPS is already running.

---


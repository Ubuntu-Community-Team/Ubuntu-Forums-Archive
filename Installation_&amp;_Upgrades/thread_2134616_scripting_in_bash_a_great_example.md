---
title: "scripting in bash a great example"
date: 2013-04-11
forum: Installation &amp; Upgrades
---

### Post by sp-1070 on 2013-04-11
So here i was today installing and removing some proograms, after having done about 10 i got bored by the process of typing 

```
apt-get remove --purge -y
```.

Sure one could simpley use the "up" button and just replace the package name of the earlier package with the one that is up for removal, but even that becomes a hassle if the pakcage name is somewhat longer or something like that.

So i started to look into a script that is used by a friend of mine and i somewhat edited it to make a cool program/script call it what you may.

Il first post the code then tell you what it does line by line.

```
 #!/bin/sh
if [ $1 = "-g" ]
then apt-get install $2 --no-install-recommends -y

elif [ $1 = "-r" ]
then apt-get remove --purge $2 -y

elif [ $1 = "-u" ]
then apt-get update && apt-get upgrade -y 

fi
```

```
#!/bin/sh
```

Tells the system what interperter should be used to run the script

```
if [ $1 = "-g" ]
then apt-get install $2 --no-install-recommends -y
```

tells that if the command is followed by -g the action to rin is apt-get install (then the argument witch in this case is always a program name) --no-install-recommends tells the apt-get to not install anny recommended programs with the program you wanted.
-y is simply so that you dont have to answer yes on the "to be installed" portion skipping one more step in the installation process.

the other codes are basicly the same with difrent functions -r to remove -purge a program without asking confirmation (a tat dangerous) and lastly -u to update apt-get and upgrade all the packages that have updates available.

now a more detailed way on how to make this script in screenshots is in the attachments.



I hope youll enjoy it and have fun !

---


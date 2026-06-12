---
title: "teamspeak 3 server"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by stream_cry on 2011-02-21
ive been looking everywhere tryed so many different ways people have posted on the internet nothing is working and the other forums arents answering any of the topics can someone please help me out on how to install teamspeak3 server on ubuntu server

i tryed it off [http://forum.teamspeak.com/showthread.php/55383-Howto-install-TeamSpeak-3-server-on-Ubuntu-10.04-%28Lucid%29?p=274923#post274923](http://forum.teamspeak.com/showthread.php/55383-Howto-install-TeamSpeak-3-server-on-Ubuntu-10.04-%28Lucid%29?p=274923#post274923) and got a few errors 

didnt try it off [http://hackdev.com/2009/12/teamspeak-3-server-on-ubuntu/](http://hackdev.com/2009/12/teamspeak-3-server-on-ubuntu/) cause the version was too old... can anyone help me out pls?

---

### Post by lukeiamyourfather on 2011-02-21
Can you be more specific about what isn't working? For all we know "it isn't working" could mean anything.

---

### Post by stream_cry on 2011-02-22
i pretty much need the steps cause im confused with these other ones they've handed out it seems to me there is different ways of doing it im just looking for the easiest way i guess

---

### Post by lukeiamyourfather on 2011-02-22
> **stream_cry said:**
> i pretty much need the steps cause im confused with these other ones they've handed out it seems to me there is different ways of doing it im just looking for the easiest way i guess

The directions seemed alright from what I was looking at. What command was giving you trouble, or is it all of it, like where to start? The more information you can give the better. If you just say it doesn't work and want the easiest way it won't help. We need to know specifically where things stopped working or specifically what part is not making sense.

---

### Post by stream_cry on 2011-02-23
i was using putty  to do it and i got up to testing to start the server and it froze so i  re did it and it did nuthing and well i tryed the update and the update  gave me an error... so not sure what happend but i checked the files and  the server admin username and password were created but it didnt tell  me the server started when i tryed it again and it didnt tell me if it  stopped i check the processes and didnt see anything...
```
root@ubuntuserver:~# update-rc.d teamspeak default
update-rc.d: warning: /etc/init.d/teamspeak missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
       update-rc.d [-n] <basename> disable|enable [S|2|3|4|5]
                -n: not really
                -f: force
```

i also wasnt sure how to config the firewall lol i dont even remember if i have 1 im just running a simple copy of ubuntu server

---

### Post by lukeiamyourfather on 2011-02-23
> **stream_cry said:**
> i was using putty  to do it and i got up to testing to start the server and it froze so i  re did it and it did nuthing and well i tryed the update and the update  gave me an error... so not sure what happend but i checked the files and  the server admin username and password were created but it didnt tell  me the server started when i tryed it again and it didnt tell me if it  stopped i check the processes and didnt see anything...
```
root@ubuntuserver:~# update-rc.d teamspeak default
update-rc.d: warning: /etc/init.d/teamspeak missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
       update-rc.d [-n] <basename> disable|enable [S|2|3|4|5]
                -n: not really
                -f: force
```

i also wasnt sure how to config the firewall lol i dont even remember if i have 1 im just running a simple copy of ubuntu server

By default the firewall is disabled. If you need to enable it I'd worry about that after you get the other services running. Try defaults instead of default, like this and also use sudo (which makes you root/administrator).

```
sudo update-rc.d teamspeak defaults
```

You can also manually stop and start the service like this, or check the status.

```

sudo service teamspeak status
sudo service teamspeak stop
sudo service teamspeak start
sudo service teamspeak restart

```

---

### Post by stream_cry on 2011-02-23
ill see what i can do but when i started the server for the first time when it froze it never started up and it didnt give me any of the server info meaning not the original server ticket

---

### Post by stream_cry on 2011-02-23
so the update seemd to work 
[EMAIL="root@ubuntuserver"]```
 
[/EMAIL][EMAIL="root@ubuntuserver"]root@ubuntuserver[/EMAIL][EMAIL="root@ubuntuserver"]:~# sudo update-rc.d teamspeak defaults
update-rc.d: warning: /etc/init.d/teamspeak missing LSB information
update-rc.d: see <[/EMAIL][http://wiki.debian.org/LSBInitScripts](http://wiki.debian.org/LSBInitScripts)[EMAIL="root@ubuntuserver"]>
 Adding system startup for /etc/init.d/teamspeak ...
   /etc/rc0.d/K20teamspeak -> ../init.d/teamspeak
   /etc/rc1.d/K20teamspeak -> ../init.d/teamspeak
   /etc/rc6.d/K20teamspeak -> ../init.d/teamspeak
   /etc/rc2.d/S20teamspeak -> ../init.d/teamspeak
   /etc/rc3.d/S20teamspeak -> ../init.d/teamspeak
   /etc/rc4.d/S20teamspeak -> ../init.d/teamspeak
   /etc/rc5.d/S20teamspeak -> ../init.d/teamspeak


```[/EMAIL]
 
 as you can see below the teamspeak server didnt react to the commands am i doing something wrong? cause i followed the commands correct.
```
[EMAIL="root@ubuntuserver"]root@ubuntuserver[/EMAIL]:~# sudo service teamspeak status
[EMAIL="root@ubuntuserver:/"]root@ubuntuserver:/[/EMAIL]# sudo service teamspeak start
[EMAIL="root@ubuntuserver:/"]root@ubuntuserver:/[/EMAIL]# sudo su
[EMAIL="root@ubuntuserver:/"]root@ubuntuserver:/[/EMAIL]# sudo service teamspeak restart
[EMAIL="root@ubuntuserver:/"]root@ubuntuserver:/[/EMAIL]# sudo service teamspeak stop

```
 
we are almost there thanks for helping so far :)

---

### Post by lukeiamyourfather on 2011-02-23
> **stream_cry said:**
> so the update seemd to work 
[EMAIL="root@ubuntuserver"]```
 
[/EMAIL][EMAIL="root@ubuntuserver"]root@ubuntuserver[/EMAIL][EMAIL="root@ubuntuserver"]:~# sudo update-rc.d teamspeak defaults
update-rc.d: warning: /etc/init.d/teamspeak missing LSB information
update-rc.d: see <[/EMAIL][http://wiki.debian.org/LSBInitScripts](http://wiki.debian.org/LSBInitScripts)[EMAIL="root@ubuntuserver"]>
 Adding system startup for /etc/init.d/teamspeak ...
   /etc/rc0.d/K20teamspeak -> ../init.d/teamspeak
   /etc/rc1.d/K20teamspeak -> ../init.d/teamspeak
   /etc/rc6.d/K20teamspeak -> ../init.d/teamspeak
   /etc/rc2.d/S20teamspeak -> ../init.d/teamspeak
   /etc/rc3.d/S20teamspeak -> ../init.d/teamspeak
   /etc/rc4.d/S20teamspeak -> ../init.d/teamspeak
   /etc/rc5.d/S20teamspeak -> ../init.d/teamspeak


```[/EMAIL]
 
 as you can see below the teamspeak server didnt react to the commands am i doing something wrong? cause i followed the commands correct.
```
[EMAIL="root@ubuntuserver"]root@ubuntuserver[/EMAIL]:~# sudo service teamspeak status
[EMAIL="root@ubuntuserver:/"]root@ubuntuserver:/[/EMAIL]# sudo service teamspeak start
[EMAIL="root@ubuntuserver:/"]root@ubuntuserver:/[/EMAIL]# sudo su
[EMAIL="root@ubuntuserver:/"]root@ubuntuserver:/[/EMAIL]# sudo service teamspeak restart
[EMAIL="root@ubuntuserver:/"]root@ubuntuserver:/[/EMAIL]# sudo service teamspeak stop

```
 
we are almost there thanks for helping so far :)

You might try calling the server itself rather than using the service command. An example is below.

```
sudo /etc/init.d/teamspeak status
```

The other flags should work there too like restart, start, stop, etc.

---

### Post by stream_cry on 2011-02-23
so idk what i did when i tryed to install teamspeak originally but every now and then the server will decide it wants to do something weird. And im not sure what its doing when i watch it when it does it.. it seems that it starts shutting down processes 1 by 1 and jsut stops... i have a mumble server already running on here and i need to add teamspeak lol any idea what it could be doing?

so yea i was repairing the packages and it did it again idk what it is :/ lol i hope i dont have to reinstall it

lol i think i repaired the issue ill post about it if it does it again.... anyway i tryed the commands and still no reaction by the server 

```
root@ubuntuserver:~# sudo /etc/init.d/teamspeak status
root@ubuntuserver:~# sudo /etx/init.d/teamspeak start
sudo: /etx/init.d/teamspeak: command not found
root@ubuntuserver:~# sudo /etc/init.d/teamspeak start
root@ubuntuserver:~#

```

---

### Post by stream_cry on 2011-02-23
so yea it looks like theres a boot up error i cant copy the code so im going to try to type it...

```

fsck from until-linux-ng 2.17.2
/dev/dsda1:Clean, 81602/4882432 files, 17291600/19513856 blocks (check in 4 mounts)[
[    17.549026] shpchp 0000:00:01.0: Cannot reserve MMIO region
The disk drive for /dev/mapper/cryptswap1 is not ready yet or not present
Continue to wait; or Press S to skip mounting or M for manual recovery
* Starting AppArmor profiles                                                             [ OK ]
* Starting MTA
                                                                             
                                                                                                      [ OK ]                        
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
bash: no job control in this shell
root@ubuntuserver:/#
```

so thats exactly what it says but it boots to that and stops and i cant do anything... but if i log in to ssh with putty i can control everything type commands and stuff

---

### Post by Tweak42 on 2011-03-07
A little off topic, but I was able to get teamspeak3 server running on a (free for a year) basic linux Amazon Web services cloud instance.  Also setup a Mumble server too.  Cool thing about it is if you mess something up, you can just nuke the instance and start over again, no muss no fuss.

---


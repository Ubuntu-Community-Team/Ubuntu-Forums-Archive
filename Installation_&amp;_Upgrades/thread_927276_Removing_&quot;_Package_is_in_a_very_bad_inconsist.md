---
title: "Removing &quot; Package is in a very bad inconsistent state&quot;"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by Cowpoke on 2008-09-22
My xubuntu installation is stuck...  I need to clean up a package whose install failed.  While I usually use the GUI, I present the command line jobs I am using to fix this.  Not sure if that has/had an impact...

My dpkg list command gives the following output:
```
root@Pony-Up:/# dpkg -l | grep sipx
pHR sipxconfig-vsftpd                          3.8.0-1                                              sipXecs sipconfig configuration for vsftpd
iHR sipxpbx                                    3.8.0-1                                              sipXecs SIP PBX

```

I am not sure how to read the three letter codes at the left margin - any interpretation is appreciated!

When I enter the dpkg purge command, I get the following:
```
root@Pony-Up:/# dpkg -P sipxpbx
dpkg: error processing sipxpbx (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 sipxpbx

```

I have tried to install/reinstall the package -- no success though. :confused:

Is there some quick way to fix this problem -- it keeps me from running any updates. :mad:

TIA!

Cowpoke

---

### Post by Pumalite on 2008-09-22
Try:
sudo dpkg --remove --force-remove-reinstreq <packagename>

---

### Post by Cowpoke on 2008-09-23
> **Pumalite said:**
> Try:
sudo dpkg --remove --force-remove-reinstreq <packagename>

Thx Pumalite!

I ran sudo su first -- this just puts me into root mode.

Running the following commands in sequence gave me the corresponding results:
```
root@Pony-Up:/# dpkg --remove --force-remove-reinstreq sipxpbx
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 171022 files and directories currently installed.)
Removing sipxpbx ...
dpkg: error processing sipxpbx (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 sipxpbx
```

```

root@Pony-Up:/# dpkg --remove --force-remove-reinstreq sipxconfig-vsftpd
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 171022 files and directories currently installed.)
Removing sipxconfig-vsftpd ...
chown: cannot access `/var/lib/sipx/configserver/phone/profile/tftproot': No such file or directory
dpkg: error processing sipxconfig-vsftpd (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 sipxconfig-vsftpd
```

Checking the status of my pckg's afterward I get:

```

root@Pony-Up:/home/jem# dpkg -l | grep sipx
rHR sipxconfig-vsftpd                          3.8.0-1                                              sipXecs sipconfig configuration for vsftpd
rHR sipxpbx                                    3.8.0-1                                              sipXecs SIP PBX

```

I notice the three character coding at the left of the results has a different first letter 'r'.  Previously, it was 'p' and 'i' respectively.

...what to do? #-o

Ride on...
Cowpoke

---

### Post by Pumalite on 2008-09-23
Try to reinstall it.

---

### Post by Cowpoke on 2008-09-23
> **Pumalite said:**
> Try to reinstall it.

...no luck. :(

---

### Post by Cowpoke on 2008-09-23
> **Pumalite said:**
> Try to reinstall it.

:guitar: 
Alright!  I got sipxconfig-vsftpd cleared out!  Thx much Pumalite!  I faked out the install/uninstall procedure by creating dummy files that were missing per the error msgs.

sipxpbx doesn't give me such discrete leads though...  It just informs me that there is an error in the post-removal subprocess...

Is there anywhere I can look for more verbose information?  Is there perhaps a switch I can use with the dpkg command?


TIA

---

### Post by Pumalite on 2008-09-23
Check /var/lib/dpkg/status
Find out the state of the package

---

### Post by Cowpoke on 2008-10-03
Hey Pumalite!

Thanks for your advice.  I was finally able to get the last remnants of this stuck package off my machine!

As I figured, I have about 23 upgrades that my machine is now picking up.  I couldn't pick up anything with that package stuck as it was.

Thanks again!
Cowpoke

...ride on...:guitar:

---

### Post by Pumalite on 2008-10-03
You are welcome. Good luck!

---

### Post by pandabeer on 2009-11-09
Thanks a lot dude,

deleting in the package from the status file totally made it working again.

Thanks

---


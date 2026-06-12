---
title: "dpkg: error processing some upgrades"
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by bobwdn on 2010-08-20
I am running Lucid 32-bit server P3 command line server version that began life as a 9.10-server, now upgraded to 10.04. Upgrade has been running since June, 2010. A few weeks ago, I realized that phpldapadmin was not running correctly. In finding the solution for the phpldapadmin issue, now, upgrades are giving me the following:```
admin@myserver:/$ sudo apt-get update[sudo] password for administrator: 
Hit http://us.archive.ubuntu.com lucid Release.gpg
Get:1 http://security.ubuntu.com lucid-security Release.gpg [189B]
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US

>>>> snip <<<<<      
                                          
Reading package lists... Done
administrator@wdnserver:/$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up grub-pc (1.98-1ubuntu7) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up samba-common (2:3.4.7~dfsg-1ubuntu3.1) ...
dpkg: error processing samba-common (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of samba-common-bin:
 samba-common-bin depends on samba-common (>= 2:3.4.0~pre1-2); however:
  Package samba-common is not configured yet.
dpkg: error processing samba-common-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 2:3.4.7~dfsg-1ubuntu3.1); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smbfs:
 smbfs depends on samba-common (= 2:3.4.7~dfsg-1ubuntu3.1); however:
  Package samba-common is not configured yet.
dpkg: error processing smbfs (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because MaxReports is reached already
        No apport report written because MaxReports is reached already
                                                                      Errors were encountered while processing:
 grub-pc
 samba-common
 samba-common-bin
 smbclient
 smbfs
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have read many posts trying to find a reference to ```
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 10
```

because this started with grub-pc being the first and only package that refused to install. I have yet to find a direct reference to 'error exit status 10'. I find many other status codes, but few of 'status 10'.

Now, unfortunately, work took me away for a few of weeks and now I am getting errors for:

 grub-pc
 samba-common
 samba-common-bin
 smbclient
 smbfs

So, I am "in over my head" as far as my experience. But, like all Ubuntu/Linux issues I am learning.

I have tried ```
apt-get -f install
``` and that does work.

I have tried ```
apt-get purge grub-pc
``` and then re-installing grub-pc still gives same error.

And finally there are many other attempts, all with the same result.

Now, confused and "over my head", can anyone help me? Please!

---

### Post by Shazaam on 2010-08-20
Have you tried...
```
sudo dpkg --configure -a
```

---

### Post by Soul-Sing on 2010-08-20
from this forum, this compl. uninstalls and reinstalls grub2



> sudo mv /boot/grub /boot/grub_OLD

sudo mkdir /boot/grub

sudo apt-get --purge remove grub2
sudo apt-get --purge remove grub-pc

sudo apt-get --purge remove grub-common

sudo apt-get install grub-pc

sudo update-grub

sudo grub-install /dev/sda 

---

### Post by bobwdn on 2010-08-21
Shazaam, thanks for your suggestion.


leoquant, 

I processed the commands you posted and I still have the same result. Because I am totally confused, I am going to ask the simplest questions, so please bear with me.

This all started with the package 'grub-pc', do I ignore, for the moment, the other packages listed (samba-common, samba-common-bin, smbclient & smbfs) and focus my attention on resolving the 'grub-pc' issue? 

A few days ago, when I tried to purge the other packages listed (samba-common, samba-common-bin, smbclient & smbfs) apt-get also wanted to purge my 'backuppc' package. I chose NOT to proceed with the purge.

BTW, when I ran those commands listed, I do not have a 'grub2' package to remove. Does this matter?

Next suggestion?

---

### Post by drs305 on 2010-08-21
If you want to try to purge and reinstall grub-pc, you can run these commands. The associated packages in Grub2 are grub-pc and grub-common. You don't need to mention "grub2".

There is a good chance you will still have problems with the other packages, but you can at least see if you can eliminate the grub-pc error. You don't need to mention both packages in the commands to get them both uninstalled/reinstalled.

```
sudo apt-get purge grub-common && sudo apt-get install grub-pc
```

Make sure your Internet connection is working and you have a reliable power source before running the command, as you will temporarily lose your bootloader. Tab to "OK" for the first couple of messages, and when it's time to select the device TAB to your Ubuntu drive, use the spacebar to select it (*), then TAB to OK and press ENTER.

---

### Post by bobwdn on 2010-08-21
drs305 thank you for your reply.

I tried your suggestion. And still have the same result:

```
Setting up grub-pc (1.98-1ubuntu7) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 10
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 samba-common
 samba-common-bin
 smbclient
 smbfs
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

However, during the purge of 'grub-pc' I was asked if I wanted to remove 'grub-pc' and that there would not be an available bootloader, if I did this. I understand that I am about to put 'grub-pc' back, so I changed the default to'yes' and proceeded.

During the re-installation of grub-pc, I received the following image:

[ATTACH]167115[/ATTACH]

that I do not know the answer and left the line blank, re-installing 'grub-pc'.

Should I enter something in this line?

---

### Post by drs305 on 2010-08-21
> **bobwdn said:**
> 

During the re-installation of grub-pc, I received the following image:

[ATTACH]167115[/ATTACH]

that I do not know the answer and left the line blank, re-installing 'grub-pc'.

Should I enter something in this line?

No, it is normally blank and you can just tab to OK.


If you still get the error, you can try this to possibly remove the error message. This method 'bypasses' APT, which is normally not recommended, but since it appears broken it may work and won't hurt anything if it doesn't.

You will rename the post-installation script so it can't run, and therefore can't generate an error message:

```
sudo mv /var/lib/dpkg/info/grub-pc.postinst /var/lib/dpkg/info/grub-pc.postinst-bad
```

If the error remains after you run your updates, change it back the way it was:
```
sudo mv /var/lib/dpkg/info/grub-pc.postinst-bad /var/lib/dpkg/info/grub-pc.postinst
```

---

### Post by bobwdn on 2010-08-21
Thanks, again, drs305.

Ok, that worked, although not quite like I thought. So, I did:

```
sudo mv /var/lib/dpkg/info/grub-pc.postinst /var/lib/dpkg/info/grub-pc.postinst-bad
```

and when I did:

```
sudo mv /boot/grub /boot/grub_OLD
sudo mkdir /boot/grub
sudo apt-get --purge remove grub2
```

Then I noticed that it did the following:

```
admin@myserver:~$ sudo apt-get --purge remove grub2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub2 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up grub-pc (1.98-1ubuntu7) ...
Setting up samba-common (2:3.4.7~dfsg-1ubuntu3.1) ...
dpkg: error processing samba-common (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of samba-common-bin:
 samba-common-bin depends on samba-common (>= 2:3.4.0~pre1-2); however:
  Package samba-common is not configured yet.
dpkg: error processing samba-common-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 2:3.4.7~dfsg-1ubuntu3.1); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smbfs:
 smbfs depends on samba-common (= 2:3.4.7~dfsg-1ubuntu3.1); however:
  Package samba-common is not configured yet.
dpkg: error processing smbfs (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    No apport report written because MaxReports is reached already
                                  Errors were encountered while processing:
 samba-common
 samba-common-bin
 smbclient
 smbfs
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Notice that the errors only list samba-common, samba-common-bin, smbclient & smbfs. The other four packages that are troublesome. So, I finished with 'update-grub' and installed grub to the hard drive with 'grub-install /dev/sda'. And the server rebooted just fine.

Now, what is your suggestion to correct these other four packages errors? As you can see, I am getting the same error exit status 10 for these!

---

### Post by drs305 on 2010-08-21
> **bobwdn said:**
> Now, what is your suggestion to correct these other four packages errors? As you can see, I am getting the same error exit status 10 for these!

You can try to use the "backup" status file. I didn't go to that originally since often it is already overwritten by the time a user posts to these forums. But let's try to restore the older status file to see if that resolves the problem:

```

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-bad
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status

```

If this doesn't work, move things back the way they were:
```

sudo mv /var/lib/dpkg/status-bad /var/lib/dpkg/status

```


If things still aren't working, once things are back the way they were, you *could* rename each of the "postinst" files for each package giving you problems as I detailed in the previous post.  I have to caution that moving all these files around is risking breaking APT to a point where you won't even know where you started.

---

### Post by bobwdn on 2010-08-22
The 'rename each of the "postinst" files' steps have resolved my issues.

I cannot thank you enough except to simple say . . . THANKS!!!!

---


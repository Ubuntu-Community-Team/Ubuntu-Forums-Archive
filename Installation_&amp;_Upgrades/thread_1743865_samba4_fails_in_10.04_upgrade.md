---
title: "samba4 fails in 10.04 upgrade"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Hotel on 2011-04-29
Hi

When I upgraded to Ubuntu 11.04 the install of the samba4 failed. Now everytime I install/remove packages I get an error about it:

```
Setting up samba4 (4.0.0~alpha15~git20110124.dfsg1-2ubuntu1) ...
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ldb: unable to stat module /usr/lib/samba/ldb/modules/samba : No such file or directory
ldb: failed to initialise module /usr/lib/samba/ldb/modules/samba : Unavailable
ldb: failed to initialise module /usr/lib/samba/ldb/modules : Unavailable
WARNING: Module [samba_dsdb] not found - do you need to set LDB_MODULES_PATH?
Unable to load modules for /var/lib/samba/private/sam.ldb: Failed to load modules from: /usr/lib/samba/ldb

Traceback (most recent call last):
  File "/usr/share/samba/setup/upgradeprovision", line 1597, in <module>
    ldbs = get_ldbs(paths, creds, session, lp)
  File "/usr/lib/python2.7/dist-packages/samba/upgradehelpers.py", line 159, in get_ldbs
    ldbs.sam = SamDB(paths.samdb, session_info=session, credentials=creds, lp=lp, options=["modules:samba_dsdb"])
  File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 53, in __init__
    options=options)
  File "/usr/lib/python2.7/dist-packages/samba/__init__.py", line 110, in __init__
    self.connect(url, flags, options)
  File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 66, in connect
    options=options)
_ldb.LdbError: (80, 'Failed to load modules from: /usr/lib/samba/ldb\n')
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This error is the same one that occurred during the upgrade. Any help to resolve this issue would be appreciated (preferably without removing samba as I regularly access windows shares).

P.S
The upgrade to 11.04 seemed to work even though it said it failed due to this error.

---

### Post by cobolt01 on 2011-04-30
I had the same problem.

---

### Post by Krister Hallergard on 2011-04-30
Same here after upgrade to 11.04, though the local network still works.
Cheers, Krister

---

### Post by nush on 2011-04-30
me too

---

### Post by daviti.giorgadze on 2011-05-01
Dear Ubuntu Support, 
Please post bug fix, same problem to my IBM ThinkPad T61


Kind Regards, 
David

---

### Post by nush on 2011-05-01
ive saved my data and done a fresh install, worked for me

---

### Post by mörgæs on 2011-05-01
+1 for the fresh install

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by lracicot on 2011-05-03
I have the same problem here too. :(

---

### Post by Krister Hallergard on 2011-05-05
Made a fresh install instead of an upgrade, and Samba still failed.  Maybe I should qualify that.  As I mentioned above the Samba shares still work, but what does not work is the configuration program:

root@DESKTOP:~# system-config-samba
Traceback (most recent call last):
  File "/usr/sbin/system-config-samba", line 44, in <module>
    import mainWindow
  File "/usr/share/system-config-samba/mainWindow.py", line 30, in <module>
    import gtk.glade
ImportError: No module named glade

Could it be so that the system-config-samba is a gnome program, whereas I am using Kubuntu 11.04?

---

### Post by lracicot on 2011-05-12
I fixed the problem.
```

sudo rm /usr/lib/samba/ldb/modules/samba 
```I don't know if it brokes something else on the system, but I still can access samba shares.

---

### Post by headvampyre@hotmail.co.uk on 2011-05-21
Hi, i know this is bringing a dead thread alive, but why dont you just compile samba4? It hardly takes any time, and is likely to be much more stable that Ubuntu's packages. Just make sure you remove Samba3 first.

---

### Post by gstat on 2011-10-15
I tried this 

sudo apt-get remove --purge samba-common
sudo apt-get remove --purge samba
sudo apt-get install samba

and it seems to work

---

### Post by f6iqa on 2011-12-13
> **gstat said:**
> I tried this 

sudo apt-get remove --purge samba-common
sudo apt-get remove --purge samba
sudo apt-get install samba

and it seems to work

I had to type
sudo apt-get autoremove
instead of
sudo apt-get remove --purge samba

Now no more warnings.
Thanks.
Joss.

---


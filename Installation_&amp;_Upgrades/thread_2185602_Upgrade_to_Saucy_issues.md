---
title: "Upgrade to Saucy issues"
date: 2013-11-03
forum: Installation &amp; Upgrades
---

### Post by daviddevee on 2013-11-03
I have searched and not found an answer to my paticular problem. So here goes my question I am trying to upgrade to from 13.04 to 13.10. The first issue was I tried using the updater GUI and that did nothing. It would just hang and then close. So Then I did some research and found the cli update. I did :

sudo apt-get update
sudo apt-get upgrade
sudo apt-get distro-upgrade

then
sudo apt-get install system-updater-core
sudo do-release-upgrade

recieved the following message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
david@HB:~$ sudo apt-get install update-manager-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-manager-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
david@HB:~$ sudo do-release-upgrade
Checking for a new Ubuntu release
Err Upgrade tool                                                               
  500  ( The request was rejected by the HTTP filter. Contact your ISA Server administrator.  ) [IP: 91.189.91.14 80]
Get:1 Upgrade tool signature [198 B]                                           
Fetched 198 B in 0s (0 B/s)                                                    
WARNING:root:file 'saucy.tar.gz' missing
Failed to fetch
Fetching the upgrade failed. There may be a network problem. 

Everything else network wise is working fine

---

### Post by heir4c on 2013-11-03
When you have the desktop version use the "Update-Manager" to upgrade:
[http://www.ubuntu.com/download/desktop/upgrade](http://www.ubuntu.com/download/desktop/upgrade)
And click on the "Upgrade"button.
When you don't get the upgrade message (see the second screenshot in the link) than you click on "Settings". 
There you go to the third Tab and in the bottom you can choose what version you want to update: LTS or Every version (or something like that, I have a Dutch version so I don't now what it says in English).
Than you close the window and reload the updatemanager.

Or install 13.10 'fresh' on a new partition, there are many problems with updating when you look at this forum. I upgrade never, because of the many troubles there are. I do always a fresh install.

---

### Post by ian-weisser on 2013-11-03
> **daviddevee said:**
> 
david@HB:~$ sudo do-release-upgrade
Checking for a new Ubuntu release
Err Upgrade tool                                                               
  [COLOR=#ff0000]500  ( The request was rejected by the HTTP filter. Contact your ISA Server administrator.  ) [IP: 91.189.91.14 80][/COLOR]
Get:1 Upgrade tool signature [198 B]                                           
Fetched 198 B in 0s (0 B/s)                                                    
WARNING:root:file 'saucy.tar.gz' missing
Failed to fetch
Fetching the upgrade failed. There may be a network problem. 

Please post the contents of your /etc/apt/sources.list
What version of Ubuntu are you trying to upgrade from?

---

### Post by lunixgeek on 2013-11-03
I am also having the same issue upgrading from 13.04 -> 13.10.
The GUI failed to continue installing right after the first two files were downloaded at the very beginning.
I then tried an install from the terminal and this is what came back.
I do have an Intel I7 with an SSD as my boot drive.  I have /tmp using real RAM.

# update-manager -d

** (update-manager:15159): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-5rvCQU6kts: Connection refused
Checking for a new Ubuntu release

** (do-release-upgrade:15270): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-5rvCQU6kts: Connection refused
authenticate 'saucy.tar.gz' against 'saucy.tar.gz.gpg'
extracting 'saucy.tar.gz'
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeFetcherCore.py", line 305, in run
    raise ex
OSError: Can not execute '/tmp/ubuntu-release-upgrader-khert3/saucy'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 152, in <module>
    fetcher.run()
  File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeFetcherCore.py", line 310, in run
    _("This usually is caused by a system where /tmp "
  File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeFetcher.py", line 50, in error
    return error(self.window_main.window_main, summary, message)
AttributeError: 'NoneType' object has no attribute 'window_main'

---


---
title: "[SOLVED] moblock uninstall error"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by sleepyenglish on 2008-01-22
When attempting to remove moblock i get the below error

> E: moblock: subprocess pre-removal script returned error exit status 6

Im using gutsy, can anyone give some pointers how i can remove moblock?

Thanks

---

### Post by jre on 2008-01-22
What's in /var/log/moblock-control.log?
Did you delete some files manually!? This might cause the error.
Try to reinstall moblock and then "aptitude purge moblock"

---

### Post by sleepyenglish on 2008-01-22
Year i may have have deleted some files manually :oops:, trying to reinstall via synaptic gives the error

> E: moblock: subprocess post-installation script returned error exit status 6

Trying aptitude purge moblock gives me the below.

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
mark@mark-laptop:~$ sudo aptitude purge moblock
[sudo] password for mark:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  libnetfilter-queue1 libnfnetlink0 moblock{p} 
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 377kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 122560 files and directories currently installed.)
Removing moblock ...
 * MoBlock: /etc/moblock/moblock.conf not installed.
invoke-rc.d: initscript moblock, action "stop" failed.
dpkg: error processing moblock (--purge):
 subprocess pre-removal script returned error exit status 6
 * MoBlock: /etc/moblock/moblock.conf not installed.
invoke-rc.d: initscript moblock, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 6
Errors were encountered while processing:
 moblock
localepurge: Disk space freed in /usr/share/locale: 1672K
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done

/var/log/moblock-control.log is

> 2008-01-21 09:26:01 GMT Begin: /usr/bin/moblock-control update
Updating blocklists ...
Updating nipfilter.dat.gz * . No update available.
 [31m*[39;49m Error 6: [http://peerguardian.sourceforge.net/lists/p2p.php:](http://peerguardian.sourceforge.net/lists/p2p.php:) Currently php redirects are not supported.
2008-01-21 19:18:55 GMT Begin: /usr/bin/moblock-control update
Updating blocklists ...
Updating nipfilter.dat.gz2008-01-21 19:19:04 GMT Begin: /usr/bin/moblock-control stop
Deleting iptablesiptables: No chain/target/match by that name
iptables: Bad rule (does a matching rule exist in that chain?)
iptables v1.3.6: Couldn't load target `moblock_in':/lib/iptables/libipt_moblock_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.6: Couldn't load target `moblock_out':/lib/iptables/libipt_moblock_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.6: Couldn't load target `moblock_fw':/lib/iptables/libipt_moblock_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
   ...fail!
Stopping MoBlock   ...done.
2008-01-21 19:19:05 GMT End: /usr/bin/moblock-control stop
 * .
 * Error 6: [http://peerguardian.sourceforge.net/lists/p2p.php:](http://peerguardian.sourceforge.net/lists/p2p.php:) Currently php redirects are not supported.
2008-01-21 19:19:47 GMT Begin: /usr/bin/moblock-control start
Inserting iptables   ...done.
Starting MoBlock   ...done.
2008-01-21 19:19:48 GMT End: /usr/bin/moblock-control start
* Logging to /var/log/moblock.log
* Ranges loaded: 209059
* Using .dat file format
* Log timestamp enabled
* DROP MARK: 10
* ACCEPT MARK: 20
* Merged ranges: 0
* Skipped useless ranges: 0
2008-01-21 19:26:19 GMT Begin: /usr/bin/moblock-control stop
Deleting iptables   ...done.
Stopping MoBlock   ...done.
2008-01-21 19:26:19 GMT End: /usr/bin/moblock-control stop
2008-01-21 19:27:23 GMT Begin: /usr/bin/moblock-control start
Inserting iptables   ...done.
Starting MoBlock   ...done.
2008-01-21 19:27:23 GMT End: /usr/bin/moblock-control start
* Logging to /var/log/moblock.log
* Ranges loaded: 209059
* Using .dat file format
* Log timestamp enabled
* DROP MARK: 10
* ACCEPT MARK: 20
* Merged ranges: 0
* Skipped useless ranges: 0
2008-01-21 20:19:03 GMT Begin: /usr/bin/moblock-control stop
Deleting iptables   ...done.
Stopping MoBlock   ...done.
2008-01-21 20:19:03 GMT End: /usr/bin/moblock-control stop
2008-01-21 20:26:02 GMT Begin: /usr/bin/moblock-control start
Inserting iptables   ...done.
Starting MoBlock   ...done.
2008-01-21 20:26:02 GMT End: /usr/bin/moblock-control start
* Logging to /var/log/moblock.log
* Ranges loaded: 209059
* Using .dat file format
* Log timestamp enabled
* DROP MARK: 10
* ACCEPT MARK: 20
* Merged ranges: 0
* Skipped useless ranges: 0
2008-01-21 20:43:49 GMT Begin: /usr/bin/moblock-control stop
Deleting iptables   ...done.
Stopping MoBlock   ...done.
2008-01-21 20:43:50 GMT End: /usr/bin/moblock-control stop
2008-01-21 20:45:23 GMT Begin: /usr/bin/moblock-control start
Inserting iptables   ...done.
Starting MoBlock   ...done.
2008-01-21 20:45:24 GMT End: /usr/bin/moblock-control start
* Logging to /var/log/moblock.log
* Ranges loaded: 209059
* Using .dat file format
* Log timestamp enabled
* DROP MARK: 10
* ACCEPT MARK: 20
* Merged ranges: 0
* Skipped useless ranges: 0
2008-01-21 21:26:05 GMT Begin: /usr/bin/moblock-control stop
Deleting iptables   ...done.
Stopping MoBlock   ...done.
2008-01-21 21:26:06 GMT End: /usr/bin/moblock-control stop
2008-01-21 21:37:36 GMT Begin: /usr/bin/moblock-control start
Inserting iptables   ...done.
Starting MoBlock   ...done.
2008-01-21 21:37:37 GMT End: /usr/bin/moblock-control start
* Logging to /var/log/moblock.log
* Ranges loaded: 209059
* Using .dat file format
* Log timestamp enabled
* DROP MARK: 10
* ACCEPT MARK: 20
* Merged ranges: 0
* Skipped useless ranges: 0
2008-01-22 09:18:43 GMT Begin: moblock-control start
Inserting iptables   ...done.
Starting MoBlock   ...done.
2008-01-22 09:18:44 GMT End: moblock-control start
2008-01-22 09:19:46 GMT Begin: moblock-control stop
Deleting iptables   ...done.
Stopping MoBlock   ...done.
2008-01-22 09:19:46 GMT End: moblock-control stop
2008-01-22 09:20:47 GMT Begin: moblock-control stop
Deleting iptablesiptables: No chain/target/match by that name
iptables: Bad rule (does a matching rule exist in that chain?)
iptables v1.3.6: Couldn't load target `moblock_in':/lib/iptables/libipt_moblock_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.6: Couldn't load target `moblock_out':/lib/iptables/libipt_moblock_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.6: Couldn't load target `moblock_fw':/lib/iptables/libipt_moblock_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
   ...fail!
Stopping MoBlock   ...done.
2008-01-22 09:20:47 GMT End: moblock-control stop
2008-01-22 09:31:53 GMT Begin: moblock-control start
Inserting iptables   ...done.
Starting MoBlock   ...done.
2008-01-22 09:31:53 GMT End: moblock-control start

---

### Post by jre on 2008-01-23
You deleted /etc/moblock/moblock.conf. Download this file: [http://moblock-deb.svn.sourceforge.net/viewvc/*checkout*/moblock-deb/moblock/moblock-0.9~rc1/moblock-0.9~rc1/debian/moblock.conf](http://moblock-deb.svn.sourceforge.net/viewvc/*checkout*/moblock-deb/moblock/moblock-0.9~rc1/moblock-0.9~rc1/debian/moblock.conf)
and copy it to /etc/moblock/moblock.conf.

Another unrelated thing: I saw in your logfile that you wanted to use the list [http://peerguardian.sourceforge.net/lists/p2p.phpANYWORD](http://peerguardian.sourceforge.net/lists/p2p.phpANYWORD). But this didn't work. Instead you can use the original file where this is a redirect to: [http://www.bluetack.co.uk/config/level1.gzANYWORD](http://www.bluetack.co.uk/config/level1.gzANYWORD). (Remove ANYWORD from the links, I just want to prevent accidental downloads of this 3MB file.) Add this link to your /etc/moblock/blocklists.list and set in /etc/moblock/moblock.conf:
```
BLOCKLIST_FORMAT="p"
```

Greets
jre

---

### Post by sleepyenglish on 2008-01-23
I did as you said jre but there was no moblock folder so i created one and placed the moblock.conf file inside and i now get the below error.

> E: moblock: subprocess pre-removal script returned error exit status 5

I should really stop deleting files and folders :confused:.

---

### Post by zvacet on 2008-01-24
```
sudo dpkg --remove --force-remove-reinstreq moblock
```

---

### Post by sleepyenglish on 2008-01-24
That didn't work im afraid zvacet, i get the below error

> (Reading database ... 124073 files and directories currently installed.)
Removing moblock ...
 * MoBlock: /usr/bin/moblock-control not installed.
invoke-rc.d: initscript moblock, action "stop" failed.
dpkg: error processing moblock (--remove):
 subprocess pre-removal script returned error exit status 5
 * MoBlock: /usr/bin/moblock-control not installed.
invoke-rc.d: initscript moblock, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 5
Errors were encountered while processing:
 moblock

I downloaded moblock-control and placed it in /usr/bin/ but still i get the same error. Could i not manually replace all the files i deleted? tho i cant remember which ones they were :-(.

---

### Post by zvacet on 2008-01-24
```
sudo apt-get install --reinstall moblock
```

This should reinstall it.After that try 

```
sudo apt-get --purge remove moblock
```

or any of previous commands.

---

### Post by sleepyenglish on 2008-01-24
Still no luck with those i still get the MoBlock: /usr/bin/moblock-control not installed error.

---

### Post by jre on 2008-01-24
The script has bo be executable:
```
chmod +x /usr/bin/moblock-control
```

---

### Post by sleepyenglish on 2008-01-24
Thanks for all the help guys that finally done the trick.

---

### Post by sleepyenglish on 2008-01-25
More then likely related but i can no longer launch mobloquer when reinstalling it along with moblock. Moblock is working but i don't really like using it without a gui and as i said the gui doesent launch. 

Any suggestions would be welcome, thanks.

Moblock ---- 0.9~rc1-6
Mobloquer ---- 0.3-1

---

### Post by jre on 2008-01-28
start mobloquer via the terminal. Then you might get some informational output what's wrong.
Note that mobloquer is still under development.

greets
jre

---

### Post by sleepyenglish on 2008-02-07
The terminal output says, does this indicate any obvious problems?

> QFSFileEngine::open: No file name specified
WARNING: Unable to open file "" for reading 
Returning null vector 
WARNING: Unable to open file "_back" for reading 
Returning null vector 
QFSFileEngine::open: No file name specified
WARNING: Unable to open file "" for reading 
Returning null vector 
WARNING: Unable to open file "_back" for reading 
Returning null vector 
Segmentation fault (core dumped)

---

### Post by jimtb on 2008-02-08
> **sleepyenglish said:**
> The terminal output says, does this indicate any obvious problems?

Hi, I'm the developer of Mobloquer. 

The errors indicate that mobloquer is trying to load wrong configuration files(with NULL paths). The first thing you should do is clear mobloquer's configuration, maybe something went wrong when you reinstalled it...Just execute the following command in a terminal:
```
rm ~/.config/Mobloquer/ -Rf
```

And then try running the program again.

:-)

---

### Post by sleepyenglish on 2008-02-08
Thanks jimtb that worked a  treat.

Do you know if Mobloquer will make it in the hardy heron repos.

---

### Post by jimtb on 2008-02-09
Well I honestly don't know but I don't think it will, the project is still not mature enough.

:-)

---

### Post by sleepyenglish on 2008-02-09
It seems stable enough for me, obviously minus the hiccup i had with it but that was self inflicted i think.

Again thanks for your help jimtb.

---


---
title: "Strange error when running apt-get"
date: 2012-02-05
forum: Installation &amp; Upgrades
---

### Post by RT100 on 2012-02-05
**never mind I figured it out. I went through and removed python-twisted-mail, -web,and -words, all better now**


[SIZE="1"]> I think i've got something wrong with my python twisted installation. I don't need twisted python, I installed it to try out a program and it didn't meet my needs. Now it's giving me all sorts of juicy errors whenever I apt-get anything at all!

Help!

```
$ sudo apt-get remove hello
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  hello
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
4 not fully installed or removed.
After this operation, 98.3 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 97552 files and directories currently installed.)
Removing hello ...
Processing triggers for man-db ...
Setting up python-twisted-web (10.2.0-1) ...
SyntaxError: ('invalid syntax', ('/usr/lib/python2.7/dist-packages/twisted/web/util.py', 318, 51, '    if not isinstance(myFailure, failure.Failure)>\n'))

dpkg: error processing python-twisted-web (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-twisted-lore:
 python-twisted-lore depends on python-twisted-web (>= 10.2); however:
  Package python-twisted-web is not configured yet.
dpkg: error processing python-twisted-lore (--configure):
 dependency problems - leaving unconfigured
Setting up python-twisted-mail (10.2.0-1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Sorry: IndentationError: ('unindent does not match any outer indentation level', ('/usr/lib/python2.7/dist-packages/twisted/mail/relaymanager.py', 528, 42, '     $  mailExchangeDeferred.addCallbeck(\n'))
dpkg: error processing python-twisted-mail (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-twisted-words (10.2.0-1) ...
SyntaxError: ('invalid syntax', ('/usr/lib/python2.7/dist-packages/twisted/words/protocols/jabber/component.py', 194, 20, '                   $                xmlstream.STREAM_AUTHD_EVENT)\n'))

dpkg: error processing python-twisted-words (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 python-twisted-web
 python-twisted-lore
 python-twisted-mail
 python-twisted-words
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

James

system: 
$ cat /proc/version
Linux version 2.6.38-13-generic-pae (buildd@palmer) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #54-Ubuntu SMP Tue Jan 3 15:11:05 UTC 2012

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty[/SIZE]

---

### Post by skizofrenito on 2012-02-17
Can you post the solution you found here? Because I have the same problem right now..

---

### Post by plucky on 2012-02-17
> **skizofrenito said:**
> Can you post the solution you found here? Because I have the same problem right now..

> never mind I figured it out. I went through and removed python-twisted-mail, -web,and -words, all better now


Good Luck

---


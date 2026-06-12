---
title: "Problem updating flash, may be proxy issue"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by roncrump on 2010-03-07
I couldn't get flash to upgrade properly, so I uninstalled and reinstalled flashplugin-installer. However, it never completes just timing out again and again on the connection to the server on which canonical have adobe flash stored.

This seems to be an on-going problem for me, it  has been weeks now with repeated re-installs of flashplugin-installer, with no joy.

I am within a university network but have the proxy settings set for wget and within synaptic and the http_proxy variable . It seems to be updating everything else except flash quite happily.

Suggestions as to how to address this either:
(a) to work correctly within synaptic and the update manager; or
(b) another way to install the flash player via an alternative route,
would be appreciated.

I am running 64-bit Ubuntu 9.10 on the machine in question.

Cheers,
Ron

---

### Post by mikewhatever on 2010-03-07
Flash is not stored on Canonical's servers. The flashplugin-installer package downloads flash from Adobe, and that's probably where the problem is. You could try manually downloading and installing the .deb package from Adobe, or otherwise, download the .tar.gz package, and extract the content to .mozilla/plugins, which is in your home folder.

---

### Post by roncrump on 2010-03-07
> **mikewhatever said:**
> Flash is not stored on Canonical's servers.

And yet in synaptic I get....

```
Preconfiguring packages ...
Selecting previously deselected package flashplugin-installer.
(Reading database ... 338046 files and directories currently installed.)
Unpacking flashplugin-installer (from .../flashplugin-installer_10.0.45.2ubuntu0.9.10.1_amd64.deb) ...
Setting up flashplugin-installer (10.0.45.2ubuntu0.9.10.1) ...
Downloading...
--2010-03-08 10:54:05--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.45.2.orig.tar.gz
Resolving archive.canonical.com... 91.189.88.33
Connecting to archive.canonical.com|91.189.88.33|:80... failed: Connection timed out.
Retrying.

```

which looks to me like its looking on the canonical site, unless that is just a link to the adobe server, of course.

I will grab the deb from adobe.

Cheers,
Ron.

---

### Post by mikewhatever on 2010-03-07
Right, that seems to be correct, however, it is the same tar.gz. you get from Adobe's downloads, with libflashplayer.so inside. As said, you need to copy the file to .mozilla/plugins or to /usr/lib/mozilla/plugins.
You could also try the native 64bit version, which is now at beta3.

---

### Post by calleee on 2010-08-12
Hi,

A little late but I have the same problem as Ron.
I'm running 64-bit Ubuntu 10.04 on the machine in question.

I get the same problem with both Update Manager and Synaptic (=
Connecting to archive.canonical.com|91.189.88.33|:80... failed: Connection timed out.

Retrying.).


I've found another workaround (which is not pretty, but anyway):

1. Start Synaptic and mark flash for reinstallation.
2. Apply and wait for the "Applying Changes" window.
3. Open Details and then watch and wait for the retrying-loop...
4. Now open a shell and run "ps -ef | grep synaptic":
root      3895  3894  0 10:37 ?        00:00:06 /usr/sbin/synaptic
root      4070  3895  0 10:50 pts/2    00:00:00 /usr/sbin/synaptic
5. Kill the child process by executing "sudo kill -9 4070" NOTE! You do this on your own risk and should of course replace 4070 with the id you get from the ps command!!!
6. Close down and re-open Synaptic (you might need to wait for a while or re-start the computer). There is a lock and I don't know how to disable it (nothing under /var/lock/..)
7. When starting Synaptic you should now get this error message:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
8. Close Synaptic again...
9. Open a shell and run "sudo dpkg --configure -a". Now flash is updated and the workaround is complete.

As I said before - not a pretty workaround and you could probably skip or improve some steps above, but I like to be accurate with the details... It might also give you smarter guy's a clue about what the real problem is.

To me it seems that the Update Manager and Synaptic does not use the correct proxy settings - but I don't know how to fix.

The commands: 
a)
echo $http_proxy
echo $no_proxy

b)
sudo bash
->
echo $http_proxy
echo $no_proxy

all give me what seems to be correct information about my proxy settings (not shown here on purpose, sorry but you have to take my word on it).

Any ideas anyone why synaptic and update manager does not follow my "system wide" settings?

---

### Post by efflandt on 2010-08-12
If you need to use a web proxy there is a setting at System > Preferences > Network Proxy that can be set to "Apply System Wide..." which may help getting packages and updates, since it should apply to anything using certain network protocols (http, etc.)

---

### Post by calleee on 2010-08-13
Thanks efflandt - but the problem is that I've already did this. But it does not help...

I have entered (verified) settings for both HTTP proxy and Secure HTTP proxy and applied this system wide. I'll try to enter for FTP as well, but wget are using http if I'm not wrong so it should not matter...

---

### Post by calleee on 2010-08-13
Nope - didn't help to add FTP as well (+ apply system wide) :-(

---

### Post by VirtualCLD on 2010-08-25
Does anyone know how to get this working?  I tried setting http_proxy and I've tried "http_proxy=http://my.proxy.intranet:8080/ apt-get install flashplugin-nonfree", but nothing works anymore.  

The frustrating thing is I got this to work a little over a month ago, but now I'm having trouble again.  I must have done something different that I don't remember.

EDIT:  Sorry, looks like it was solved here:
[http://ubuntuforums.org/showthread.php?t=1540136](http://ubuntuforums.org/showthread.php?t=1540136)

---

### Post by jeremybrooks on 2011-10-28
You need to tell wget which proxies to use. See this thread for details: [http://ubuntuforums.org/showthread.php?t=1540136]("http://ubuntuforums.org/showthread.php?t=1540136")

Oops, I see somebody else pointed to that URL as well. :-)

---

### Post by oldos2er on 2011-10-28
Closed. Please don't bump old threads.

---


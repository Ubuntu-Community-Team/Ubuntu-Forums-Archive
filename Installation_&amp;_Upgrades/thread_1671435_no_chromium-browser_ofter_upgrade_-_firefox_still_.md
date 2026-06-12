---
title: "no chromium-browser ofter upgrade - firefox still works"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by gahligahli on 2011-01-20
Ubuntu 10.04 LTS 64 bit
Acer Revo R3700
chromium-browser from daily builds ppa 


Hello hello, 

After doing todays ubuntu updates my chromium browser has broken, by way of failing to load.  Firefox still works and is what I am using to post this.    

I have read this thread: 

[http://ubuntuforums.org/showthread.php?t=1666129&highlight=chrome](http://ubuntuforums.org/showthread.php?t=1666129&highlight=chrome)

As in the above thread, chromium-browser loads fine when run with sudo (naughty)

My error is as follows: 

```
userone@revo:~$ chromium-browser 
[2010:2021:682719490:FATAL:external_pref_extension_loader.cc(63)] Check failed: PathService::Get(base_path_key_, &base_path_). 
Aborted
```I looked for the **/opt/google** directory but I have none, possibly from using  a different install method to above-mentioned thread?  

Any solutions or even clues would be appreciated.


**Thread Update:**  

I have made no changes, but chromium-browser now loads under my normal user privileges, but with the error of: 

[B]Your preferences can not be read. 

Same features may be unavailable, and changes to preferences won't be saved[/B]


Hmmmm...

---

### Post by Criz Collins on 2011-01-20
exactly same issue here since my update 30 minutes ago.
But I still can not start chromium with the error mentioned in the first post.
Btw. Ubuntu 10.10 (Maverick) here

Reverting back to the previous version worked for me:

# sudo dpkg -i /var/cache/apt/archives/chromium-*.642.*

---

### Post by garvinrick4 on 2011-01-20
I am sure if it is in the daily's it will be fixed shortly.

---

### Post by lionbeast on 2011-01-20
i've got the same problem here. i'm still on lucid lynx and just did the update.

does anybody know how i could get my bookmarks without chromium launching?

---

### Post by lionbeast on 2011-01-20
i've got the same problem here. i'm still on lucid lynx and just did the update.

does anybody know how i could get my bookmarks without chromium launching?

---

### Post by jackos on 2011-01-20
Same problem after today's upgrade, same fix worked:

sudo dpkg -i /var/cache/apt/archives/chromium-*642.*
dpkg: warning: downgrading chromium-browser from 10.0.644.0~svn20110120r71911-0ubuntu1~ucd1~maverick to 10.0.642.0~svn20110118r71618-0ubuntu1~ucd1~maverick.
(Reading database ... 157961 files and directories currently installed.)
Preparing to replace chromium-browser 10.0.644.0~svn20110120r71911-0ubuntu1~ucd1~maverick (using .../chromium-browser_10.0.642.0~svn20110118r71618-0ubuntu1~ucd1~maverick_i386.deb) ...
Unpacking replacement chromium-browser ...
dpkg: warning: downgrading chromium-browser-inspector from 10.0.644.0~svn20110120r71911-0ubuntu1~ucd1~maverick to 10.0.642.0~svn20110118r71618-0ubuntu1~ucd1~maverick.
Preparing to replace chromium-browser-inspector 10.0.644.0~svn20110120r71911-0ubuntu1~ucd1~maverick (using .../chromium-browser-inspector_10.0.642.0~svn20110118r71618-0ubuntu1~ucd1~maverick_all.deb) ...
Unpacking replacement chromium-browser-inspector ...
Setting up chromium-browser-inspector (10.0.642.0~svn20110118r71618-0ubuntu1~ucd1~maverick) ...
Setting up chromium-browser (10.0.642.0~svn20110118r71618-0ubuntu1~ucd1~maverick) ...
Processing triggers for man-db ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...

---

### Post by gahligahli on 2011-01-20
Thanks for the info Criz Collins!  

The command successfully executed but alas still the same issue, doh.    



And lionbeast, your bookmarks are here:  

~/.config/google-chrome/Default/Bookmarks

:)

---

### Post by gahligahli on 2011-01-20
edit, multi post.

---

### Post by gahligahli on 2011-01-20
edit: multi post

---

### Post by gahligahli on 2011-01-20
edit: multi post

---

### Post by gahligahli on 2011-01-20
edit: multi post

---

### Post by gahligahli on 2011-01-20
edit: multi post

---

### Post by viggo on 2011-01-20
> **Criz Collins said:**
> 
Reverting back to the previous version worked for me:

# sudo dpkg -i /var/cache/apt/archives/chromium-*.642.*

Also, version 643 is working on lucid
# sudo dpkg -i /var/cache/apt/archives/chromium-*.643.*

---

### Post by plasmidmap on 2011-01-20
Sorry double post, see below.

---

### Post by plasmidmap on 2011-01-20
The downgrade fix did not work for me since I don't seem to have a cache for chromium however, this did work:

Temporary work-around:

0. Make a backup copy of /home/username/.config/chromium , just in case.
1. Run chromium as root.  This will hijack your chromium preferences folder, setting root as owner of your preferences.
> sudo chromium-browser
2. Close chromium.
3. Take back ownership of your chromium preferences:
> sudo chown -R username /home/username/.config/chromium

chromium then loads as normal.

---

### Post by plut0 on 2011-01-20
You can fix this by downloading the previous build from yesterday.  Browse to:
[http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/)

Download version 643, make sure you grab the appropriate release and arch for your system.  Then you can install with dpkg.

---

### Post by Mortuis on 2011-01-20
I had the same problem, plasmidmap's solution in post #15 worked for me.

---

### Post by Mortuis on 2011-01-20
I had the same problem, plasmidmap's solution in post #15 worked for me.

---

### Post by gahligahli on 2011-01-20
Post #15 worked for me, back to happy with chrome.  

Thanks plasmid!

---

### Post by TOfregato on 2011-01-23
Thanks *plasmidmap*! Worked like a charm ;)

---


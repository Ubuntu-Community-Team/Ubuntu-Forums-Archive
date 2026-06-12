---
title: "[Issue] do-release-upgrade -d from 18.04.6 LTS to newer version"
date: 2023-05-31
forum: Installation &amp; Upgrades
---

### Post by doiche on 2023-05-31
Hi Guys, good day.


**lsb_release -a**
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.6 LTS
Release:    18.04
Codename:    bionic

**uname -mrs**
Linux 4.14.180-178 armv7l



So, I'm trying to upgrade my Ubuntu 18.04.6 LTS to once last month bionic support was over.

So, as always,  I checked the /etc/update-manager/release-upgrades to see if Prompt was set as tls:

 **cat /etc/update-manager/release-upgrades**# Default behavior for the release upgrader.


[DEFAULT]
# Default prompting behavior, valid options:
#
#  never  - Never check for, or allow upgrading to, a new release.
#  normal - Check to see if a new release is available.  If more than one new
#           release is found, the release upgrader will attempt to upgrade to
#           the supported release that immediately succeeds the
#           currently-running release.
#  lts    - Check to see if a new LTS release is available.  The upgrader
#           will attempt to upgrade to the first LTS release available after
#           the currently-running one.  Note that if this option is used and
#           the currently-running release is not itself an LTS release the
#           upgrader will assume prompt was meant to be normal.
Prompt=tls
 

After checked if Prompt was equal tls I tried to:

[B]apt update
[/B]Hit:1 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) bionic InRelease
Hit:2 [http://deb.odroid.in/5422-s](http://deb.odroid.in/5422-s) bionic InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
[B]
apt list --upgradable[/B]
Listing... Done

[B]apt upgrade
[/B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


And rebooted it just to be assure that I'm not running an old upgrade without a fresh boot..

After that I ran:

[B] apt --purge autoremove
[/B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


and ran:



**do-release-upgrade -d**
Checking for a new Ubuntu release
Upgrades to the development release are only 
available from the latest supported release.

 

And that is the question... why is this message being displayed? 
**"Upgrades to the development release are only available from the latest supported release."**

Anyone faced that message already?
:confused::confused:

So I also tried to call **do-release-upgrade -d **with a debug on:


**DEBUG_UPDATE_MANAGER=1 do-release-upgrade -d**
Checking for a new Ubuntu release
MetaRelease.__init__() useDevel=True useProposed=False
/etc/update-manager/meta-release: [https://changelogs.ubuntu.com/meta-release](https://changelogs.ubuntu.com/meta-release) 
/etc/update-manager/meta-release: [https://changelogs.ubuntu.com/meta-release](https://changelogs.ubuntu.com/meta-release) 
/etc/update-manager/meta-release: -development 
/etc/update-manager/meta-release: -proposed 
metarelease-uri: **[https://changelogs.ubuntu.com/meta-release-development](https://changelogs.ubuntu.com/meta-release-development)**
MetaRelease.download()
have self.metarelease_information
MetaRelease.parse()
current dist name: 'bionic'
found distro name: 'lunar'
found distro name: 'mantic'
**current dist not found in meta-release file**
Upgrades to the development release are only 
available from the latest supported release.

The content of **[https://changelogs.ubuntu.com/meta-release-development](https://changelogs.ubuntu.com/meta-release-development) **does not have bionic entry.... it does have [COLOR=#000000]Lunar Lobster [/COLOR][COLOR=#000000]23.04 and [/COLOR][COLOR=#000000]Mantic Minotaur [/COLOR][COLOR=#000000]23.10.

[/COLOR][COLOR=#000000]I also tried to change the [/COLOR]Prompt on **/etc/update-manager/release-upgrades **to normal instead tls but I got same message...

Is this happening because bionic becomes out of date? 
Is it possible to circumvent this behavior/issue and still upgrade Bionic?


Any help is really appreciate

---

### Post by guiverc on 2023-05-31
> **doiche said:**
> 
**do-release-upgrade -d**
Checking for a new Ubuntu release
Upgrades to the development release are only 
available from the latest supported release.

 
And that is the question... why is this message being displayed? 
**"Upgrades to the development release are only available from the latest supported release."**


You're trying to jump to the `-d` or *development *release, which is currently Ubuntu *mantic*, or what will be released as Ubuntu 23.10 in October 2023 from 18.04.

The `-d` tells it to go to the *development* release; so why use it?

Ubuntu 20.04.1 was released long ago, thus `-d` isn't needed as is documented (*it was documented that `-d` was needed when 20.04 was initially released only; as it was needed before 20.04.1 was released**, thus if you saw it as necessary you were reading very old documentation*).  Upgrades to an LTS do **not**  open at initial release (ie. 20.04), they'll open **after**  the release of the .1 (ie. 20.04.1) thus `-d` isn't required.

If you want to use the `-d` you'll need to be on Ubuntu 22.10, where the `-d` can be used to go to *mantic* (23.10) currently.

I'll add in case helpful, 

A normal *release-upgrade* will use this file - [https://changelogs.ubuntu.com/meta-release](https://changelogs.ubuntu.com/meta-release) 

A *release-upgrade* will use this file if `-d` is used; ie. for those wanting to go to the *development* release (*or what I'm using now*) - [https://changelogs.ubuntu.com/meta-release-development](https://changelogs.ubuntu.com/meta-release-development)

---

### Post by doiche on 2023-05-31
Hi @guiverc, thank you for replying it.

Right, but even running it without -d I'm getting same message:
Check this out:
 

**DEBUG_UPDATE_MANAGER=1 do-release-upgrade **Checking for a new Ubuntu release
MetaRelease.__init__() useDevel=True useProposed=False
/etc/update-manager/meta-release: [https://changelogs.ubuntu.com/meta-release](https://changelogs.ubuntu.com/meta-release) 
/etc/update-manager/meta-release: [https://changelogs.ubuntu.com/meta-release](https://changelogs.ubuntu.com/meta-release) 
/etc/update-manager/meta-release: -development 
/etc/update-manager/meta-release: -proposed 
**metarelease-uri: [https://changelogs.ubuntu.com/meta-release-development](https://changelogs.ubuntu.com/meta-release-development)**
MetaRelease.download()
have self.metarelease_information
MetaRelease.parse()
current dist name: 'bionic'
found distro name: 'lunar'
found distro name: 'mantic'
**current dist not found in meta-release file**

And without the debug:
[B]
do-release-upgrade [/B]
Checking for a new Ubuntu release
Upgrades to the development release are only 
available from the latest supported release.


 


Upgrades to the development release are only 
available from the latest supported release.


even without the -d option, **do-release-upgrade** looks like to be calling the metarelease-uri: [https://changelogs.ubuntu.com/meta-release-development](https://changelogs.ubuntu.com/meta-release-development) instead [https://changelogs.ubuntu.com/meta-release](https://changelogs.ubuntu.com/meta-release)

To be honest I even tried to change the URL on meta-release to "force it" to use the correct URL... it does not work either.... 

cat /etc/update-manager/meta-release
# default location for the meta-release file


[METARELEASE]
URI = [https://changelogs.ubuntu.com/meta-release](https://changelogs.ubuntu.com/meta-release)
**#URI_LTS = [https://changelogs.ubuntu.com/meta-release-lts](https://changelogs.ubuntu.com/meta-release-lts)**
URI_LTS = [https://changelogs.ubuntu.com/meta-release](https://changelogs.ubuntu.com/meta-release)
URI_UNSTABLE_POSTFIX = -development
URI_PROPOSED_POSTFIX = -proposed



And yes, that is the weird behavior that I'm not understanding

And yep, release-upgrades is setup with Prompt normal.... these outputs are from now... this moment...

**  cat /etc/update-manager/release-upgrades**# Default behavior for the release upgrader.


[DEFAULT]
# Default prompting behavior, valid options:
#
#  never  - Never check for, or allow upgrading to, a new release.
#  normal - Check to see if a new release is available.  If more than one new
#           release is found, the release upgrader will attempt to upgrade to
#           the supported release that immediately succeeds the
#           currently-running release.
#  lts    - Check to see if a new LTS release is available.  The upgrader
#           will attempt to upgrade to the first LTS release available after
#           the currently-running one.  Note that if this option is used and
#           the currently-running release is not itself an LTS release the
#           upgrader will assume prompt was meant to be normal.
Prompt=normal



Any idea?

---

### Post by doiche on 2023-05-31
Guys, as update.

After investigating the /usr/bin/do-release-upgrade source itself and change the default value of:
parser.add_option ("-d", "--devel-release", action="store_true",
                     dest="devel_release", default=False,
                     help=_("If using the latest supported release, "
                            "upgrade to the development release"))


it points me to 


Checking for a new Ubuntu release
ERROR:root:parse failed for '/var/lib/update-manager/meta-release'
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py", line 380, in download
    self.parse()
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py", line 317, in parse
    self.new_dist_available(upgradable_to)
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py", line 234, in new_dist_available
    self.new_dist = none
NameError: name 'none' is not defined
No new release found.




so checking the /usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py line 234 I changed it fron none to dist and Bingo!


Checking for a new Ubuntu release
Get:1 Upgrade tool signature [1554 B]                                                                                                                                                        
Get:2 Upgrade tool [1338 kB]                                                                                                                                                                 
Fetched 1340 kB in 0s (0 B/s)                                                                                                                                                                
authenticate 'focal.tar.gz' against 'focal.tar.gz.gpg' 
extracting 'focal.tar.gz'


Reading cache


Checking package manager


Continue running under SSH? 


This session appears to be running under ssh. It is not recommended 
to perform a upgrade over ssh currently because in case of failure it 
is harder to recover. 


If you continue, an additional ssh daemon will be started at port 
'1022'. 
Do you want to continue? 


Continue [yN] 






Thank you all for insites! Hope this helps others in future

---

### Post by Tadaen_Sylvermane on 2023-05-31
Good to hear. Next step. How to use code tags! Not trying to be insulting but it's hard to separate your posted terminal output from everything else. I'm amazed no one else mentioned this one yet.

---


---
title: "Version problem with &quot;click&quot; package after upgrade to 15.04"
date: 2015-05-05
forum: Installation &amp; Upgrades
---

### Post by iscott2 on 2015-05-05
After upgrading my Ubuntu Gnome from 14.10 to 15.04 I had a bunch of problems with package configuration and version dependencies. I was able to fix most of these by purging the gnome3-team/gnome3 ppa and doing "sudo dpkg --configure -a" and "sudo apt-get -f install" a couple of times.

Now the only packages that have problems are "click" and "click-apparmor". When I try to do "sudo apt-get upgrade" I get this:

```
The following packages have unmet dependencies:
 click : Depends: python3-click (= 0.4.33) but 0.4.38.5 is installed
         Recommends: ubuntu-app-launch-tools but it is not installed or
                     upstart-app-launch-tools
 click-apparmor : Depends: python3-apparmor-click (= 0.2.11.2) but 0.3.8 is installed

```

But when I run "sudo apt-get -f install" to fix the dependencies, this is the error I get:

```
Preparing to unpack .../click_0.4.38.5_amd64.deb ...
Traceback (most recent call last):
  File "/usr/bin/click", line 31, in <module>
    from click import commands
ImportError: cannot import name 'commands'
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/click", line 31, in <module>
    from click import commands
ImportError: cannot import name 'commands'
dpkg: error processing archive /var/cache/apt/archives/click_0.4.38.5_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Preparing to unpack .../click-apparmor_0.3.8_amd64.deb ...
Traceback (most recent call last):
  File "/usr/bin/click", line 31, in <module>
    from click import commands
ImportError: cannot import name 'commands'
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/click", line 31, in <module>
    from click import commands
ImportError: cannot import name 'commands'
dpkg: error processing archive /var/cache/apt/archives/click-apparmor_0.3.8_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/click_0.4.38.5_amd64.deb
 /var/cache/apt/archives/click-apparmor_0.3.8_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I've tried just installing the correct package versions like this:
```
sudo apt-get install python3-click=0.4.33 python3-apparmor-click=0.2.11.2

```But I'm told that the specified versions can't be found for either package.

I'm really stuck. Any help would be greatly appreciated!

---

### Post by iscott2 on 2015-05-05
I found a deb package for the specified version of click and tried to install it like this:

```
sudo dpkg -i click_0.4.33_amd64.deb
```

But I got a similar error message:
```

Preparing to unpack click_0.4.33_amd64.deb ...
Traceback (most recent call last):
  File "/usr/bin/click", line 31, in <module>
    from click import commands
ImportError: cannot import name 'commands'
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/click", line 31, in <module>
    from click import commands
ImportError: cannot import name 'commands'
dpkg: error processing archive click_0.4.33_amd64.deb (--install):
 subprocess new pre-removal script returned error exit status 1
Errors were encountered while processing:
 click_0.4.33_amd64.deb

```

---

### Post by iscott2 on 2015-05-07
I found the solution in the comments on this bug: [https://bugs.launchpad.net/ubuntu/+source/click/+bug/1386354](https://bugs.launchpad.net/ubuntu/+source/click/+bug/1386354)

I first had to uninstall the click python libraries using pip:

```
[COLOR=#333333][FONT=monospace]sudo pip3 uninstall click
```

Then I ran "sudo apt-get -f install" and the click packages upgraded fine. My package system is working again.[/FONT][/COLOR]

---


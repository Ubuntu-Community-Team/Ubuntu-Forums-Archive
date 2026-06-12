---
title: "how upgrade from 12.04 to 12.10  in terminal - please help"
date: 2012-09-21
forum: Installation &amp; Upgrades
---

### Post by Andre-D on 2012-09-21
After attempting to install a libpng1.4.12 I cannot log on anymore on GUI, it crashes back to logon - most likely it's the unity that is crashing.

I thought I could clean-up by installing 12.10

"sudo do-release upgrade -d"  does not find any new release.
so .. how can I upgrade ? - or clean up whatever mess the install script caused ?

---

### Post by kansasnoob on 2012-09-21
Look here:

[http://ubuntuforums.org/showthread.php?p=12238802#post12238802](http://ubuntuforums.org/showthread.php?p=12238802#post12238802)

---

### Post by kansasnoob on 2012-09-21
I should add though that upgrading from a broken OS is quite likely to result in a broken OS ;)

---

### Post by irv on 2012-09-21
Hope you had your system backed up? If not you can boot with a Live DVD or USB, run the live session mount your old OS partition and backup your files before doing a nice clean install. The post before me is right. Don't want to install over a broken OS you will just end up with more problems.

---

### Post by funicorn on 2012-09-21
try this
# vi /etc/update-manager/release-upgrades
make sure 'Prompt=normal' in that file ( in case it's 'Prompt=lts')
then 
# do-release-upgrade -d

I usually do this through software-properties-gtk, so I'm not sure it works.

---

### Post by Andre-D on 2012-09-21
Yes, I have backup.
Thank you for the answer, the problem was Prompt=lts in the release-upgrades, that stopped me from getting the offer.

I hope the upgrade switches out that many libraries, and it will work.

Otherwise I have another question for you, that almost deserves another thread:
Should I install x64 ? - it seems to me taht all the applications I need exist in x64 versions, then there is some need for mono and python, atmel compiler etc..
Is there still good reasons not to install x64 ? - like there was 2 years ago ?

---

### Post by irv on 2012-09-21
> **Andre-D said:**
> Yes, I have backup.
Thank you for the answer, the problem was Prompt=lts in the release-upgrades, that stopped me from getting the offer.

I hope the upgrade switches out that many libraries, and it will work.

Otherwise I have another question for you, that almost deserves another thread:
Should I install x64 ? - it seems to me taht all the applications I need exist in x64 versions, then there is some need for mono and python, atmel compiler etc..
Is there still good reasons not to install x64 ? - like there was 2 years ago ?

If your system is designed to run a 64bit OS, go for it. I have the AMD64 and have been running the 64bit for a couple of years now with no problems.

---

### Post by funicorn on 2012-09-21
Firstly I think you have no choice other than upgrading to 12.10 amd64, since you already work on 12.04 amd64.
Secondly amd64 now works as good as i386, except that some (very few I think) softwares are built on i386 system of which only dynamic(i386 lib. dependent) binaries are provided hence can not run on a  amd64 platform.

---

### Post by josephmills on 2012-09-21
is you config file set up not to let you upgrade distros releases ?

```
cd /etc/update-manager/
```
then 

```
gksudo gedit release-upgrades
```
make sure that the end line looks like this. 
```
# Default behavior for the release upgrader.

[DEFAULT]
# Default prompting behavior, valid options:
#
#  never  - Never check for a new release.
#  normal - Check to see if a new release is available.  If more than one new
#           release is found, the release upgrader will attempt to upgrade to
#           the release that immediately succeeds the currently-running
#           release.
#  lts    - Check to see if a new LTS release is available.  The upgrader
#           will attempt to upgrade to the first LTS release available after
#           the currently-running one.  Note that this option should not be
#           used if the currently-running release is not itself an LTS
#           release, since in that case the upgrader won't be able to
#           determine if a newer release is available.
Prompt=normal

```

if it looks like that then 
what is your meta-release file look like? could you paste that here please and thanks

---


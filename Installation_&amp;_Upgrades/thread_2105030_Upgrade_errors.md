---
title: "Upgrade errors"
date: 2013-01-15
forum: Installation &amp; Upgrades
---

### Post by SteWieH on 2013-01-15
whenever I try to upgrade from 10.04 to 12.10 i get the following error
do-release-upgrade 
> 
Checking for a new ubuntu release 
ERROR: failed to read '/etc/update-manager/release-upgrades': 
File contains no section headers. 
file: /etc/update-manager/release-upgrades, line: 1 
' Default behavior for the release upgrader.\n'  
is there a way to fix this?

---

### Post by ibjsb4 on 2013-01-15
Like it says, default is hosed ..

So [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
gksudo gedit /etc/update-manager/release-upgrades
```

And fix the offending line.  All lines with a hash mark (#) at the beginning are not program lines and are only there for information purposes.  So any line # out can say anything you want it to say without interfering with the program.  

You will notice the last line is set to "lts", this will allow you to upgrade to 12.04 (the next LTS).  If after you upgrade to 12.04, if you wish to move on to 12.10 you must change the prompt equal to normal (Prompt=normal).

Here's my /etc/update-manager/release-upgrades

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
Prompt=lts
```Any questions?  Post back :)

---

### Post by SteWieH on 2013-01-15
here is my current upgrade. looks exactly like yours
>  
Default behavior for the release upgrader.

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
prompt=lts


oh I see I need a # at the very beginning strange

---

### Post by ibjsb4 on 2013-01-15
Yep, you got it :)

# Default behavior for the release upgrader.

---


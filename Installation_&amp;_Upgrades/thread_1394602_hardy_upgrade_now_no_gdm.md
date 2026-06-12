---
title: "hardy upgrade now no gdm"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by badman35 on 2010-01-30
as the title say's How do i get this fixed I can not even log in as root with (sudo -s) say's i'm not on the suders list is there any way you all could give me a hand with this? If more info is needed just tell me how to get it and I will try and get it.. This system is my step daughter and I remote login to do all updates. Any help would be helpfull she has some reports due  and they are on that system.. Thanks In Advance......

---

### Post by quixote on 2010-01-31
The sudoers problem can be fixed.  I don't know if that'll solve the gdm issue, though.  the few times I've had gdm problems, I just had to reinstall :(.  If it does not solve the gdm issue, then boot with a liveCD, open nautilus (file manager), click on the drive that has your stepdaughter's files (that mounts the drive) and move the critical ones to removable media.  As a matter of fact, it might be the best idea to do that first, before trying to fix sudo.

The system, I take it, starts up, but it just won't let you do anything that requires root privileges, right?  The other problem is that I'm not sure it will let you apply the fix remotely.  (Obviously, the ability to change who has root privileges is a pretty big deal....)

Boot into recovery mode, not regular mode.  Select the option for command prompt (I think it says with networking) at the bottom. At the command line type (without quotes) "sudo visudo".  (Actually, come to think of it, you probably don't need "sudo" since you're already root....)

This'll bring up a file (using the nano text editor), that looks more or less like this: ```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
**%admin ALL=(ALL) ALL**
```
Most of the lines are comments, but the last line, %admin etc, is the one you want to be sure is there.  Only arrow keys and backspace work in nano.  No mouse.  Hit ctrl-x to quit, then "y" to save the changed file.  That returns the behavior to the usual expected, where the primary user can be sudo.

Shut down by typing "halt now".Then reboot into ordinary graphical mode.

Hope this solves the problem!

---

### Post by badman35 on 2010-02-01
Yes quixote It does boot and load but no gdm or sudo -s for me it goes straight to CLI and pops up and error something about no gdm group and when I sudo -s to gain root rights it says that i'm no in the sudoers list...But everything else workes fine it boots up no error on memmory checks or hardware.... I will work on that in the morning when i'm fresh and awake and before i go to work (SOHO) I just have to go to the next room. Oh and thanks info I will post back here if it works or not... any and all help with this is greatly appreciated

---

### Post by quixote on 2010-02-01
The business about "no gdm group" is bizarre.  If all it did was blow up that one group, it's possible to recreate groups, although I'm not sure of the procedure for a system group like that.  Let's hope that's all it takes.

The usual way  to add an ordinary group is: ```
sudo groupadd *[groupname]*
```
But gdm is a system group, and has a group ID of 0.  The only other group with the lowest ID number is root itself.  I've never had to try adding a group essential to the functioning of the whole system, so I'm not speaking from experience here.  If you type "man groupadd" it gives you the manual pages for the command.  Judging by the options listed, the command would be
either ```
sudo groupadd --force --system gdm
```The -f switch means it will leave gdm alone if the group is already there.
or ```
sudo groupadd -gid 0 --system gdm
``` if gdm absolutely has to have a 0 groupID.  If unspecified, it'll give the group a higher number, which wouldn't be good, I suspect.  So, as you see, I'm not sure what is the right way to do this.  There might be something deep in the Ubuntu wiki somewhere.

Judging by the way it looks on my system, it's not actually necessary to explicitly add your login user to that group.

---


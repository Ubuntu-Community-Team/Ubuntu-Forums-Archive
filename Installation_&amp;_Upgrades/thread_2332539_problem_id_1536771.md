---
title: "problem id 1536771"
date: 2016-08-01
forum: Installation &amp; Upgrades
---

### Post by ken poy on 2016-08-01
Hello,  This i hope a simple answer to a basic question.  i have the 1536771 error and have checked the responses one of which follows.
i have rel16.04 and have installed all maintenance.  My question:  how do i get and install the fix??  what is rel16.04.3??  
Please help with what to do.   thanks ken

edit 8/2/16  i had used 16.04 about a month without a problem.  the problem started occurring after applying the latest maintenance (updates).  is there a way to restore the prior code??

this is a copy of the problem from the internet:

**************************************************************************************************

[COLOR=#ff0000]Edit 8/6/16:[/COLOR]  issued the APT-Cache  command with the following results;

ken@ken-Latitude-E6420:~$ apt-cache policy ubuntu-gnome-default-settings
ubuntu-gnome-default-settings:
  Installed: 16.04.4
  Candidate: 16.04.4
  Version table:
 *** 16.04.4 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe i386 Packages
        100 /var/lib/dpkg/status
ken@ken-Latitude-E6420:~$ 

Hope this helps thanks  ken

***********************************************************************************************
[COLOR=#ff0000]Edit 8/10/16
[/COLOR]Issued the Apt-Cache command see previous update
it seems i am at rel16.04.4  and still have the error 
   i did not have the error prior to installing latest updates. perhaps fix lost at 16.04.4???
not sure where to go from here.   thanks  ken[COLOR=#000000][/COLOR]
[COLOR=#ff0000]
Edit 8/13/16[/COLOR]
following is [COLOR=#000000]the Detail of the error, did a report error but not sure where the report is, i tried logs.

[/COLOR]executable path
  /sbin/plymouthd
Package
  plymouth 0.9.2-3ubuntu13.1
problem type
  crash
title
  plymouthd crashed with SIGSEVG in Script_obj_deref_direct()

sure sounds like original problem.

Perhaps i am alone with tis problem and there is no interest.
my 80th birthday is soon so will nap for a while to save my energy.     thanks ken

if there is no interest will close for lack of interest next week.
 

***Post of original problem ********************************************************************

. For this particular problem, this has been fixed in ubuntu-gnome-default-settings.

ubuntu-gnome-default-settings:
  Installed: 16.04.3
  Candidate: 16.04.3
  Version table:
 *** 16.04.3 500
        500 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
        500 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) xenial/universe i386 Packages
        100 /var/lib/dpkg/status

I no longer get a SIGSEGV in script_obj_deref_direct() due to this fix.

no longer affects:    plymouth (Ubuntu)
Changed in ubuntu-gnome-default-settings (Ubuntu):
status:    Confirmed &#8594; Fix Released
Changed in ubuntu-gnome:
status:    New &#8594; Fix Released
importance:    Undecided &#8594; High
summary:    - plymouthd crashed with SIGSEGV in script_obj_deref_direct()
+ plymouthd crashed with SIGSEGV in script_obj_deref_direct() -> Parser
+ error : Error opening file /lib/plymouth/themes/ubuntu-gnome-logo
+ /ubuntu-gnome-logo.script

---

### Post by deadflowr on 2016-08-01
>  what is rel16.04.3?? 

A non-existent version of Ubuntu, as of right now.
But that's not what that means in this particular case.
for this it's the package version for the ubuntu-gnome-defualt-settings package in 16.04.
Your post is a copy/paste from this launchpad bug:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-gnome-default-settings/+bug/1536771]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-gnome-default-settings/+bug/1536771")
and this exact comment:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-gnome-default-settings/+bug/1536771/comments/6]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-gnome-default-settings/+bug/1536771/comments/6")

but our problem is, you haven't given use any idea of what you need help with.
is that package installed?
use
```
apt-cache policy ubuntu-gnome-default-settings
```
to find out.
if it is, then see if it is 16.04.3 or newer
(the current version I see is 16.04.4)
If the package is older then 16.04.3 (like 16.04.2 or .1), try running a system update, using the software updater/ update-manager.

If it is already up-to-date, then something else might be going on.
Hope this makes sense.
good luck

---

### Post by ken poy on 2016-08-17
Hello, i had edited the original post/thread with updates.  perhaps i should do a reply to thread with new information. i do not do this often so any is appreciated.   thanks ken[COLOR=#ff0000]

Edit 8/6/16:[/COLOR][COLOR=#000000] issued the APT-Cache command with the following results;[/COLOR]

[COLOR=#000000]ken@ken-Latitude-E6420:~$ apt-cache policy ubuntu-gnome-default-settings[/COLOR]
[COLOR=#000000]ubuntu-gnome-default-settings:[/COLOR]
[COLOR=#000000]Installed: 16.04.4[/COLOR]
[COLOR=#000000]Candidate: 16.04.4[/COLOR]
[COLOR=#000000]Version table:[/COLOR]
[COLOR=#000000]*** 16.04.4 500[/COLOR]
[COLOR=#000000]500 [/COLOR][http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu)[COLOR=#000000] xenial/universe amd64 Packages[/COLOR]
[COLOR=#000000]500 [/COLOR][http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu)[COLOR=#000000] xenial/universe i386 Packages[/COLOR]
[COLOR=#000000]100 /var/lib/dpkg/status[/COLOR]
[COLOR=#000000]ken@ken-Latitude-E6420:~$ [/COLOR]

[COLOR=#000000]Hope this helps thanks ken[/COLOR]

[COLOR=#000000]************************************************** *********************************************[/COLOR]
[COLOR=#ff0000]Edit 8/10/16
[/COLOR][COLOR=#000000]Issued the Apt-Cache command see previous update[/COLOR]
[COLOR=#000000]it seems i am at rel16.04.4 and still have the error [/COLOR]
[COLOR=#000000]i did not have the error prior to installing latest updates. perhaps fix lost at 16.04.4???[/COLOR]
[COLOR=#000000]not sure where to go from here. thanks ken[/COLOR]
[COLOR=#ff0000]
Edit 8/13/16[/COLOR]
[COLOR=#000000]following is [/COLOR][COLOR=#000000][COLOR=#000000]the Detail of the error, did a report error but not sure where the report is, i tried logs.

[/COLOR][/COLOR][COLOR=#000000]executable path[/COLOR]
[COLOR=#000000]/sbin/plymouthd[/COLOR]
[COLOR=#000000]Package[/COLOR]
[COLOR=#000000]plymouth 0.9.2-3ubuntu13.1[/COLOR]
[COLOR=#000000]problem type[/COLOR]
[COLOR=#000000]crash[/COLOR]
[COLOR=#000000]title[/COLOR]
[COLOR=#000000]plymouthd crashed with SIGSEVG in Script_obj_deref_direct()[/COLOR]

[COLOR=#000000]sure sounds like original problem.[/COLOR]

[COLOR=#000000]Perhaps i am alone with tis problem and there is no interest.[/COLOR]
[COLOR=#000000]my 80th birthday is soon so will nap for a while to save my energy. thanks ken[/COLOR]

[COLOR=#000000]if there is no interest will close for lack of interest next week.[/COLOR]

---

### Post by ken poy on 2016-08-20
Hello,  i received 1 reply form DeadFlowr some time ago.  did as he suggested and am at 16.04.4.   i have the problem at each boot (occurs twice).
i have 2 systems both fail.  i am tempted to reinstall  16.04 with no maintenance and see what happens.  i really like 16.04 so far other than this system error.
please reply with anything...  thanks ken

---


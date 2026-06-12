---
title: "How to Upgrade Minimal Installation of Xubuntu"
date: 2015-07-29
forum: Installation &amp; Upgrades
---

### Post by lambdafox on 2015-07-29
I am running Xubuntu 14.10 (amd64).

I used the minimal install disk, and chose "xfce minimal"

Since support is ending for 14.10, I want to upgrade to 15.04.

I do not, however, want to spend the next few days uninstalling the components from the full Xubuntu desktop that I do not use.

What is the proper way to accomplish that?

Thank you for your help.

---

### Post by Bashing-om on 2015-07-29
lambdafox; Hello;

May I offer that a online upgrade will only affect what is presently installed. Will not install any additional applications;
If you verify what is set within the update manager :
```

cat /etc/update-manager/release-upgrades

```
that "prompt=normal" is set;
Then :
```

sudo do-release-upgrade

```
The deed will be done to upgrade to release 15.04 .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by lambdafox on 2015-07-29
```
~$cat /etc/update-manager/release-upgrades
```

returns:

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
Prompt=never

```


```
~$sudo do-release-upgrade
```

returns:

```
Checking for a new Ubuntu release
No new release found
```

---

### Post by Bashing-om on 2015-07-29
lambdafox; Hey ??

What was the advise I gave you ?
> 
that "prompt=normal" is set;


And you have the setting :
> 
Prompt=never

Where you have the advisory:
> 
 never  - Never check for a new release.


And now you wonder the why :
> 
Checking for a new Ubuntu release
No new release found

--------------------------------

Do you need our guidance to edit the file " /etc/update-manager/release-upgrades " to permit the release-upgrade to proceed ?

[INDENT][INDENT]we can do that too - we are here to help
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-07-29
Settings> Software and Update> Updates> set last setting 'Notify me ... ' to 'Any new release'. Close and it will update. You should be notified there is 15.04 available.

I'm presuming Xubuntu minimal is Xubuntu-core?

---

### Post by lambdafox on 2015-07-29
> **Bucky Ball said:**
> Settings> Software and Update> Updates> set last setting 'Notify me ... ' to 'Any new release'. Close and it will update. You should be notified there is 15.04 available.

I'm presuming Xubuntu minimal is Xubuntu-core?

Hey, Bucky.  Thank you I changed the setting and will proceed...

When you install with the minimal disk, you may choose "xubuntu minimal" as your desktop or choose none and then afterward, do the xubuntu-core^ install.  I did the first, but as I understand it, the result is the same.

{poking fun at 				 					[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar1111508_1.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1111508") 				 				 					 						 	[**[COLOR=#DD4814][B]Bashing-om**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1111508") } I think you missed in my signature that I am new to linux and would have no clue how to proceed if that was not what I found {big smile on my face, wink wink}

---

### Post by Bashing-om on 2015-07-29
lambdafox; Hey, hey;

I do understand, not a problem .
this :
> 
Join Date
Dec 2013

as my indication that you have some familiarity with the operating system.

Let us know how you are getting along .

[INDENT][INDENT]we get ya fixed up
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-07-30
> **Bashing-om said:**
> 

[INDENT][INDENT]we get ya fixed up
[/INDENT][/INDENT]

Or fall over trying. :)

---


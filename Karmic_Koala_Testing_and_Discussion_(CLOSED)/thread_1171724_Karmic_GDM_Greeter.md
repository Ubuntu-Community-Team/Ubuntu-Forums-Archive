---
title: "Karmic GDM Greeter"
date: 2009-05-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by MadsRH on 2009-05-27
Today there was [a session titled "Karmic GDM Greeter". ]("https://blueprints.edge.launchpad.net/ubuntu/+spec/dx-karmic-gdm-greeter")I guess this was regarding the so called [facebrowser]("http://anotherubuntu.blogspot.com/2008/11/gdm-login-experience.html"), but sadly I can't find any Gobby document about it and nobody have been blogged about it. 

Does anyone know what was discussed? :confused:

---

### Post by meeples on 2009-05-27
wow thats the first time ive seen the face browser it looks amazing :O

---

### Post by wsonar on 2009-05-27
Cool looks like there stepping things up

---

### Post by Slug71 on 2009-05-27
Its probably been cancelled too.

---

### Post by super.rad on 2009-05-27
> **Slug71 said:**
> Its probably been cancelled too.

haha yeah they are probably planning to make something new....that will do exactly the same

---

### Post by zekopeko on 2009-05-27
> **Slug71 said:**
> Its probably been cancelled too.

that's way they are talking about it, because it's been canceled :D.

they are probably just waiting to integrate the new GDM (the upstream one ie. GNOME's) in karmic so that they have a nice fallback if you don't have 3D acceleration.

Stop being so pessimistic, Slug71.

---

### Post by ktp on 2009-05-27
> **super.rad said:**
> haha yeah they are probably planning to make something new....that will do exactly the same

:lolflag:

---

### Post by Slug71 on 2009-05-27
> **zekopeko said:**
> that's way they are talking about it, because it's been canceled :D.

they are probably just waiting to integrate the new GDM (the upstream one ie. GNOME's) in karmic so that they have a nice fallback if you don't have 3D acceleration.

Stop being so pessimistic, Slug71.


:lolflag:

---

### Post by MadsRH on 2009-05-28
Seriously, noone knows? 8-[


Let's hope MacSlow will blog about it soon.

---

### Post by MacUntu on 2009-05-28
I only got single user systems, so nothing too exciting for me.

---

### Post by meborc on 2009-05-28
it shows in the schedule that it is videotaped... lets hope the UDS videos will be uploaded to video.ubuntu.com soon

---

### Post by MadsRH on 2009-05-28
Found it!!!

Here's the Gobby document, but sadly this isn't exactly thrilling:

> * switchting to the new gdm this cycle would be nice if we want to use it for the next lts (not the sort of changes to do in a lts cycle)

* there is no graphical configuration tool (e.g., gdmsetup), that's not a blocker and writting a small one would be easy

* derivatives need to manually make theme changes (no migration tool)

* we don't want to switch to the new upstream version if only the standard gtk login screen is available but want something nicer

* the fusa ubuntu changes need to be ported to the new codebase (the fusa applet has been moved to gdm in the new version)



Desktop team can migrate to GDM using standard greeter
Adopting GDM 2 will force changes in FUSA
So required:
 * Desktop team to include new GDM
 * Dx team to update FUSA
 * Dx team to create new greeter (see req.s)
 * Dux to design greeter
 * Derivatives to update theming

Greeter Required Features
 * Accessible login
 * Ability to roll back to standard GNOME login
 * Ability for derivative theming
 * Auto login
 * Change language
 * Change session
 * Shutdown
 * Ability to migrate existing sessions


== Requirements ==

* Degrade gracefully when there are lots (i.e. 1000's) of users
* Don't try and read anything from home directories when there are lots (i.e. 1000's) of users

== Additional Development ==

List of features for the future 3D greeter/face browser
 * present a user interface with potentially the name of the machine or the domain
  * present a different interface if there are less or more than 6 users
 * let the user enter its name
 * let the user enter its password, or a passphrase, or connect a smartcard (through PAM, but there are usability issues)
 * (option) let the user select an "enterprise" domain (Sun, Windows, etc.)
 * let the user select the type of session he/she would like to enter
 * login on the local system
 * login on a remote system
 * select another keyboard mapping
 
 
Link with the whole boot experience: the greeter should provide an optional splash feature (putting a logo on screen), maybe inside the greeter process, or not if we can put that in a script inside the greeter session, if that does not impact the speed or user experience 

== Scope ==Non-functional requirements
 * accessibility support
 * support I18N
 * support user faces (~/.face)
 * support theming
 
Theming details
 * change the background screen
 * change the fonts and color of the various labels
 * 

Note: the new greeter does not currently support remote login


== Potential Regressions ==
 - miss
== Visual Design ==

= POR =
 * Desktop team to get GDM 2 into Karmic
 * Desktop team to use gconf to theme greeter in a Ubuntu way
 * Dx team to modify FUSA to be compatible with GDM 2
 * Dx team to modify greeter if time available

---

### Post by davideotape on 2009-05-28
> **MadsRH said:**
> Found it!!!

Here's the Gobby document, but sadly this isn't exactly thrilling:

The gobby documents aren't exactly easy to find or very well organized, are they?

---

### Post by shafin on 2009-05-29
> **MadsRH said:**
> Found it!!!

Here's the Gobby document, but sadly this isn't exactly thrilling:
Looks promising enough to me.
So after deciphering, it says:
*Greeter is already being worked on, there is a prototype somewhere.
*Might make it to Koala if they can get remote login working
Am I right?

---


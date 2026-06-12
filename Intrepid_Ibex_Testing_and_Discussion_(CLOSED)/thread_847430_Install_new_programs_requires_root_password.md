---
title: "Install new programs requires root password"
date: 2008-07-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2008-07-02
I'm unable to install any addtional programs in Kubuntu Alpha KDE4.1 via Applications - Add/Remove Programs or update via the menus.  I can update/upgrade via the bash terminal.  Is this a bug or a current restriction ?

---

### Post by olskar on 2008-07-02
Isnt root password always required for that? :confused: Or is KDE different from gnome?

---

### Post by GuitarRocker2562 on 2008-07-02
I think he is saying you must provide root's password, not your password to become root. That would be a bug.

---

### Post by Kevbert on 2008-07-03
Yes, I also have Kubuntu 8.04.  With 8.04 you have to provide your login username and password to install new programs and updates/upgrades.  With Intrepid it specifically asks for the root password (which is not set up by default).

---

### Post by Gina on 2008-07-03
Normally unset passwords default to an empty string so you just press Return when asked for password.  If this isn't the case, not only is it a bug but a very serious bug. A "show stopper"! :(

---

### Post by caryb on 2008-07-03
I can confirm this! (phew I thought it was just me) I have enabled the root password & I have to use it instead of my elevated password to use Synaptec & Adept (which crashes)


Cary

---

### Post by Kevbert on 2008-07-03
> **Gina said:**
> Normally unset passwords default to an empty string so you just press Return when asked for password.  If this isn't the case, not only is it a bug but a very serious bug. A "show stopper"! :(
Thanks Gina.  I've raised bug report #165619 on the KDE bug tracker.
CaryB - it may be worth adding a comment on this as I've had to report another bug which was supposedly fixed on previous versions of KDE and another one which has been notified as a duplicate (yet I go to that bug and it's similar, but not the same).

---

### Post by Nullack on 2008-07-03
Would it be because no dev has done kdesudo yet?

---

### Post by Kevbert on 2008-07-03
Hi.  The KDE bug tracker team have closed that bug and suggested it's a distro problem.  Now reported on Launchpad (bug [#245168]("https://bugs.launchpad.net/ubuntu/+source/adept/+bug/245168"))

---

### Post by caryb on 2008-07-03
I have logon to Ubuntu on this laptop & it does not have that problem! I have updated the bug report to reflect this info.


Cary

---

### Post by 23meg on 2008-07-03
[QUOTE=Kevbert]I've raised bug report #165619 on the KDE bug tracker.[/QUOTE]

Is there a specific reason you reported it in the upstream bug tracker rather than Ubuntu?

---

### Post by Kevbert on 2008-07-03
> **23meg said:**
> Is there a specific reason you reported it in the upstream bug tracker rather than Ubuntu?
The reason that I've reported bugs on the KDE Bug Tracker is due to the fact that all the 'report bug' links under the Help menu for each application point to that location in Intrepid Kubuntu Alpha1.  If this is wrong you probably need to point this out on a Sticky.  I've noticed that a few bugs have been rejected as being distro specific on the KDE Bug Tracker.

---

### Post by caryb on 2008-07-04
This problem is not solved for me in todays updates.

Just was prompted for 2nd lot of updates & needed the root password not mine :-(


Cary

---

### Post by Kevbert on 2008-07-04
The problem is still there for me too.  I've noticed that there is now a new menu item - Manage Packages and that Add/Remove Packages/KDE3 has been removed.  I now have 11 packages which have been held back.

---


---
title: "Window controls/adjustments gone after upgrading from Lubuntu 18.04 to 19.10"
date: 2020-04-06
forum: Installation &amp; Upgrades
---

### Post by Peter_R._Wood on 2020-04-06
I just upgraded my system from Lubuntu 18.04 to 19.10 using apt dist-upgrade from the command line. I can boot up and almost everything works just like before (display, audio, input devices, wired and wireless network), EXCEPT that all of my windows are missing their close/resize buttons, and there is no window chrome to select in order to move or resize the windows.

I have noticed that if I switch to a Plasma desktop from the LightDM login screen, I do get all of these controls, but of course it's a completely different desktop environment. The default Lubuntu environment is the one with issues.

Any ideas what could be causing this?

---

### Post by CelticWarrior on 2020-04-06
> **Peter_R._Wood said:**
> I just upgraded my system from Lubuntu 18.04 to 19.10 using apt dist-upgrade from the command line.

No, you didn't. Not with that 'apt dist-upgrade' anyway.
So, please, describe the steps you took to upgrade to 19.10, as that will probably give a clue about what happened.

---

### Post by Peter_R._Wood on 2020-04-06
> **CelticWarrior said:**
> No, you didn't. Not with that 'apt dist-upgrade' anyway.
So, please, describe the steps you took to upgrade to 19.10, as that will probably give a clue about what happened.

Unfortunately I don't remember every step and dialog along the way, so I'll recollect as best I can.


[LIST=1]
[*]In the Software & Updates app, Update tab, changed 'Notify me of a new Ubuntu version' from 'Long-term support versions' to 'Any new version'.
[*]Close the window and confirmed my choice, allowing the app to refresh the package database.
[*]From command line, ran sudo apt update
[*]From command line, ran sudo apt dist-upgrade
[*]From command line, ran reboot
[*]After reboot, ran Software Updater app, which said something to the effect that my packages were up to date, but that a new release was available.
[*]Chose to upgrade to the new release.
[*]Proceeded through the upgrade gui. I think the main thing I changed was where it gave me a choice between gdm and sddm, I chose sddm. My main reason for doing this was that my brief research showed it was a new display manager and I wanted to try it out.
[*]After the upgrade dialog indicated the upgrade was finished, I chose to reboot the system.
[*]Upon reboot I found that I had a new greeter screen which I'm assuming was sddm. I logged in using this screen and saw that my default Lubuntu desktop had an updated style (task bar, system menu, icons, etc), and that I could launch and use apps, but that my windows lacked any control widgets.
[/LIST]

All of the above being said, however, I do have an update that I've found a workaround. After poking around in the system menu, I found -> Preferences -> LXQt settings -> Session Settings, and suspecting that the window manager might be an issue since my windows weren't really being 'managed' very well per se, I changed "Window Manager" setting from its current setting of:

[B]compiz
[/B]
to

[B]openbox
[/B]
After doing this, logging out and logging back in, I found that my windows once again had controls and functioned as expected. The other options in that dropdown were kwin, kwin_x11, and mutter. I'm wondering if there was an issue with the use of 'compiz' as the window manager.

---

### Post by CelticWarrior on 2020-04-06
Yes, with that method you actually upgraded the release. And it's the normal way.

The problem was the many changes between releases: 18.04 was the last one using LXDE. Now it uses LXQt. a normal release upgrade is therefore not recommended as it can causes issues similar to the ones you reported.

I would fresh install 20.04 some time after its release (end of April).

---

### Post by gdesilva on 2020-05-02
Hi Peter,

Probably you may have already gone for 20.04 and the problem is fixed but if not, the issue appears to be that you have lost the window decorator setting on your compiz settings manager. Try the following;

1. Open CCSM (Compiz settings manager)
2. select Window Decorator plugin
3. specify the decorator you want to use - I think the default value is gtk-window-decorator. If you want to use Emerald, make sure to install it first.

---

### Post by guiverc on 2020-05-02
Lubuntu 18.04 LTS and prior releases of Lubuntu used the LXDE desktop.

All releases from 18.10 upwards use the LXQt desktop, and as such it's not an easy transition, which is plagued with issues. The Lubuntu team created (prior to 18.10's release) notes to try and mitigate these issues, but there were still issues depending on what changes had been made to your system meaning problems are still likely even if following the instructions. As such the decision was made that upgrades are unsupported.

If you note the Lubuntu 20.04 LTS release notes ([https://lubuntu.me/focal-released/](https://lubuntu.me/focal-released/))

> ***Note***[COLOR=#555555][FONT=Ubuntu], due to the extensive changes required for the shift in desktop environments, the Lubuntu team does not support upgrading from 18.04 or below to any greater release. [/FONT][/COLOR]**Doing so will result in a broken system.**[COLOR=#555555][FONT=Ubuntu] If you are on 18.04 or below and would like to upgrade, please do a fresh install.[/FONT][/COLOR]

A similar note exists in the 18.10 release notes too ([https://lubuntu.me/cosmic-released/](https://lubuntu.me/cosmic-released/))

It's possible yes (the box I'm using now was release-upgraded), but I would recommend re-installing anyway for piece of mind (fixing issues took me quite a bit of work measured in days)

---


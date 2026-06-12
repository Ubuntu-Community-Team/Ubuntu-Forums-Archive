---
title: "Upgrade from 18 LTS to 20 LTS - lost config"
date: 2020-10-04
forum: Installation &amp; Upgrades
---

### Post by bugbear6502 on 2020-10-04
Been waiting for the 18->20 upgrade process to go live, and this morning it was available.

Having updated (and backed up) my 18 LTS machine, I ran
```
sudo do-release-upgrade

```
And (after a couple of hours) the machine was back up.

I appear to have lost a great deal of "tuned" config and/or behaviour that I had done to the machine.

[B]Desktop switching
[/B]
Ctrl-tab no longer switches me between desktops. I can SEE the short cut in ~/.config/openbox/lubuntu-rc.xml

```
 <keybind key="C-Tab">
      <action name="GoToDesktop">
        <to>right</to>
        <wrap>yes</wrap>
      </action>
    </keybind>

```

[B]Touchpad
[/B]My code to disable the touchpad no long works

```
synclient TouchpadOff=1

```

Works from the terminal, but my copy of this line in ~/.config/lxsession/Lubuntu/autostart isn't working

[B]Wallpaper
[/B]I have lost my chosen wallpaper from my desktop.

[B]Alt Click
[/B]This is actually used by a website that I find valuable, so I removed this key-binding from "Frame" in ~/.config/openbox/lubuntu-rc.xml

My guess is that (in fact) the upgraded machine is running different processes and managers, and that my "old" config is applicable to software that isn't (in fact) running anymore.

Before I start playing whack-a-mole with each of my problems, can anyone comment on the overall effect/changes of this 18 -> 20 upgrade of a Lubuntu machine?

  BugBear

---

### Post by Impavidus on 2020-10-04
Lubuntu? I don't think an upgrade from Lubuntu 18.04 to 20.04 is officially supported. The changes in Lubuntu are so large that an upgrade is unlikely to work well. So you can clean out the old, no longer needed config files from your home directory and configure everything again and hope for the best. Best not to start the upgrade at all and just fresh install.

---

### Post by GhX6GZMB on 2020-10-04
> **Impavidus said:**
> Lubuntu? I don't think an upgrade from Lubuntu 18.04 to 20.04 is officially supported. The changes in Lubuntu are so large that an upgrade is unlikely to work well. So you can clean out the old, no longer needed config files from your home directory and configure everything again and hope for the best. Best not to start the upgrade at all and just fresh install.

I agree. The change from LXDE to LXQt is probably more than the configurations can survive.

---

### Post by bugbear6502 on 2020-10-05
OK, after a steep learning curve, I did a clean install of Lubuntu, retaining my /home partition with all my user data.

I will now try to re-implement my various changes. I suspect most of them simply need moving to the "right" config file for the new model.

I will likely be back with more specific questions.

(and  have "other" issues arising from that install, obviously)

   BugBear

---

### Post by GhX6GZMB on 2020-10-05
> **bugbear6502 said:**
> OK, after a steep learning curve, I did a clean install of Lubuntu, retaining my /home partition with all my user data.

I will now try to re-implement my various changes. I suspect most of them simply need moving to the "right" config file for the new model.

I will likely be back with more specific questions.

(and  have "other" issues arising from that install, obviously)

   BugBear

You've chosen the right way to go.

I now have a bit over a year of experience with Lubuntu/LXQt (19.04 to 20.04 LTS) and have made the following (often "go back to start and don't collect $100") experiences:

Use the GUI tools for installation, removal, maintenance and configuration whenever possible.
 Muon for applications and fonts, the built-in LXQt tool for managing PPAs.

You can do everything manually/CLI as usual, but LXQt maintains installations databases that are then useless because they are out of sync.

BTW: the first thing I uninstall is snapd. I don't need one more level of abstraction and overhead. But that's just me.

---

### Post by bugbear6502 on 2020-10-06
I am making slow progress, but progress nonetheless.

Keyboard shortcuts work in pretty much the same way, but are in a different file.

My old (edited) file was 

[FONT=courier new]~/.config/openbox/lubuntu-rc.xml
[/FONT]
The newly active file is
[FONT=courier new]
~/.config/openbox/lxqt-rc.xml[/FONT]

Putting my changes in there worked nicely.

I used to have

[FONT=courier new]synclient TouchpadOff=1
[/FONT][FONT=courier new]@lxterminal --geometry=80x24
[/FONT]
in a file

[FONT=courier new]~/.config/lxsession/Lubuntu/autostart
[/FONT]
This has been superceded by a Desktop file inside 

[FONT=courier new]~/.config/autostart

[FONT=arial]running qterminal. I have not yet managed to persuade qterminal to start at 80x24[/FONT][/FONT].

I have not yet worked out how to run my synclient command at login.

But - to paraphrase meatloaf - four out of five ain't bad.

   BugBear

---

### Post by guiverc on 2020-10-06
> **bugbear6502 said:**
> 
Before I start playing whack-a-mole with each of my problems, can anyone comment on the overall effect/changes of this 18 -> 20 upgrade of a Lubuntu machine?


The [Lubuntu 20.04 release notes]("https://lubuntu.me/focal-1-released/") mention I think rather clearly

> ***Note***, due to the extensive changes required  for the shift in desktop environments, the Lubuntu team does not support  upgrading from 18.04 or below to any greater release. Doing so will  result in a broken system. If you are on 18.04 or below and would like  to upgrade, please do a fresh install.

Yes if you look, a guide was written for the 18.04 to 18.10 upgrade path during the *development* process (*Lubuntu 18.10 was the first Lubuntu with LXQt, Lubuntu 20.04 being the fourth*). However due to problems still experienced by users in *testing*, the idea of providing support was dropped, and the guide never made 'public' on the Lubuntu web site (ie. *found with the code behind the manual pages* etc).

Yes it's possible, I did it following the guide, but I still had problems for near 3 weeks before all of a sudden everything fell into place & my system was perfect again (I can't recall how many hours, when I needed to use my computer I'd just login using XFCE/Xubuntu as I have both). All I remember was it wasn't fun and took a fair amount of time.

If I was doing it again, I'd just re-install without format (ie. so user configuration & files are kept, only system directories get wiped). That was far quicker & produced a neater & faster result (*alas I've not done that with 20.04, and can't recall when I last tested it, 19.10 or quite possibly 19.04*). The only changes to that method have occurred in the last ~month so I'd believe it'd work fine with 20.04 media & I suspect 20.04.1 media too (it may not be possible into the future though, eg. *groovy*/20.10, but that's because of a Ubuntu wide change).

---

### Post by bugbear6502 on 2020-10-11
Good news - by using 

sh -c "<command>"

as the entry in Autostart directory, I have managed to issue the command to disable my touchpad. This concludes my requirments for "legacy" config carry over from 18 -> 20.

Bad news:

Sadly, Gimp, Inkscape and Ruby Ripper all crash at various times. I will try "straight" Ubuntu to see if that helps - my Old Dell Vostro 1700 is (just) with the requirment spec.

EDIT: It's not my day; new thread on Ubuntu installer issues
[https://ubuntuforums.org/showthread.php?t=2451796](https://ubuntuforums.org/showthread.php?t=2451796)


    BugBear

---

### Post by bugbear6502 on 2020-10-15
Latest stage in the saga - my machine is not happy (not powerful enough) running full Ubuntu/Gnome.

Further googling shows me that Gimp has "issues" with the Clipboard under LXQT, reported from 2018 to the present time. I *may* revert to Lubuntu for performance reasons, but not if the Gimp clpiboard issue cannot be resolved. A Linux without Gimp is no use to me - I use it daily.

   BugBear

---

### Post by Impavidus on 2020-10-15
Besides Ubuntu and Lubuntu there are more flavours. Ubuntu Mate and Xubuntu are lighter than Ubuntu, but are GTK-based, not Qt. Maybe you should try one of those.

---


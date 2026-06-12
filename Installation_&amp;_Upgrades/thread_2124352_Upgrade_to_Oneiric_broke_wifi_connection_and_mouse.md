---
title: "Upgrade to Oneiric broke wifi connection and mouse PLEASE HELP!"
date: 2013-03-10
forum: Installation &amp; Upgrades
---

### Post by Luxx on 2013-03-10
I am tearing my hair out. I had a working system with Maverick, but I thought I needed to upgrade just to make sure things would work right to get a working LIVE USB -- that is another issue.

I upgraded once and had permissions issues in Naultilus, so I just upgraded again thinking those issues were likely to be resolved in Oneiric. I just made problems worse.

When I log in there is a mouse cursor in the middle of the screen that will not move. I have a USB mouse and it was working just fine before the upgrade. I tried unplugging it and plugging it back in, but the cursor still just sits in the middle of the screen and I can't use my mouse at all.

Second problem is that the upgrade also broke my wifi connection. I have tried to scan for it in terminal, but no interface is recognized. I am completely stuck. Can the mouse situation be fixed from terminal? Can the wifi be fixed from terminal without knowing what my interface is, or with it not being recognized?

I don't have a touch screen or touchpad.
It is a desktop with a Gigabyte multi-core DDR2 motherboard - not a commercial build (like Dell or something)
Netgear 32-bit wireless pci adapter

---

### Post by p_code on 2013-03-10
> **Luxx said:**
> I am tearing my hair out. I had a working system  with Maverick, but I thought I needed to upgrade just to make sure  things would work right to get a working LIVE USB -- that is another  issue.

I upgraded once and had permissions issues in Naultilus, so I just  upgraded again thinking those issues werye likely to be resolved in  Oneiric. I just made problems worse . . .

To get your system working here are some things you can try-

- First, just try switching your keyboard and mouse to different USB  ports (with some hardware, some ports may be  recognized and others not).

- Alternately, try forcing some of the more common compatibility boot options like nolapic, etc.

- Revert to Lucid or Maverick - or better still, update to 12.04 Precise.

I know how you feel, because I also am now dealing with a ton of hassles  trying to update all my systems to Precise since support is ending for  Lucid.

Lucid 10.04 was a GREAT release,  lots of features, 99% of which worked  seamlessly right out of the box, but from there forward, it's been  one-step-forward, two-steps-back so far as I can see.

Other than so-called 'enhancements' which didn't do diddle squat for me,  release wise, every single Ubuntu release from Lucid forward has been a  major disappointment.

In Lucid, after a decade of development, the Gnome 2 interface was   finally becoming competitive with what I was seeing literally 15 years  ago in Windows 98 -  fairly flexible user configurable start-bar menus, a  good selection of  really useful system tray plug-ins, and nice context  menu integration  with support for things like 'extract here' in the  archive manager.

Time and again, I have tried upgrades and other Linux distros, but always ended up reverting back to Lucid.

Unfortunately, that is no longer an option with Canonical yanking support for Lucid.

I have found that the 12.04 release works reasonably well - and is  fairly stable - but feature wise, it's been a HUGE disappointment, since  lots of things that were working in Lucid are either broken now, or  completely missing, in Precise.

Having my desktop 'dumbed down' to look like an idiot 'smart phone'  wasn't an option, so I had to disable and remove Unity, and fall back to  the stupid  'different-just-for-the-sake-of-being-different-aren't-we-clever' Gnome3  'classic' interface (which meant giving up Compiz!) - then remove a  bunch of other crap like the really stupid ill-concieved zeitgeist  spy-ware framework - and then put up with a few other minor irritations  like my blue tooth headset suddenly not working - and wah-la all hail  the NEW UBUNTU.

In other words - the really great thing about 12.04 is that - after a  lot of fiddling- IT'S ONLY A LITTLE WORSE THAN THE 10.04 RELEASE.

Sorry if I seem sarcastic here, but I was really disappointed in BOTH  Unity, and Gnome3 (what were they thinking?), but after getting used to  the minor irritations of the Gnome 3 'classic' desktop, it's at least  usable, and at least stability wise, I can say 12.04 has been excellent -  so getting back to your present USB keyboard issues - I would give  12.04 a try, as I suspect you might have a little better luck getting  every thing working.

---

### Post by Luxx on 2013-03-10
Without an internet connection I couldn't update to Precise, and couldn't do much of anything about my internet connection without a mouse, but I found a fix.

Holding down the SHIFT key at boot I selected previous versions, recovery mode. That was simple enough. Once I was logged in my connection worked and I ran ```
sudo apt-get update

```and then ```
do-release-upgrade
```
from terminal. So now I'm on Precise with Gnome classic and things seem to be working as they should, almost.

I still don't have permissions in nautilus (gksudo nautilus), the trash bin is missing and I can't open my Documents folder. I get the following error:

Could not open home/user/Documents
The file is of an unknown type.

It's definitely progress and I did save my important stuff elsewhere, so the Documents folder really isn't going to be missed, but it's annoying. I actually like my computer the way it is now, as long as things work.

Note:
I have had problems with every upgrade. I would like to try a distro with rolling upgrades that don't require changing my entire desktop environment and file menus, most of which I have customised to what I use. I couldn't stand Unity. I couldn't stand the "dumbed down" environment that kept me from fiddling with (or fix) things I shouldn't fiddle with. Isn't that what Linux is all about? That was what hooked me. I could customise and break anything I wanted to, and then I could learn how to fix them or install something that worked better. Terminal is my friend and I don't need it replaced with GUIs. I need to learn the language to do things myself. I am grateful to all those who keep working on things and creating packages and work-arounds so I can still use my computer the way I want to, and of course, the awesome online support communities. Many thanks.

---

### Post by p_code on 2013-03-11
It's great that you got it sorted out from a command line session.

I suggested the live-CD because I couldn't see how you could make the required downloads without WiFi working, but I'm glad you were able to get something figured out to work around that.

The problems you are seeing with your desktop are not because of any non-standard thing you did in the install, it's just that Ubuntu 12.04 has REALLY poor support for the Gnome3 fallback 'classic' desktop (no where near the number of support tools that Gnome 2 had in Lucid for example)

Fortunately, your ability to come up with this fix shows that you have much better than average console interface skills, so you will be happy to know that there is a simple terminal fix using a few gsettings commands from the terminal that will add the icons for the missing trash/recycle folder to your desktop (as well as pop-up folders for newly mounted devices, and your main 'My Computer' icon, if you want them).  Foolishly I didn't write them down, but if you Google you can find them quickly.

Again, glad you got it going :)

---


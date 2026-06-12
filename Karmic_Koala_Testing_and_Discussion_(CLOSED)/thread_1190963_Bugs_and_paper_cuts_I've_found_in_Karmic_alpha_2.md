---
title: "Bugs and paper cuts I've found in Karmic alpha 2"
date: 2009-06-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Craigy90 on 2009-06-18
Hello everyone!

I hope this is the right place to post this.

Due to all of the trouble that an Intel graphics card gives in Jaunty, I decided to try out Karmic alpha 2. I have only been running the alpha with no updating, because I don't really want stuff to break too badly. Definitely a big improvement overall so far , but there are still a few 'paper cuts' that crop up here and there. I have an Intel 965 graphics card.

I would like to post the problems that I have encountered, in no particular order. Please let me know if a bug report is appropriate or not, and I will link to an existing one or open a new one if none exists. If you guys encounter the same problem, please reply and let me know what you did (if anything) to solve it. This thread is not meant to be a bug report, but rather a list of problems I've had, and links to the actual bug reports.

Enough introduction, I'll get on with it! :)

[SIZE="5"]Bugs[/SIZE]

[SIZE="4"]Crash when switching to dual monitors with compiz enabled[/SIZE]
Basically, X freezes, and a power cycle is required to fix things. Also, the external monitor must be unplugged while booting to prevent the same problem when logging in again.
Bug report: this is the closest I've found, but it's not exactly my problem: [https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/146298](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/146298)

[SIZE="4"]Cursor can move off-screen when dual-monitors do not form rectangular area[/SIZE]
Using my built-in laptop screen and an external monitor, (with compiz disabled), yields a non-rectangular screen area (the 1280x800 screen is to the left of the 1680x1050 screen, and there is a rectangular box below the laptop screen). I would expect that this area would be treated as if it was not part of the screen, but instead X allows the cursor to enter this area, and get lost off-screen.
Bug report: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/389519](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/389519).

[SIZE="4"]Tooltips and other stuff should be displayed on external monitor, get rendered on primary[/SIZE]
Stuff gets rendered on the wrong screen, such as tooltips or pretty much anything in blender.
Bug report: none found or reported yet.

[SIZE="4"]Firefox crashes when enabling/disabling compiz[/SIZE]
Using Firefox 3.0.10, when I have enough tabs open, and turn compiz on or off, Firefox crashes.
Bug report: none found or reported yet.

[SIZE="4"]Problems with sound[/SIZE]
Don't really know what to say here, except that sound is kind of buggy, and I assume that it is in progress and will be fixed soon. Right now I have PulseAudio enabled for all playback, and only one program seems to be allowed to play sounds at a time. Also, when a program starts to play sound, sometimes there will be silence for a few seconds and then things start working. The system seems to disable sound output frequently, and only start it (or try to) when an actual sound is playing. I guess that makes this problem intermittent.
Bug report: none found or reported yet.

[SIZE="5"]
Paper cuts[/SIZE]

[SIZE="4"]When dragging to de-maximize a window, window changes shape/location unnecessarily (compiz on or off)[/SIZE]
Alright, this is pretty picky, but that's why I labeled it a paper cut! It's kind of hard to explain, only that when you drag a minimized window down, it kind of freaks out. Has anyone else noticed this?
Bug report: none found yet.

[SIZE="4"]Empathy problem importing Google Talk account[/SIZE]
First of all, my AIM account was imported successfully from Pidgin, which is cool. It tried to import my GTalk account, but recognized it as a Jabber protocol (I don't know if that's how it's supposed to be) and gave a network error when trying to connect. I deleted the account and created a new account in Empathy and things are working fine.
Bug report: here is the bug report for importing the GTalk account: [https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/388522](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/388522). Should I say that creating a new GTalk account in Empathy is a workaround?

[SIZE="4"][SOLVED] Empathy problem importing and creating IRC account[/SIZE]
I could not figure out how to do IRC. Empathy lists IRC as an import option, but does nothing when clicking import. Do I have to install a plugin or something for it to handle IRC?
Bug report: this matches the IRC problem, and gives a solution: [https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/388906](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/388906). Installing telepathy-idle fixes the problem. It seems the account was imported, but not displayed in accounts. Could we have this package automatically installed or suggested when people need IRC?

Other than that, things are running fine :). No more painfully noticeable tearing when moving windows around (with or without compiz), and better performance for videos, etc.

I think I have a basic understanding about reporting bugs, but I would appreciate advice on which package I should report some of these bugs against, and how to collect the appropriate data. Especially the system freeze for dual-monitors with compiz, and the firefox crashing when turning compiz on or off. These problems involve compiz, but also other programs, so should I collect info for all program involved?

Thanks.

P.S. The term 'paper cut' is pretty catchy!

---

### Post by super.rad on 2009-06-18
> **Craigy90 said:**
> Hello everyone!

[SIZE=4]Empathy problem importing Google Talk account[/SIZE]
First of all, my AIM account was imported successfully from Pidgin, which is cool. It tried to import my GTalk account, but recognized it as a Jabber protocol (I don't know if that's how it's supposed to be) and gave a network error when trying to connect. I deleted the account and created a new account in Empathy and things are working fine.
Bug report: here is the bug report for importing the GTalk account: [https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/388522](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/388522). Should I say that creating a new GTalk account in Empathy is a workaround?


GTalk is Jabber (if you set it up in pidgin you use the xmpp protocol which is for jabber/gtalk) but as empathy has a protocol for gtalk I guess this is a bug

---


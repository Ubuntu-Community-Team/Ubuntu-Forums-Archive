---
title: "Recent updates messed up some ACPI scripts and other functions (12.04)"
date: 2013-10-17
forum: Installation &amp; Upgrades
---

### Post by almikul on 2013-10-17
After a recent update, I noticed that ACPI functions responsible for suspension, hybernating, power button, etc stopped functioning properly. I do not know whether scripts in /etc/acpi were physically replaced or not. When I execute these scripts manually from the command line, they mostly work fine. 

In addition, display management tool (in Settings) stopped working properly. Now, when I make some change and press "apply" button, it shows the following error message: "GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `org.gnome.SettingsDaemon.XRANDR_2' on object at path /org/gnome/SettingsDaemon/XRANDR". I can still manage my screens using xrandr manually, but I suspect this is just a part of a bigger problem. 

Also, the recent update reset some custom details of the theme I am using on my Cinnamon desktop. Such things as icon theme, window borders, controls, etc were reset. I am not sure what went wrong, but all these things (theme, acpi, display) were changed/screwed up after the most recent upate on 12.04 LTS. As I mentioned, I am using Cinnamon desktop, if it makes any difference. 

Has anybody else experienced anything like this? It is really frustrating, as until recently, my laptop was working perfectly fine on 12.04. I really need to make sure I have a stable Linux OS because I use it for work. Your feedback would be much appreciated.

---

### Post by Tumblestump_Fomplebottom on 2013-10-18
Yes I am also having problems with ACPI now, after upgrading from Xubuntu 13.04. 

No matter what setting I put into the power manager it goes into some kind of messed up suspend when I close laptop lid. And it's not even a real suspend even though the light on the laptop flashes like it is because when I open it back up it starts a whole new session like it was rebooted. So there is no way to close the laptop without the whole system basically shutting down. Kind of annoying. There seems to be nothing to manually work around this bug in /etc/acpi as far as I can tell.

---

### Post by krakonos on 2013-10-19
The same here, my monitor turns black after some time and there is no way to disable this behaviour. And even better the last update (3.2.0-54-generic) has changed default theme in gnome classic and arbitrary switch three different themes .

---

### Post by krakonos on 2013-10-21
Is there some solution - it causes me a lot of troubles - and nothing changed after update to 3.2.0-55-generic and some Cinnamon updates - I don't understand why it is updated - I already uninstalled  Cinnamon right after update to 3.2.0-54-generic when the problems occurred

---

### Post by Tumblestump_Fomplebottom on 2013-10-22
I can't even figure out where those ACPI settings are stored. The ACPI manpage suggests you can manipulate it with sysctl but all I get when I try is an error, "cannot stat /proc/sys/hw/acpi". /etc/acpi seems to not control these settings either. So I tried just turning off ACPI in my BIOS but no setting exists there for this machine, go figure. 

We might be on our own with all this, I asked in the IRC channel and was told it was not ever going to be fixed because it was probably something with my DSDT table, whatever that means. And that I would need to recompile my own kernel and load a new DSDT into it. Which is totally BS if all of us had laptops that worked fine before the upgrade, where you could easily change a setting and it **actually worked**, why suddenly the need to compile kernels to fix a problem that the devs introduced obviously due to some unaddressed bug.

---

### Post by krakonos on 2013-10-22
Does that mean it never will be solved? So now impossibility to switch themes (or set up them in any way) and forced hibernation after 10 minutes (what cannot be changed) are new wonderful gifts from Canonical? I've already tested Fedora and I'm going to switch as fast as possible - I was too lazy but this is something I cannot go over any more - and I recommend  it to everybody who doesn't want to be guinea pig. By the way I was used to live with random (not so random - once a day but often more frequent) total system freeze

---

### Post by Tumblestump_Fomplebottom on 2013-10-22
I found a couple bug reports for this in Launchpad, looks like a fix is being worked on after all. 
This is the bug for gnome users.
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1180513](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1180513)
If you are using XFCE, this is the bug for that version
[https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1222021](https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1222021)

temporary workaround is to change settings in  /etc/systemd/logind.conf
There's a setting in there, HandleLidSwitch=
change the setting from suspend to ignore.

---


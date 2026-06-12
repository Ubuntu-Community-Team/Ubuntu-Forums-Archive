---
title: "trouble upgrading from 10.10 to 11.04 getting errors"
date: 2012-04-10
forum: Installation &amp; Upgrades
---

### Post by ledzepjes on 2012-04-10
I was having all sorts of problems upgrading from 10.10 to 11.04 recently. In particular, when I would issue the command:

sudo apt-get dist-upgrade

I would get the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

and if I went the graphical route, using upgrade manager and selecting the upgrade to 11.04 button, it would output everything up to calculating the upgrade and hang for 5-10 mins until reporting "could not apply changes fix broken packages" something to that effect?


I then tried:

sudo apt-get do-release-upgrade

and got:

An unresolvable problem occurred while calculating the upgrade: 
E:Error, pkgProblemResolver::Resolve generated breaks, this may be 
caused by held packages. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug against the 
'update-manager' package and include the files in 
/var/log/dist-upgrade/ in the bug report. 


I then unselected all the ppa's that I had, for Opera, Ubuntu Tweak, Shutter, Chrome, etc. Tried again, same result.

I don't know if it was my kernals, or something else, because I did several things, but I had two kernals installed, 2.6.32-30, and 2.6.32-32. I searched for them in the synaptic and removed 2.6.32-30, then search the file system for files with linux-headers-2.6.32-30, linux-headers-2.6.32-30-generic and linux-image-2.6.32-30 in the name and deleted them. I then reinstalled that specific kernal using synaptic, then proceeded to do the same for 2.6.32-32.

I then rebooted and started synaptic again, and this time the packages for the kernal 2.6.32-32 where highlighted with ! marks, I proceeded to right click and the option was to upgrade which I chose for each one, (again only 4 or 5), it finished and I rebooted.

at some point, I checked the repositories again and it only listed one:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse universe main
the only source in /etc/apt/sources.list that wasn't commented out with #, all the rest of the sources were commmented out at the beginning with #

I then tried the command again:
sudo apt-get do-release-upgrade
this time it went through to the calculating changes part and asked if I wanted to proceed (y or n)
of course I typed "Y"!

the upgrade completed! now I had Ubuntu 11.04

hope this helps someone even if it fully confuses most

I also used info from these threads:
[http://ubuntuforums.org/showthread.php?t=1741565](http://ubuntuforums.org/showthread.php?t=1741565)
[http://ubuntuforums.org/showthread.php?t=1859338](http://ubuntuforums.org/showthread.php?t=1859338)


on a side note, my Firefox is crashy crashy, and since I've upgraded all the way to 11.10, all the way from 10.04, it said the version was and still is 3.6???

Thank Goodness for trusty ole Opera, so I can type this


how do I finally upgrade my Firefox?

ps, I miss the gnome 2 style calender with optional map below the calendar showing a map with moving shadow and light over parts of the globe as the earth rotated. I'm very analyitical, so any extra information makes me feel better. When it comes to information the more the merrier. I'm not liking the push to dumb the interface down, atleast if the interface is dumbed down graphically, shade or deselect the master options and make the use of admin password show the hidden options (case in point, the startup manager is not showing all the startup items any more - missing an option to "unlock" the full list of startup items, similar to the "unlock" button in ubuntu tweak(and yes I know that's a 3rd party app)). I also miss the default use of synaptic package manager, it's by far and away superior in terms of finding software and much quicker when you know the name and want to know the version and all that is listed in the columns next to it. I find it very clunky and awkward using the Ubuntu Software Center, since the same packages aren't listed in both and many times packages are missing from the software center. I like how synaptic has all of them available in a list so I can see as much information I can in text. I don't like things being hidden from me, just a personal quibble. 

All that being said, nice job on the interface of 11.10. I can tell a lot of work went into the design and it is all in all very slick, nice job again. I will just have to work on customizing it, maybe moving the dock to the bottom? option in the future? or move the top title bar to the right side or any side for that matter? I will have to work on turning back on my compiz effects which seem to have all been turned off. But all in all, it's nice work, unity is very... it gives a very polished unifying feeling.

(although unity does crash and when it does, I ctrl+alt+F6 and type:
unity --release
then ctrl+alt+F7 and unity comes back

---

### Post by zvacet on 2012-04-11
I know synaptic is not ( don´t know why) install bydefault.You can always install it with

```
sudo apt-get install synaptic
```

I don´t use FF but I know 11.10 has latest version.Try with 

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by ledzepjes on 2012-04-12
I just noticed that there are many items missing from the Startup  Applications wizard? where did they go and how do I manage the missing  items? I had bluetooth turned off from starting up, but I don't see  bluetooth in the startup manager anymore, and I notice in the shutdown  screen it shows bluetooth being shutdown??

---

### Post by 2F4U on 2012-04-12
The startup items are now hidden by default and not intended to be changed by the user. If you want to be able to deactivate startup items, you have to change the associated configuration files. This post shows how to do it:

[http://www.upubuntu.com/2011/10/how-to-view-and-disable-hidden-startup.html](http://www.upubuntu.com/2011/10/how-to-view-and-disable-hidden-startup.html)

My recommendation is to backup the files before you change them.

---

### Post by ledzepjes on 2012-04-12
2F4U after going the the site you recommended, I typed the command:
cd /etc/xdg/autostart/ && ls > /home/user/Downloads/startup.txt

[PHP]at-spi-dbus-bus.desktop
at-spi-registryd.desktop
at-spi-registryd-wrapper.desktop.dpkg-bak
bluetooth-applet.desktop
bluetooth-applet-unity.desktop
deja-dup-monitor.desktop
evolution-alarm-notify.desktop
gdu-notification-daemon.desktop
gnome-at-session.desktop
gnome-do.desktop
gnome-fallback-mount-helper.desktop
gnome-keyring-daemon.desktop.dpkg-bak
gnome-keyring-gpg.desktop
gnome-keyring-pkcs11.desktop
gnome-keyring-secrets.desktop
gnome-keyring-ssh.desktop
gnome-power-manager.desktop
gnome-screensaver.desktop
gnome-settings-daemon.desktop
gnome-settings-daemon-helper.desktop.dpkg-bak
gnome-sound-applet.desktop
gnome-user-share.desktop
gnome-volume-control-applet.desktop
gsettings-data-convert.desktop
gwibber.desktop
indicator-applet.desktop
jockey-gtk.desktop
nautilus-autostart.desktop
nm-applet.desktop
nvidia-autostart.desktop
onboard-autostart.desktop
orca-autostart.desktop
parcellite-startup.desktop
polkit-gnome-authentication-agent-1.desktop
polkit-kde-authentication-agent-1.desktop
print-applet.desktop
pulseaudio.desktop
pulseaudio-kde.desktop
telepathy-indicator.desktop
ubuntuone-launch.desktop
update-notifier.desktop
user-dirs-update-gtk.desktop
vino-server.desktop
zeitgeist-datahub.desktop[/PHP]

so my bluetooth has been set back to startup, which is why it's being listed as being shutdown when I shutdown the computer

I'll have to remove it, since I don't have anything that is bluetooth on my desktop, one less thing

---

### Post by ledzepjes on 2012-04-13
I upgraded my firefox from help in another posting
[http://ubuntuforums.org/showthread.php?t=1956411](http://ubuntuforums.org/showthread.php?t=1956411)

Now I just need to remove my Bluetooth from startup and get my Hauppauge PVR-350 showing TV again, and I can consider this upgrade from 10.10 to 11.10 a success, well more so than a failure atleast, still have some minor quibbles like getting my "restart" to show up in the shutdown menu besides logoff and hibernate, and being able to pin shortcuts and icons back to the title bar at top, but those are minor

my tv thread is here:
[http://ubuntuforums.org/showthread.php?t=1958183](http://ubuntuforums.org/showthread.php?t=1958183)

I'm trying to get CSMonkey TV Remote working again, at the moment it only starts VLC on the Home Shopping network and I can't change the channel with the remote! Home Shopping Channel AAAAAH!

edit: tv remote seems to be changing channels and I have video and audio, don't understand that one, why it would only show the home shopping network for past couple days is beyond me, not funny

it's not working in fullscreen mode, only shows still pic and audio fullscreen?

---

### Post by ledzepjes on 2012-04-14
ok, so now I got the startup manager to show all previously hidden startup items by typing

```
cd /etc/xdg/autostart/
```
then
```
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

a reboot, (which now takes more clicks than before like most things in Unity, it requires more work to get the same things done compared to the fully functioning and very useful Gnome 2, which you have to get to by clicking shutdown, then restart (ala the M$ way of "advanced" UI design), in my opinion, Gnome 2 had all the best benefits of being simple-robust-and useful,...by combining the best of both Windows and Mac UI's. I prefer a top menu bar with Applications-Places-System ala mac, minus the not-functional global menu and sprinkle a bottom task tray bar to show tasks and running applications and to be able to switch between open windows(best of windows and mac ui in my humble opinion).

with that being said, had to get it off my chest, I saw and then unchecked the Bluetooth from startup, and now it no longer mentions it when I shutdown

---


---
title: "Totally stuck after upgrading to 12.04"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by linux_votary on 2012-04-26
Hey folks!

Ever since Ubuntu 7.04 was launched, I have been loyal to Ubuntu till now. This is the first time I have been stuck up completely!
Everything was working awesome on my 11.10 box till I upgraded to 12.04 yesterday. It has left the system totally unusable now!

I run Ubuntu on my Acer Aspire 4720z, 2.5 gigs of RAM.


[LIST]
[*]My touchpad does not work anymore, neither does the USB mouse. I can't even see the pointer moving. If I launch any application, it shows the loading pointer, and then suddenly dissapears!
[*]My Internet doesn't work. Forget my wi-fi that worked at a snap in 11.10.  Precise doesn't even recognize my LAN cable. The lights blink, but there's no connection!!
[*]nm-applet refuses to launch, throws wierd errors at the terminal
[*]My screen resolution has become low and crappy. Had a look at the display properties. Selecting 1024x768 does no good.
[*]The boot up screen has gone missing. From GRUB, it shows me a black screen, then directly to the login screen
[*]Ctrl+Alt+Fn to launch command line sessions do not work. Instead, show me a completely black screen.
[/LIST]
FYI, I had also installed KDE alongside Gnome. Thankfully, it spared my keyboard! It's still working..

Please help me fix these... I have invested 100s of MBs of download and time to upgrade this! I neither have patience nor the connection speed to download a new copy and run through all of this again!


Any sort of help would be much appriciated!

---

### Post by Tornikee on 2012-04-26
I have similar issues - low screen resolution, USB mouse doesn't work anymore, some other problems as well.

---

### Post by OleR on 2012-04-26
Same problem here, it seems. Thinkpad X220 without dedicated graphics.Ubuntu 64 bit 11.10->12.04.

---

### Post by jadtech on 2012-04-26
for some  for what ever reason 12.04 seens to set touch pad off by default  use what ever function key  for your computer to turn it on or activate it for some it is that simple ..

---

### Post by OleR on 2012-04-26
This would not explain why usb mouse and trackpoint and touchpad all don't work. And Alt+Ctrl+F1-F6 also not. I tried it with the touchpad enable/disable button, but that did not work.

---

### Post by darkod on 2012-04-26
It might not be related, but the OP says he upgraded yesterday???? 12.04 LTS was released today if I am not mistaken. Is it possible it was an upgrade to the pre-release version?

I am not saying all people who have issues did the same, it's just strange that someone would upgrade to the final version on the 25th when it was released on the 26th.

For everybody, if you run it in live mode, do you see some of the same issues?

And don't forget that not all upgrades go trouble free. That's why clean install are always recommended. Configure your system to have separate /home partition and you can do clean installs easy when ever you want.

---

### Post by jadtech on 2012-04-26
for some of the pre-releases there was a depackaging bug that was found there is a bug report on it here on lunch pad

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/924079](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/924079)

the solution for this bug was to install apt python-apt update  upgrade first  as this was required to unpackage some parts of the release related to video drivers and such .. 

not sure if some of the issues could be related to this or not

this was how I did my upgrade to 12.04 beta about 7 to 10 days ago after failing  and re-installing several times and failing

---

### Post by OleR on 2012-04-26
I finally downloaded the iso (12.04, live version 64 bit) and was able to boot just fine. So it is not a hardware problem, rather an issue with not having done the clean install. For all its worth, I will post here my .xsession_errors from the harddrive, and you will see there are tons of errors in there, not sure they are related. But at least that is something of a hint for those who understand a little better what might be going on.

Here is an excerpt from the file, most of these warning repeat many many times:

> 
gnome-session[1411]: WARNING: Session 'ubuntu' runnable check failed: Exited with code 1
gnome-keyring-daemon: insufficient process capabilities, unsecure memory might get used
gnome-session[1411]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1516:46: Unrecognized image file format
(gnome-settings-daemon:1481): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1595:73: Couldn't recognize the image file format for file '/usr/share/themes/Ambiance/gtk-3.0/assets/scrollbar_handle_vertical.png'
(gnome-settings-daemon:1481): color-plugin-WARNING **: failed to get edid: unable to get EDID for output
Window manager warning: Failed to load theme "Ambiance": Line 195 character 94: Couldn't recognize the image file format for file '/usr/share/themes/Ambiance/metacity-1/trough_left.png'
unity-2d-panel: [DEBUG] Scanning panel plugin directory "/usr/lib/unity-2d/plugins/panel" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-appindicator.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-appname.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-indicator.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-legacytray.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-separator.so" 
unity-2d-panel: [DEBUG] Configured plugins list is: ("appname", "!legacytray", "indicator") 
...


I am a bit surprised by the contents, because as far as I know, I had neither Gnome nor Unity2D installed. Also these seem to explain my missing icons, but not necessarily my other problems (mouse, tty1...)


EDIT: I cannot seem to upload the actual file. Maybe someone can already see somehing from the excerpt.

---

### Post by mkowske on 2012-04-27
Exact same problems as you... ugh.. I have to do a fresh install??

Any other "fix" for this? I'm guessing not... seems like a whole slew of things is messed up at this point.

I was able to boot with the old 3.0 kernel and got my mouse and screen resolution back but still no icons and compiz seg faulted immediately so Gnome is totally unusable, but at least I can get to a command prompt with ctrl-alt-F1 to move some files for backup.

I always get so excited when a new Ubuntu is released and end up installing it right away even though I have problems EVERY TIME. Best to wait, but so hard.

---

### Post by mkowske on 2012-04-27
More problems... the Ubuntu CD installer doesn't recognize my existing Ubuntu installation, which would be fine... except I only get two options when installing: 1) Erase everything and 2) Something else

I chose something else so I can use my existing partitions (and not destroy my windows partition and all my backed up data) but it only shows /dev/sda with the only option to create a new partition table. I know they are there... I can see them in fdisk...

---

### Post by dFlyer on 2012-04-27
> **linux_votary said:**
> Hey folks!

Please help me fix these... I have invested 100s of MBs of download and time to upgrade this! I neither have patience nor the connection speed to download a new copy and run through all of this again!

Any sort of help would be much appriciated!

My advice is to backup everything if you have not already, and download the live desktop cd about 700 megs and do a fresh install. The only other options are spend mega hours trouble shooting which is time consuming which you stated above you don't have the time for or switch to another OS/distro which will be very time consuming and possible mega downloads.

For me a complete install with additional programs and restore of about 200 GIG of photo's takes less than 3 hours including the download of the live desktop.

But than if you want to learn, by troubling shooting your OS, usually linux can be fixed, sometimes with just a few clicks of the mouse or command line edits, up to mega hours of research trial and errors. Again time spent is yours. If you want to try and fix, pick one problem and lets see if we can work through it, but lets do it one problem at a time.

---

### Post by darkod on 2012-04-27
> **mkowske said:**
> More problems... the Ubuntu CD installer doesn't recognize my existing Ubuntu installation, which would be fine... except I only get two options when installing: 1) Erase everything and 2) Something else

I chose something else so I can use my existing partitions (and not destroy my windows partition and all my backed up data) but it only shows /dev/sda with the only option to create a new partition table. I know they are there... I can see them in fdisk...

That might be because the disk has raid meta data remains on it if it was used in fakeraid earlier. In this case the installer doesn't show the partitions.

Another reason is if there is error or corruption in the partition table. That would be why it doesn't show partitions.

You can check for raid meta data with:
sudo dmraid -E -r /dev/sda

If that asks you to remove meta data, you have it. But only remove it if you are NOT running raid, otherwise it will destroy your array.

For errors in the partition table you can check with fixparts. Usually it can repair smaller errors.

---


---
title: "Alarm Clock in Panel?"
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by Sugi on 2011-01-13
I must be overlooking something here, but I can't find out how to add "Alarm Clock Applet" to my panel.  In Ubuntu Software Center, there's a picture of the program right in the panel and feature to add to panel, but there's no option for me to do this. "Add to Panel" doesn't have the application either.

FIXED:
It should appear in your notification applet.  Start up the application with > /usr/bin/alarm-clock-applet Have it start up at boot by right clicking on the alarm clock and select preferences and select 'start automatically at logon'.
Thanks [[COLOR="Blue"]matt_symes[/COLOR]]("http://ubuntuforums.org/member.php?u=1067998")!
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=181830&d=1295841794[/IMG]


Ubuntu 10.10 x64
alarm-clock-applet 0.3.1-1
Sugi

---

### Post by Frogs Hair on 2011-01-13
An alarm clock applet can be found in the software center.

---

### Post by karthick87 on 2011-01-13
```
sudo apt-get install alarm-clock
```

---

### Post by weedeater64 on 2011-01-13
I'm not sure from your post if you have installed it or not.

If not install it.

Then if it doesn't show up on the panel, find it in your application menu, right click on it, and you'll get several options, including "add to panel"

---

### Post by matt_symes on 2011-01-13
Hi

```
sudo apt-get install alarm-clock-applet
```

That is what i use. I don't know if it differs from those suggested above.

[https://launchpad.net/ubuntu/lucid/i386/alarm-clock-applet](https://launchpad.net/ubuntu/lucid/i386/alarm-clock-applet)

If you can't add it to the panel open a terminal and type

```
/usr/lib/alarm-clock-applet/alarm-clock-applet
```

or log out and log back in and see if appear in the 'add to panel' option.

Kind regards

---

### Post by Sugi on 2011-01-14
Hello everyone, sorry for the confusion.  The application is installed and running on my computer.  I just can't find the option to add to panel.  What's the command to restart gnome, like we use to do with restarting metacity.

Sugi

---

### Post by dino99 on 2011-01-14
gnome-panel --replace &

---

### Post by Sugi on 2011-01-20
gnome-panel --replace &
restart
and
/usr/lib/alarm-clock-applet/alarm-clock-applet
Didn't work before or after restart.  When I input that into the terminal, it says it doesn't exist even though I can load up the program and use it no problem.  Just no panel app icon.

Sugi

---

### Post by matt_symes on 2011-01-21
Hi

What is the output of 

```
ls -l /usr/lib/alarm-clock-applet/
```

That is small L above.

Kind regards

---

### Post by Sugi on 2011-01-22
It doesn't exist, but the program is installed on my computer.  I open the application by the terminal with this command 'alarm-clock-applet'.

Sugi

---

### Post by matt_symes on 2011-01-22
Hi

Open a terminal and type

```
sudo updatedb
```

then enter your password. Let it update then type

```
locate alarm-clock-applet
```

Post the path back here. I'm interested to know where it's installed on your system

Kind regards

---

### Post by Sugi on 2011-01-22
Here's the output:
> locate alarm-clock-applet
/etc/xdg/autostart/alarm-clock-applet.desktop
/home/Sugi/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/alarm-clock-applet.desktop
/usr/bin/alarm-clock-applet
/usr/share/alarm-clock-applet
/usr/share/alarm-clock-applet/alarm-clock.ui
/usr/share/app-install/desktop/alarm-clock-applet.desktop
/usr/share/applications/alarm-clock-applet.desktop
/usr/share/doc/alarm-clock-applet
/usr/share/doc/alarm-clock-applet/changelog.Debian.gz
/usr/share/doc/alarm-clock-applet/changelog.gz
/usr/share/doc/alarm-clock-applet/copyright
/usr/share/locale/ar/LC_MESSAGES/alarm-clock-applet.mo
/usr/share/locale/be/LC_MESSAGES/alarm-clock-applet.mo
/usr/share/locale/bg/LC_MESSAGES/alarm-clock-applet.mo
/usr/share/locale/ca/LC_MESSAGES/alarm-clock-applet.mo
/usr/share/locale/da/LC_MESSAGES/alarm-clock-applet.mo
/usr/share/locale/de/LC_MESSAGES/alarm-clock-applet.mo
/usr/share/locale/es/LC_MESSAGES/alarm-clock-applet.mo
/usr/share/locale/fi/LC_MESSAGES/alarm-clock-applet.mo
/usr/share/locale/fo/LC_MESSAGES/alarm-clock-applet.mo
/usr/share/locale/fr/LC_MESSAGES/alarm-clock-applet.mo
/usr/share/locale/gl/LC_MESSAGES/alarm-clock-applet.mo
/usr/share/locale/he/LC_MESSAGES/alarm-clock-applet.mo
/usr/share/locale/hi/LC_MESSAGES/alarm-clock-applet.mo
/usr/share/locale/hu/LC_MESSAGES/alarm-clock-applet.mo
/usr/share/locale/id/LC_MESSAGES/alarm-clock-applet.mo
/usr/share/locale/ja/LC_MESSAGES/alarm-clock-applet.mo
/usr/share/locale/ms/LC_MESSAGES/alarm-clock-applet.mo
/usr/share/locale/nb/LC_MESSAGES/alarm-clock-applet.mo
/usr/share/locale/nn/LC_MESSAGES/alarm-clock-applet.mo
/usr/share/locale/pl/LC_MESSAGES/alarm-clock-applet.mo
/usr/share/locale/pt/LC_MESSAGES/alarm-clock-applet.mo
/usr/share/locale/pt_BR/LC_MESSAGES/alarm-clock-applet.mo
/usr/share/locale/ru/LC_MESSAGES/alarm-clock-applet.mo
/usr/share/locale/zh_CN/LC_MESSAGES/alarm-clock-applet.mo
/usr/share/man/man1/alarm-clock-applet.1.gz
/var/cache/apt/archives/alarm-clock-applet_0.3.1-1_amd64.deb
/var/lib/dpkg/info/alarm-clock-applet.list
/var/lib/dpkg/info/alarm-clock-applet.md5sums


Sugi

---

### Post by matt_symes on 2011-01-23
Hi

I am beginning to think you might have a different version of the alarm-clock-applet than i have.

```
matthew@matthew-laptop:~$ locate alarm-clock-applet 
/usr/lib/alarm-clock-applet
/usr/lib/alarm-clock-applet/alarm-clock-applet
/usr/share/alarm-clock-applet
/usr/share/alarm-clock-applet/glade
/usr/share/alarm-clock-applet/glade/alarm-clock.glade
/usr/share/doc/alarm-clock-applet
/usr/share/doc/alarm-clock-applet/changelog.Debian.gz
/usr/share/doc/alarm-clock-applet/changelog.gz
/usr/share/doc/alarm-clock-applet/copyright
/var/cache/apt/archives/alarm-clock-applet_0.2.6-2_i386.deb
/var/lib/dpkg/info/alarm-clock-applet.list
/var/lib/dpkg/info/alarm-clock-applet.md5sums
/var/lib/dpkg/info/alarm-clock-applet.postinst
/var/lib/dpkg/info/alarm-clock-applet.prerm
matthew@matthew-laptop:~$ 
```

As you can see, after a purge and reinstall this is where it has put the files and they are at a different location (with other files) than yours. The version i am using is  0.2.6-2 from synaptic.

BTW: I am using 10.04 so maybe that is the issue.

You installed the alarm-clock-applet from synaptic package manager ?

Kind regards

---

### Post by Sugi on 2011-01-23
I installed it from Ubuntu Software-Center version 0.3.1-1 (alarm-clock-applet).  We are differently on different versions, but I wonder, why my version isn't including the panel add-on.

Sugi

---

### Post by matt_symes on 2011-01-23
Hi

I have just booted into 10.10 and installed the alarm-clock-applet and i see your problem. You do not get that problem with 10.04 and the lower version of the applet. 

I will have a play. If i get success i will post back.

Kind regards

---

### Post by matt_symes on 2011-01-23
Hi

There is a difference in behaviour between the version for 10.04 and 10.10 but i have managed to get it working in 10.10.

In 10.04 you can add it as a panel applet, however in 10.10 it appears differently. This is what i did.

In the terminal i typed

```
/usr/bin/alarm-clock-applet
```It appeared as an notification applet on the right (looks like an alarm clock). Right click on the alarm clock and select preferences and select 'start automatically at logon'. You can set the alarm by left clicking on it and selecting the + button on the left.

This should fix it for you.

Please see attached screenshot

Kind regards

---

### Post by Sugi on 2011-01-24
Hello again Mr. matt_symes,
With your help and a little troubleshooting. I finally got it working!  Pretty much, it wasn't updating the notification for me. I wasn't sure why, but all I had to do was re-add my notification applet and it finally showed up!  I would never thought about that.

Side Note:
On installation, the alarm clock is already set to start up by default.  Did you get this as well?

Thanks!
Sugi

---

### Post by carlturney on 2011-02-12
Here are a few issues on getting Alarm Clock Applet by Pseudoberries to work, after installing, as far as I can see...

As of this date, Synaptic Package Manager only installs 0.2.6 and Update Manager does not update it any higher than that.  On the same date, the Pseudoberries website encourages you to (a) install it more "by hand" and (b) install version 0.3.1

Some versions of alarm-clock-applet (or is it some versions of Ubuntu?) put it in
   /usr/lib/alarm-clock-applet
while other versions of the applet (or Ubuntu?) put it in
   /usr/bin/alarm-clock-applet

The executable alarm-clock-applet program resides in a directory of the same name.

Using Synaptic Package Manager on Ubuntu 10.4.1 to install AlarmClockApplet 0.2.6 did NOT result in it being seen in Applications > anything (e.g. Accessories, System Tools, nor Ubuntu Software Center) (even after rebooting) unlike some of the advice out there on the subject.

Trying to run the program from the terminal...
(1)  Are you logged in as your normal self, or as sudo?  (Does that make any difference?)
(2)  If you don't remember to type ./ before the alarm-clock-applet it will say program not found (or some such) even when you are right in the correct directory.
(3)  With me running AlarmClockApplet 0.2.6 from a terminal session on Ubuntu 10.4.1 it only resulted in the terminal freezing up until I did some Ctrl-D or similar.  It did not result in the AlarmClockApplet appearing anywhere in the GUI environment, unlike some advice out there.

The bottom of   [http://alarm-clock.pseudoberries.com](http://alarm-clock.pseudoberries.com)   tells you to go to
The launchpad project page     [https://launchpad.net/alarm-clock/](https://launchpad.net/alarm-clock/)  for bugs & questions
Where, cleverly hidden in one of the threads often repeated on this problem, the creator [Johannes H. Jensen]("https://launchpad.net/%7Ejoh") explains to newbies that THIS is what you do to the applet once it is installed...

Along the panel at the very top of your screen: 
Left click in a blank area.
Right click.
Choose Add to Panel
Choose Alarm Clock
Choose Add

At this point I finally got the AlarmClockApplet icon in my panel, and I could start using it.

Cheers, Carl, New Zealand

---


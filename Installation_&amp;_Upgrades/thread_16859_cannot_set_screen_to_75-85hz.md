---
title: "cannot set screen to 75-85hz"
date: 2005-02-24
forum: Installation &amp; Upgrades
---

### Post by zoidberg on 2005-02-24
hi.

i cannot set my screen up to 60hz.

outch my eyes are burning

im on 1024x768 and i have a geforce 4 integrated grafique device. the nforce drivers appear to be installed.

---

### Post by p!=f on 2005-02-24
Post your xorg.conf or XF86Config-4.conf here and tell us what monitor you have.

---

### Post by zoidberg on 2005-02-24
sorry i am very noob and i try to search these files with "computer/search for files" menu and i found nothing

i try too to find my monitor settings in device manager and i dont find it..


in 800x600 i can set it to 72hz..

in windows, i can set it to 1024x768 in 75 and 

my monitor is a Envision 17" flat (not LCD)

thanks for your help

---

### Post by p!=f on 2005-02-24
What Ubuntu do you run? Warty or Hoary?
Is this Envision 775e, 720, 510e...?

Anyway, open the terminal and type
```

cat /etc/X11/XF86Config-4.conf

```
or
```

cat /etc/X11/xorg.conf

```
(depends on what version of xserver you run)

Search for something like this:
```

Section "Monitor"
        Identifier      "AOC HT731"
        HorizSync       30-95
        VertRefresh     50-160
        Option          "DPMS"
EndSection

```
and paste it here

---

### Post by zoidberg on 2005-02-24
Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	28-49
	VertRefresh	43-72
	Option		"DPMS"
EndSection

---

### Post by p!=f on 2005-02-24
Cool. Now the model number please so we know what horizontal and vertical refreshes it supports.

You might want to try to replace this:
```

Section "Monitor"
Identifier "Generic Monitor"
HorizSync 28-49
VertRefresh 43-72
Option "DPMS"
EndSection

```
with this
```

Section "Monitor"
Identifier "Generic Monitor"
HorizSync 30-70
VertRefresh 50-90
Option "DPMS"
EndSection

```
and try it.

---

### Post by zoidberg on 2005-02-24
okay thanks i will try this when i will found the way to get root access and change/edit all files :)

im stuck with my install login

---

### Post by p!=f on 2005-02-24
To get a root prompt
```

sudo -s

```
To make an operation which requires superuser privileges (ie editing file in /etc)
```

sudo nano -w /etc/X11/XF86Config-4.conf

```
(note: replace nano with your favorite editor, ie gedit)

---

### Post by zoidberg on 2005-02-24
i was found about the sudo -s command but i was looking for the damn name of the editor! thanks.


and yep my refresh rate is now ok! 

my eyes thanks you a lot of time :)


well, next step for me is for use RPMs

---

### Post by p!=f on 2005-02-24
[QUOTE=zoidberg]
my eyes thanks you a lot of time :)


well, next step for me is for use RPMs[/QUOTE]
Glad to hear your eyes are not blinking anymore. :)

There're no RPMs in Debian world. Only sweet DEBs. :) Fire up "synaptic" for the most comfortable work with packages or "man apt-get", "man apt-cache", "man dpkg" to get a point what's that all about.
Be warned!
```

[~] > LANG=en apt-get -h | tail -1
                       This APT has Super Cow Powers.

```
;)

Good times with Ubuntu.

---


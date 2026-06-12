---
title: "Problems installing V 6.06.1 LTS"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by taipan899 on 2007-01-19
Hi All,

I am unable to install the V 6.06.1 LTS oif Ubuntu on my computer
I have to run the install program from F6 with the line "linux acpi=off noapic nolapic" to start the installation.
I then get an error message, which i have abreviated to:
Warning error (EE) error (NI) not implenated (??) unknown
Unknown log file /val/log/xorg.0.log
using config file /etc/x11/xorg.conf.
It then drops me into the command line as SU.

Where do I go from here?

System:
Intel m/board D946GZ
chip Intel dual core
hd 2X SATA

Taipan899:confused:

---

### Post by taipan899 on 2007-01-20
Hi Again:) ,

After researching my problem I have come up with part of rhe answer.8) 

This is what I have done...

Boot from CD
 press F6 <enter>
[COLOR="Cyan"]linux acpi=off nopic nolapic [/COLOR]<enter>
enter
machine then runs and logs on in non-graphic mode
$ [COLOR="Cyan"]cd /etc/X11[[/COLOR]<enter>
then I ran the Xconfiguration process
[COLOR="Cyan"]$ sudo dkpg-reconnfigure xserver-xorg[/COLOR] <enter>
then answer lots of questions about the computer
[COLOR="Cyan"]$ /etc/ init.d/gdm star[/COLOR]t
$ [COLOR="Cyan"]gdm start[/COLOR]... [COLOR="Red"]<fail>[/COLOR]

Now all I need is for somebody to tell me what to enter into gdm setup.

System:
Intel: M/board DG946GZ
Processor: Dual core
Hard Drives: Western Digital SATA 2X
Monitor: Samsung SyncMaster 955df

I am looking forward to a reply.

Regards Taipan899

---


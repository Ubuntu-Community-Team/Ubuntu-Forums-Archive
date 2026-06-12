---
title: "KControl/Konqueror not saving proxy entries"
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by gsmani_vpm on 2008-10-01
Problem Description:
====================
kcontrol -> Internet & Network -> proxy
I am setting "Manually Specify the Proxy settings" -> setup:
http: www-blah.com 80
Check the box "Use the same proxy for all protocols"

on exiting and restarting kcontrol/konqueror, the proxy was reset to "Connect to Internet directly"

KDE/Kubuntu version:
====================
Installed Ubuntu Hardy and installed kde-desktop over that.
KDE version: 3.5.9

The other desktops I have:
Fluxbox
xfce

Observations:
=============
when I do a
>sudo su
>su myusername -c kcontrol (/konqueror. This is done as root)
and set the proxy to www-blah.com 80, and when I view it back in the same approach,(su-ing from root) the setting seems to be retained. But when I invoke from menu or commandline from "myusername" user, it resets this back to "Connect to Internet directly"

Anyone came across similar problem? I never encountered this issue with other KDE 3.5.9 versions. Is this a problem with installing kde-desktop over ubuntu? I am stuck now as none of the programs work over the proxy(I use akregator, kmail a lot)

Any suggestions are welcome. I can also post the outputs of the commands if someone wants to try some suggestions..(ofcourse after interpreting the command ;) )

Please let me know in case anyone hit this issue already. I am really hoping that this is not a but, but something to do with my setting. But I haven't done much customization since I installed kde-desktop. This is the case from that moment.

Thanks everyone in advance!!

---

### Post by gsmani_vpm on 2008-10-07
I am right now using the workaround for kcontrol and other things. For browsers I am using opera as alternative. And it so far works very well.. :) (Though I think by the responses, this problem has to do something specific with my settings :(..)

By the way I am very new to ubuntu forums(but have bit of experience with linux itself). So I think I can post my problems in a better way from next time.. :)

---


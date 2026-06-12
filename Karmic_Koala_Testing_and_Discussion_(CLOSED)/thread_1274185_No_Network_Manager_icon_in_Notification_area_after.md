---
title: "No Network Manager icon in Notification area after upgrade"
date: 2009-09-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zika on 2009-09-24
I've upgared just now. Among other upgrades there was an upgrade for Network Manager. Now there is no NM icon in notification area. It works but starting nm-applet through Alt-F2 gives nothing ... Any ideas?
```
~$ ps -e|grep Network
 2033 ?        00:00:00 NetworkManager
~$ nm-applet
nm-applet: error while loading shared libraries: libnm-glib-vpn.so.0: cannot open shared object file: No such file or directory
~$ sudo updatedb
~$ locate libnm-glib-vpn.so
/usr/lib/libnm-glib-vpn.so.1
/usr/lib/libnm-glib-vpn.so.1.0.0
```

---

### Post by psyke83 on 2009-09-24
> **zika said:**
> I've upgared just now. Among other upgrades there was an upgrade for Network Manager. Now there is no NM icon in notification area. It works but starting nm-applet through Alt-F2 gives nothing ... Any ideas?

Preferences -> Appearances. Ensure you're using the Human theme, and manually select* the Humanity icon theme (using the Customize button). Then log out and back in to see if the icon is restored.

*This is only necessary because the latest human-theme update which selects the Humanity icons as default is not yet built and uploaded. You may also need to manually install humanity-icon-theme if you're too impatient to wait for the official update which pulls it in.

---

### Post by zika on 2009-09-24
> **psyke83 said:**
> Preferences -> Appearances. Ensure you're using the Human theme, and manually select* the Humanity icon theme (using the Customize button). Then log out and back in to see if the icon is restored.

*This is only necessary because the latest human-theme update which selects the Humanity icons as default is not yet built and uploaded. You may also need to manually install humanity-icon-theme if you're too impatient to wait for the official update which pulls it in.No, I'm not impatient, once You told me what is the cause of my "problem" I'm cool. I'll wait. Thank You!

---

### Post by psyke83 on 2009-09-24
> **zika said:**
> No, I'm not impatient, once You told me what is the cause of my "problem" I'm cool. I'll wait. Thank You!

Well, I'm not certain that will fix the problem. I guessed that since the Humanity icons is now default, the older Human icon theme may be missing the icon you're talking about. I haven't seen any missing icons on my system, and I'm using the Humanity theme

Be sure to let us know if the problem continues. Oh, and the error in your post indicates that the network-manager-vpnc/network-manager-openvpn packages aren't installed, which shouldn't cause theme problems, I think.

---

### Post by ianc on 2009-09-24
I'm not certain it'll fix the problem either...

I'm using the Hanso theme with Breathe icons & it's disappeared for me too since updating just now.

---

### Post by tekstr1der on 2009-09-24
> **psyke83 said:**
> Well, I'm not certain that will fix the problem. I guessed that since the Humanity icons is now default, the older Human icon theme may be missing the icon you're talking about. I haven't seen any missing icons on my system, and I'm using the Humanity theme

Be sure to let us know if the problem continues. Oh, and the error in your post indicates that the network-manager-vpnc/network-manager-openvpn packages aren't installed, which shouldn't cause theme problems, I think.

The Humanity icons by default were only for a few hours yesterday. They quickly switched back to human-icon-theme which removed the Humanity set.

```
human-theme (0.31) karmic; urgency=low

  * Switch back to human-icon-theme for now, there are some unresolved issues,
    and it's not clear yet which one to default to in karmic.


```

I am also experiencing no network as to latest updates and cannot start nm-applet. I get the same errors as the OP.

---

### Post by lbolla on 2009-09-24
> **zika said:**
> I've upgared just now. Among other upgrades there was an upgrade for Network Manager. Now there is no NM icon in notification area. It works but starting nm-applet through Alt-F2 gives nothing ... Any ideas?
```
~$ ps -e|grep Network
 2033 ?        00:00:00 NetworkManager
~$ nm-applet
nm-applet: error while loading shared libraries: libnm-glib-vpn.so.0: cannot open shared object file: No such file or directory
~$ sudo updatedb
~$ locate libnm-glib-vpn.so
/usr/lib/libnm-glib-vpn.so.1
/usr/lib/libnm-glib-vpn.so.1.0.0
```

try:
sudo ln -s /usr/lib/libnm-glib-vpn.so.1 /usr/lib/libnm-glib-vpn.so.0

it worked for me.
L.

---

### Post by psyke83 on 2009-09-24
> **tekstr1der said:**
> The Humanity icons by default were only for a few hours yesterday. They quickly switched back to human-icon-theme which removed the Humanity set.

```
human-theme (0.31) karmic; urgency=low

  * Switch back to human-icon-theme for now, there are some unresolved issues,
    and it's not clear yet which one to default to in karmic.


```

I am also experiencing no network as to latest updates and cannot start nm-applet. I get the same errors as the OP.

Ok, I misinterpreted the problem as a missing icon for the applet, but the applet was functioning. Thanks for the clarification.


By the way, we're at [human-theme 0.33]("https://lists.ubuntu.com/archives/karmic-changes/2009-September/009512.html") now:
> human-theme (0.33) karmic; urgency=low

  [ Martin Pitt ]
  * index.theme.in: Switch icon theme to Humanity.

  [ Kenneth Wimer ]
  * Changing colors in Human theme to chocolate brown
  * Adding HumanLogin theme for GDM


---

### Post by tekstr1der on 2009-09-24
> **psyke83 said:**
> By the way, we're at human-theme 0.33 now:
@psyke93 - thanks. What I was getting at though was that without a network connection, the user would be at the 0.31 state (unable to update to 0.33) and would not have the Humanity set available. That is all I was trying to point out regarding your first guess as to the issue.

@lbolla - Doesn't look like linking is going to do the trick for me:

```
~$ locate libnm-glib-vpn.so
/usr/lib/libnm-glib-vpn.so.0
/usr/lib/libnm-glib-vpn.so.0.0.0
```

EDIT: Never mind. I'm a dummy. Works great. Thanks.

---

### Post by zika on 2009-09-24
> **lbolla said:**
> try:
sudo ln -s /usr/lib/libnm-glib-vpn.so.1 /usr/lib/libnm-glib-vpn.so.0

it worked for me.
L.I planned to do exactly that but I'm afraid that doing it that way I could jeopardize some of pending upgrades ... Anyhow, thank You.
It works ...
Update:Upgrade for humanity-icon-theme and several others just came in, I've cleared symbolic link and done upgrade but the problem persisted. So I've made symbolic link again and icon is there again and everything works. I write this just for the sake of completeness ...

---

### Post by Michalxo on 2009-09-24
Yes, thanks lbolla for that symbolic linking.. Works fine again.
I knew it has to be something with that, but did not know what to link with what :)

---

### Post by HomerSp on 2009-09-24
I had exactly the same problem (although I couldn't access the internet at all), solved it by using lbolla's solution. Thanks!

---

### Post by philinux on 2009-09-24
Network working fine but no icon. Fully update and rebooted with human theme and humanity icons. 

Also only got half a trash can icon.:P

[edit] removed and added back and trash can ok.

---

### Post by tekstr1der on 2009-09-24
The bug regarding this:

[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/427400](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/427400)

now has a fix committed:

```
gnome-main-menu (0.9.12+dfsg-0ubuntu2) karmic; urgency=low

  * libnm-glib soname transition for NM 0.8 - LP: #427400


```

EDIT: Looks like there are a lot more packages depending on this fix. The bug I linked to is tracking all those package fixes. Still could be a little while before this sorts out entirely.

---

### Post by philinux on 2009-09-24
I try never to use workarounds during testing. Waiting is always the best idea. Especially if things are working albeit behind the scenes.

---

### Post by zika on 2009-09-24
We've got a new nice NM icon, at least in Human->aud-Default theme ...
Yes, I'm not fond of changing stuff in the middle of reorganization but I figured that this link is going to be there eventually, by looking to other links concerning NM in that folder ...

---

### Post by mellowtothemax on 2009-09-24
> **lbolla said:**
> try:
sudo ln -s /usr/lib/libnm-glib-vpn.so.1 /usr/lib/libnm-glib-vpn.so.0

it worked for me.
L.

This fixed it for me too.  Cheers. It was doing my head in.

---

### Post by dadedo123 on 2009-09-24
sudo ln -s /usr/lib/libnm-glib-vpn.so.1 /usr/lib/libnm-glib-vpn.so.0


I typed this command in the terminal and it told me that command is not found?

---

### Post by joey-elijah on 2009-09-24
I'm hoping this solves it for me too! Going down for a reboot....

---

### Post by Slug71 on 2009-09-24
> **lbolla said:**
> try:
Sudo ln -s /usr/lib/libnm-glib-vpn.so.1 /usr/lib/libnm-glib-vpn.so.0

it worked for me.
L.

+1

---

### Post by dentaku65 on 2009-09-24
Try

```
sudo cp /usr/lib/libnm-glib-vpn.so.1 /usr/lib/libnm-glib-vpn.so.0

```
```
nm-applet &
```

:P

---

### Post by dadedo123 on 2009-09-24
> **dentaku65 said:**
> Try

```
sudo cp /usr/lib/libnm-glib-vpn.so.1 /usr/lib/libnm-glib-vpn.so.0

```
```
nm-applet &
```

:P

It worked for a few seconds then it went away. My wireless is not working.

> hassan@HassanX2008:~$ sudo cp /usr/lib/libnm-glib-vpn.so.1 /usr/lib/libnm-glib-vpn.so.0
[sudo] password for hassan: 
hassan@HassanX2008:~$ nm-applet &
[1] 2376
hassan@HassanX2008:~$ ** (nm-applet:2376): DEBUG: applet_common_device_state_changed
** (nm-applet:2376): DEBUG: applet_common_device_state_changed
** (nm-applet:2376): DEBUG: applet_common_device_state_changed
** (nm-applet:2376): DEBUG: applet_common_device_state_changed
**
ERROR:applet.c:537:applet_menu_add_items_top_and_fold_sorted_helper: assertion failed: (items)





---

### Post by dadedo123 on 2009-09-24
Did it again, it crashed 2x. Now it's working for the third time. Hope it doesn't crash.

---

### Post by motang on 2009-09-24
> **lbolla said:**
> try:
sudo ln -s /usr/lib/libnm-glib-vpn.so.1 /usr/lib/libnm-glib-vpn.so.0

it worked for me.
L.

Thanks it worked for me.

---

### Post by tekstr1der on 2009-09-24
> **tekstr1der said:**
> The bug regarding this:

[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/427400](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/427400)

Fixes are commited. Tacky to quote myself, but this issue is all fixed with the latest updates. No need to create the symlink if you have functional networking. I deleted the symlink prior to the official package upgrade to ensure it didn't bork anything.

---

### Post by tlois on 2009-09-24
Maybe I'm too tired to think, but I just lost connection with update and it is on a computer desktop that only has wireless access.  Can I do anything about this without internet connection?

On my laptop, so will check back later.

edit- dentaku, thanks.  reread your post and is working.  my almost 50-year-old eyes cannot tell the difference between an I and an L sometimes.  Working now.  Thanks.  Without copy and paste I'm useless.

---

### Post by ljrossi on 2009-09-25
4 days searching, no network on laptop , karmic . I will try this later on faulty network detecion.

Should be a warning for ubuntu team, no net, cant be solve easy , the user just cant get to the internet  , shouldnt be there a offline help or something already built, on how to make a manual internet concetion just in case ?
Maybe a Firefox add on, that puts Ubuntu offline help, to get online.

Regards

---


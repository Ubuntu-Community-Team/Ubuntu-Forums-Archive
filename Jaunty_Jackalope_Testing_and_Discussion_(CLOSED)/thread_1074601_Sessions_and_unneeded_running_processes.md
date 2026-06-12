---
title: "Sessions and unneeded running processes"
date: 2009-02-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by taavikko on 2009-02-19
Rant->

Just wondering why few applications doesn't honor settings defined in
sessions.

Few examples. 

cups. I haven't got printer, so I've disabled cups from sessions.
When upgrade is available that requires restarting. then it's enabled...
Shouldn't it check status and then determine that if it needs to be started at all.

Bluetooth. My computer doesn't have one, so why it is enabled by default.
Kernel...

wpa_supplicant. Same as above, don't have wlan devices, and this is enabled. So not that this isn't configurable with sessions.
network-manager.


So what I'm ranting about is that there are processes that are running even that I don't have any need for them. And I'll suspect I'm not the only one who's affected or annoyed by this?

---

### Post by ronacc on 2009-02-19
not to worry , you don't have those settings anymore anyway , they have taken sessions out of the system>prefs menu and also removed system>quit , they just keep making things better and better .:(

---

### Post by Chrisj303 on 2009-02-19
Where is SESSIONS now?

---

### Post by chrisccoulson on 2009-02-19
> **ronacc said:**
> not to worry , you don't have those settings anymore anyway , they have taken sessions out of the system>prefs menu and also removed system>quit , they just keep making things better and better .:(

System -> Preferences -> Sessions got renamed to Startup Applications. It is still there in the menu and still does the same thing

> gnome-session (2.25.91-0ubuntu1) jaunty; urgency=low

  * New upstream version (LP: #330815):
    - Avoid restarting applications when shutting down.
    - Improve logout/shutdown dialog messages.
    **- Change the capplet name.**
  * 80_new_upstream_session_dialog.patch:
    - Updated for the upstream logout/shutdown dialog
      changes.
  * 98_autotools.patch:
    - New version update.

 -- Chris Coulson < [email]chrisccoulson@googlemail.com[/email]>   Tue, 17 Feb 2009 22:34:30 +0000

---

### Post by taavikko on 2009-02-19
> **Chrisj303 said:**
> Where is SESSIONS now?

That's called "Startup applications" so it's just been renamed.

---


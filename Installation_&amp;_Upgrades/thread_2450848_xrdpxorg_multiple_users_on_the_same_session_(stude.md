---
title: "xrdp/xorg multiple users on the same session (students/teacher)"
date: 2020-09-22
forum: Installation &amp; Upgrades
---

### Post by obuno on 2020-09-22
Hi there all,

I'm looking at some help onto finding a working setup in order to host xrdp (on lubuntu 20.04) and providing a way to share a unique "student" session with another user and/or the same user based on a different host/ip/connection.
My setup is currently working on the xRDP side, all up to what i want expect that I can't find a way to "share" the student session with a teacher. Preferably if possible I'd like to stick with the xrdp/xorg/lxqt combo.

Thanks for any help,
Kind regards,
obuno

---

### Post by TheFu on 2020-09-22
I don't know how to do it with rdp or vnc. Sorry. The problem with VNC and RDP is they have zero security in their connections.  

x2go allows at least 1 "view-only" session [https://wiki.x2go.org/doku.php/doc:usage:desktop-sharing](https://wiki.x2go.org/doku.php/doc:usage:desktop-sharing). x2go uses ssh-based authentication and security.

Or you could simply share the entire desktop on any of the streaming services like Jitsi Meet and allow 50 students to watch concurrently.  Students would view using a webRTC capable browser (Chromium/Chrome/Brave/Firefox .... etc.). I connect using this:
```
$ firejail --private /usr/bin/chromium-browser https://meet.jit.si/{make-up-url-for-this-part}  & 
```
but just pointing most browsers at the URL is sufficient: https://meet.jit.si/{make-up-url-for-this-part} . May want to setup a password. Jitsi is pretty democratic - meaning anyone can kick others out or mute people in the meeting. Jitsi can be setup to record sessions to Dropbox - or anyone can just record it using any of the available screen recording tools like SimpleScreenRecorder (X11-only). My LUG meets this way weekly. This week, we had 16 people in the session from all over the country east coast to west coast.

You can run your own Jitsi Meet server, if you like or if the internet bandwidth requirements are too great so a LAN solution is required.  [https://www.brring.com/2020/04/04/setting-up-a-jitsi-server-in-less-than-15-minutes/](https://www.brring.com/2020/04/04/setting-up-a-jitsi-server-in-less-than-15-minutes/) When you setup your own server, more controls are available.  For adult meetings, we've not had problems once the etiquette was known.

If you just want to share a terminal, **tmux** can do this with 1 other person. [https://brianmckenna.org/blog/guest_tmux](https://brianmckenna.org/blog/guest_tmux)

Sorry, I don't know the answer. Maybe the alternatives can work?

---

### Post by obuno on 2020-09-22
Dear TheFu, thanks a lot for your feedbacks, I'll read and test drive your options. Honestly x2go might be any easay implementation, based on the student wills as well to share it's desktop, will defo try this out.
Maybe I'll also try a VNC based backend approach although i don't really fancy that.

I'll keep you posted. If anyone else has some insights, it's more then welcome!

Kind regards,
obuno

---

### Post by obuno on 2020-09-23
So just coming back the share that x2go is actually very nice and suite's my needs very well.
Thanks for the notch !

kr,
obuno

---

### Post by TheFu on 2020-09-23
Thanks for the feedback.  I know some tech conferences that use x2go desktop share mode from the presenter's laptop to their recording systems. This offloads recording from the presenter's machine. It works pretty well, provided networking and firewalls don't get in the way.

If this is really working for you, please help the community by marking this thread as **SOLVED** - _thread tools_ button near the top of the page.

---


---
title: "Remote desktop to Jaunty from XP"
date: 2009-03-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by davsinc2007 on 2009-03-04
Hi all, Noob here.  I just installed Jaunty and am trying to VNC to it from an XP box.  I can connect fine but I have no mouse control, only the desktop is viewed.  I searched through other posts and the only recommendation I could find was to shut down desktop effects, which I did.  Didn't help my situation.  Was wondering if anyone has experienced this and could provide a work-around.  Thanks in advance.

---

### Post by Rocket2DMn on 2009-03-04
Moved to Jaunty Jackalope Testing and Discussion.
If you are a beginner, we suggest using a stable version of Ubuntu, the latest of which is 8.10 Intrepid Ibex.  Jaunty is still in development and is subject to higher than normal amounts of breakage.  Typically only developers and enthusiasts familiar with the system use development versions of Ubuntu, it isn't for people who need a stable system.

---

### Post by mhjacks on 2009-03-20
There is a package called xrdp that allows remote desktop.  It's in Intrepid (current stable Ubuntu) and works well.

---

### Post by mdalacu on 2009-04-03
i have the almost same problem, mouse works but the screen doesn't get updated, if i relogin the screen reflects the hidden mouse clicks. I think there is a problem with the vnc server. I'm using Ubuntu Jaunty Beta (updated to 4 Apr 2009)

---

### Post by Efros on 2009-04-03
This was an issue in the past with the VNC server not working well with compiz. If you disable compiz on the target machine you can access a desktop that is usable from XP. Not the most satisfactory of solutions but it works, hopefully will be fixed for the full release.

---

### Post by snkngshps on 2009-04-03
I'm having a similar issue. When I connect, my mouse is at the top left hand corner. I can click, but I can't move it (so essentially all I can do is click on the applications menu and just use my keyboard from there). Are the no workarounds/fixes without disabling compiz?

---


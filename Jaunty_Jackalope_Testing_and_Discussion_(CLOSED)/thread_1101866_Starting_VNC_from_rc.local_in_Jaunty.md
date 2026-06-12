---
title: "Starting VNC from rc.local in Jaunty"
date: 2009-03-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mhjacks on 2009-03-20
Hi everyone,

I'm trying to start a VNC session with vnc4server in Jaunty.  The process starts OK, but all I get is the X start screen - the session (which defaults to GNOME) doesn't load.

When I run the same script (rc.local) from the command line via a logged in session, the VNC session starts as expected.

I'm not sure this is a bug - I think it may be related to policykit (since I had to grant explicit permission to use sound players that way for my VNC session user).

I've seen this issue using both i915 and Nvidia proprietary video drivers.

---

### Post by mhjacks on 2009-03-23
I am also tracking this as a question in launchpad:

[https://answers.launchpad.net/ubuntu/+question/65042](https://answers.launchpad.net/ubuntu/+question/65042)

---


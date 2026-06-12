---
title: "Getting Dual-Head, &quot;Big Desktop&quot; Working"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by JSeymour on 2010-01-08
Recently I installed an ATI Radeon HD 2400 Pro 256MB PCI card in my new-to-me Dell PowerEdge 1600SC.  Next I planned to upgrade my 19" flat-screen LCD monitor to a 24" wide-screen version, when a friend suggested that, for the way I mostly would use the system (software development and the like), I'd be better-off with two 19" monitors, because I'd have more screen real estate.  Well, since I already had a matching 19" monitor, that'd certainly be a lot less expensive, so I figured I'd give it a go.

I should note, at this point, that I'm using ATI's proprietary **fglrx** driver.

The first problem I ran into was attempting to use ATI's amdcccle (Catalyst Control Center) utility.  It didn't see the monitor hooked-up to the card's VGA connection.  So I ran *aticonfig --initial=dual-head --screen-layout=right* and that got the ball rolling: Now I had two separate desktops.  Then I simply went back into amdcccle and enabled Xinerama.  (There was some re-starting of X involved in there, somewhere, I'm sure.)  Voila!  I had what I wanted!

Or so I thought.

I was then informed by an on-line colleague that direct rendering would be disabled with Xinerama enabled, slowing-down rendering.  Didn't want that.  So off to figure out how to get it working with Xrandr.

A couple hours later, and none the wiser, I finally put-together bits and pieces I found elsewhere on the web and did this:
[LIST]
[*]Restored the **/etc/X11/xorg.conf** I'd had before running aticonfig the first time.  (Always make sure config files are backed up somewhere before embarking on an adventure like this!)
[*]Ran **aticonfig --initial -f**
[*]Edited **/etc/ati/amdpcsdb** and, in the section **[AMDPCSROOT/SYSTEM/DDX]**, added the line **EnableRandR12=Sfalse**
[*]Edited **/etc/X11/xorg.conf** and in the **Devices** section added **Option      "EnableRandR12" "false"**
[*]Rebooted
At this point I had cloned screens
[*]Ran **aticonfig --dtop=horizontal**
[*]Re-started X by logging off and back on
[/LIST]

Done!  I have just what I wanted and, according to **glxinfo**, I have direct rendering.

Hope this helps somebody else!

An amusing side-effect of this configuration: My screen-saver displays a bunch of pictures that my wife, I and friends have taken over the years.  Now, when it kicks-in, each monitor displays a different picture at any point-in-time. :)

Jim

---

### Post by gsmanners on 2010-01-09
Kudos! In my experience, just getting dual head to work with ATI was a huge pain.

---


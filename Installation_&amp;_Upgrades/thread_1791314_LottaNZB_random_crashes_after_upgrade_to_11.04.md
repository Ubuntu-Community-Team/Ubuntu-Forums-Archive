---
title: "LottaNZB random crashes after upgrade to 11.04"
date: 2011-06-26
forum: Installation &amp; Upgrades
---

### Post by jjsh on 2011-06-26
As per the title, really. I've upgraded to 11.04, ran updates, but I can't stop LottaNZB randomly crashing out. It will be running fine one moment, then 'zap' it disappears. I've tried going through the apps running at the same time, and there doesn't appear to be any pattern. In fact, I've left it running with nothing else open and have returned to a computer with no running apps. Sometimes, however, it will run fine for several hours, completing all of it's downloads, although this is pretty rare. LottaNZB's logs appear to wipe after a crash (unless I'm missing something) so I'm none the wiser why it happens.

Has anyone got any ideas what to try next? It ran faultlessly on Ubuntu 10.x

---

### Post by mendhak on 2011-07-02
I've been noticing the same thing, this is on a fresh install of Ubuntu 11.04.  I suspect this has something to do with the backend, sabnzbd, which it's now using.  It was using HellaNZB in Ubuntu 10.04 and 10.10.  

The best I can think of is attempt to run lottanzb from the terminal with the -d option (for debug messages).  Unfortunately, i haven't seen the crash-disappear happen yet when running from the terminal.  

Don't know if it's significant but I keep noticing this regularly:

> 

/usr/share/lottanzb/lottanzb/core/__init__.py:95: PangoWarning: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Ubuntu 7.03125', text=''
  gtk.main()



It does not cause lottanzb to crash though.  If you're able to reproduce it, please paste the terminal output, it might help figure out what's going on, or even help with searching.

---

### Post by mendhak on 2011-07-02
Coincidentally, I managed to get the error after I posted. Here is what I have:


*** glibc detected *** /usr/bin/python: **
Gdk:ERROR:/build/buildd/gtk+2.0-2.24.4/gdk/gdkregion-generic.c:1110:miUnionNonO: assertion failed: (y1 < y2)
Aborted

---

### Post by mendhak on 2011-07-02
Found the launchpad bug:

[https://bugs.launchpad.net/lottanzb/+bug/692635](https://bugs.launchpad.net/lottanzb/+bug/692635)

---

### Post by jjsh on 2011-07-04
Thanks for your replies ~ I'll keep an eye on launchpad for a fix.

---


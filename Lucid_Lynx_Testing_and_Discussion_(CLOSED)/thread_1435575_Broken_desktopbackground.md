---
title: "Broken desktop/background"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by plun on 2010-03-21
Updated earlier this evening and the background is gone.. just white.

Maybe this Nautilus update causing this...?
[https://lists.ubuntu.com/archives/lucid-changes/2010-March/008502.html](https://lists.ubuntu.com/archives/lucid-changes/2010-March/008502.html)

Cannot see any bug either....
[https://bugs.launchpad.net/ubuntu/+source/nautilus?field.searchtext=&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/ubuntu/+source/nautilus?field.searchtext=&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

---

### Post by ronacc on 2010-03-21
updated a couple of hours ago and I'm not seeing this , updateing again now but just gcc and related coming down this time I don't think that will do anything to the bg .

---

### Post by plun on 2010-03-21
> **ronacc said:**
> updated a couple of hours ago and I'm not seeing this , updateing again now but just gcc and related coming down this time I don't think that will do anything to the bg .

Well, we are 2 users including me within my local national ubuntu forum with this error...  

A light theme gives a white background and a dark theme gives a black background.  No way to change the background.

I have also tested gconf-editor and change settings for Nautilus.

Not a big problem anyway...;)

RGBA...??? Messed around with that....

---

### Post by ronacc on 2010-03-21
maybe thats why I'm not getting it . I don't have a standard theme or BG .

---

### Post by shrimpy89 on 2010-03-23
On my machine, it was the recent Nautilus update that caused this problem to occur.  I had experimental RGBA installed (fun stuff!), and the nautilus update turned my background gray.  Also, infinite Nautilus windows would try to open until I logged out.  From reading the changelog, the developers removed the Nautilus patch that prevented this infinite loop bug (and the broken background, apparently).  

It was originally patched in preparation for RGBA support in Lucid, but it is now pushed back to Lucid +1.  I would assume that that's the reason for removing it.  My "solution" was to uninstall the RGBA ppa.

---

### Post by shrimpy89 on 2010-03-23
*facepalm*

I should have checked out the OP's links before posting.  That's the changelog I was talking about.  Removing the RGBA ppa and reverting the altered packages to vanilla Ubuntu fixed the problem for me, so it's a pretty safe bet that RGBA is to blame.  Which is unfortunate, because I find it to be a nice touch.

---

### Post by peddy on 2010-04-12
Confirmed that it is RGBA support causing the problem. I am still affected by the problem in Lucid Beta 2 with the latest gtk2-module-rgba.

Instead of uninstalling RGBA support, you can add 'nautilus' to the end of /etc/profile.d/gtkrgba.sh. This workaround will disable rgba support for nautilus altogether.

---

### Post by peddy on 2010-04-12
Oh, I just fixed this problem by 'downgrading' to the version of nautilus that was in the ppa (open synaptic, find nautilus, nautilus-data, libnautilus-extension1, ctrl-e on each of them, force the version with 'ppa' in it).

---


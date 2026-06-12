---
title: "Firefox 3.0 won't run"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by wayfarer51 on 2008-06-25
I recently upgraded to FF 3.0, first using the download from getfirefox.com.  Later, it was updated by the Update Manager to full 3.0.  After a while, it was updated again by the Update Manager, and suddenly stopped working.

So then I get panic.

I started trying to remove/install/remove/install. sometimes in different places, sometimes using the terminal, sometimes using the Synaptic Manager, sometimes using the Archive Manager.  What I seem to have now is a mess of Firefoxes spread all over the HD, and no way to sort it out.  Is there any way I can just wipe out all of the Firefoxes on the HD, and just start again?  Of course, I'd like an easy way, but anyway will be OK with me.  I just want FF back.

I'm posting this to the Mozillazine forums also in the hope I might find some help there, too.

Thanks,
Neill

---

### Post by ajmorris on 2008-06-26
Hi there,
The download from getfirefox.com, You would just have to delete the files from where you extracted. For the firefox from the repos, you can do apt-get remove --purge firefox  and remove your .mozilla/firefox directory in your home folder... although, really, you only need to delete the profile directory in ~/.mozilla/firefox. Also, if you start firefox through a terminal, what errors do you get?

AJ

---


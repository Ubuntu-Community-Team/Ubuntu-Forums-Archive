---
title: "can no longer log in to main account"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by chris_tikva on 2008-08-02
I seem to have screwed something up while trying to install the speedtouch firmware. The first sign of trouble was when I noticed that I was no longer able to copy files to my home directory although I could copy them to a subdirectory. I restarted the system and when I logged in I got an error message:

.dmrc file is being ignored.

and a suggestion that the permissions should be 644. I checked that using recovery mode and that seemed ok. However I can't get rid of that error. Also my home directory permissions are rwxr_xr_x - I don't know if that's what they should be.

If I log in using my guest account then it works.

Any way out of this hole I seem to have dug for myself?

Chris

---

### Post by sisco311 on 2008-08-02
run this from recovery mode:
```
chown -R *username:username */home/[I]username
[/I]chmod 0755 /home/*username*
chmod 0644 /home/*username/*.dmrc
```
replace *username  *with your login name.

---

### Post by chris_tikva on 2008-08-02
Thanks, that works well and I'm back in!

The username had been changed to "root" for reasons unknown to me.

---


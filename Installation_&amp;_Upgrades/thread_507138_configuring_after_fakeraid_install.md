---
title: "configuring after fakeraid install"
date: 2007-07-22
forum: Installation &amp; Upgrades
---

### Post by secshunayt on 2007-07-22
After one destroyed Windows installation and several temporary moments of insanity, I finally managed to get Ubuntu 7.04 installed, alongside Windows, with the FakeRaidHowto. However, now that the system is installed, I have a few problems.
[LIST]
[*]Under System->Administration, only a few of the usual tools are present. Most importantly, synaptic is not there.
[*]Unlike every install of Ubuntu I have done on this motherboard, my sound does not work.
[*]Some strange things in the terminal. Rather than starting with, say, "chris@ubuntu-base," all I have is a "$." Do I have no hostname?
[*]Under Applications, there is no "add/remove programs" link. Part of the missing administrative tools, I believe.
[/LIST]

Is there some sort of system configuration that the Ubuntu installer does to give you the tools, that was not covered in the FakeRaidHowto? Is there a package I can install that will give them to me?

On a final note, synaptic can be launched from the command-line; however, every time it launches it acts as though it's the first time it has been.

Any help would be most appreciated!

---

### Post by jlintz on 2007-07-28
add yourself to the admin group and do a visudo to make sure that the line

%admin ALL=(ALL) ALL

exists.  Also change your shell to bash.  ch -s /bin/bash

I had the same problems after my install

---


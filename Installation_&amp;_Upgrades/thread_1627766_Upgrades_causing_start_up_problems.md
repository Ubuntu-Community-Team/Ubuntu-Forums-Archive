---
title: "Upgrades causing start up problems"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by Marco_F on 2010-11-21
I'm using 10.04 and just today installed some updates from the update manager I'm not very experienced so I just install what is there (Not sure if that's a bad idea). Anyway during installation of the updates it prompted me with something about grub and gave me the option of choosing a loader or something. I chose to keep the same one that I had. Then after restarting I get to the ubuntu splash screen but then the screen is just black and won't go to the login screen. I have no idea what I have screwed up and any help would be appreciated. Sorry I don't have more info, I should have been paying more attention.

---

### Post by sikander3786 on 2010-11-23
Welcome to the forums :-)

> Then after restarting I get to the ubuntu splash screen but then the screen is just black and won't go to the login screen

Keeping that in mind, I think there should be no problem with Grub itself.

Which graphics card are you using?

You can try pressing and holding down the Shift key at Bios screen. Once you see the Grub menu, you can use an older kernel and see if it can boot successfully.

If that isn't successful either, highlight the first entry on the Grub menu and press 'e' to edit it. Navigate to "quiet & splash", delete them and type "nomodeset" in their place. Press Ctrl + X to continue boot and see if it takes you to the desktop this time.

---


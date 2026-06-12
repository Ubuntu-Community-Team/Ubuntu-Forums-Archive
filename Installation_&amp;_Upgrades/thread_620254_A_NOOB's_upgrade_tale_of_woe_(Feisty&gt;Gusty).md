---
title: "A NOOB's upgrade tale of woe (Feisty&gt;Gusty)"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by bendrichard on 2007-11-22
When my GF turned on her computer yesterday the upgrade manager popup said there was a upgrade available. The upgrade went smoothly until the restart at the end of the upgrade.

The OS restart didn't get beyond the Ubuntu welcome screen & the progress bar (which didn't show any progress) There were no error messages.

I restarted with the Feisty ISO in the CD and got to the rescue dialog prompt. After searching the forum I found the following "sudo aptitude dist-upgrade" In reply I found this on the screen "a shell (/bin/sh-1) was found on your root file system (/dev/hda1) but an error occurred while running it"

I wouldn't mind doing a clean install and starting over but my GF has bookmarks and a few doc's she's telling (yelling!) that she would really like to have access to.

I'm very new Ubuntu user and have very limited command line experience. Is there a way of recovering her data?

Thanks in advance

---

### Post by luisfcup on 2007-11-23
Try to boot from live-cd with Feisty or Gusty (normal live-cd start, not the rescue), look for the data you what to save and backup it.
Then its probably possible that you can restore you system but if you can't, you will have the critical data safe.

---


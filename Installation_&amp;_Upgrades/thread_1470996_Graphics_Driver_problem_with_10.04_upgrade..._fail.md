---
title: "Graphics Driver problem with 10.04 upgrade... fails to display anything on reboot"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by Jonasan Cope on 2010-05-03
hey folks,

realise we are testing a new build so bugs are likely... and i'm sure someone is already on to fixing this ... but just wondered if anyone had experienced something similar.....

had been running karmic on my T41 Thinkpad very nicely up till now. Just upgraded today to 10.04.

upgrade process seemed to go fine. but on restart the ubuntu logo was displayed as normal while it loaded, then suddenly it froze and a fractured blue line appeared across the middle of the screen. then the display changes to a set of confused flashing lights and a very low resolution - no desktop, just colourful flashing lights and a big mouse cursor. no input works. just sits there flashing at me!

rebooted into recovery mode and can get my system up in low graphics mode so I'm ok for now. I guess this will be sorted out soon enough. have read other threads on here about graphic issues with 10.04 - i am also running a ATI card (Modility 32 MB).

anyone else found this on upgrade? any solutions? cheers

---

### Post by visual_decoy on 2010-05-03
hey dude, i feel your pain. i have a t400 and i haven't upgraded it yet because i fear breaking my setup. so i'll be watching this tread with interest :)

have you tried installing the proprietary ati driver?

---

### Post by Jonasan Cope on 2010-05-03
not exactly sure how to go about the proprietary drivers, and read on another thread that the ATI driver dosn't support 10.04 yet. so probably just going to leave it for the moment.

strange occurences in low graphics mode as well - my close minimise and maximise buttons for all windows have gone to the top left? backwards? wacky... 

still probably shouldn't have upgraded in the middle of a web design project!.. must get back to it. will check back in later to see if anyone has come up with a solution or an update is offered to fix the issue.

---

### Post by Jonasan Cope on 2010-05-04
well my bad...

should have read all the release notes properly first before posting - apologies

turns out grub was my issue. when trying to get karmic on my system i had lots of issues with grub - so when the updater asked me if i wanted to reinstall or update grub i thought it might not be a good idea.

having read the release notes properly, I have now run update-grub and low and behold...10.04 boots perfectly, no graphics issues - and much faster!

thank you so much for the excellent work on this distro.

sorry for the unnecessary post again. 

visual-decoy - take the plunge mate, i reckon they have thoroughly beta tested this, its probably only install mistakes that are upsetting most of the people on here. but the choice is yours.....

---

### Post by Jonasan Cope on 2010-05-04
oh, and selecting a new appearance option from the menu shifted my buttons back into the right places!!

---

### Post by groovomata on 2010-05-06
> **Jonasan Cope said:**
> hey folks,

realise we are testing a new build so bugs are likely... and i'm sure someone is already on to fixing this ... but just wondered if anyone had experienced something similar.....

had been running karmic on my T41 Thinkpad very nicely up till now. Just upgraded today to 10.04.

upgrade process seemed to go fine. but on restart the ubuntu logo was displayed as normal while it loaded, then suddenly it froze and a fractured blue line appeared across the middle of the screen. then the display changes to a set of confused flashing lights and a very low resolution - no desktop, just colourful flashing lights and a big mouse cursor. no input works. just sits there flashing at me!

rebooted into recovery mode and can get my system up in low graphics mode so I'm ok for now. I guess this will be sorted out soon enough. have read other threads on here about graphic issues with 10.04 - i am also running a ATI card (Modility 32 MB).

anyone else found this on upgrade? any solutions? cheers
If I can bother you, how do you get into low graphics mode? My 10.4 installation only boots into a screen of vertical purple lines. When I reboot and press shift I can get to the grub menu and from there I can select recovery mode, but I don't see how to get into a low graphics mode. Unfortunately recovery mode gets me the purple vertical lines as well. 
Thank you,
Erik.

---


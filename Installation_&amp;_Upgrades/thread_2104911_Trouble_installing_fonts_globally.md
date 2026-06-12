---
title: "Trouble installing fonts globally"
date: 2013-01-14
forum: Installation &amp; Upgrades
---

### Post by Doughnut Jimmy on 2013-01-14
I am having trouble installing some .ttfs that I earlier added to a Win7 system and now am trying to add to a 64-bit 12.04 LTS system. I initially installed the fonts to my /home/.fonts folder and all worked well (after sudo fc-cache -f -v the fonts were available in LibreOffice).

Later decided to remove them from /home/.fonts and install in /usr/share/fonts/truetype so the fonts can be used globally. First deleted from /home/.fonts folder and rebuilt cache. Check LibreOffice and they were removed successfully. Then copied in pasted into new folder /usr/share/fonts/truetype/myfonts and rebuilt cache. There was an "invalid cache" warning, so rebuilt cache again. No error this time. Rebooted, but fonts not available in LibreOffice. Went to tweaks/fonts section of Ubuntu Tweak, and the names of the installed fonts appear but the example characters below the names are black-bordered white rectangles (NOT "The quick brown..." in the selected font).

Uninstalled from /usr/share/fonts, reinstalled in /home/.fonts, and the fonts worked again in LibreOffice. Uninstalled from /home/.fonts, installed in /usr/share/fonts, not working again (this time used sudo fc-cache -rv).

Additionally, I downloaded a new font from the web and placed file in /usr/share/fonts. After sudo fc-cache -f -v this new font shows up working normally in LibreOffice. None of the others work, however, unless in /home/.fonts.

Last try: tried sudo mv ~/.fonts/name.font /usr/share/fonts/ for all of the fonts. They are now located in /usr/share/fonts and working on my administrator account. However, they still don't work for any other accounts (standard or guest).

Any ideas what the heck is going on??? I would still like to use these fonts globally.

---


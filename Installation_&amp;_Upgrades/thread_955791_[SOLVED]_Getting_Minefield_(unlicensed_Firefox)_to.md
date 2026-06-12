---
title: "[SOLVED] Getting Minefield (unlicensed Firefox) to use system default locales"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by CharonM72 on 2008-10-22
I recently installed an unlicensed version of Firefox (Minefield) and now it refuses to switch my locale to whatever Ubuntu has as its default and will only use English. I can manually switch the locale through about:config, but I'd much prefer it to switch by itself. What string should I put in general.useragent.locale to replace en_US so it'll be the system default?
If someone with a working version of Firefox with a dynamic locale would go to about:config and read me the general.useragent.locale string for me, that would likely solve it.

EDIT: Installing Firefox language packs through the repository does not apply them to this version of Firefox, and I really really don't want to have to manually install every language pack I need. Is there a way to fix this? Or for that matter, purge all traces of Firefox and reinstall it licensed? (Purging all Firefox files and deleting Firefox directories in usr/lib does not work). Or, do the Xulrunner language packs work for Firefox? They are listed in "Languages" in the plugins list, and are all enabled, but obviously do not work.

---

### Post by CharonM72 on 2008-10-22
Fixed- running firefox-3.0 instead of firefox ran the licensed version with the dynamic locale.

---


---
title: "Never-ending problem in upgrading Xubuntu 7.04 to 7.10"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by DonQuichote on 2007-10-18
I have the gratest trouble upgrading my system. I started the update with update-manager -d, like was said on the ubuntu home page.

I have a package called texlive on my system, which is a remnant of tying to get docbook to work. Generating PDF from docbook is beyond hope, because is needs a toolchain that has a few missing links.

However, the upgrade process still wants to upgrade texlive-base-bin, and I killed the update of that package after it had run for 9(!) hours. I killed it by trying ctrl-break and ctrl-c in the output terminal window.

All well so far, I had to click away a few obvious dependency problems, but I noticed the upgrader continued by installing packages that were already installed. After an hour or so, it re-tried to hang on the texlive-base-bin package again.

Is there a way to gracefully exit the upgrade process? It will never complete this way. If I exit it it non-gracefully, how do I repair the package system? Last time I tried (which was when the tex package was installed) I spent 2 hours searching the net on how to remove just one package.

Other remarks about the installer:
When a configuration file has to be replaced, it asks the user if the old or the new one has to be used, while showing a unified diff. Is there any way to start a diff editor on such an occasion? Keeping the old file is obviously wrong, as the diff was not issued without reason. Replacing is also the wrong answer, because it throws away the config, which an updater should not do. And the unified diff is not very helpful to innocent (non-developer, that is) users. It really disappoints me that the upgrader only asks questions of which it does not accept any right answer.

Thanks in advance for your help.

Edit: The loop is not infinite. Look, I typed the whole solution and this fine forum threw it all away.

---

### Post by tkrisz on 2007-10-22
> **DonQuichote said:**
> 
Other remarks about the installer:
When a configuration file has to be replaced, it asks the user if the old or the new one has to be used, while showing a unified diff. Is there any way to start a diff editor on such an occasion? Keeping the old file is obviously wrong, as the diff was not issued without reason. Replacing is also the wrong answer, because it throws away the config, which an updater should not do. And the unified diff is not very helpful to innocent (non-developer, that is) users. It really disappoints me that the upgrader only asks questions of which it does not accept any right answer.


I was thinking exactly the same.
Maybe the updater could find out a suggestion for the  new config file. Or is it a dream?

---


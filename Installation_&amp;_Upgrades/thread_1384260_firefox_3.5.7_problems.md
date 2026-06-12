---
title: "firefox 3.5.7 problems"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by aljoriz on 2010-01-18
I downloaded the tar.gz of firefox 3.5.7 and installed it via the old tweak from psychocats using this command at the terminal with the firefox3*tar.gz at my home directory:

if [[ ! -f /usr/bin/firefox ]]; then sudo apt-get update && sudo apt-get install firefox; fi && if [[ -e ~/.mozilla ]]; then cp -R ~/.mozilla ~/.mozilla.backup; fi && sudo tar -jxvf firefox-3*.tar.bz2 -C /opt && rm firefox-3*.tar.bz2 && sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup && sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins && sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox && sudo ln -s /opt/firefox/firefox /usr/bin/firefox

farmville works well but lags on the 3.5.7 specially when chatting with more than 2 people

Now I wonder how do I revert to the original ubuntu firefox?

---


---
title: "all is fine, updates Kubuntu..."
date: 2019-08-04
forum: Installation &amp; Upgrades
---

### Post by spi2 on 2019-08-04
all is fine, updates Kubuntu, I have install Skype and Chrome, but in Chrome do not keep the settings after shutdown, what can I do?

---

### Post by Impavidus on 2019-08-05
This is guesswork. Maybe Chrome's config files are not writable for the user. Maybe the config files are owned by root. This may happen when you run applications with sudo when you shouldn't (**never** run a web browser with sudo). I don't use chrome, so I don't know where it stores its config files, but my guess is somewhere in $HOME/.config or $HOME/.chrome or $HOME/.google. Find it and make sure everything is owned by you and you have write permission.

---


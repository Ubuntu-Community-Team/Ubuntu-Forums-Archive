---
title: "Expert installation mode?"
date: 2005-08-04
forum: Installation &amp; Upgrades
---

### Post by erik-the-red on 2005-08-04
How much control does the expert installation mode give me?

I may have to do this for Breezy Badger.

---

### Post by tomchuk on 2005-08-05
[QUOTE=erik-the-red]How much control does the expert installation mode give me?

I may have to do this for Breezy Badger.[/QUOTE]
 How much control do you need? Even in regular mode, you can Ctrl-Alt-f2...f6 to activate consoles and manually run whatever commands you need to.

---

### Post by erik-the-red on 2005-08-05
[QUOTE=tomchuk]How much control do you need? Even in regular mode, you can Ctrl-Alt-f2...f6 to activate consoles and manually run whatever commands you need to.[/QUOTE]
 I guess there's too much software installed that I don't use.

Perhaps I can streamline the installation?

---

### Post by tomchuk on 2005-08-05
Gotcha, yes expert mode will only install what you need to boot a system and install packages with apt. You'll have to manually install everything else you need.

---

### Post by erik-the-red on 2005-08-05
[QUOTE=tomchuk]Gotcha, yes expert mode will only install what you need to boot a system and install packages with apt. You'll have to manually install everything else you need.[/QUOTE]
 Thanks for the reply.

Will expert mode installation also allow me to individually select package groups? I remember the Slackware installer can allow a user to do this.

---

### Post by tomchuk on 2005-08-06
Once you reboot into your minimal Ubuntu system after the expert install, you can run tasksel to select groups of packages to install. If you're going to do this, it might just be easier to do a regular install and manually prune the applications you don't want.

---


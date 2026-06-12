---
title: "Thunderbird 3 - add Dictionaries (Shredder)"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by Tido on 2009-12-23
Hi

I work with Ubuntu 9.10 - Karmic Koala.
via the deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main  I've installed the latest Thunderbird 3 (Shredder 3.0.1pre)

So far so good, runs nice, searching is much better, but has only english-dictionary. 
When I go to Edit/Preferences /Composition/Spelling and click on : Download more Dictionaries : nothing happens!

Can I somewhere download the dictionary and copy it in the correct folder or so? 

Any hint appreciated

---

### Post by Poytu on 2010-01-07
[https://addons.mozilla.org/en-US/thunderbird/browse/type:3](https://addons.mozilla.org/en-US/thunderbird/browse/type:3)

---

### Post by Tido on 2010-01-09
> **Poytu said:**
> [https://addons.mozilla.org/en-US/thunderbird/browse/type:3](https://addons.mozilla.org/en-US/thunderbird/browse/type:3)

Thank you very much!!! \\:D/
I never expected to search there. Addons are for me something else.

Br,
Tido

---

### Post by cwhisperer on 2010-05-17
> **Poytu said:**
> [https://addons.mozilla.org/en-US/thunderbird/browse/type:3](https://addons.mozilla.org/en-US/thunderbird/browse/type:3)

Installed and restarted Shredder, but the dictionaries I installed are not selectable and not shown in the list. In the add-on window I still see the message: This add-on will be installed when Shredder is restarted.... Any help? Regards

---

### Post by lenooh on 2012-06-11
> **cwhisperer said:**
> Installed and restarted Shredder, but the dictionaries I installed are not selectable and not shown in the list. In the add-on window I still see the message: This add-on will be installed when Shredder is restarted.... Any help? Regards

Just had the same problem... and solved it.
To get spellcheck in Thunderbird (actually seems to be system-wide) install the "myspell-<language_code>" package.

Just search for "myspell" and then install your language of choice:
```
sudo apt-cache search myspell
```
then install the chosen language by:
```
sudo apt-get install myspell-<language_code>
```
and of course replace <language_code> with your language.

---


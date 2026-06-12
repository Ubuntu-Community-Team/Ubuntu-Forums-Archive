---
title: "Keep getting an error message when trying to update and install apps"
date: 2020-04-09
forum: Installation &amp; Upgrades
---

### Post by justinjstewart on 2020-04-09
The error message is:
"Unable to download updates:
failed to refresh cache: E: The repository 'http://
ppa.launchpad.net/clipgrab-team/ppa/ubuntu eoan Release'
does not have a Release file."

I am brand new to Ubuntu with the exception of having tried it back in or around 2003ish whenever Ubuntu was first becoming popular. I was not willing to devote time to learning the terminal but now I am as learning more about how computer systems actually function is something I am interested in. However that is not to say that I wish to completely rely on the terminal either.

---

### Post by deadflowr on 2020-04-09
Either open the program called Software and Updates 
and go to Other Software and disable/remove the entry for clipgrab,

or run this in the command line
```
sudo add-apt-repository -r ppa:clipgrab-team/ppa
```
No archives for it exist for 19.10.

---


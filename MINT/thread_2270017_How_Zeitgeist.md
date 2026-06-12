---
title: "How? Zeitgeist?"
date: 2015-03-19
forum: MINT
---

### Post by N00b_H3r3 on 2015-03-19
Hello.

I have questions how can I completely remove Zeitgeist?

I use this command...
sudo apt-get --purge remove zeitgeist

and get this log ...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'zeitgeist' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.

But on Update Manager have...

[IMG]https://www.imageupload.co.uk/images/2015/03/19/updatemanager.png[/IMG] ??

---

### Post by ajgreeny on 2015-03-19
Are you using Mint?  I don't have such an update-manager in any of my *ubuntu VBox installs, but I think it looks like Mint's version as that shows those Level numbers from 1 - 5.

Do you have synaptic installed as it is the best GUI package manager and may tell you a bit more about zeitgeist's status.

---

### Post by N00b_H3r3 on 2015-03-19
Hi, ajgreeny. 

Yes I use Mint. I find in synaptic libzeitgeist-2.0-0 and libzeitgeist-1.0-1 installed but if I  try uninstall completely synaptic say "To be removed: nautilus" for libzeitgeist-1.0-1 and "To be remove: totem-plugin, unity, unity-tweak-tool" for libzeitgeist-2.0-0. Can it is be removed without removing the other tools?

---

### Post by ajgreeny on 2015-03-19
Looks like it can not be removed as it is a dependency of nautilus which I do not use, being on xubuntu. It also seems you have only the library packages installed from that list, not zeitgeist itself. Am I right?
Why do you want to remove them; they do not cause any problems, I assume?

---

### Post by N00b_H3r3 on 2015-03-19
"It also seems you have only the library packages installed from that list, not zeitgeist itself." 

Yes only library.

"Why do you want to remove them; they do not cause any problems, I assume?" 

No problem, but I do not need anything from the zeitgeist...

**Edit:** I completely remove library. System works fine, thats it. Thank you for your time and help.

---

### Post by deadflowr on 2015-03-19
moved to **MINT** sub-forum

---


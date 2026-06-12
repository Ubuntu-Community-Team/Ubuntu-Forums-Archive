---
title: "Freeze on Update 12.04LTS"
date: 2014-03-24
forum: Installation &amp; Upgrades
---

### Post by shane18 on 2014-03-24
I'm a very basic Ubuntu user, had it running for 6 months on my Samsung N210 and was very happy. 
Yesterday I ran software updated overnight (plugged in) and this morning it won't boot. It shows the Ubuntu logo, colours one of the dots then freezes. I've gone into recovery mode and tried a different (previous) version. No good 
I've tried networking mode and ran update and upgrade. Nowt!
I don't know which logs I need to look at or what to examine, sorry, but will post what people ask me if it will help

Obviously I've tried searching for a solution and can't find one, so any help would be gratefully received

Thanks

Shane

---

### Post by ibjsb4 on 2014-03-25
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get -f install
```

Get any errors?

---

### Post by shane18 on 2014-03-25
I tried startx and there was no x-window active. So I installed one (as per the error suggestion) and it allowed me to access the desktop (the resolution was different to normal). Decided that if I upgraded to 12.10 it might be a fresh install and that worked,

Thanks

Shane

---


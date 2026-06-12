---
title: "Automatically Install Sources For An Application's Source"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by netyire on 2007-06-10
Hello all! :D

I recently read stuff about speeding up Ubuntu through prelinking and preloading, and even something about GNU_HASH if I'm not wrong. (Its on the forums)

I wondered if compiling an application would optimize its execution. After checking the forums, there was some information about this. I followed the instructions or adapted it accordingly.

Then I tried compiling an application, namely ktorrent 2.1.4. Originally, I think my system lacked the required dependencies to compile the app, however, after trying to install ktorrent (2.1) via apt-build, I realized it (apt-build) installed the required dependencies! (Yay! If it could have installed ktorrent, automatic installation of dependencies for the compilation of an application's source is pretty impressive).

Anyway, something went wrong with the installation (I think this is because of gpg signing, but don't worry, I happy to leave this issue unresolved). I've compiled ktorrent 2.1.4 with code optimization enabled and, after prelinking, I'm quite sure the startup is 6 seconds shorter!

Thanks for reading this far! If I am not wrong, you can automatically install the required libraries to compile an application by typing: ```
 apt-get build-dep <appname> 
```

[COLOR="SeaGreen"][B]Question: "How do you remove the automatically installed dependencies in an automatic fashion?"
[/B][/COLOR]
Thanks! (Yes, I know its a bit long :()

---


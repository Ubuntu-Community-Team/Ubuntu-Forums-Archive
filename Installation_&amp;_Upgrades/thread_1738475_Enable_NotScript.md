---
title: "Enable NotScript?"
date: 2011-04-24
forum: Installation &amp; Upgrades
---

### Post by cortimi on 2011-04-24
[COLOR=Black]I am trying to enable the password for NotScripts for Google Schrome. I have no idea how to access the area I need to so I can change the password. The website for NotScripts says to navigate to "~/.config/google-chrome/Default/Extensions/odjhifogjcknibkahlpidmdajjpkkcfn" and just how am I supposed to do that?

Latest Ubuntu, latest Chrome
[/COLOR]

---

### Post by conradin on 2011-04-24
"~" indicates a home directory.
From your home directory type in the terminal:
```

cd .config/google-chrome/Default/Extensions/

ls


```
"odjhifogjcknibkahlpidmdajjpkkcfn"
might be the folder or file name, but more likely, its some randomly assigned name. .config is some hidden folder.

---

### Post by cortimi on 2011-04-24
Any idea how to get there from the gui, or how do I open that file from the terminal?

---

### Post by fdrake on 2011-04-24
```
gedit ~/.config/google-chrome/Default/Extensions/NameOfExtension
```
put the name of the extension you see in the list of the command of the previous post

---


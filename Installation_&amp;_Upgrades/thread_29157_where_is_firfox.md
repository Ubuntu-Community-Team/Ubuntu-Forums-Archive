---
title: "where is firfox"
date: 2005-04-23
forum: Installation &amp; Upgrades
---

### Post by gigi on 2005-04-23
Hello 
hope this is not a stupid question but it sounds like,...
Where can i find firefox on my new installed kubuntu?
The package mozilla-firefox-locale-en-gb is installed. 
But I cannot find an entry in the Menu

Thanks fro every help

---

### Post by xzentorian on 2005-04-23
Applications->Internet->Firefox

---

### Post by gigi on 2005-04-23
[QUOTE=xzentorian]Applications->Internet->Firefox[/QUOTE]
 There is only: kfrb, kopete, kpp, konversation, krdc ,... but no firefox :-(

---

### Post by Gary Powers on 2005-04-23
Drop to terminal and use the command "mozilla-firefox" .... or you can create a launcher on the desk using the same command.

Gary

---

### Post by gigi on 2005-04-23
[QUOTE=Gary Powers]Drop to terminal and use the command "mozilla-firefox" .... or you can create a launcher on the desk using the same command.

Gary[/QUOTE]
 It seems that there realy is no mozillo on my system. a find . -name  moz* doesn't brings a good result.
Does someone know if it will be installed by default?
Is it possible to make an online update to get all necessary packages for firefox ?
Whats the easiest way to get a firefox?

---

### Post by gigi on 2005-04-23
[QUOTE=gigi]It seems that there realy is no mozillo on my system. a find . -name  moz* doesn't brings a good result.
Does someone know if it will be installed by default?
Is it possible to make an online update to get all necessary packages for firefox ?
Whats the easiest way to get a firefox?[/QUOTE]
 ok done, after uncomment of the lines 
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hoary main restricted
in file  /etc/apt/sources.list

the package manager shows firefox ant thunderbird  now it's working well :-)))

---

### Post by bored2k on 2005-04-23
[QUOTE=gigi]There is only: kfrb, kopete, kpp, konversation, krdc ,... but no firefox :-([/QUOTE]
 First of all, you are in Kubuntu. Kubuntu has no firefox by default [not that I know of].

---

### Post by crazybill on 2005-04-24
If you type which firefox, you will see that the running binary is usr/bin/firefox

However, for plug-ins, the lib files path for firefox is /usr/bin/mozilla-firefox

---


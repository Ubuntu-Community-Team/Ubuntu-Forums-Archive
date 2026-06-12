---
title: "Google Chrome in 12.04 Install Errors"
date: 2012-09-22
forum: Installation &amp; Upgrades
---

### Post by awesomeusername on 2012-09-22
Having problems installing Google Chrome... 

```

Errors were encountered while processing:
 google-chrome-stable:i386

```


```

$ sudo  apt-get install google-chrome-stable
$ E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```




Tried a bunch of potential solutions I found Googling, but no go. I suck at Linux so it could be something stupid... Help please :)

---

### Post by vasa1 on 2012-09-22
Didn't you (?) already get the answer over at [askubuntu.com]("http://askubuntu.com/questions/191791/chrome-install-failed-on-ubuntu-12-04")? There it was suggested that you get Chrome from Google's site rather than from wherever you seem to be trying to get it from.

---

### Post by awesomeusername on 2012-09-22
I have tried that actually.

---

### Post by vasa1 on 2012-09-22
> **awesomeusername said:**
> I have tried that actually.
And what happened? You should get into verbose mode if you want a solution :)
The more you explain what happened, even if it's a bunch of nasty-looking errors, the more likely it is that someone may figure things out for you.

"I have tried that actually" just isn't enough.

---

### Post by hogriderj on 2012-09-25
Maybe I can interject as I am having the same problem. I have tried downloading the 32-bit installer from Google's website to the "Downloads" folder. I renamed the *.deb file to chrome.deb and then tried using Terminal and entered the following:
cd /Downloads
sudo dpkg -i chrome.deb

(See attached image).

It did not work. And to be more  verbose, it only states that errors were encountered while processing. It appears after processing triggers for man-db.

Any ideas ubuntu gurus? For both of us?

---

### Post by vasa1 on 2012-09-25
> **hogriderj said:**
> ...
(See attached image).
...
In such cases, don't post an image; it shows only a limited number of lines. Next time copy the entire output and paste it here between code tags (the # symbol above the text area).

Delete whatever you've downloaded. Start afresh and please follow exactly what the download page recommends. I suggest you visit dl.google.com. Also, accept the suggestion to let Google install a ppa.

And when you have the .deb, just right click on it and choose install via Ubuntu Software Center (or words to that effect). No need of terminal heroics ;)

---


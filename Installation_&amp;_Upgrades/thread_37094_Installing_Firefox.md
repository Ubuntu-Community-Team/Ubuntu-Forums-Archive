---
title: "Installing Firefox"
date: 2005-05-25
forum: Installation &amp; Upgrades
---

### Post by carbon unit on 2005-05-25
Hello, Im trying to install Firefox 1.0.4 over 1.0.2, when I download the file I get a archive manager, where do i go from there to instal 1.0.4?

---

### Post by Staesys on 2005-05-25
Extract it to a folder in your home directory. I use "temp". open a root terminal and cd to that directory. Run the firefoxinstaller "./firefoxinstaller" is the command, I believe.

It will ask you for an install directory, be sure you don't just click past it, it's easy to miss. Install it into /usr/lib/mozilla-firefox (default location for ubuntu).

Before installing it though, you might want to back up your plugins directory first, or they'll go byebye when you upgrade.

This should do it.

-Paul

---

### Post by sapo on 2005-05-25
I would recommend you installing the one in the backports repositories using apt-get

for more info:
[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

---

### Post by carbon unit on 2005-05-26
That didnt seem to work, there has to be a easier was to install programs ](*,)

---

### Post by Seti on 2005-05-27
Just go over to the Mozilla website ([http://www.mozilla.org/products/firefox/](http://www.mozilla.org/products/firefox/) ) and download The newest [Firefox](http://download.mozilla.org/?product=firefox-1.0.4&os=linux&lang=en-US) .
Just download the file, don't use the "open with file-roller"; choose the "Save to disc" option.
Save the .gz to your home directory and do:
```
tar xvzf firefox-1.0.4.gz
``` 
 Then just cd to the new directory it makes called "firefox-installer".

Then just do ```
./firefox-installer
``` 

This will run the installer and you can just install it right into the same "firefox-installer" folder. AFAIK there is nothing wrong with doing it this way and you don't even have to mess with root or sudo or anything else; Firefox is there in that folder.

---


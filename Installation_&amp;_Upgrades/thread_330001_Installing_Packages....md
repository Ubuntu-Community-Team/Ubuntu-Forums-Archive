---
title: "Installing Packages..."
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by motermouth on 2007-01-02
I'm new with ubuntu and I'm running edgy. I just had another post where I asked if there was a way to get repositories on another computer and then bring them over and i found out about packages. Anyways I was wondering how I should install those packages once I've brought them over on my removable memory chip. The one that I would like to install is a .deb file. Thanks for the help...

~Motermouth~

---

### Post by earobinson on 2007-01-02
you should be able to double click the deb file to install it.

But if you have a bunch of files you want to install you can use the command line ```
sudo dpkg -i <package name>
``` if they are all in the same dir you could use this command ot install them all ```
 sudo dpkg -i *
``` of cource you would have to browse to the correct dir first

---

### Post by earobinson on 2007-01-02
[QUOTE=motermouth]Hey I have one more quick question for you...

the code was: sudo dpkg -i <package nae>

whats the -i for?[/QUOTE]
Its always best to post your questions to the thread, I will reply there even if its to say I dont have an answer that way everyone can see the results.

In regards to your question the -i stands for install. If you want more info on any linux command you can always use the man command ```
man dpkg
``` for example will tell you more info about the dpkg command including what the -i stands for.

---


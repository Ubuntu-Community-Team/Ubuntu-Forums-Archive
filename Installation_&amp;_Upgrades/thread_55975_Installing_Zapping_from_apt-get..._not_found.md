---
title: "Installing Zapping from apt-get... not found?"
date: 2005-08-10
forum: Installation &amp; Upgrades
---

### Post by Donshyoku on 2005-08-10
I am trying to install and play with Zapping for TV watching/recording.  It seems to be fairly popular on the forums.

I tried sudo apt-get install zapping, and it didn't find the package.  It isn't shown in Synaptic either.

Do I need to add a repository for it, and if so which one?  I don't know much, but I can edit my repository list, heheh.  

Thanks again!

---

### Post by adwait on 2005-08-10
You need to enable universe in your repositories. Heres how:

```
sudo gedit /etc/apt/sources.list
```

Open it up, and at the end of the URLs, add the word "universe" after hoary-main, hoary-updates etc. Save and close the file. THe run
```
 sudo apt-get update
sudo apt-get zapping 
```
That should do it..

---

### Post by Donshyoku on 2005-08-10
Thanks, I got it installed, but I have a question...

How do I display through composite connection?  I have the cords wired just fine, and I made a channel in the list for composite and nothing.  Also, choosing the input source as composite seemed to do nothing.  Just a black screen.

I am going to DL TVTime and see if I get anything in it as I know that my TV tuner works fine with it (judging from using it in Fedora Core 4)...

---

### Post by adwait on 2005-08-10
Sorry no idea, I haven't ever used it :). I guess, you would be better of asking in a separate thread.

---


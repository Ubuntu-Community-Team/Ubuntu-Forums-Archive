---
title: "Gimp"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by wombil on 2007-07-19
Hello All'I am trying to install the gimp help files,so far I have an icon on my desktop,
"gimp-help-en- 2+0.9-1 all.deb"  I am having trouble installing this onto the computer or into the gimp program to be able to use it.Can anyone help with this problem?
Thanks,
Wombil.

PS is there a way to increase the font size permantly so I can throw my magnifying glass out?

---

### Post by matthewboh on 2007-07-19
To install the help files, just run the Synaptic Installer (under System | Administration | Synaptic) and search for gimp.  I think it's called gimp-help-common or something like that.  Select it to be installed, and it installs it for you.

The problem with the font - just go into System | Preferences | Font and select the Application font style - it will affect all of your programs.

---

### Post by KIAaze on 2007-07-19
You could also just double-click on the .deb file you have and follow the instructions. :)
But synaptics is always a better solution since the files come from a trusted source (unless you added some special repositories) and it also makes the removal process easier.

---

### Post by wombil on 2007-07-19
Thanks fellers,
Will do all this tonight when I get a chance.
Cheers,
Ray.

---

### Post by wombil on 2007-07-20
Thanks again fellers,got gimp-help-en off the synaptic installer.Seems to be what I need.
In one section it mentions parasites on layers and then goes on to say,"If you don't understand it
don't worry about it".         I love that bit, suits me.
                                              Thanks again.

---

### Post by Herman on 2007-07-20
There's a great website for  learning all about GIMP is called [GIMP SAVVY]("http://gimp-savvy.com/") and it features the book [Grokking the GIMP]("http://gimp-savvy.com/BOOK/"), by Carey Bunks. 
It's almost a must-read for anyone learning how to use GIMP, I highly recommend it.

Regards, Herman :)

---

### Post by wombil on 2007-07-22
Thanks Herman,I'll certainly have a look at this.
I have downloaded  Gimp-help-en ok and its working well. When uodate manager starts it has 
Gimp-help-Common available for installation with a warning:-
 You are about to install software that can't be authenticated ! Doing this could allow a malicious individual to damage or control your system.
I have installed the other updates but not this one.Is it safe to install this update and is this warning similar to the windows ones that are mostly ignored anyway?
        Thanks heaps for the other help fellers,
         Wombil.

---

### Post by KIAaze on 2007-07-22
gimp-help-common can be found on [http://packages.ubuntu.com/](http://packages.ubuntu.com/), so I suppose that it's an official package and safe to use.

If you only have official repositories (archive.ubuntu.com, security.ubuntu.com (main, restricted, universe, multiverse)) in "System -> Administration -> Software Sources", downloading it through update manager or synaptic should be safe.

The message you got means that there has been a problem with the GPG private/public key authentication.
I don't know in detail how it works, but I don't think you need to worry too much about it right now.
I got this message a few times too.

On the other hand, I don't want you to take on bad Windows habits too. ^^
Such warnings are not useless and shouldn't always be ignored.
So if you add extra repositories and download unofficial packages, be careful. ;)

---

### Post by wombil on 2007-07-22
Thanks KIAaze,I thought it would be ok but just making sure as I dont want to stuff up a clean system.
                         Thanks mate.

---


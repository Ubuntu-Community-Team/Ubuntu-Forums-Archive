---
title: "Lost Panel after executing Aptitude command on Python"
date: 2015-02-10
forum: Installation &amp; Upgrades
---

### Post by jchen015 on 2015-02-10
So guys, I executed the Aptitude to uninstall my python(v2.7) due to some development work. However, i think i typed in something and all my other files were also removed.

Now when i reboot into Ubuntu (v12.04), My desktop has no Panels and I am unable to perform any operations.

The link below shows the errors...

Link : [https://www.dropbox.com/sh/763dbcysv0scjvl/AABnUN7ZtnlUYv3rmFQV0ZD7a?dl=0](https://www.dropbox.com/sh/763dbcysv0scjvl/AABnUN7ZtnlUYv3rmFQV0ZD7a?dl=0)


Furthermore, I have alot of dependency problem. 
E.g. 

[FONT=Consolas]The following packages have unmet dependencies:[/FONT]python-software-properties : Depends: python (< 2.7) but 2.7.3-0ubuntu2 is to be installed
                          Depends: python-pycurl but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
What is the issue???

Please help....

Regards,
Julius

---

### Post by v3.xx on 2015-02-10
Sounds like this.

[http://askubuntu.com/questions/187227/i-run-sudo-apt-get-remove-python2-7-can-i-restore-my-ubuntu-now](http://askubuntu.com/questions/187227/i-run-sudo-apt-get-remove-python2-7-can-i-restore-my-ubuntu-now)

---

### Post by jchen015 on 2015-02-11
Referencing from the model answer.

"[COLOR=#333333][FONT=UbuntuRegular]To do this, manually download the [/FONT][/COLOR]python2.7[COLOR=#333333][FONT=UbuntuRegular] package (and its dependencies), and manually install them using [/FONT][/COLOR]dpkg[COLOR=#333333][FONT=UbuntuRegular] (bypassing APT, which requires Python). Once that's installed, [/FONT][/COLOR]apt[COLOR=#333333][FONT=UbuntuRegular] should work again, and so [/FONT][/COLOR]apt-get install ubuntu-desktop[COLOR=#333333][FONT=UbuntuRegular] will restore your system. (If [/FONT][/COLOR]apt-get[COLOR=#333333][FONT=UbuntuRegular] still doesn't work, you might also need to download and install any missing dependencies.)"

Can someone please help me understand what is manually download the python 2.7 package (and its dependencies), and manually install them using dpkg?

How do we even do this? I am having problem with the ubuntu desktop, how do i even run the installation? 

Unless I reinstall the whole Ubuntu12.10 , which I need idea on how to do it without entering the Ubuntu Desktop. Can I have the ubuntu-12.10.iso file to boot it from a USB drive to perform reinstallation?[/FONT][/COLOR]

---

### Post by v3.xx on 2015-02-11
Your first post says 12o4, which has long term support support till 2017.  You last post says 12.10, which is a sort term release and has reached end of life and no longer supported.  Which one are you running?
> Can someone please help me understand what is manually download the python 2.7 package (and its dependencies), and manually install them using dpkg?

Its a simple command that can lead to mental anguish.
```
sudo dpkg -i **name of package**
```
Dpkg does not understand dependencies like apt-get, so you must manually add these.  Sometimes its just a few depends, sometimes it leads to dependency hell, where you get into the depends of the depends of the dependencies.

You may not be comfortable with any of this and to be honest I would not be either.

Consider starting over with a fresh install.  Like I said, 12.04 is support till 2017.  14.04 is the latest release out with long term support and is supported till 2019.

---


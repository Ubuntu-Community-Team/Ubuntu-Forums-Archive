---
title: "Re-installing versus upgrading"
date: 2005-12-06
forum: Installation &amp; Upgrades
---

### Post by steevc on 2005-12-06
I did an upgrade of my Hoary+Kubuntu -> Breezy a while back. This caused me quite a few [problems]("http://www.bagofspoons.net/cgi-bin/pyblosxom.cgi/Computer/20051022ubuntu.html").

I managed to fix those issues, but lately my system seems to be getting less stable. Various applications are crashing and I can't install some packages.

I'm thinking I should make a fresh start and re-install. I'd probably start from Kubuntu this time. KDE 3.5 looks interesting. Is it possible to get that as part of a Kubuntu install CD or will I have to upgrade afterwards?

Before I got Ubuntu I had Knoppix. I kept my home directory (on it's own partition) and was able to keep most of my settings. Is it possible that some of those could cause me problems?

Is there any way to list all the packages I added since installing Ubuntu so I can make sure I get everything back?

I really like Ubuntu and it seems my problems are an exception, so I want to give it another go.

---

### Post by cdhotfire on 2005-12-06
If you dont mind downloading it all, you can do a semi fresh install upgrade.:rolleyes:

Ive tested it works great.

Add all the breezy nessesary repositories, and:

```

$ sudo apt-get install debfoster

``` 
Then were not add the programs you want to keep, rhythmbox, amule, that sort of thing

```

$ sudo gedit /var/lib/debfoster/keepers

``` 
Then to that file add
```

debfoster
ubuntu-minimal

``` *Put any extra packages you want to keep under these 2.

Then just press crtl + alt + f1, and you should be in a black screen with white letters. :o

Now press crtl + c, if it doesnt show something like bob@smith:~$.

Now do:
```

$ sudo debfoster -f

``` 
This will remove all packages except for the ones in the keepers file.

After its all done just do

```

$ sudo apt-get dist-upgrade

``` 
and you should be set to go. Plus you get to keep all your home things + configurations.:cool:


To see what you have installed currently,
1. Go to Synaptic ( System -> Administrator -> Synaptic..)
2. Then at the bottom there are 4 buttons, click status, 
3. Then select Installed

---

### Post by steevc on 2005-12-07
Thanks. That sounds like a possibility. I gather that debfoster is a tool to purge packages you don't want.

> Then just press crtl + alt + f1, and you should be in a black screen with white letters.

Does that kill the X server? I do at least know what a console screen looks like :)

Having to download everything is not too big an issue as I have a 2Mb connection. I recently had to reinstall KDE after it got removed when I was trying to sort out Skype.

One of my other issues is with getting sound working from multiple applications at once. I've played with the settings suggested in other posts with a lack of success. I gather that this may have been fixed in Breezy, but would that only apply in a fresh install? I'm assuming a standard upgrade does not change the various set-up files whereas an install would create them with the latest recommended settings.

I'll have a play and report back.

---

### Post by cdhotfire on 2005-12-16
debfoster, as the name implies fosters whatever debs you want to keep, and allows you to take away others without dependecie problems.  And yes, crtl + alt + f1, kills x.

---

### Post by dejitarob on 2005-12-18
ctrl+alt+f1 switches to a virtual console and does not kill x. To do this, log out and switch to a virtual console with ctrl+alt+f1 (or f2, f3, etc, ctrl+alt+f7 switches back to x). Login and type sudo '/etc/init.d/gdm stop' (/etc/init.d/kdm if you have kubuntu). ctrl+alt+backspace kills and restarts x but you lose any unsaved data. 

I had some problems when I upgraded from 4.10 to 5.04 but I recently upgraded to Kubuntu 5.10 on my other box and it seems fine. I would just give the upgrade a shot since it literally takes just a few minutes to complete. If you run into any problems that you can't seem to figure out you could then to a fresh install and save your home directory and keep your settings. I though I saw a few backup guides on the forums that describe this in depth.

---

### Post by steevc on 2005-12-18
After cleaning up my sources file I've got back to a more stable system. There's still a few issues, but I need to isolate them to work out what they are. No doubt I will be back here with more questions soon.

Thanks for the suggestions.

---


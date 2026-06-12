---
title: "Eclipse 3.4 in Intrepid?"
date: 2008-08-31
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by vishalrao on 2008-08-31
Synaptic shows the eclipse package is at version 3.2 at the moment. Any chance of the package being updated to Eclipse 3.4?

---

### Post by BackwardsDown on 2008-08-31
I found the bug-report here:
[https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/123064/](https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/123064/)

---

### Post by xlinuks on 2008-08-31
I think it's a good idea to have a list of programs that keep being updated to the latest version regardless. Since Ubuntu is increasingly used (among other things) as a testing and development platform - the first programs in the list should be Eclipse, NetBeans and their most common plugins. I for one never use NetBeans from the Ubuntu repos cause it's always too old. I'm pretty sure many people act as I do.

---

### Post by Nullack on 2008-08-31
Its a MOTU package so take it up with them. They have a mailing list and an IRC chan.

---

### Post by uBeer on 2008-09-01
Would indeed be nice to have it in the repos. I use it a lot for my studies, so I have to download it from the website to get the latest and the greatest. Hope it'll be updated!

---

### Post by tepsipakki on 2008-09-01
Packaging Eclipse 3.4 is not a trivial task due to new dependencies etc. Better help the Debian folks with it, the maintainer has asked for help on debian-java@. It most likely won't make it in 8.10.

---

### Post by ger_macaco on 2008-10-08
Would it be OK to install it from Eclipse's website? I mean, would it be stable or really buggy?

---

### Post by mrinaldotnet on 2008-10-08
> **ger_macaco said:**
> Would it be OK to install it from Eclipse's website? I mean, would it be stable or really buggy?

Perfectly stable and very easy to do, just go for it. I stopped using Ubuntu's version of Eclipse around two distros ago... :)

---

### Post by fballem on 2008-10-08
Some detailed instructions for installing Eclipse 3.4 in Hardy Heron are found here [http://ubuntuforums.org/showthread.php?t=941461](http://ubuntuforums.org/showthread.php?t=941461). They should work for Intrepid. Please let me know if they don't

Many thanks,

---

### Post by frodon on 2008-10-08
Instaling eclipse is really easy, untar the archive downloaded from the eclipse website somewhere on your drive and double click the eclipse icon, you're done :)

Then later you can use alacarte to add an entry somewhere in your ubuntu menus.

I just did this to have eclipse ganimede on my hardy box and it took me just few seconds.

---

### Post by mihai.ile on 2008-10-08
> **frodon said:**
> Instaling eclipse is really easy, untar the archive downloaded from the eclipse website somewhere on your drive and double click the eclipse icon, you're done :)

Then later you can use alacarte to add an entry somewhere in your ubuntu menus.

I just did this to have eclipse ganimede on my hardy box and it took me just few seconds.

This is what I have been doing since Ubuntu Dapper.
Actually the website version is less buggy/faster than the one from repositories (from my experience it always was so).

---

### Post by fballem on 2008-10-09
> **mihai007 said:**
> This is what I have been doing since Ubuntu Dapper.
Actually the website version is less buggy/faster than the one from repositories (from my experience it always was so).

I'm curious to know where eclipse is installed to if the download is double-clicked. I think it installs to the ~/eclipse folder, which is probably not the best place to install.

---

### Post by mihai.ile on 2008-10-09
Well since Windows 98 days I had a "Programs" folder where I put applications that do not need an install. Think of it as my personal "Program Files" folder that windows has.
Here in Ubuntu I use the same "~/programs" folder where I put things like Eclipse, Google GWT, Teamspeak, etc.

Oh and eclipse is not "installed" on double click, it's just an archive that I extract under "~/programs" and then make the shortcut in the gnome menus.

---

### Post by frodon on 2008-10-09
@fballem It installs nowhere, it's a standalone application, it's the power of java !

You can even keep your install on usb key and use it on several different linux PC, i tested the same install on usb key on ubuntu and RedHat and it works like a charm.

---

### Post by wgrant on 2008-10-09
> **frodon said:**
> @fballem It installs nowhere, it's a standalone application, it's the power of java !

Wrong. It is the power of having self-contained apps. Little to do with it being written in Java.

---

### Post by fballem on 2008-10-09
> **mihai007 said:**
> Well since Windows 98 days I had a "Programs" folder where I put applications that do not need an install. Think of it as my personal "Program Files" folder that windows has.
Here in Ubuntu I use the same "~/programs" folder where I put things like Eclipse, Google GWT, Teamspeak, etc.

Oh and eclipse is not "installed" on double click, it's just an archive that I extract under "~/programs" and then make the shortcut in the gnome menus.

If I'm reading your note correctly, then if there is a second user on your computer, they would need either a second copy extracted under their ~/programs folder, or they would need access to your ~/programs folder.

The main reason that I 'install' eclipse in the way that I do is so that multiple user accounts can share a single copy of eclipse. Another reason is so that if there is a standard way in which eclipse should be configured, then I only have to make the change in one place. The last reason is space - if there are multiple accounts, there needs to be only a single copy of the core eclipse files. Please note that individual user settings still reside in the ~/.eclipse folder. There are other reasons, such as only needing to install updates once.

There are many ways to solve a problem. The way that I have found to solve the problem of installing eclipse is one that works in many environments, including commercial environments.

Regards,

---


---
title: "Possible Problems to be Encountered: Installing 10.10 over an old Ubuntu dual OS"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by Oventoaster on 2011-01-29
Hello Everyone,

I havent given up yet on installing Ubuntu 10.10, I found this alternate installer version and hoping that this one might work.

anyways, since Im still currently downloading ubuntu-10.10-alternate-i386.iso, I'd like to know what are the possible problems I might encounter IF:
[B]
"I already have an installed Jaunty Jacalope dual booting with Windows 7 and I'm planning on "overwriting" my installed Jaunty with ubuntu 10.10" [/B]

by overwrite meaning I want to use the disk space being occupied by my Jaunty for installing ubuntu 10.10, i dont really know if thats possible but feel free to bash me if not.

I already do have I little idea on what might happend.
-there might be some weird stuff on that grub thingy and I might not be able to boot to windows 7
-what Im planning might not be possible since ubuntu will instead format my disk
-or my laptop will just completely exlode because of windows 7 and ubunut 10.10 battling to the death on who's os is going to prevail, wiping the whole universe of sentient life.

ok the last part might not happen but who knows.

If you'd done this before or have an even better method on installing ubuntu 10.10 over an old ubuntu build with windows 7 in it, 

**PLEASE (WITH CHERRY AND ICE CREAM ON TOP)** [B]IM ULTIMATELY BEGGING FOR HELP OR ANY INFO THAT MAY BE USEFULL

[/B]I dont want another of my thread being ignored to oblivion. and I'll pretty much hate you if you told me to google it (I obiously did that already)

Thanks
OvenToaster (will give free toast to who ever helped)

---

### Post by mikewhatever on 2011-01-29
You said it your last thread that you'd successfully installed Ubuntu 10.10 from usb. What happened to that?
The alternate installer is text based and thus is a bit harder to use. If installing from a usb stick worked before, I'd suggest that.

---

### Post by Oventoaster on 2011-01-29
did I!? nah.. it didnt work really...

what did worked was that the USB version got installed successfully on my "Desktop" PC not on the laptop.. 

maybe I got too exited when I manage to get pass the infinite white dot loading and decided to post that it worked but ultimately failed, so I installed the old jaunty instead and out of frustration forgot to post that the problem still exist...

ok sorry bout that I get shorterm memory loss sometimes...

well anyways any Idea or guides I might use when Installing the text based version??

Thankies
P.S apreciated your post :D

---

### Post by Oventoaster on 2011-01-29
> **mikewhatever said:**
> You said it your last thread that you'd successfully installed Ubuntu 10.10 from usb. What happened to that?
The alternate installer is text based and thus is a bit harder to use. If installing from a usb stick worked before, I'd suggest that.

I was able to find my last post:

> [B]Trial 8
-[/B]I did tried installing the CD on my Desktop selecting *Install Ubuntu* and again It worked perfectly, but is still not working on my Laptop 

I wanted that to be Installed on my laptop but it didnt work... :(
plus [JaJaBinks]("http://ubuntuforums.org/member.php?u=698873") has the same problem, not even [Gungan]("http://en.wikipedia.org/wiki/List_of_Star_Wars_races_%28F%E2%80%93J%29#Gungan") can handle such a sinister problem O_O

---

### Post by mikewhatever on 2011-01-29
Well then, good luck with the alt cd.

---

### Post by Oventoaster on 2011-01-29
thats it? only words of encouragement? no tip or guide or anything? :frown:

oh well.. finished downloading it hope this one works fine, and thanks for wishing me luck :D

---

### Post by mikewhatever on 2011-01-30
Here is a site with guides on how to use the alt installer.
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)

As for what might happen, well, you might format something or create partitions you don't want. You also might hit the four primary partitions limit or not like the blue background colour of the installer. A dozen of other unexpected things might happen, so make sure you have a backup.

---

### Post by kansasnoob on 2011-01-30
> **mikewhatever said:**
> Here is a site with guides on how to use the alt installer.
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)

As for what might happen, well, you might format something or create partitions you don't want. You also might hit the four primary partitions limit or not like the blue background colour of the installer. A dozen of other unexpected things might happen, so make sure you have a backup.

+1!

Specifically this page:

[http://members.iinet.net.au/~herman546/p2.html](http://members.iinet.net.au/~herman546/p2.html)

Just be sure you properly identify your existing Jaunty partitions by device designation before beginning. Do you understand device designations well?

Browse through that web page and if you have any questions at all please do ask.

---

### Post by Oventoaster on 2011-01-30
omg thanks! your a life saver :D though I think I'll try backing stuffs up first maybe doing it next next saturday... 

and heres a star :KS enjoy!
ehem dont want to close the thread yet though I may post some stuffs here again if it failed miserably or my laptop suddenly exploded :D

---

### Post by kansasnoob on 2011-01-30
I just happened to think that since that shows using the Guided-resize option when you get to this screen:

[http://members.iinet.net.au/%7Eherman546/p2.2/2_.001_previous-changes-to-disk.png](http://members.iinet.net.au/%7Eherman546/p2.2/2_.001_previous-changes-to-disk.png)

You'll want to choose Manual and then select your existing Jaunty partitions to install on. The next screen will be similar to this:

[http://members.iinet.net/%7Eherman546/p3/3.002.png](http://members.iinet.net/%7Eherman546/p3/3.002.png)

NOTE: it's very, very important to select the proper partitions here!!!!!!!

After selecting each partition a screen will appear that looks like this:

[http://members.iinet.net/%7Eherman546/p3/3.003.png](http://members.iinet.net/%7Eherman546/p3/3.003.png)

So you have several options to complete and I'd want to know what your Jaunty partitions look like before making any more comments. So, if you want more detailed help, please boot into Jaunty and post the output of:

```
sudo parted -l
```

```
df -H
```

BTW that's a lower case L in the first command, and intentionally a CAP H in the latter.

---


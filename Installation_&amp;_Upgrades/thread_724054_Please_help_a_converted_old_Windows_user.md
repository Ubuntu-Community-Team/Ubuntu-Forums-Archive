---
title: "Please help a converted old Windows user"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by Rob2008 on 2008-03-14
HELP PLEASE.,

Fed up with windows so have wanted to try Linux for some time now. Tried Red Hat long time ago but didn't like it
So... loaded Ubuntu and VERY impressed with it, i am told that the Linux community are very helpful in fixing problems so.....

Tried Beryl and actually got it working after a struggle, but unfortunately the Emerald themes do not work i have also lost my close min, etc icons.

At one stage i had the problem that the plug in for Emerald was out of date.:confused:

Played around with my xorg.conf  so not sure if that has something to do with it ?:(

Really want to stick with Linux this time and not go back to Windows, what i want is to be able to use two windows programs in Ubuntu they are Microsoft Money 2005 and Microsoft Publisher I know i can use WINE but found that difficult to set up and i was not successful

Any help / advise would be appreciated THANK YOU !

Rob

---

### Post by luisromangz on 2008-03-14
Beryl is old software, you should use Compiz Fusion instead, which is the project resulting from the merger of Beryl and its father project Compiz.

Your xorg.conf may have something to do, but better check it after you tried compiz fusion.

Using wine is quite easy, but maybe you want a newer version of it, as it improves much which each version, and they release one once a couple of weeks. Use this repository:

deb [http://wine.budgetdedicated.com/apt/](http://wine.budgetdedicated.com/apt/) gutsy main

Once wine is installed, programs install like in windows. Chances are that the programs works or not, as running one os software in another is almost a miracle, and wine although an incredible project doesn't foul all windows software yet. If it doesn't work, then you can either look for a Linux equivalent of that software, or try keeping a windows box around for those times you need to use the software.

---

### Post by gtdaqua on 2008-03-14
or if u have good hardware u can run VMware and install windows on it - just for using Money and Publisher. But Wine is a brilliant project and i guess those apps should work. 

Btw, you need to add the line "deb [http://wine.budgetdedicated.com/apt/](http://wine.budgetdedicated.com/apt/) gutsy main" to your "/etc/apt/sources.list" file.

or simply type:

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
sudo echo deb http://wine.budgetdedicated.com/apt/ gutsy main >> /etc/apt/sources.list

```

the first line backs up ur existing file and the second inserts the URL at the bottom of the file.

---

### Post by Rob2008 on 2008-03-14
Thank you for the quick replies.

*Beryl is old software, you should use Compiz Fusion instead, which is the project resulting from the merger of Beryl and its father project Compiz.*

Yep using Compiz but Emerald thing not working :( 
I have had it working before but since i out Compiz on its not working.

---

### Post by NightwishFan on 2008-03-14
Open a terminal and type:
```
emerald --replace
```
What does it say?

---

### Post by Rob2008 on 2008-03-14
> **NightwishFan said:**
> Open a terminal and type:
```
emerald --replace
```
What does it say?

The cursor just flashes does nothing :confused:

---

### Post by NightwishFan on 2008-03-14
Nothing shows up in the terminal?

---

### Post by luisromangz on 2008-03-14
If emerald is not working, try using gtk-window-decorator. Reading another threads it seems that it's difficult to make compiz choose gtk-window-decorator instead of emerald, if the latter is installed. That's why I suggested using fusion-icon to launch compiz, as it manages that fairly well.

---

### Post by Rob2008 on 2008-03-14
> **NightwishFan said:**
> Nothing shows up in the terminal?

Took ages but nothing shows up.

---


---
title: "Wine Issues ( 5.10 Breezy)"
date: 2006-06-24
forum: Installation &amp; Upgrades
---

### Post by senkila on 2006-06-24
(If in wrong area, please move it =) )

Heya. Having abit of trouble with wine. 
What I'm planning on installing Netscape and then a plugin for it so I can chat on a place called [Oasiz](http://www.oaserv.co.uk).
So what I've done so far is built Wine from source by following [this](http://www.winehq.org/site/download-deb) guide (its near the bottom).
When I right click the file and select "Open With" and select "Wine Windows Emulator", more or less nothing happens. Yet when I select "Wine", an error pops up saying ```
Netscape will not run on this version of windows. This version of Netscape runs on the following OS'
Windows 98, 98SE
Windows ME
Windows 2000
Windows XP, Windows XP SP2

```

Tried running it with Cedega, but when it gets to the install screen, It hangs so I have to do the favor of Ctrl+Alt+Backspace.

Any idea's or How-Tos?

Cheers

---

### Post by Winblowz on 2006-06-24
To install WINE all you need to do is 
```
apt-get install wine
```

---

### Post by manicka on 2006-06-24
[QUOTE=Winblowz]To install WINE all you need to do is 
```
apt-get install wine
```[/QUOTE]

you need sudo there as well

```
sudo apt-get install wine
```

---

### Post by manicka on 2006-06-24
Also, the thread title says a problem with breezy but your profile indicates you are a Dapper 6.06 user. What version of Ubuntu is the problem on?

---

### Post by senkila on 2006-06-25
Ah yea, sorry about that part, probably confused alot of people.
I'm currently runnin' on Breezy, no idea why it shows up as 6.06 in my profile...

And a side note to the smartasses in this thread, apperently you didn't read right. I -have- WINE. its not WORKING, get the hint?

---

### Post by manicka on 2006-06-25
[QUOTE=senkila]
And a side note to the smartasses in this thread, apperently you didn't read right. I -have- WINE. its not WORKING, get the hint?[/QUOTE]

People are suggesting that you use the Wine packages that are available in the repos rather than build from source (no one is being a smartass and you'll get a lot more help by toning things down). I think you'll find it a much more reliable way to do things and will give you the latest stable version of wine. Getting the latest wine for breezy is slightly different process than in Dapper as it's not available in the main repos.

I would suggest reinstalling wine using the method in this this how-to.

[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

N.B. rename your .wine directory to .winebak and allow the wine directory to when you run winecfg the first time.

---


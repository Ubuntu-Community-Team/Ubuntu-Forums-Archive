---
title: "I am getting nowhere o this forum, 14.04 is a mess!"
date: 2015-05-14
forum: Installation &amp; Upgrades
---

### Post by Peter_Bartolovich on 2015-05-14
Two identical nettops, sitting 6 feet apart, running 32bit 14.04 Unity/firefox browser/w/google search after a October 2014 online  auto-upgrade from 12.04 (only ubuntu-no Microsoft/wine/adobe, propietary allowed in this house) both, on the same broadband. 

When these two received upgrade notifications back in October both were auto-upgraded.  one unit took the program upgrade and has worked fine ever since....... the other "sister-computer" has had constant, never-ending, mess-in-its-pants problems  that noone on here has been able to help me with for the last 8 months.

The "one" computer loaded up 14.04 and immediately created five vinstant /new problems :

1) it "lost" the ubuntu software center (it Unity icon-loads, goes through the whirly-circle "loading process", flashes briefly on the monitor, and then is gone), the many many many hours of wasted "fixes" and attempted repairs by the experts accomplished nothing.

2) it placed a red do not enter circle in my header, that says:
      Unknown Error:'<class'SystemError'>'
(E:Type'debhttp://dl.google.com/linux/chrome/deb/'  is not known on line 1 in sources.list.d/google.list)'

*packages have unmet dependencies*--- which no one on here has been able to solve, all the wasted hours have gone nowhere !

3) it replaced my 12.04 google chrome browser with Firefox, and made chrome absolutely unloadable or available ever again ! (even after the accumulated sixteen long hours of ubuntu online help suggestions and failed attempts by the supposed ubuntu experts).

4) it makes any attempt to use the clumsy/dumb terminal fail with a notice of:
 E: Type 'debhttp://dl.google.com/linux/chrome/deb/' is not known on line 1 in source list /etc/apt/sources.list.d/google.list
E: The list of sources could not be read.

5) the Terminal failure on all other sometimes five minute long operations always ends saying something about:  the inability to read an Opera file and a google chrome stable file, (I cannot find that exact fault wording right now,)

I am ready to become a single computer user, since 14.04 has destroyed mine..... I have three very large intl websites up on bluefish/Gftp and cannot screw around with a strip and reload, I need help !!1

I have spent  (wasted)  easily overy 150 hours trying to follow the experts advice, nothing works ! 14.04 screwed up "my" computer big-time,

---

### Post by QIII on 2015-05-14
Having reviewed your posts on *this *forum, I find four from November 2014 in a thread where you did not provide information requested; one in January in a thread where you did not provide information requested; and this one.

Hardly a great flurry of attempts to fix things over the last 8 months *here*.  We can't answer for what other advice you may have followed elsewhere.

You would get better help if you were willing to work with those willing to help you.

This thread was started with a laundry-list of vague problems.  That is hard to deal with and threads become convoluted and confusing.  Many users will see that sort of post and simply walk away.

I would suggest starting individual threads, one for each specific issue, and then responding to those who want to help.  Nobody here has a crystal ball or a magic wand.  Feedback is necessary.

---

### Post by matt_symes on 2015-05-14
Hi

Firstly take note of QIII's post.

Almost all of your problems are related to this

```
debhttp://dl.google.com/linux/chrome/deb/
```

in the file

```
/etc/apt/sources.list.d/google.list
```

Open a terminal and type

```
sudo rm /etc/apt/sources.list.d/google.list
```

Enter your password. It will not be echoed to the screen.

Then type

```
echo deb http://dl.google.com/linux/chrome/deb/ stable main | sudo tee /etc/apt/sources.list.d/google.list
```

Then type 

```
sudo apt-get update
```

```
sudo apt-get install -f 
```

Finally type

```
sudo apt-get upgrade
```

If you get any errors on any of the above commands then post back the errors.

That should, hopefully, get you nearer.

Now i am making a massive assumption that this is the correct url as i don't use chrome

```
http://dl.google.com/linux/chrome/deb/
```

Kind regards

---

### Post by Bashing-om on 2015-05-14
Peter_Bartolovich: ^^

Confirmation of Mat's response:
```

sysop@1404mini:~$ cat /etc/apt/sources.list.d/google-chrome.list
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main # re-enabled 06Jul2014 on upgrade to trusty
sysop@1404mini:~$ 

```

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by matt_symes on 2015-05-14
Hi

Thank you bashing-om :p

Kind regards

---


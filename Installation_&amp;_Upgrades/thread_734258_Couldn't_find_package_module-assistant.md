---
title: "Couldn't find package: module-assistant"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by Bonanzaman on 2008-03-24
Trying to compile smartlink driver with:

$ sudo module-assistant auto-install sl-modem

and get:

  Couldn't find package: module-assistant

Where to from here?

Gutsy on a Dell Optiplex GX240
P IV, 512RAM, 40GBHD

---

### Post by kellemes on 2008-03-24
Install the package first..
```
sudo apt-get install module-assistant
```

---

### Post by Bonanzaman on 2008-03-24
Yessir, tried that, still get

Couldn't find package: module-assistant

??

---

### Post by Bonanzaman on 2008-03-24
OK, in full then after:

*sudo apt-get install module-assistant*

I am getting:

[I]Reading package lists...done
Building dependency tree
Reading state information...done
E: Couldn't find module-assistant[/I]

---

### Post by kellemes on 2008-03-24
And you have the universe repositories enabled in /etc/apt/sources.list?
It should be there..
[http://packages.ubuntu.com/gutsy/module-assistant]("http://packages.ubuntu.com/gutsy/module-assistant")

---

### Post by Bonanzaman on 2008-03-24
OK, got the .deb files downloaded and ran:

*$ sudo module-assistant auto-install sl-modem *

which ran the module-assistant, but I got module-assistant error:

[I]Installation of the sl-modem-source source failed
Ignoring this package. Maybe you need to add something to sources.list, maybe the contrib and non-free archives[/I]

How would I find the sources.list folder, and what to look for there?

---

### Post by Bonanzaman on 2008-03-24
OK, with 
/etc/apt/sources.list I get:

permission denied

?? What's up with that??

---

### Post by Bonanzaman on 2008-03-25
OK, so why am I not getting a request for my password here
as usual?

---

### Post by kellemes on 2008-03-25
You need the multiverse repositories enabled for "sl-modem-source"

Please post the output of
```
cat /etc/apt/sources.list
```
I will tell you what to change..

You can also do the following and copy the hole text in a post..
```

gksudo gedit /etc/apt/sources.list
```

---

### Post by Bonanzaman on 2008-03-25
Thanks, kellemes.....it is:

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

........ and 4 more lines with ubuntu.com links....I can type them out as well
if needed.......

of course I am trying to install the modem, so I have no internet connection!

---

### Post by kellemes on 2008-03-25
> **Bonanzaman said:**
> 
of course I am trying to install the modem, so I have no internet connection!

Yes, you are.. I actually forgot about that ;-)
Well.. I'm currently sort of.. speechless, I really don't know how you need to handle this to be honest. :confused:
Sorry Bonanzaman.

Maybe someones else can jump in here?
Maybe you can change the title of this thread to "Installing sl-modem-source without internet" or something like that.

---

### Post by Bonanzaman on 2008-03-25
OK, we will give that a shot!  It has become an exercise in burning files, ect to discs.....all I need is internet access and the flood gates open up!!

Can anyone get me a little further along here?

THANKS!

---

### Post by Bonanzaman on 2008-03-25
Started a new thread "Installing sl-modem-source without internet" but have received no answer....Couldn't I download the needed source codes on my windows/internet enabled machine to a cd, and then transfer to my Ubuntu machine??
Problem is, I don't know which files are needed?????

---

### Post by kellemes on 2008-03-25
[http://packages.ubuntu.com/gutsy/sl-modem-source]("http://packages.ubuntu.com/gutsy/sl-modem-source")

This shows the package and it's dependencies..
To show you the complexity.. One of it's dependencies is "debhelper", now.. click on debhelper and you'll see it's dependencies.. one of them is "perl".. now click on perl and you'll see it's dependencies.. etc.. etc.. etc.. etc.. Even though a lot of those packages you probably already have, this is a mess.

I understand you've already visited the following page?
[https://help.ubuntu.com/community/DialupModemHowto]("https://help.ubuntu.com/community/DialupModemHowto")

I hate to say this.. but maybe you'll have better luck using another distro?
Ubuntu isn't well know for supporting the not so bleeding edge of technology, shamefully enough.

---

### Post by Bonanzaman on 2008-03-25
Gulp! I think I understand the problem ( a little). I wonder if changing to an
external modem wouldn't be easier? I have heard they work pretty well with Ubuntu. Or would I be facing the same issue(s)?

---

### Post by kellemes on 2008-03-25
> **Bonanzaman said:**
> Gulp! I think I understand the problem ( a little). I wonder if changing to an
external modem wouldn't be easier? I have heard they work pretty well with Ubuntu. Or would I be facing the same issue(s)?

A lot of modems are so called winmodems.. they won't function without closed source drivers or at least give you an often impossible challenge, as you've noticed.
So you can search for a modem supported in Ubuntu (can't tell you myself) or keep trying..
As I understand it you need a modem that doesn't need additional software (often made for Windows) to function, this will probably be external indeed.. Maybe USB? Search the forums for recommendations.

Another important link: [linmodems]("http://www.linmodems.org/")
A linmodem is a winmodem with support for GNU/Linux, so this site is worth a browse.
Good luck.

---

### Post by Bonanzaman on 2008-03-25
OK, just did a little research, and went on Ebay and picked up a "hardware" external modem........We'll see how that goes....they are cheap enough to try as I really want to keep Ubuntu!
Thanks for your responses!

---


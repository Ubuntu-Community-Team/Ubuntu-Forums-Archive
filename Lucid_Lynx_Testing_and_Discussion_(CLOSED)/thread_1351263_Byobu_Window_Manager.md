---
title: "Byobu Window Manager?"
date: 2009-12-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by vrkalak on 2009-12-10
[COLOR=DarkSlateBlue]I just upgraded my Xubuntu 9.10 Karmic to the new *Lucid 10.04 Alpha 1.*[/COLOR]
Got a couple of error messages, that I already sent in.

Everything seems to work OK, so far.

What's with this new **Byobu Window Manager**?

---

### Post by maheshasolkar on 2009-12-10
It looks (and works) like some sort of a 'screen' variant.

[http://en.wikipedia.org/wiki/GNU_Screen](http://en.wikipedia.org/wiki/GNU_Screen)

---

### Post by seeker5528 on 2009-12-10
[https://launchpad.net/byobu](https://launchpad.net/byobu)

[http://www.gnu.org/software/screen/](http://www.gnu.org/software/screen/)

Later, Seeker

---

### Post by duanedesign on 2009-12-11
byobu used to be called 'screen-profiles' It is Screen shipped with some default profiles that show some very helpful information. Also some additional screen-bindings designed to make screen easier to use. 

screenshot (click for full size)
[[img]http://farm3.static.flickr.com/2670/4176096052_391164b5dc_t.jpg[/img]]( http://farm3.static.flickr.com/2670/4176096052_d7a45a69ba_o.png)

Some features it offers (and you can add your own), there is:

[LIST]
[*] Screen windows list
[*] Battery status
[*] CPU count
[*] CPU frequencies
[*] Current date/time
[*] Disk space
[*] EC2 cost
[*] Fan speed
[*] hostname
[*] IP Address
[*] Load average
[*] Mail count
[*] Memory available/used
[*] Network transfer speeds
[*] Temperatures
[*] Processes running (count)
[*] Users logged-in (count)
[*] Wifi quality
[*] Updates available
[/LIST]

To install in Karmic or earlier, first add the byobu teams repository.
```
sudo add-apt-repository ppa:byobu
```

And then type:

```
sudo apt-get install byobu byobu-extras
```

to install byobu and some extra stuff for byobu.

Type "byobu" to start a new byobu session, and type F9 to get to the menu.

---

### Post by Gourgi on 2009-12-12
kirkland did wonderfull job in byobu ;)
amazing piece of software, i'm following it since the beginning and using it everyday. glad to be in the default install

---


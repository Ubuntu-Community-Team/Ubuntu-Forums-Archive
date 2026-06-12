---
title: "Firefox 3.5.3 unable to connect to Hotmail"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by grandtoubab on 2009-10-09
Hello,
When I try to connect to my Hotmail account with Firefox I get an error  :confused:
Erreur d'analyse XML : mal formé
In english something like XML analysis error: bad construction

When I use Opera browser it is ok.

Is this a known error in Firefox?

---

### Post by dinxter on 2009-10-09
you sometimes get this with an update in xulrunner, is it ok after a reboot?

---

### Post by guriinii on 2009-10-09
I think this is the problem with Facebook, try Clear Private Data. I'm not certain though.

---

### Post by grandtoubab on 2009-10-09
> **guriinii said:**
> I think this is the problem with Facebook, try Clear Private Data. I'm not certain though.

No it is the same, private or not :(

For Dinxter: it happens everytime

A funny thing ? when I use a preview of Firefox 3.7 
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk]("http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/")/

All works fine:guitar:

---

### Post by dinxter on 2009-10-09
hmm, that is strange... i can only suggest trying to reinstall a couple of things

$sudo apt-get install --reinstall firefox-3.5 xulrunner-1.9.1 xulrunner-1.9.1-gnome-support 

and restarting, its the only time i've seen this problem is with some sort of xulrunner/firefox update mismatch type thing. maybe someone else knows more

---

### Post by grandtoubab on 2009-10-09
Hello 
Done .. but not succesful
Below a screen capture of modules loaded
Thanks for your help
Anyway it is not a big problem I can use Opera as well :)

---

### Post by dinxter on 2009-10-09
i'm guessing you've still got firefox-3.0 on there? you can get rid of xulrunner-1.9 packages, 1.9.1 is the new one, having both at once may be causing some issues. if that doesnt work you could try getting rid of any firefox-3.0 related packages and see if that does it

---

### Post by grandtoubab on 2009-10-09
I remove xulrunner-1.9 but no change:confused:

If a use the add on [URL="https://addons.mozilla.org/fr/firefox/addon/59"]https://addons.mozilla.org/fr/firefox/addon/59
[/URL]and switch as I use I.E 7 it works.
So it is Bill problem after all :lolflag:

---


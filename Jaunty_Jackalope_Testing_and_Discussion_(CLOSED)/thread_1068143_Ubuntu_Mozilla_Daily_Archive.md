---
title: "Ubuntu Mozilla Daily Archive"
date: 2009-02-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by plun on 2009-02-12
Nice stuff......:popcorn:

FF3.1, 3.2, Thunderbird 3

[http://www.asoftsite.org/s9y/archives/158-Ubuntu-Mozilla-Daily-Archive-with-firefox-3.1-and-3.2-for-hardy,-intrepid-and-jaunty.html](http://www.asoftsite.org/s9y/archives/158-Ubuntu-Mozilla-Daily-Archive-with-firefox-3.1-and-3.2-for-hardy,-intrepid-and-jaunty.html)


> **Ubuntu Mozilla Daily Archive with firefox 3.1 and 3.2 for hardy, intrepid and jaunty**

Hi,

thanks to [Fabien]("http://www.launchpad.net/~fta/") we have now a daily PPA for bleeding edge mozilla packages set up and running.

A main reason to track those daily builds is to notice packaging or upstream regressions as they come. Its much easier and more efficient to fix bugs if we have a narrow regression window than debugging something whose commit we cannot easily spot.

To get things started we added firefox-3.1 (xulrunner-1.9.1) and firefox-3.2 (xulrunner-1.9.2) to our daily build bot for now; more packages will be added based on demand and time.

Fortunately, the ubuntu mozillateam uses packaging techniques having backporters in mind and hence can easily provide the same builds for all &#8220;current&#8221; ubuntu releases (meaning: hardy, intrepid, jaunty are supported for now).

If you are curious and want to track daily builds, subscribe to the &#8220;ubuntu-mozilla-daily&#8221;

PPA:   [https://launchpad.net/~ubuntu-mozilla-daily/+archive](https://launchpad.net/~ubuntu-mozilla-daily/+archive).

Feel free to spread this around and encourage advanced users and mozilla fans to track that PPA, but remember that the daily packages are auto built without much testing and hence you might end up in unexpected bugs. So, be prepared to downgrade to the previous daily when that happens.

[B]Also keep in mind that you shouldn&#8217;t file regressions of those daily packages in launchpad. Instead come to *_#ubuntu-mozillateam_* and let us know directly (alternatively send a mail to mailto:ubuntu-mozillateam@lists.ubuntu.com).
[/B]
Enjoy!


:popcorn:

---

### Post by JK3mp on 2009-02-12
Nice.

---

### Post by jfernyhough on 2009-02-12
Is there any advantage to this over having a local copy (e.g. I have FF3.2 and TB3.0 in ~/bin/) ?

---

### Post by plun on 2009-02-12
> **jfernyhough said:**
> Is there any advantage to this over having a local copy (e.g. I have FF3.2 and TB3.0 in ~/bin/) ?

Yup...  Fabien :guitar:

And easily speak to someone if a challenge occurs at IRC.
Its then better to run a Ubuntu built version.

---

### Post by plun on 2009-02-14
TB3/Shredder is for the moment broken..... will soon be fixed.

---

### Post by jfernyhough on 2009-02-14
Looks like FF3.2 is also borked. :) Giving some XUL error...

---

### Post by plun on 2009-02-14
> **jfernyhough said:**
> Looks like FF3.2 is also borked. :) Giving some XUL error...

Works just fine for me but I havent study any terminal outputs.

Its fast....:lolflag:   also running RC5.

Never used such a fast Ubuntu  :guitar:

---

### Post by jfernyhough on 2009-02-14
Bah - must be something with my profile. Created a new clean profile and it works fine. With my full profile I get the attached error (with yummy Compiz blurred transparency :D)

---

### Post by plun on 2009-02-14
> **jfernyhough said:**
> Bah - must be something with my profile. Created a new clean profile and it works fine. With my full profile I get the attached error (with yummy Compiz blurred transparency :D)

OK...well, works just fine for me.. but I am running Compiz from GIT..:oops:
No terminal-output errors.

Maybe a visit to IRC and #ubuntu-mozilla solves it...?

I asked "asac" about TB3, he probably also knows about FF3.2 or howto
deal with this error, "fta was not around and they are friendly so just ask...:)

---


---
title: "Firefox 3.0 + Firefox 2.0.0.14"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by EMCGFX on 2008-05-07
I've finally go Ubuntu 8.04 final working, everything but firefox, well kind of. I've removed default installed Firefox 3.0 and installed Firefox 2.0.0.14 manually. But now my Java/Quick/Real and other plugins does not work, only flash works :confused: Infact when I type "about:config" I see this > [screen shot]("http://i30.tinypic.com/2h4hteh.png") <

Is it possible for me to install Firefox 3 in separate directory ? So it won't over right my "/home/[username]/.mozilla/firefox". Can I use firefox2 and firefox3 profiles ? I want to use both versions because, at this point I don't like some features in 3.0 and since its beta version its not as stable.

If not, then maybe its possible to fix that plugins problem in version 2.

Any help, will be appreciated. Thank You.

---

### Post by EMCGFX on 2008-05-07
DONE! ;-) With some digging on google, I found perfect solution. Profiles is amazing!

Leave Firefox 3.0 and just install Firefox 2.0.0.14 from Synaptic. The package you need is "firefox-2"


Create separate profiles:

For Firefox 3:
firefox -ProfileManager -no-remote

For Firefox 2:
firefox-2 -ProfileManager -no-remote


Create shortcuts for different profiles:

firefox -P firefox3 -no-remote

firefox-2 -P firefox2 -no-remote

NOTE: Change firefox3 and firefox2 with your desired profiles that you created.


To create firefox file manager shortcut:

For Firefox 3:
firefox -ProfileManager -no-remote

For Firefox 2:
firefox-2 -ProfileManager -no-remote

NOTE: Profile Manager works on both versions 3 and 2 so you can use ether.


and now, I am enjoing bolf firefox 2 and 3 ;-) I use firefox 3 for media, since firefox 2 is not detecting plugins properly ;-) and firefox 2 for everyting else. Then when firefox 3 stable come out I simply delete firefox 2 and use the 3 stable =D Till then I can use bolf, whoooohoooo!

---

### Post by stinger30au on 2008-05-07
i just installed both from the repos....

did not bother with seperate directorys.... i let the o/s worry about that

everything working fine so far

---

### Post by dlridings on 2008-05-07
> **stinger30au said:**
> i just installed both from the repos....



Which repository did you find 2.0.0.14 in? I'm looking for an older version too. The 3 Beta 5 is a disappointment, to say the least.

---

### Post by EMCGFX on 2008-05-07
@stinger30au, #3: I use profiles for diferent purposes ;-) I have five profiles, and I love it. For example I use one profile to install and test add-ons and themes ;-)

@dlridings, #4: You can use synaptics to instal firefox-2.

---

### Post by kilroy0097 on 2008-05-08
I personally think it would have been nice for the upgrade install of 8.04 to give the user the option to upgrade to Firefox 3 or keep Firefox 2.0.0.14. Firefox 2 has been stable for me and all the plug-ins and add ons I had worked perfectly. Now I have to go through the process of attempting to get Firefox 2 to work again with everything. Could have been avoided entirely with a simple dialog box, "Install Firefox 3? Yes/No".

Thank goodness it didn't touch Thunderbird. That would have been even more of a headache.

---


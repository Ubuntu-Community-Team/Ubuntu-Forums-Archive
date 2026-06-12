---
title: "Wrong language in Firefox for Ubuntu"
date: 2011-02-22
forum: Installation &amp; Upgrades
---

### Post by HannuMR on 2011-02-22
After installation new Ubuntu 10.04.2 fully in finnish language, Firefox is only in english, and in preferences impossible to change the language.
Who is quilty, Mozilla or Canonical? :)
Ideas?

---

### Post by sanderd17 on 2011-02-22
do you have all updates installed? some langpacks are in the updates.

If you do, can you delete the firefox profile.
```

rm -r ~/.mozilla

```

this will delete all ff settings, so also your bookmarks and installed add-ons.

---

### Post by deconstrained on 2011-02-22
> **sanderd17 said:**
> If you do, can you delete the firefox profile.
```

rm -r ~/.mozilla

```

this will delete all ff settings, so also your bookmarks and installed add-ons.
[IMG]http://i239.photobucket.com/albums/ff76/dcstrd/facepalm.jpg[/IMG]
[http://kb.mozillazine.org/Language_packs](http://kb.mozillazine.org/Language_packs)
[https://addons.mozilla.org/en-US/firefox/language-tools/](https://addons.mozilla.org/en-US/firefox/language-tools/)

---

### Post by grahammechanical on 2011-02-22
Canonical is responsible for Ubuntu. Mozilla is responsible for Firefox. Have you tried using the Help option in Firefox? It will take you to the website. 1,475 people have the same problem. The answer apparently is to download the correct language version. If you want to use Firefox and switch between languages then you must download and install both language versions.

Canonical have chosen to include just one language version of Firefox but multiple language packs of Ubuntu with the download CD. This way we add programs according to our needs. Otherwise the Live CD would become a Live DVD and then a Live double-sided DVD and people would not be able to install because they did not have the right drive.

Your complaint is with Mozilla.

Regards

---

### Post by deconstrained on 2011-02-22
> **grahammechanical said:**
> Canonical is responsible for Ubuntu. Mozilla is responsible for Firefox. Have you tried using the Help option in Firefox? 
EXACTLY my point.

Changing Firefox and adding features are always best done through Firefox.

---

### Post by Koffeehaus on 2011-02-22
Hi I have a similar problem, but with the spell checking.

 I'm not registered in Firefox forums, so I thought I'd give it a shot here first. By default it is set to American English. I'm from the UK so it doesn't really work for me. Even after installing British English I still have US as default every time I restart the browser. Is there any way to remove the US altogether? Please help with localiZation. :D

---

### Post by wojox on 2011-02-22
Go into Tools > Add-ons and disable English.

---

### Post by Koffeehaus on 2011-02-22
Btw, usually the language of an application is 'bundled' with the system's locale. So it is actually more of an Ubuntu thing rather than Mozilla's. Try going to

System > Administration > Language Support

The system will then check for additional language support. Click to install it.


Otherwise in Language & Text menu click Install / Remove Languages. Check Finnish, also check Translations and Spellchecking.

Apply Changes, then Apply System-Wide. Restart. This should "Suomi-cise" all the applications you have on your computer.

---

### Post by deconstrained on 2011-02-22
> **Koffeehaus said:**
> Hi I have a similar problem, but with the spell checking.

 I'm not registered in Firefox forums, so I thought I'd give it a shot here first. By default it is set to American English. I'm from the UK so it doesn't really work for me. Even after installing British English I still have US as default every time I restart the browser. Is there any way to remove the US altogether? Please help with localiZation. :D
That's funny because by default I got UK English and had to install the American English dictionary for spellchecking.

Nevertheless, you should go to Mozilla for the appropriate plugin, not Canonical.

---


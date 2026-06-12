---
title: "apt-get, how do I search?"
date: 2005-05-06
forum: Installation &amp; Upgrades
---

### Post by motionsiren on 2005-05-06
Im looking for the xemacs package names, im sure apt-get has them, i just don't know where to get the appropreiate spelling. Is there a --search function for apt-get or something? It'd really be useful.

---

### Post by nemin on 2005-05-06
[QUOTE=motionsiren]Is there a --search function for apt-get or something? It'd really be useful.[/QUOTE]
apt-cache search

---

### Post by GeneralCody on 2005-05-06
If you are going to use xemacs, i conclude u are running in X.
Why do things hard when u can specify searches easy in Synaptic?

---

### Post by nemin on 2005-05-06
[QUOTE=GeneralCody]If you are going to use xemacs, i conclude u are running in X.
Why do things hard when u can specify searches easy in Synaptic?[/QUOTE]I think a lot of people, like me, prefer 'apt-cache search' because it's faster or just because they don't like GUIs :p

---

### Post by GeneralCody on 2005-05-06
[QUOTE=nemin]I think a lot of people, like me, prefer 'apt-cache search' because it's faster or just because they don't like GUIs :p[/QUOTE]

Ok. Contest of the day:
You use apt-cache and search for all packages with "backup" in the description (not the name), and I'll use synaptic. See what finishes first...

:-) , but for quick searches, I agree with apt-cache beeing faster.

Another nice thing is that with synaptic u can also mark the package the search retrieves for installation, with a click and don't have to write the packagename in another apt-get install command.

But u allready know this...

---

### Post by cutOff on 2005-05-06
Yeah, you are right. Anyway 'apt-cache show package' will show you a description of the package.

---

### Post by kvidell on 2005-05-06
[QUOTE=GeneralCody]Ok. Contest of the day:
You use apt-cache and search for all packages with "backup" in the description (not the name), and I'll use synaptic. See what finishes first...[/QUOTE]
 I've gotten clever with looking for very broad things and narrowing it down with a simpe pipe in to grep -i.
Hasn't let me down yet :) (I've found some strange things from completely arbitrary grep phrases.)
- Kev

---

### Post by az on 2005-05-06
sudo aptitude

and then do /

There are always many ways of doing things in open source software....

---

### Post by kvidell on 2005-05-06
[QUOTE=azz]sudo aptitude

and then do /

There are always many ways of doing things in open source software....[/QUOTE]
 Only thing I use aptitude for is what would otherwise be apt-get update, and only because I think it's prettier with the greens and yellows than bland terminal colourizing *coughs*
Did I mention I'm a bit off in the head?
- Kev

---


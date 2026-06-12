---
title: "defrag"
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by TheFlamingBush on 2006-10-18
Just a question, is there a Defrag for Ubuntu?.....and are cookies cleaned up, I like to keep my system cleanish, but so far i havent seemed to be able to find a programm that cleans up the system?....why is that?

When i download images and movies and programs where do they go?....do they leave an image somewhere that i can clean up when i get rid of them or want to get rid of them?

a registry cleaner?......a system cleanup utility?.....:-|

---

### Post by Jussi Kukkonen on 2006-10-18
Linux file systems generally do not need defragging, so there's no program for it as far as I know.

cookie cleaning depends on your browser, so does download direcotry. The default d/l directory is probably either your home dir (shortened ~) or the Desktop (~/Desktop/).

There is no registry on linux, the closest thing would be gconf (for gnome) but I haven't seen it get massive like registry does. System cleanups aren't really necessary either... That's the case at least if you only install stuff from repositories -- in that case synaptic or aptitude is pretty much the only thing you'll need.

---

### Post by blackgecko_au on 2006-10-18
Hi,

Try **man e2fsck**, but this is usually done automatically on boot about every 30 mounts.

---

### Post by TheFlamingBush on 2006-10-18
thanks Jussi....ive just been going through a few articles and realise now i asked a question that might have seemed a little silly.

no registry! ....wow! LOL

I do have a question though, if you go to a sight that allows you to download movies, and then you download them and watch them, ;).... are they stored on your system?.....is there anywhere specifically where i should be looking to clean up files?

I also installed a few programs from other places, other than the repositories, and wondered if i could clean them up, removing all traces of them easily?.....usually ide use a clean up utility after unistall just to wipe those disparate traces that are left around the place, but i havent found anything like that in Linux.

another quick question if you dont mind....is there anyway to hide your IP address when surfing?.....with windows firewalls you can do this as a matter of course, but i have found that my IP and thus location are available to all and sundrey when i surf with Linux.....not very good for annonymous surfing, and leaves you open a bit to others who might wish to do you harm for their own reasons.

---

### Post by wieman01 on 2006-10-18
> **TheFlamingBush said:**
> another quick question if you dont mind....is there anyway to hide your IP address when surfing?.....with windows firewalls you can do this as a matter of course, but i have found that my IP and thus location are available to all and sundrey when i surf with Linux.....not very good for annonymous surfing, and leaves you open a bit to others who might wish to do you harm for their own reasons.
The IP address is assigned to you by your service provider. If you are connected to a router, there is no way you can hide it. Not even Windows can do that UNLESS you make use of a proxy. Firewalls are no help, either. I am afraid the only solution would be a proxy, but usually you have to pay for such a server (despite the fact that I know there are 'open' proxies around).

---

### Post by Jussi Kukkonen on 2006-10-18
> **TheFlamingBush said:**
> no registry! ....wow! LOL
That's mostly a good thing, but having a gaziollion dot-files in your homefolder is not that usable either...
> I do have a question though, if you go to a sight that allows you to download movies, and then you download them and watch them, ;).... are they stored on your system?.....is there anywhere specifically where i should be looking to clean up files?
They'll be saved in one, or maybe two places. If you actually save the file it will obviously be saved in to the download directory (check the options in your browser), but also in the browsers cache like everything else the browser downloads while you surf. In Firefox you can get rid of cache and other privacy problems from *Tools-->Clear Private Data*, other browsers have something like this too.

> I also installed a few programs from other places, other than the repositories, and wondered if i could clean them up, removing all traces of them easily?.....usually ide use a clean up utility after unistall just to wipe those disparate traces that are left around the place, but i havent found anything like that in Linux.
You can't really trust those clean up utilities anyway... Who knows if they miss something? I really advice against running binary installers unless you absolutely trust the provider. .deb-packages and third party repositories are a little better, since you can (at least in theory) open up the package and check if the uninstall really works and most importantly because the package managers take care of uninstalling.
[/QUOTE]


> another quick question if you dont mind....is there anyway to hide your IP address when surfing?.....with windows firewalls you can do this as a matter of course, but i have found that my IP and thus location are available to all and sundrey when i surf with Linux.....not very good for annonymous surfing, and leaves you open a bit to others who might wish to do you harm for their own reasons.
I think you are mistaken: You can't hide your IP (without outside help)... If the web server can send you html and images it by definition must know your IP. 

The outside help I refered to is either an anonymizing proxy (you surf through the proxy, they know your ip, but others do not) or Tor (a distributed version of the same, quite slow for everyday use). Something you might also be interested in is Privoxy, a privacy enhancing proxy you can run on your own machine -- it filters cookies, ads and whatever you want.

---

### Post by TheFlamingBush on 2006-10-18
Jussi and wieman, thankyou very much for your help, it has been most informative. I shall check out a couple of those suggestions Jussi, and look for a decent proxy for those hard to trace moments! ;)

---


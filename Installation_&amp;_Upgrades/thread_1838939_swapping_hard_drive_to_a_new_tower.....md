---
title: "swapping hard drive to a new tower...."
date: 2011-09-04
forum: Installation &amp; Upgrades
---

### Post by Derringer81 on 2011-09-04
so here is where im at: 
I have spent the last several hours combing through the forums and i cant seem to find the answer that helps.......or im just doing it wrong, so the situation is:

I am running Ubuntu server 11.04 on an old dell i found (Portfolio website, so there's not much there, and very low traffic) and it died. so i took the hard drive out and put it in another tower (icky HP...but it works).

it booted up and as i figured it wasn't working right...

so now, how do i fix it? im thinking i have to use live cd (or recovery prompt or whatev) to fix it but im not sure how. i tried to use the all grub fixes i could, but that is not working right. 

so do i have to do a fresh install and re-setup all the LAMP stuff, is there a partial install trick that will work, basically is there even a way to salvage this mess without doing a fresh install?

please fell free to link other forum posts, step by step guides, call me an idiot if it helps....

---

### Post by oldfred on 2011-09-04
I believe in fresh installs. 

But most of the time Linux just works in a new system. Often it may be video related if a different video card if you are using one in a server? 

Does BIOS see drive ok? Without that nothing will work.

You can run this from liveCD to see if it is a boot related issue:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by Derringer81 on 2011-09-04
Yea the BIOS sees it, and it appears to boot OK....after a second look, there appears to be just driver issues...

(so im calling myself an id10t and looking to update the drivers.....)

---

### Post by Derringer81 on 2011-09-04
any one know how to update drivers in this scenario?

---

### Post by Hakunka-Matata on 2011-09-05
**System>Administration>Additional Drivers **or maybe **Hardware Drivers**

---

### Post by Derringer81 on 2011-09-05
all i have is a terminal (which i cannot read outside of live CD) as this is Ubuntu server.....could i do an upgrade to 11.10 beta?

---

### Post by Hakunka-Matata on 2011-09-06
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Derringer81 on 2011-09-06
...and no internet (new hardware)....

Its ok, Fresh install it is.... :neutral:

---


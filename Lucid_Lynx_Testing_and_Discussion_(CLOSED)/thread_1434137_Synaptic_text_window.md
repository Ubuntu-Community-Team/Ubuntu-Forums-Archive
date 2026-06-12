---
title: "Synaptic text window"
date: 2010-03-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by cecilpierce on 2010-03-19
Does anybody here know how to make the fonts bigger in Synaptic's "Applying Changes" window ?

---

### Post by kurros on 2010-03-19
> **cecilpierce said:**
> Does anybody here know how to make the fonts bigger in Synaptic's "Applying Changes" window ?

I dont know how to change it in the synaptic UI (without modifying the source) but you could open up a terminal window, zoom in and run

*sudo tail -f /var/log/apt/term.log*

and it will update as it runs. Kind of kludgy but I'm not sure what your goal is here.

Though if you are doing that you might as well just use apt-get from the same terminal :D

Alternatively if your video card supports Desktop Effects, you can set it to Extra (in the Apperance control panel Visual Effects tab) and zoom in the whole desktop using Windows Key + Scroll Wheel. There are other advanced uses of this scaling (specific window, etc) that you can dig into as well with compizconfig-settings-manager.

---

### Post by cecilpierce on 2010-03-21
Thanks, I guess thats what I'll have to do or get some reading glasses !

---

### Post by ssam on 2010-03-21
does system->preference->apperarance->fonts have an effect?

if not you could file a bug saying that it should.

---

### Post by ranch hand on 2010-03-21
> **ssam said:**
> does system->preference->apperarance->fonts have an effect?

if not you could file a bug saying that it should.
You need to look at the bottom of the list at the "monospace" option for things like your synaptic window.

---


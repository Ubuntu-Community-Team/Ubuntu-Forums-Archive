---
title: "Update history for 8.04?"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by buccaneere on 2008-07-18
Where is it in my machine? I need to start un-installing updates to solve page loading problems...

Thanks!

ed.:
I found this (attached). Do I just mark each one for un-installation in synaptic, until I find the problem?

Thanks again...

---

### Post by Partyboi2 on 2008-07-18
You can view installed, upgraded and removed package history in synaptic under file>history

---

### Post by kaligus on 2008-07-18
> **Partyboi2 said:**
> You can view installed, upgraded and removed package history in synaptic under file>history

Thanks that solved half of my issues without my having to ask ;)

But is there a way to make the history available in a spreadsheet or similar so one can compare several machines?

---

### Post by Partyboi2 on 2008-07-18
> **kaligus said:**
> Thanks that solved half of my issues without my having to ask ;)

But is there a way to make the history available in a spreadsheet or similar so one can compare several machines?
You could try[FONT=monospace]
[/FONT]```
dpkg --get-selections> history.txt
``````
sudo dpkg --set-selections< history.txt
``````
sudo apt-get dselect-upgrade
```*change history to what ever you want to call it.
You can then view the history in a text file.
Another one you could try is
```
sudo cat /var/log/apt/term.log > history.txt
```

---

### Post by kaligus on 2008-07-19
Thanks :) I had previously read about that trick, and it didnt make the light bulb in my light up.

Is there a way to get versions of all of those packages, that actually is what I am after.  Making sure several machines are equally updated.

My appologies for only half asking my question DOOhhhh!

---

### Post by Partyboi2 on 2008-07-19
you could try
```
dpkg -l |more
```

---

### Post by kaligus on 2008-07-19
> **Partyboi2 said:**
> you could try
```
dpkg -l |more
```
that did the trick thank you so much :)

pausing to re-read the dpkg manual to see how I missed it first time through

---


---
title: "Upgrade mostly complete, 2 &quot;broken&quot; pkgs I can't remove"
date: 2005-11-16
forum: Installation &amp; Upgrades
---

### Post by kline on 2005-11-16
I finally upgraded from 5.04 to 5.10; but synaptic reports that there are two broken packages that need to be deleted.  I chose the "Filters"  option; it popped up a
widget/dialog with the appropriate boxes check-marked.  There are only two action buttons, tho: OK and CLOSE.  Neither one gets rid of the broken packages.             It's probably time to go back to the cmd-line and fix this.

Can anybody get me past this obstacle--using whatever buttons in synaptic, or xterm and the right commands?

---

### Post by Kyral on 2005-11-16
What packages?

---

### Post by MartinG on 2005-11-16
Have you tried the synaptic menu option: Edit-> Fix broken packages?

---

### Post by kline on 2005-11-16
[QUOTE=MartinG]Have you tried the synaptic menu option: Edit-> Fix broken packages?[/QUOTE]

No, but I'll check it out, thanks.  

Synaptic reported Zero about the package names; only that there are 2 that need to
be removed before the upgrade is complete.

---

### Post by Kyral on 2005-11-16
Pop open a terminal and do this

```
sudo apt-get -f install
```

---

### Post by kline on 2005-11-16
[QUOTE=Kyral]Pop open a terminal and do this

```
sudo apt-get -f install
```[/QUOTE]

Thanks, I'll remember the -f switch the next time.  I was able to use the synaptic 
Edit -> Fix this time.  Ten or 15 minutes and a reboot, and I'm upgraded to 5.10!

Now that I've gotten thru my first Fire of Network Upgrading, I'll write a shell script to automate the process.  Thanks to everybody who's helped; this is an outstanding bunch.

gary

---

### Post by Kyral on 2005-11-16
Automate jumping to Breezy?

---


---
title: "Reinstalling Ubuntu Software Center"
date: 2012-01-12
forum: Installation &amp; Upgrades
---

### Post by rapcitynetwork on 2012-01-12
hi, i need help on reinstalling the ubuntu software center, i was unistalling the key ring acsess because i hated the password authentication and the ubuntu software center got uninstalled with me even selecting to uninstall ubuntu software center, can anyone help me reinstall it, i tried going to the dash home and selecting the software center app but nothing shows up is their a salution in fixing the problem, if yes can you tell me how?

---

### Post by saneearth on 2012-01-12
Open the terminal and type sudo apt-get install synaptic. After synaptic is install search for the ubuntu software center and install it with synaptic. I actually just started with synaptic, because I am unsure what the software center is actually called. You could try apt-get ubuntusoftwarecenter, but likely will not get anything. Synaptic in my humble opinion is much quicker, especially for installing multiple packages.

---

### Post by rapcitynetwork on 2012-01-13
> **saneearth said:**
> Open the terminal and type sudo apt-get install synaptic. After synaptic is install search for the ubuntu software center and install it with synaptic. I actually just started with synaptic, because I am unsure what the software center is actually called. You could try apt-get ubuntu software center, but likely will not get anything. Synaptic in my humble opinion is much quicker, especially for installing multiple packages. thanks but is it just safer to uninstall ubuntu and reinstall it faster then using the synaptic? or no?

---

### Post by bluexrider on 2012-01-13
In terminal:

```
sudo apt-get purge software-center
```
then
```
sudo apt-get update
```
then 
```
sudo apt-get install software-center
```
DONE

---

### Post by MG&amp;TL on 2012-01-13
> **rapcitynetwork said:**
> thanks but is it just safer to uninstall ubuntu and reinstall it faster then using the synaptic? or no?

No. definitely faster to just reinstall the software centre.

Correcting saneearth, (no disrespect, your answer was great):

```
sudo apt-get install software-center
```

will bring back your software centre. You do not need to install synaptic.

Incidentally, saneearth:

```
apt-cache search <search term>
```

does the business quite nicely. :)

---


---
title: "Depencies hell"
date: 2005-12-03
forum: Installation &amp; Upgrades
---

### Post by theD3viL on 2005-12-03
Example:


apt-get install supertux - one of depencies is supertux-data. I install it.


Then i wanna remove ALL of supertux...thats why i do this:

apt-get remove --purge supertux - its give me this: supertux* remove? I click y.

Then for sure have look if i have supertux-data still installed and do this: 

apt-get remove --purge supertux-data .. and its say: remove supertux-data* ?

Why? How can i remove all the depencies of installed program...when i wanna install supertux is depencies installed, when wanna remove it...noone ask me for depencies?!


Tnx for answers. :confused:

---

### Post by teaker1s on 2005-12-03
use synaptic and alter preferences to see recommended packages as dependencies:KS

---

### Post by theD3viL on 2005-12-13
I dont wanna see...i just wanna pernament remove depencies !:(

---

### Post by teaker1s on 2005-12-13
okay maybe I'm not making my self clear.
 if you use synaptic to install and remove programs you can set preferences to see recommended packages as dependencies.
this has the benefit of warning you when your removing something if you will uninstall or break something else if you check.

terminal
'sudo synaptic'

---


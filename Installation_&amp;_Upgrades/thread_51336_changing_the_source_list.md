---
title: "changing the source list"
date: 2005-07-23
forum: Installation &amp; Upgrades
---

### Post by chinabright on 2005-07-23
**HI I know what my source.list says and i know what i want it to say i can even get it into the nano editor and cange it to what i want but it dosent give me an option to acceptmy changes how do i cange the soure.list please**

---

### Post by DJ_Max on 2005-07-23
[QUOTE=chinabright]**HI I know what my source.list says and i know what i want it to say i can even get it into the nano editor and cange it to what i want but it dosent give me an option to acceptmy changes how do i cange the soure.list please**[/QUOTE]
 [http://ubuntuforums.org/showpost.php?p=268483&postcount=26](http://ubuntuforums.org/showpost.php?p=268483&postcount=26)

---

### Post by spanishwasabi on 2005-07-23
[QUOTE=chinabright]**HI I know what my source.list says and i know what i want it to say i can even get it into the nano editor and cange it to what i want but it dosent give me an option to acceptmy changes how do i cange the soure.list please**[/QUOTE]

Hi,

The hard way:
- Open your favorite text editor with root privileges (I use vi, very handy for manual configuration, KEdit will do though).
- Write your modifications, and save it the way you would save any other file.
- Do a
# apt-get update
# apt-get upgrade

The easy way:
System->Administration->Synaptic Package Manager
When the windows open:
Settings->Repositories
Change the settings to add/remove the repositories you whish.
Reload

And it's done.

Enjoy,

G

---


---
title: "NS2 using apt-get/software-centre ubuntu11"
date: 2012-04-04
forum: Installation &amp; Upgrades
---

### Post by mbasitrizvi on 2012-04-04
Ive been successfully able to install ns2 using apt-get. It even installed using the software centre.

But now i wnat to install a new queue. for that i need to go to ns_install_folder\queue\

the problem is that i cant find the install folder. there are some install folders but niether of them contain a queue folder.

where the *$^&$@@! did ubuntu install ns2?? where is the queue folder?

ive tried a manual install using the ns-all_in_one pkg...way too many errors and warnings pop up.... auto install via apt-get always works...

---

### Post by Paddy Landau on 2012-04-05
> **mbasitrizvi said:**
> ive tried a manual install using the ns-all_in_one pkg...
Yes, always install via the package manager (Ubuntu Software Centre, Synaptic Package Manager or apt-get) whenever possible.

Install Synaptic Package Manger if you haven't already done so. Select ns2. Select the Installed Files tab, and you will see every path and file installed. Or, if you prefer the CLI, use the command:
```
dpkg-query --listfiles ns2
```That should help you find the path.

However, I'm wondering if you shouldn't instead be using your personal queue rather than the system-wide one (I don't know ns2). If that is the case, there should be a folder in your home folder, possibly hidden. Open Nautilus to your home folder. If you don't see an ns2 folder straight away, press Ctrl-H (or menu View > Show Hidden Files) and search for [FONT=Lucida Console].ns2[/FONT] or something like that.

---


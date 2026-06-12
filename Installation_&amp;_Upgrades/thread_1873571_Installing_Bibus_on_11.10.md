---
title: "Installing Bibus on 11.10"
date: 2011-11-01
forum: Installation &amp; Upgrades
---

### Post by chmegr on 2011-11-01
Hi all! 

Pardon my ignorance, but I am a newbie (recently went all Ubuntu) and am unsure how to download bibus. 

When I try it through the software center, it gives me a, "Package dependencies cannot be resolved - This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time." Then under details, it says, "The following packages have unmet dependencies: bibus: Depends: python (>= 2.7.1-0ubuntu2) but 2.7.2-7ubuntu2 is to be installed."

First of all, what does this mean? Also, how can I install bibus?

It seems that bibus is the best at what it does for libreoffice, so I would really like that on my computer. Any help would be much appreciated.

---

### Post by jheronimus on 2011-11-10
Hi,

same problem here. You can still install Bibus from there: [http://packages.debian.org/sid/bibus](http://packages.debian.org/sid/bibus)

but unfortunately it does not work properly (problems during formatting). I am afraid we have to wait for developers to fix the bug(s)!

---

### Post by vanadium on 2011-12-02
Bug report here: [https://bugs.launchpad.net/ubuntu/+source/bibus/+bug/849174](https://bugs.launchpad.net/ubuntu/+source/bibus/+bug/849174)

Still not corrected.

---

### Post by vanadium on 2011-12-02
Formatting appears to work installing the newer version, 1.5.2.2, from SourceForge: [http://sourceforge.net/projects/bibus-biblio/](http://sourceforge.net/projects/bibus-biblio/).

---

### Post by seeker.k3 on 2011-12-28
I'm new as well, but I did sort this out. If you're still wanting to know how, here's what I did.

Open the terminal, add 2 lines to the sources list, save & close, add a key, and then install bibus and the dependencies.

Open the terminal: Alt + Ctrl + t

At the prompt, type: 

```
gksudo gedit /etc/apt/sources.list
```

Add the following lines:
## Bibus
deb [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./
deb-src [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./

Save & close.

At the prompt, type the following 3 commands, one command at a time (enter each one):

```
sudo apt-get update
```

```
wget -q http://switch.dl.sourceforge.net/sourceforge/bibus-biblio/pmartino.gpgkey -O- | sudo apt-key add -
```

```
sudo apt-get install bibus libsqliteodbc python-pysqlite2 python-wxgtk2.6 python-uno 
```

Note that you may see a long command go onto the next line, but copy the whole thing. Note that the second command ends in a hyphen. Also, the third command is installing lots of stuff, so you have to be patient.
Good luck.

---

### Post by seeker.k3 on 2011-12-28
Correction: add a key, then update, then download and install the packages.
I see the lines of code I wrote here are not quite in the right order. After adding the lines to the sources list, add the key, then update, then download and install the packages.

At the prompt, type:

```
wget -q http://switch.dl.sourceforge.net/sourceforge/bibus-biblio/pmartino.gpgkey -O- | sudo apt-key add -
```

```
sudo apt-get update
```

```
sudo apt-get install bibus libsqliteodbc python-pysqlite2 python-wxgtk2.6 python-uno
```
That should install it in 11.10.

---

### Post by Catabite on 2012-01-21
I followed Seeker's instructions, and Bibus did in fact install, but I'm not actually able to add new references, etc.  I'm new to Ubuntu, so perhaps I'm doing something wrong?  When I try to search via Pubmed, I get this error message:

Error during query.
Is your network connection working?
If required, you can set a proxy in the extended preferences.

I'd appreciate any light you could shed on what might be going wrong!

---

### Post by seeker.k3 on 2012-01-25
Hopefully, someone that actually knows about this can help out. In the meantime: Are you able to add a new reference manually? To do that, you have to select the right thing in the left panel. For example, select "All my references". Then go up to the menu bar, "References", and "New reference" should be available. It won't be available if you select "PubMed", for example, in that left panel. Hopefully you can type in your own reference info, and link to files on your computer.

Searching PubMed:
I don't think I had any problems with PubMed, but you might have to fiddle with it a bit. From the menu bar, "Edit", and then "Preferences". Check the box "Advance Preferences", bottom left. You can see about 7 tabs. PubMed is the 11th, so you have to scroll to the right to get to it. I've got the following settings:
PubMed eutils site- [http://eutils.ncbi.nlm.nih.gov/entrez/eutils](http://eutils.ncbi.nlm.nih.gov/entrez/eutils)
PubMed view site- [http://view.ncbi.nlm.nih.gov/pubmed](http://view.ncbi.nlm.nih.gov/pubmed)
Proxy settings- System parameters

You might need a proxy setting. 
When you search PubMed, you can right click on a result to go to the website.
Let us know if you make progress or not.
I'm fudging it a bit, so if anyone can add to this, it'd be good.

---


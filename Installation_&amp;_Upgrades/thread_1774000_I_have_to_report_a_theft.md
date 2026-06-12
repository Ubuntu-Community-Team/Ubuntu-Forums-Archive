---
title: "I have to report a theft"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by SteveHillier on 2011-06-02
I just upgraded from Maverick to Natty.
I could not use the gui but used apt-get upgrade.  Everything seemed to work OK, but...
Someone has stolen Firefox from my system!
Or have they.  It does not appear in the menu system but the software centre reports that it is installed.
I ran apt-get install firefox and it reported Firefox was installed but where is it?
I tried adding an item to the menu but I cannot seem to find a file that can be included into the menu.
How can I get to it to use it.
If someone can help me find the fox I would be very grateful.

---

### Post by aidenscool09 on 2011-06-02
Try typing
```
firefox
```
into a terminal.

If that works, then do
```
ln -s /user/bin/firefox /home/<username>/
```
and try adding that link to your menu.

If it doesn't work, try doing:
```
sudo nautilus /usr/lib/firefox-<version number>
```
<version number> being the version of firefox (4.0.1) in my case. In many cases it's something like 3.6.2 .

As a fallback to none of them working, do this:

```
sudo apt-get remove firefox 
sudo apt-get install firefox
```

     ~aidenscool09

---

### Post by SteveHillier on 2011-06-03
Many thanks to aidenscool09 but...
none of the above seem to work.
I have run synaptic and marked firefox for installation and then get the following message
> Package firefox has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list
Anyone got any other ideas or has the fox gone so deep into his burrow he is never coming back out?

---

### Post by bulldog on 2011-06-03
Did you have a look at your repository's?
I get the feeling there's something wrong with that.

However,you could install Ubuntu-Tweak and enable a repository which include your fox from there.

---

### Post by wojox on 2011-06-03
```
which firefox
```

```
whereis firefox
```

---

### Post by SteveHillier on 2011-06-03
Guys,
Thanks for your input.  
I have decided to cut the c..p and have installed a full clean install of Natty.
I now have a fox visible although I believe he might be related to my last fox he does have a different coat pattern.
I now have the long process of moving everything across and how I will ever keep track of everything on my 3 HDD with 4 boot options I don't know.
Anyway I will give it a day of two and then close this thread.

---


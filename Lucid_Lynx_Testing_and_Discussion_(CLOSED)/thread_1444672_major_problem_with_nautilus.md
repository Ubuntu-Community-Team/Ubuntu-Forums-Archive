---
title: "major problem with nautilus"
date: 2010-04-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by drinkleadsoup on 2010-04-01
Both of my machines, 9.1 and 10.04, have a file manager that is not responding.  Does anyone else have the same issue?

---

### Post by drinkleadsoup on 2010-04-01
this is what happens as of 6:30 pm.  I tried reinstalling nautilus.  Upon restart, I now have a purple log in screen.  once I log in, something happens, then it redirects me to the log in screen again.  I'm so confused.

I can access a root cli, but when I try to start nautilus, I get a cannot open display error or a GTK warning.

Who knows?

Any help will be taken graciously.

---

### Post by ubunterooster on 2010-04-01
get thunar 

I know, this won't fix nautilus but it is an alternative to it

---

### Post by drinkleadsoup on 2010-04-01
I did install thunar, but it also only allows for the endless loop of logging in at the purple screen.

I am afraid to install thunar on my 9.1 machine because I feel like it is what has led my 10.04 machine to the endless log in screen.  ...or something connected to it.  

Thanks for the help, and I will keep trying from my side.

---

### Post by conradin on 2010-04-01
I had a similar problem with lucid last month. What I did was reinstalled gnome from on of the other terminals. Not sure if thats the best advice, but in my case, it was what worked.

---

### Post by drinkleadsoup on 2010-04-01
I tried reinstalling gnome, but there are two conflicting packages, epiphany-browser and swfdec-mozilla, that are keeping me from installing gnome.

Thanks.

---

### Post by drinkleadsoup on 2010-04-01
UPDATE:

OK.  I have gnome reinstalled.  Now I am back to square one where the file manager is not responding.

What does we think now?

---

### Post by Johnny B on 2010-04-01
I had this problem in 9.10, not in lucid yet
check top for gvfsd-metadata
then see [http://ubuntuforums.org/showthread.php?t=1421580]("http://ubuntuforums.org/showthread.php?t=1421580")

---

### Post by drinkleadsoup on 2010-04-02
I guess that I do not have a full gnome install.  Apparently there is still a conflict between swfdec-mozilla and epiphany-extensions.

I am not finding any resources for this on the internet other than the fact that it is a known bug.  

Any help?

---

### Post by drinkleadsoup on 2010-04-02
UPDATE:

my 9.1 machine will not install gnome-desktop-environment due to the fact it depends on fast-user-switch-applet and recommends fam.

I'm still so confused.

---

### Post by NightwishFan on 2010-04-02
The gnome-desktop-environment dependency issue is a known bug. You might want to install gnome-core for a lighter Gnome environment, then work your way up. The correct package to install Ubuntu is ubuntu-desktop.

Try resetting the nautilus preferences, do this from a terminal:
```
gconftool-2 --recursive-unset /apps/nautilus/
```

Then do:
```
rm -r .nautilus
```

Log out and back in.

---

### Post by drinkleadsoup on 2010-04-02
I have tried that.  Gnome comes up with conflicting dependencies no matter what I do.  Gnome-core is installed.  I still have no file manager though.

I tried until 2:30 this morning, then I quit.  I wish I was getting paid to figure out this.

Thanks for the suggestions.

I will keep taking them.

---

### Post by NightwishFan on 2010-04-02
Run this command:
```
sudo apt-get remove gnome-desktop-environment && sudo apt-get -f install
```

That should clean up dependencies for you to install ubuntu-desktop. If you have gnome-core installed you already can build gnome up. If nautilus isnt working it is not because of dependencies. Does this happen if you use Ubuntu on a live CD?

---

### Post by drinkleadsoup on 2010-04-02
Thanks.  Still no dice.

[HTML]The following packages have unmet dependencies:
  gnome: Depends: gnome-desktop-environment (= 1:2.22.2~4ubuntu8) but it is not going to be installed
         Depends: gnome-vfs-obexftp but it is not installable
E: Broken packages[/HTML]

is the terminal output.

---

### Post by NightwishFan on 2010-04-02
Edit. I will get back to you.
Here:
[https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages](https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages)

---

### Post by drinkleadsoup on 2010-04-02
Synaptic tells me the broken dependencies are fixed.

Then, I try to install gnome through synaptic, and I get this.

[HTML]gnome:
 Depends: gnome-desktop-environment but it is not going to be installed
 Depends: gnome-vfs-obexftp  but it is not installable

[/HTML]

Thanks.

---

### Post by NightwishFan on 2010-04-02
I already stated the gnome metapackages are broken. It *is* reported, I do not see why they have not been fixed yet. :KS

You need to install **ubuntu-desktop** or just **gnome-core** and add the programs you want individually.

---

### Post by drinkleadsoup on 2010-04-02
I have both ubuntu-desktop and gnome-core installed.  Do you think it would help if I removed gnome-core and did a fresh install?  Or, do you think that would totally screw things?

Thanks.

---

### Post by NightwishFan on 2010-04-02
Fix the nautilus issue? Probably would. If Nautilus works on the live cd then a reinstall will fix it.

---

### Post by drinkleadsoup on 2010-04-06
Still no resolve with the file manager not responding.  Does anyone have an idea?

---

### Post by drinkleadsoup on 2010-04-08
So far, this has fixed it on my 9.1 machine, but there is no avail on the 10.04 machine.

boot newest kernel in recovery mode through grub,
choose root with networking,
type:
[HTML]apt-get remove nautilus[/HTML],
choose yes,
When done, type:
[HTML]apt-get install nautilus[/HTML],
When done, type:
[HTML]apt-get install ubuntu-desktop[/HTML],
and when done, type:
[HTML]reboot[/HTML].

This is working so far so good.  I just wish I knew what was up with my 10.04 machine.

---

### Post by Steve Francis on 2010-04-09
> **drinkleadsoup said:**
> Still no resolve with the file manager not responding.  Does anyone have an idea?

drinkleadsoup - sorry that you're still having problems.

I had a breakthrough with my identical problem and I left you a link in this post:
[]("http://ubuntuforums.org/showpost.php?p=9100045&postcount=12")[http://ubuntuforums.org/showpost.php?p=9100045&postcount=12](http://ubuntuforums.org/showpost.php?p=9100045&postcount=12)

Nautilus seems to be back to normal for me. Hope that you have similar success. It has been very frustrating and I lost some confidence in Ubuntu.

---

### Post by RJARRRPCGP on 2010-04-09
Based on other symptoms, if you keep having package installation failure problems, then you may have file system corruption. You should wipe the HDD, check the SMART, repartition, recreate the filesystem(s), reinstall and try again.

---


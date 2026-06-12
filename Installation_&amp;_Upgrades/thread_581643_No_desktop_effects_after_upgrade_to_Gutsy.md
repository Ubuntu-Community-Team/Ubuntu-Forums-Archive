---
title: "No desktop effects after upgrade to Gutsy"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by PaulFXH on 2007-10-19
I've just upgraded Ubuntu to Gutsy on my MacBook (C2D, 2.16 GHz).
A few things seem to be missing, in particular Desktop Effects.
So, this does not show up in the System menu. Plus, when I try to install it from Synaptic, I get this message:
> desktop-effects:

Package desktop-effects has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list


But, I have all of the repositories (universe, multiverse) checked. So, what's up with this?

---

### Post by ogcub on 2007-10-19
THere is no more desktop effects applet in Gutsy. You should use Appearance applet instead. It has desktop effects tab

---

### Post by PaulFXH on 2007-10-19
OK, thanks.
I presume you are referring to the "Visual Effects" tab.
However, if I check either "normal" or "extra", the dialog box immediately becomes grayed out and cannot be closed. Then after about maybe 30 seconds, the radio button on "none" becomes checked (without me doing anything) and the dialog box is ungrayed and the box can now be closed.
But, this still looks like I just can't get compiz-fusion to work even though the fusion-icon shows up in the Gnome-Panel.
Perhaps it is related to my graphics card (Intel integrated 945 GM). However, in Feisty, all desktop effects worked perfectly.

---

### Post by swells5 on 2007-10-19
[http://kevin.vanzonneveld.net/techblog/article/upgrade_to_ubuntu_gutsy_with_compizfusion/](http://kevin.vanzonneveld.net/techblog/article/upgrade_to_ubuntu_gutsy_with_compizfusion/)
try this link. i had compiz fusion working well in feisty but same problem as you described after upgrading. It seems it has something to do with the repositories for the compiz in feisty. Anyway, I enables the Nvidia driver as described in the link above, disabled the tuxfamily repositories that I was using in feisty for compiz install and updates. then removed compiz "sudo apt-get remove compiz*" and then followed his instructions to install compiz (basically copy/paste his lines). now compiz works fine in gutsy, when you click the system->preferences->appearance->visual affects-->preferences button , you get the compiz settings manager screen and I'm back to where I was in feisty. hope this helps

---

### Post by PaulFXH on 2007-10-19
@swells5
Thank you very much. That exactly solved my problem and now I have desktop-effects in Gutsy=D>
And I was just about to download the install CD to do a clean install of Gutsy as I assumed I had a bad install.
So, it seems that all of those third party repositories and the older version of CF were what was messing me up.
Thanks again and have a great weekend
Paul

---

### Post by Levo75 on 2007-10-20
I followed all the instructions, but i still get this message: "The Composite extension is not available"

[IMG]http://i20.tinypic.com/13z7c0g.png[/IMG]

---

### Post by PaulFXH on 2007-10-20
You should have something like this at the end of your /etc/X11/xorg.conf file
```
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

---

### Post by Levo75 on 2007-10-20
> **PaulFXH said:**
> You should have something like this at the end of your /etc/X11/xorg.conf file
```
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

When i try to save it, i get a message saying i don' t have enough permission to do so.
:( Help?

---

### Post by PaulFXH on 2007-10-20
You mean it says you don't have permission to save the /etc/X11/xorg.conf file?
If so, that because you must open your text editor as "root" which means you use sudo:

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by Levo75 on 2007-10-20
> **PaulFXH said:**
> You mean it says you don't have permission to save the /etc/X11/xorg.conf file?
If so, that because you must open your text editor as "root" which means you use sudo:

```
sudo gedit /etc/X11/xorg.conf
```

This is awesome, it's all working!

Thank you for the help!

---

### Post by DouglasAWh on 2007-10-20
I've got Compiz installed and can go through system to edit, but CTRL ALT arrow doesn't move the cube?  What could be going on?  Do I need to restart or something?

---


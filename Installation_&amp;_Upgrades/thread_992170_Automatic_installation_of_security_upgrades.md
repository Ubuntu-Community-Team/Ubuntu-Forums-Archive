---
title: "Automatic installation of security upgrades"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by kuhn on 2008-11-24
Hi,

I have seen documentation about configuring Ubuntu to automatically install security updates without prompting or notifying the user. Apparently, you could configure this via the GUI by selecting System-->Administration-->Software Sources

Then you would click on the "Internet Updates" tab, and it would allow you to configure the frequency that it checks for updates and also there was a checkbox labeled "Install security updates without confirmation". 

However, I have 8.04LTS (Hardy) installed and I don't see any "software sources" choice in the System-->Administration menu. Has it been moved? Or is there some other way to configure this now?

Ideally I'd like to know what configuration file this information is kept in so I could edit the config file directly in order to update the configurations on many boxes quickly rather than have to use the gui on each box. 

Any info on this is appreciated.

-- Scott

---

### Post by Pumalite on 2008-11-24
To edit the file:
1.-Back it up:
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
1.-Edit:
gksudo gedit /etc/apt/sources.list
Make the changes, Save, exit.

---

### Post by kuhn on 2008-11-24
Hi,

Thanks Pumalite for your response.

Is it not the case that /etc/apt/sources.list controls which repositories are used to receive upgrades? This is good, but...

What I'm trying to do is configure *how often* the system automatically checks for available updated packages and also configure whether or not security updates are installed automatically.

Thanks
Scott

---

### Post by cariboo on 2008-11-24
If you have somehow removed the System-->Administration-->Software Sources entry from the menu. Right-click on Applications and select Edit Menus, make sure the is a check mark beside Administration-->Software Sources.

You can also accomplish the same thing by going to System-->Administration-->Synaptic Package Manager-->Settings-->Repositories-->Updates.

Jim

---

### Post by decard_pain on 2008-11-24
i'm using intrepd but i think it's the same ...
go into synaptic 
then go to settings 
repositories

this is identical to the sofware sources in the admin tab

hope this helps


edit 
cariboo907 beat me to it

---

### Post by kuhn on 2008-11-24
Thanks guys -- this is interesting.  My system does not have this option. I should have mentioned, I didn't do a standard hardy installation, I hand picked a set of packages to try to create a custom install, and I bet I'm missing a package that gives those menu options.

When I run Synaptic, and click on Settings-->Repositories, there is no Updates button or tab.

And when I right-click on the Applications menu, and select "Edit Menus", then under the Administration Menu there is no selection called "Software Sources"!

Any idea what package provides that menu item? I think one way to find out would be to right-click on the "Software Sources" item, and select "properties" and it should show what the associated command is. If I knew the command I think I could use dpkg to figure out what package provides the command.

Also, as a side note, I found that there is a directory /etc/apt/apt.conf.d, and I think the files in this directory may be what gets edited to ultimately control these settings. Not sure about that just yet though.

Thanks,
Scott

---

### Post by oldos2er on 2008-11-24
Mine says "gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk"

 Hope this helps.

---


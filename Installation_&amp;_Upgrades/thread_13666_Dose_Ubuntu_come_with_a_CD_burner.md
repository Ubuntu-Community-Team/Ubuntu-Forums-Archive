---
title: "Dose Ubuntu come with a CD burner"
date: 2005-02-02
forum: Installation &amp; Upgrades
---

### Post by Eejay on 2005-02-02
Dose anyone happen to know the command to obtain then install a cd burner named K3b I want to download ISO images from the Internet then burn them on to a cd, I just now noticed that there aren't any Cd burners listed in the applications menu

---

### Post by ubuntu_fan on 2005-02-02
Much more eloquently than I could put it...

See [Ubuntu Guide - Adding extra repositories](http://www.ubuntuguide.org/#extrarepositories) to add the universe repository.

Then update your Synaptic List and you'll see k3b as an option to install.

This is also explained in [this post](http://ubuntuforums.org/showpost.php?p=52488&postcount=2)

---

### Post by hashimoto on 2005-02-02
It is quite simple to burn iso's in Ubuntu: Right click on the iso-image and select "burn to disc". If memory serves, you must have a empty disc in the burner.

BR
Hashimoto

---

### Post by Wim Sturkenboom on 2005-02-02
Stick an empty CD in and it will start the cd-writer.

To start it manually, enter the following command in Applications -> Run Application```
nautilus --no-desktop burn:
```

I've read somewhere that double-clicking an ISO file also start the cd-writer but don't know.

---

### Post by Eejay on 2005-02-02
[QUOTE=ubuntu_fan]Much more eloquently than I could put it...

See [Ubuntu Guide - Adding extra repositories](http://www.ubuntuguide.org/#extrarepositories) to add the universe repository.

Then update your Synaptic List and you'll see k3b as an option to install.

This is also explained in [this post](http://ubuntuforums.org/showpost.php?p=52488&postcount=2)[/QUOTE]

Thanks for the info
I just finished updating, however don't see KB3 on the control Panel , I ran a line in the run command then kb3 began scanning for cd devises, then after a few minutes just .. hangs 

is there a script that will place k3b in the control panel under the multimedia settings, the other method only makes an attempt to start the program, than hangs, not sure if this is some type to bug that is causing KB3 to hang. maybe this is happening because KB3 is meant for KDE...

---

### Post by Eejay on 2005-02-02
[QUOTE=Wim Sturkenboom]Stick an empty CD in and it will start the cd-writer.

To start it manually, enter the following command in Applications -> Run Application```
nautilus --no-desktop burn:
```

I've read somewhere that double-clicking an ISO file also start the cd-writer but don't know.[/QUOTE]

That method worked as well thanks for the tip

---


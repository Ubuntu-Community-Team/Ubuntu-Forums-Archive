---
title: "How do I install this game:http://sc2.sourceforge.net/downloads.php?"
date: 2005-05-03
forum: Installation &amp; Upgrades
---

### Post by Zensunni on 2005-05-03
I'm a bit confused about how to do the apt-get. Could someone walk me through this? Also, does any one know how to install winamp from this rar file:[http://www.afterdawn.com/software/audio_software/audio_players/winamp_for_linux.cfm?](http://www.afterdawn.com/software/audio_software/audio_players/winamp_for_linux.cfm?)

Thanks for any help i might receive, and sorry about the dumb questions clogging up the forums  :-# .

---

### Post by Firetech on 2005-05-03
[QUOTE=Zensunni]I'm a bit confused about how to do the apt-get. Could someone walk me through this? Also, does any one know how to install winamp from this rar file:[http://www.afterdawn.com/software/audio_software/audio_players/winamp_for_linux.cfm?](http://www.afterdawn.com/software/audio_software/audio_players/winamp_for_linux.cfm?)

Thanks for any help i might receive, and sorry about the dumb questions clogging up the forums  :-# .[/QUOTE]
 1. Download the .rpm file you linked to a known location
2. Open a terminal window and go to the known location from 1.
3. Run "fakeroot alien [filename].rpm". (If you get an error about fakeroot, run "sudo apt-get install fakeroot")
4. Run "sudo dpkg -i [filename].deb"
([filename] should be replaced by the appropriate filename... No, I have not tested this... XMMS is sufficient for me.)

If you're confused with apt-get, why don't you run synaptic? (It should be somewhere in the menu. It's a GUI to apt-get...)
To install .deb-files, you have to use "dpkg -i", though.

---

### Post by jobezone on 2005-05-03
There's a decent winamp clone in the Universe (or multiverse) repository called "xmms".

Open "Package Manager", it's in the System menu on the top. Click on the menu Edit ->Repositories . Choose "add repository", and check Universe and Multiverse . After you close the dialog, Synaptic (the name of the Package Manager) will update the available packages which you will from now on have available to you.
Click on search, type "xmms" , click on the small square on the left of the xmms package that was found, and choose Install.
Click apply, and it will be installed on your system.
To launch, press alt+F2 and type "xmms". It should be on your menu as well, but I'm not sure.

Use synaptic to look for software you want, you may have a good replacement there for the usual software you use in windows.

Still, you can allways install winamp :) It's in .rpm format, which isn't ubuntu's format for packages. You'll need to convert it to the .deb format. I guess what the previous post said is what you should do.

I sugest you have a look at [http://www.ubuntulinux.org/wiki](http://www.ubuntulinux.org/wiki) for documentation about installing specific applications, configuring and using ubuntu. You also have documentation if you click the Help icon.

---

### Post by az on 2005-05-03
Do _not_ install the rpm!

What the link on the page is saying is that it is in debian already.  You can find the game in universe.  Just enable the universe repository, update and search synaptic for uqm.  It will be in your synaptic database.

apt-get install uqm
means that is the command you would use if you were not using synaptic.

---

### Post by Firetech on 2005-05-08
[QUOTE=azz]Do _not_ install the rpm!

What the link on the page is saying is that it is in debian already.  You can find the game in universe.  Just enable the universe repository, update and search synaptic for uqm.  It will be in your synaptic database.

apt-get install uqm
means that is the command you would use if you were not using synaptic.[/QUOTE]
It's a pretty confusing thread... One question in the topic and on inside the post... The program the post question (to which I answered) is about, isn't in the repositories...

---


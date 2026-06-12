---
title: "Fiesty Fawn upgrade error"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by Stelmate on 2007-05-05
Here is my situation, my PS died in the middle of a upgrade.  I don't know which part but sometime during the night it just gave out.  I managed to get a new one in there and boot my machine and everything APPEARED normal but it kept telling me I had like 512 packages to install.  So I installed everything and now I'm missing some sorta of fonts or something. At random places I get little square brackets instead of letters.  Like in a terminal window the File Edit (etc) options are just filled in with square brackets and no letters, same thing when I right click, all the options are just square brackets.  Also I tried a 
sudo apt-get install dist-upgrade and I failed out with the following error:
Errors were encountered while processing:
 /var/cache/apt/archives/libslab0_1%3a2.18.1-0ubuntu2.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas on how to fix this?  I really don't want to wipe my system.

---

### Post by nanonomic on 2007-05-05
Umm.... yes this happened to me to, not exactly the same thing.


But what happened to me was I upgraded 

My system specs: Inter Pentium 4 3.0 ghz 512 RAM Beryl& AIGLX running

so what happened to me is I was installing the packages and it kinda froze so i shut off the computer and then i couldnt boot.  when i went into recovery mod it froze at the console font and keymap



So what i did was i put in the live cd and mounted the hard disk, burned my important files onto 2 cd's and reinstalled 6.10 and updated and upgraded and now im fine :)


can you boot?

---

### Post by mocha on 2007-05-06
Reinstall is not necessary.  Try this.

Download/Burn a Feisty Live CD

Open a terminal, and enter these commands one at a time.

```
sudo mkdir /media/drive
sudo mount /dev/<the drive with your system> /media/drive
sudo chroot /media/drive
```

From here you can fix/restart the upgrade.

```
sudo dpkg --configure -a
sudo apt-get -f install
```

I reran the above commands a few times to make sure everything that could be fixed/upgraded was.  You should also do a "sudo apt-get dist-upgrade" at least twice after the above commands are done.

Reboot (to the hard drive) and you should be able to get into the desktop, however X may refuse to start like it did for me.  I have an nVidia card, and I had to edit "/etc/x11/xorg.conf" and remove instances of "nvidia" and change them to "nv" in order to get back into the desktop. 

Once you are back in the desktop you should rerun

```
sudo dpkg --configure -a
sudo apt-get -f install
```

I believe I also did

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get dist-upgrade
```

At this point Synaptic or Adept (as well as apt) should be telling you that you are all up to date and no further packages need configuring or updating.  You can then go back into the "/etc/x11/xorg.conf" file and change the instances of "nv" back to "nvidia".  Reboot and everything should be back to normal but Feisty instead of Edgy.

I've had problems upgrading every single Ubuntu/Kubuntu version and have had to learn these tricks.

---


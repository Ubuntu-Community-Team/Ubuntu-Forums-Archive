---
title: "Virtual cd drive in ubuntu"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by tapash on 2007-06-01
Is it possible to create a virtual drive in ubuntu 7.04 just like windows does using poweriso or Nero. Please reply

---

### Post by Blender on 2007-06-01
You don't need a virtual "drive". ISOs are natively supported by the kernel itself.
Take a look at some the results of [this Google search]("http://www.google.com/search?q=linux+mount+iso&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a").

Most of these involve using the console. I don't know if there's a GUI application for this.

---

### Post by cantubus on 2007-07-29
What about mounting other image formats, like .gi?

---

### Post by Le Dé on 2007-08-10
I don't know for .gi , but you cant take a look to AcetoneISO, you can convert : .bin, .mdf, .nrg , .img , .daa , .cdi , .xbx , .b5i , .bwi , .pdi to .iso and then mount them easily. For more infos, you can check out : [http://doc.ubuntu-fr.org/acetoneiso]("http://doc.ubuntu-fr.org/acetoneiso") , I know, it's in french, but the commands are still the same. You just need to have before installing : kommander, kdebase-bin, kdelibs4c2a, konsole, konqueror, p7zip and fuseiso. For the ones like me who'd like to mount their isos.

---

### Post by pradhishkumar on 2007-09-13
iso images are natively supported ok.. but the system doesnt see it as a physial drive. example use synaptic and cick add cd option for restoring packages. it detects if ther is any physical cd rom otherwise it doesnt do anyting. is there a real software like virtual clone drive for windows which can be used almost like aphysical drive,. if anybody can help i ll greatly appreciate this

---

### Post by bulletxt on 2007-09-14
AcetoneISO2 can Mount ISO BIN NRG MDF IMG images. They are automatically mounted in a folder.
Windows works in a different way.
Are you tring to play intall a game? Just mount the image and won't have problems with cedega. just browse to the folder and select the typical "setup" or "install" file that all games have.

however keep in mind AcetoneISO2 does not do any hack to bypass protected games like Daemon Tools.

please be sure to download latest 1.0.2 version . [www.acetoneteam.org](www.acetoneteam.org)

---

### Post by mariosx on 2008-01-12
> **pradhishkumar said:**
> iso images are natively supported ok.. but the system doesnt see it as a physial drive. example use synaptic and cick add cd option for restoring packages. it detects if ther is any physical cd rom otherwise it doesnt do anyting. is there a real software like virtual clone drive for windows which can be used almost like aphysical drive,. if anybody can help i ll greatly appreciate this

there is also Gmount-iso in the add-remove programs ((K)ubuntu 7.10)

---


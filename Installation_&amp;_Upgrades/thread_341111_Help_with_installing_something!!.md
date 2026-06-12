---
title: "Help with installing something!!"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by motermouth on 2007-01-18
Hey,
   I'm currently running edgy and I have this program called porvay or something like that and I can't open it. I followed the exact instructions but when I go to click on the icon, I click and nothing happens.

   Also could you help me find a program (open source, or free) where you can design 3D art things? Or maybe even a house design program so that I could make 3D models or pictures of things for people, such as end tables? 

   One more question. I have another program and to install it all I had to do was extract the files into a folder and it ran...so to get rid of it do I just delete the files or do I need to do an uninstalltion? If I do need to unstall something....how??

Thanks so much!!
Motermouth

---

### Post by Jussi Kukkonen on 2007-01-18
> **motermouth said:**
> Hey,
   I'm currently running edgy and I have this program called porvay or something like that and I can't open it. I followed the exact instructions but when I go to click on the icon, I click and nothing happens.

Can't really help if you don't know the name of the program or link to the instructions you followed.

EDIT: you probably mean povray. You might want to read some tutorials or documentation -- when I last used povray (years ago admittedly) it was used from the command line...
> 
   Also could you help me find a program (open source, or free) where you can design 3D art things? Or maybe even a house design program so that I could make 3D models or pictures of things for people, such as end tables? 

Blender is in the repositories. It's difficult to learn, but powerful.

> 
   One more question. I have another program and to install it all I had to do was extract the files into a folder and it ran...so to get rid of it do I just delete the files or do I need to do an uninstalltion? If I do need to unstall something....how??

Just delete the files.

---

### Post by JamieC on 2007-01-18
> **motermouth said:**
> Hey,
   I'm currently running edgy and I have this program called porvay or something like that and I can't open it. I followed the exact instructions but when I go to click on the icon, I click and nothing happens.


Hm, nothing happens at all? Have you checked to see if the process is running? If not open a new terminal and type the following (replacing <application> with the name of the application or program, don't forget to quit it (CTRL + C)):
```

top | grep <application>

```

> **motermouth said:**
> 
   Also could you help me find a program (open source, or free) where you can design 3D art things? Or maybe even a house design program so that I could make 3D models or pictures of things for people, such as end tables? 


Hm, as far as 3D design goes you could try [Blender](http://www.blender.org/)?

> **motermouth said:**
> 
   One more question. I have another program and to install it all I had to do was extract the files into a folder and it ran...so to get rid of it do I just delete the files or do I need to do an uninstalltion? If I do need to unstall something....how??


What type of installer was it? An RPM? 

> **motermouth said:**
> 
Thanks so much!!
Motermouth

You're welcome.

---

### Post by mcduck on 2007-01-18
Povray ](*,)

Ok, the good apps I've found are Blender (except the not-so-intuitive user interface) and k3d (much easier to learn, probably not as powerful as Blender is. Don't be fooled by the name, it's a Gnome app :) )

---

### Post by motermouth on 2007-01-18
Thanks!!

however i dont want a very complex 3D program. I checked out some such as blender and I couldn't figure out anything. Is there any "beginner" 3D programs out there? (Open source, free)

---

### Post by mcduck on 2007-01-19
Try k3d.

Ot then there's Wings3D, but that's just a mesh modeler, not actual 3D renderer so you can only build 3D models with it and then you need to import them to some other program.

---


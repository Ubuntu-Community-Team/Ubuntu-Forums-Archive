---
title: "where does add/remove saves the .deb files"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by mesbah_1242 on 2010-03-10
i am using ubuntu 9.04 jaunty. i want to save the .deb files of the applications i have installed. now the synaptic package manager saves the .deb files to /var/cache/apt/archives . but where does the add/remove saves the the .deb files? if anyone know please reply.

---

### Post by plucky on 2010-03-10
> **mesbah_1242 said:**
> i am using ubuntu 9.04 jaunty. i want to save the .deb files of the applications i have installed. now the synaptic package manager saves the .deb files to /var/cache/apt/archives . but where does the add/remove saves the the .deb files? if anyone know please reply.

Same place.

Good Luck

---

### Post by Frogs Hair on 2010-03-10
Hi,
 
I,m sure if this is what you want , but I use Dophin File Manager and I select home on the file menu . On the tool bar under view I select show Hidden and this shows file folders for installed programs.

---

### Post by MelDJ on 2010-03-10
should be in the same place as both are fronts of apt

---

### Post by mesbah_1242 on 2010-03-11
i dont know but my add/remove does not saves .deb packages in /var/cache/apt/archives . in there i only find the .deb downloaded by synaptic. any other assumptions......

---

### Post by plucky on 2010-03-11
> **mesbah_1242 said:**
> i dont know but my add/remove does not saves .deb packages in /var/cache/apt/archives . in there i only find the .deb downloaded by synaptic. any other assumptions......

Can you give an example of what you installed using Ubuntu Software Centre and why you think it didn't save the .deb file in /var/cache/apt/archives?

---

### Post by TeDiouS on 2010-03-11
He might mean the Add/Remove, I thought the Software Center came w/ 9.10?

No clue where they are.

And in Nautilus: CTRL+H shows hidden files/folders. And is an option in the menus. Just tick the box.

I would search for the debs with a wild card on root, ***.deb ** root= **/**.
But that seems too TeDiouS. ;)

---

### Post by mesbah_1242 on 2010-03-13
> Can you give an example of what you installed using Ubuntu Software  Centre and why you think it didn't save the .deb file in  /var/cache/apt/archives? 	

i have installed LYX a front end for latex using add/remove. also have installed vlc using it.
but i don't see any texlive .deb files in my /var/cache/apt/archives directory. i save the markings of synaptic pakage managers into a text files. there are several of pakages which are installed but not saved .deb files where it should save. and i figured that the softwares installed using add/remove have missing .deb files in the /var/cache/apt/archives directory.

---


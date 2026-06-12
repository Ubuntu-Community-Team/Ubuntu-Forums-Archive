---
title: "bad file descriptor?"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by oboedad55 on 2009-09-23
I'm getting an error message when trying to install a couple of programs. One is Picasa and the other is fotoxx. The message: dpkg: "unable to read filedescriptor flags for <package status and progress file descriptor>: Bad file descriptor"

Any ideas?

---

### Post by sports fan Matt on 2009-09-23
Had the same trying to install Opera 10.  Couldnt figure out how to install though..the directions werent clear

---

### Post by oboedad55 on 2009-09-23
> **sox fan Matt said:**
> Had the same trying to install Opera 10.  Couldnt figure out how to install though..the directions werent clear

Some strange bug? Maybe it will get fixed in an update. I'm using Opera 10 as we speak. Hmmm...

---

### Post by sports fan Matt on 2009-09-23
Its possible.  Ive tried for a few days and the same result every time.

---

### Post by oboedad55 on 2009-09-23
> **sox fan Matt said:**
> Its possible.  Ive tried for a few days and the same result every time.

Have you tried version 9.64?

---

### Post by sports fan Matt on 2009-09-23
I havent tried that version..no.

---

### Post by keenish27 on 2009-09-23
I've ran into this problem with several deb packages.  Usually if you do a dpkg -i <file.deb> it works.

---

### Post by oboedad55 on 2009-09-23
> **keenish27 said:**
> I've ran into this problem with several deb packages.  Usually if you do a dpkg -i <file.deb> it works.

I saw that suggestion elsewhere but no love. Do you think it might be because these are Jaunty .debs?

---

### Post by mc4man on 2009-09-24
I believe something has broken with gdebi, synaptic still works though.

To test I had a .deb on desktop, got the same error trying to install it.

I use a local repo in ~ to add .debs i build, so after putting the .deb in my repo and updating, it installed cleanly thru synaptic.

(was worried for a sec I'd have to rebuild some packages I built earlier today

---

### Post by morryis on 2009-09-24
I get this error for a few deb-packages that worked at least until alpha 4

---

### Post by sports fan Matt on 2009-09-27
I still have the same result.  As a result, had to use evolution for email till this is fixed (ubuntuzilla wont work, needs libstdc++5)

---

### Post by mhgsys on 2009-10-10
Srry. I answered 2 the wrong thread.

---

### Post by pravin on 2009-10-13
I get the same error message while installing skype.

---

### Post by randomsearch on 2009-10-15
I can confirm this on Karmic Beta, installing packages from VirtualBox's website. dpkg from commandline works fine.

---

### Post by jasonhoekstra on 2009-10-18
Also getting same error message with VirtualBox 3.0.8 Karmic Koala package and Adobe Flash 10 package.  dpkg -i works fine.

---

### Post by jgeeting on 2009-10-19
I was able to get a .deb file to install from the command line as well.
I'm new enough I had to look up how to do it but it worked.

---


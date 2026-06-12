---
title: "Project Neon (Amarok) on Intrepid?"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Ubuntiac on 2008-10-08
Is there anyway to get Amarok 2's "project neon" (nightly updates without needing to know compiling from source) in Intrepid?

I looked around, but the only PPA's seem to just be for Hardy. It seems strange though that development PPA's wouldn't be around for the development version of (K)ubuntu... :confused:


[EDIT] Solved this. Answer is down on post #5.

---

### Post by inportb on 2008-10-08
Well, the next best thing would be amarok-kde4 in the default repositories.

---

### Post by xerosis on 2008-10-08
Just use the hardy repo it works fine. Saying that, it's currently broken for me at the moment...

---

### Post by Ubuntiac on 2008-10-08
> **xerosis said:**
> Just use the hardy repo it works fine.

Mine just complains that "Package libopenexr2ldbl has no installation candidate" as amarok-nightly depends on amarok-nightly-kdelibs which depends on it.

Is there another PPA (Hardy?) which I should have in my sources?

---

### Post by Ubuntiac on 2008-10-14
Just downloaded it from [http://packages.ubuntu.com/hardy/i386/libopenexr2ldbl/download](http://packages.ubuntu.com/hardy/i386/libopenexr2ldbl/download) and installed the deb. I have the project neon hardy lines in my sources, all dependancies seem to be satisfied and it's installing now. :popcorn:

[EDIT] Yep. It definitely worked. Neon ahoy! :D

---

### Post by gjoellee on 2008-10-14
well that works perfectly :D

---

### Post by talkingwires on 2008-10-15
> **Ubuntiac said:**
> Just downloaded it from [http://packages.ubuntu.com/hardy/i386/libopenexr2ldbl/download](http://packages.ubuntu.com/hardy/i386/libopenexr2ldbl/download) and installed the deb. I have the project neon hardy lines in my sources, all dependancies seem to be satisfied and it's installing now. :popcorn:Hey, thanks for this. I tried out Neon a few months ago, and it was pretty flaky. But, now that Amarok hit its' second beta, I wanted to give it another whirl but it was a no-go on Intrepid... until now! Thanks for the tip.

---

### Post by ykpaiha on 2008-10-15
I have added these lines on /etc/apt/sources.list
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main universe multiverse restricted
To get amarok kde4.

---


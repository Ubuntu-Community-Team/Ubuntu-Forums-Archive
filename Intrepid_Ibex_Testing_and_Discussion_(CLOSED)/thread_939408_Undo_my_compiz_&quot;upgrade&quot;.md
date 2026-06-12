---
title: "Undo my compiz &quot;upgrade&quot;"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by patrickaupperle on 2008-10-05
I am using ubuntu 8.10 and I decided to upgrade my compiz with this repo:
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) intrepid main
I know it was a bad idea. Please help me undo it. It removed a lot of features.

---

### Post by patrickaupperle on 2008-10-06
Bump Please help

---

### Post by geirha on 2008-10-06
Not sure if the apt has an easy way of doing this. If it does, I don't know about it. The procedure I would try though, is first, turn off visual effects
```
metacity --replace &
```

Then find the list for that archive by looking in /var/lib/apt/lists/. It's probably named something like ppa.launchpad.net_apt_dists_intrepid_main_binary-i386_Packages

List all packages it provides with: ```
grep '^Package: ' /var/lib/apt/lists/ppa.launchpad.net*Packages
```

Uninstall those packages, then remove the archive from sources.list, run **sudo aptitude update** and then reinstall compiz. 

The success of this process depends on the dependancies of the packages you uninstall, if any of them attempt to uninstall ubuntu-desktop or gnome or any such important packages as well, you should abort the process.

---

### Post by wgrant on 2008-10-06
If you disable the repository and apt-get update, you should find the packages under the "Installed (local or obsolete)" status filter in Synaptic. You can then force-version the needed packages back to the version in intrepid.

---

### Post by geirha on 2008-10-06
> **wgrant said:**
> If you disable the repository and apt-get update, you should find the packages under the "Installed (local or obsolete)" status filter in Synaptic. You can then force-version the needed packages back to the version in intrepid.

Ah, there was an easy way. Nice to know :)

---

### Post by patrickaupperle on 2008-10-06
> **wgrant said:**
> If you disable the repository and apt-get update, you should find the packages under the "Installed (local or obsolete)" status filter in Synaptic. You can then force-version the needed packages back to the version in intrepid.

Thank you, that should have worked. Unfortunately there were all kinds of problems. Downgrading wanted to remove all kinds of packages. Instead I am just completely re installing compiz. Why would downgrading remove more packages then removing? Ill get back to you on how well it worked.

---

### Post by patrickaupperle on 2008-10-06
Oh my gosh, compiz will not reinstall.

```
patrick@patrick-laptop:~$ sudo apt-get install compiz
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-gnome but it is not going to be installed
          Depends: libcompizconfig0 (>= 0.7.7+git20080807) but it is not going to be installed
E: Broken packages
patrick@patrick-laptop:~$ 

```
I screw everything up.:mad: I really should not be in the beta:lolflag:

---

### Post by patrickaupperle on 2008-10-06
Bump Please help me get compiz back.

---

### Post by inportb on 2008-10-06
Dude, you're bumping this topic way too often.

I would:
1) remove compiz
2) remove the repository
3) update and install compiz

---

### Post by BwackNinja on 2008-10-06
I'd say to do a "sudo apt-get clean" to get rid of all the compiz packages so they can be redownloaded as the right ones after uninstalling compiz.

---

### Post by patrickaupperle on 2008-10-06
> **inportb said:**
> Dude, you're bumping this topic way too often.

I would:
1) remove compiz
2) remove the repository
3) update and install compiz

I removed compiz and the repo. Then I tried to reinstall. The post above contains what happened. I am sorry about over-bumping, but I really like compiz.

---

### Post by inportb on 2008-10-06
Uh, did you update?

(Also, what BwackNinja said might be useful too, but I never had to use it in a similar situation.)

---

### Post by patrickaupperle on 2008-10-06
> **inportb said:**
> Uh, did you update?

(Also, what BwackNinja said might be useful too, but I never had to use it in a similar situation.)

I did not even see his post. Anyway, my problem is solved. What I did was:
1. Wanted Desktop effects really bad
2. Installed kubuntu-desktop to get kde 4 and kde effects
3. Tried to install compiz with adept (don't ask why)
4. It worked mostly, I was surprised, and suggested a termianl command (apt-get install -f, I think)
5. I ran the command and it installed compiz-gnome
6. I went back to gnome and compiz worked
7. I removed kde and most all its parts, everything I could find anyway.

Thank you all who helped. :)

---


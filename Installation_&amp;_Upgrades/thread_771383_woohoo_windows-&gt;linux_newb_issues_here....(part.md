---
title: "woohoo windows-&gt;linux newb issues here....(party, party)"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by Eplanet on 2008-04-27
i am taking xubuntu for a test run b4 studio test run. ok, so here is windows->linux newb ques.

i dl some files for music program (aldrin), it just saved to desktop. i can select the folder in Synaptic, but thats all. when i right click & try gdebi its missing dependencies. ha. well i know there should be an option to dl them if possible (python & zzlib were some, popular i know). so what steps do i need for a package manager, or whatever, to install them and their dependants?

oh, and where is the desktop cd iso for ubuntustudio? i may have to install that via wubi also, it dont show up in synaptic search.

LONG LIVE
           A N Y T H I N G

(just need something to shout about after getting linux going)

edit-also if you pick something in the package manager and it needs such and such dependant, do you need to manually enter all of them. i tried something and one would upgrade, but it said 
  Depends: python-gtk2 (>=2.12) but 2.10.4-0ubuntu3 is to be installed
 Depends: libzzub0 but it is not going to be installed
 Depends: python-zzub but it is not going to be installed

and still need to know how-to for rest of post (install d/l'ed vs repository), thx

---

### Post by Eplanet on 2008-04-28
bump, and...


i now have studio running (7.10)

i have headphones plugged in, but sound is also coming out of speakers

---

### Post by Peter09 on 2008-04-28
Are you able to install files from Synaptic? Have you enabled the repositories in the software sources application (you can use Synaptic).

Not sure where you problem lies from your description.

PC

---

### Post by Eplanet on 2008-04-28
ok,

i have added a 3rd party repository (aldrin, a music synth at sourceforge).
when i tried to install it earlier, it wouldnt automatically install dependancies (see above for "error" message). i thought that was supposed to be automatic.

and about the headphone/speaker, unless its commonplace, maybe its a driver thing? i dl the driver for audio & video card. they both say i need to be a super-user to install. maybe ubuntu can let newbie-user install next release? i cant login as root from normal screen? how do i login as root? (keep in mind, mine is a wubi install)

"allow local system administrator login" under Login Window Preferences? ill try that..

and i did manually enter dependencies and marked for install, but it didnt do anything, i dont think. what do i need to do to get it to install. wow, i am dumb, but it is also getting late. nite, hope i dont have to bump.

---

### Post by Peter09 on 2008-04-28
In Ubuntu you just add the sudo command to the beginning of a command to issue it a superuser.

You should go into synaptic->settings->repositories and select everything except the source code repositories and the CD.

Now you can go into synaptic and search for any applications within those repositories. Just tick the box, apply and the application is installed.

It is possible to add other repositories if you find applications that are third party ones which are linked to a repository, but that another story.

PC

---

### Post by Peter09 on 2008-04-28
Looking at the messages from synaptic that you posted, are you sure it did not install? While it does talk about dependencies I cannot see where it failed.

PC

Edit -> sorry can see problem on dependencies, misread post.

---


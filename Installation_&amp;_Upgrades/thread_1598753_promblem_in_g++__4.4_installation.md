---
title: "promblem in g++ _4.4 installation"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by bahador.saket on 2010-10-16
Dear all

Recently, I have installed ubuntu 10.4.
I am going to install g++_4.4 but I am facing with errors.
I have tried three types of installation so far.

when I am trying to install g++ by using [SIZE=2]ubuntu software center[/SIZE]
I am facing with following error:
[COLOR=DarkOrange] "This error could be caused by required additional software packages which are missing or not installable.   Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time."
[/COLOR]
when I am using[SIZE=2] synaptic package manager[/SIZE]

[COLOR=DarkOrange]g++-4.4:
  Depends: gcc-4.4-base (=4.4.4-14ubuntu5) but 4.4.3-4ubuntu5 is to be installed
  Depends: gcc-4.4 (=4.4.4-14ubuntu5) but 4.4.3-4ubuntu5 is to be installed
  Depends: libstdc++6-4.4-dev but it is not going to be installed[/COLOR]


And when I am going to use the following command in [SIZE=2]Terminal[/SIZE]

[COLOR=DarkOrange]sudo apt-get install build-essential[/COLOR]

I faced by following error: 
[COLOR=DarkOrange]  The following packages have unmet dependencies:
  build-essential: Depends: g++ (>= 4:4.4.3) but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
E: Broken packages[/COLOR]


[COLOR=Black]could you plz help me?

Regards,
Bahador
[/COLOR]

---

### Post by group256 on 2010-10-17
Try to install all the updates in your update manager. Then try again and report back.

Sometimes due to some dependencies and fresh install, some packages may not be available.

---


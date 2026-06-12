---
title: "Im sure this is a stupid question...ugrading warty to hoary!"
date: 2005-04-24
forum: Installation &amp; Upgrades
---

### Post by Trab on 2005-04-24
well, im currently using Warty right now, and its very stable.... but hoay seems to be working fine for everyone right? (if you dont reccomend upgrading for w/e reason, post it here too please...) im wondering if their is a way to upgrade warty to hoary without losing my stuff.... i have my home DIR on a seperate partition, and ive been able to move it easily before, but i would really like to just upgrade the core of warty to hoary without losing well anything if it can be helped....any ideas? thanks much!
-Trab

---

### Post by Gary Powers on 2005-04-24
From the Unofficial Guide .......... this is how I originally got to Hoary .........

Read General Notes
$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
$ sudo gedit /etc/apt/sources.list
Find this section
...
## Uncomment the following two lines to fetch updated software from the network
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
...
Replace with the following lines
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted
Save the edited file (sample)
$ sudo apt-get update
$ sudo apt-get dist-upgrade

Gary

---

### Post by XDevHald on 2005-04-24
I think what he mean to put was...

**sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup**
**sudo gedit /etc/apt/sources.list**

Then replace all your **warty **with **hoary **and then save your sources.list and then use your Ubuntu Update Manager to start using Hoary repositories. :)

Hope you don't mind me re-confirming your post Gary :)

---

### Post by Trab on 2005-04-24
...wont this just use hoary repositories, as opposed to hoary's core? im kinda confused.... wat the heck the unbuntu update manager.... (if its in synaptic, i think i know, but if not...?!)
thanks
-Trab

---

### Post by XDevHald on 2005-04-24
When changing the sources.list you're basically just changing repository packages, think of it as like driving a car, you have a lexus LS but you noticed that the GS has more in the package and is more equipped in the ride...also it's not glitchy and drives much smoother than the LS does, it's basically the samething, so when changing your car you have to do some financial changes, it's basically the samething with warty to hoary same Distro, just different version of product :)

---

### Post by Trab on 2005-04-24
so the only difference between warty and hoary is the repositories....? like when i DL the new gaim version, thats it....ur analogy kinda confused me....lol

---

### Post by XDevHald on 2005-04-24
hehe, sorry about that, was in a creative mood there. Let's start fresh :)

You'll be getting new versions: [b]YES

[/b]Better Security Updates: [b]Yes

[/b]Smoother loading on applications: [b]Yes

[/b]Cleaner repositories and dependencies: **Yes**

Hehe, hope that covers your question, if you have another question, I'll be sitting at the door waiting :)

---

### Post by Trab on 2005-04-24
so all i have to do is change repositories, and i have hoary...? wow if thats wat u mean, then Ubuntu is the aboslute sexiest ever! thanks Doc

---

### Post by XDevHald on 2005-04-24
lol, yes it is teh sexeh one ;) And yes all you have to do is just change **warty **to **hoary **in the sources.list and you're set, just use Ubuntu Update Manager an enjoy!

Glad to be of some services :)

---

### Post by Trab on 2005-04-24
one last thing, wat is ubuntu update manager?

---

### Post by XDevHald on 2005-04-24
It's in your Task bars: [b]System > Administration > Ubuntu Update Manager

[/b]This is a VERY useful tool for you to use to check up on repo's and view what kind you want to install, it also let's you check off the ones you don't want, say you have 182 just for example, and you have a few that you don't want, just uncheck them and it will leave those repo's out, and install the rest of them.

---

### Post by Trab on 2005-04-24
im not finding it.... is it synaptic? thats the only thing i found....i think synaptic is the updated version of Ubuntu Update Manager right? dunno...latz

---

### Post by Ufo on 2005-04-25
If I'm not mistaken, Warty did not have Ubuntu Update Manager.

I just upgraded my Warty to Hoary with Synaptic on saturday.
Changed in settings repositories from warty to hoary, did "update", "mark all upgrades" and "apply".

For me it took something like an hour. Then I rebooted computer and had hoary.
Everything has worked fine for me, but I have not been using my computer very much after upgrade.

Good luck for upgrade :-)

---

### Post by tread on 2005-04-25
The update manager is really unnecessary if you use synaptic .. it provides a simplified interface to synaptic. I don't think it does anything more, so you are safe using synaptic if you know how to.

---


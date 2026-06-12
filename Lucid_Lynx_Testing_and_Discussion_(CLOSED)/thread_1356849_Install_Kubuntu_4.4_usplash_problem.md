---
title: "Install Kubuntu 4.4 usplash problem"
date: 2009-12-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Tompalaz on 2009-12-16
Hi.
I understand that if I install kubuntu-desktop I will get KDE 4.4.

I tried install kubuntu-desktop but get following problem:
> The following packages have unmet dependencies:
  kubuntu-desktop: Depends: kubuntu-artwork-usplash but it is not going to be installed
                   Depends: usplash but it is not going to be installed
E: Broken packages
tomas@lucid:~$ 

Is there any way to install KDE without the usplash thingy?
Sure, I could compile it from source, but still....

---

### Post by caryb on 2009-12-16
Upslash is on the way out! If you install plymouth it will uninstall upsplash & fix the problem. Just a cautionary warning the new splash will have Ubuntu instead of Kubuntu but I expect this will be fixed soon.


Cary

---

### Post by Tompalaz on 2009-12-16
Thanks for your answer. 
I've already installed plymouth :( didn't fix it.Can you think of anything else that might work?  
> **caryb said:**
> Upslash is on the way out! If you install plymouth it will uninstall upsplash & fix the problem. Just a cautionary warning the new splash will have Ubuntu instead of Kubuntu but I expect this will be fixed soon.


Cary

Edit: if I use aptitude then it might work. But it wants to remove gdm, think i'll pass. 
> The following packages will be REMOVED:
  gdm{a} gdm-guest-session{a} libdrm-nouveau1{u} libplymouth2{u} 
  plymouth{a} 
The following packages are RECOMMENDED but will NOT be installed:
  network-manager-kde

---

### Post by caryb on 2009-12-16
Confused you are using Kubuntu but have gdm installed:confused:

Cary



BTW when I used aptitude it wanted to uninstall lots so I used apt-get & it was more reasonable about it!

---

### Post by Tompalaz on 2009-12-16
Nah, I'm on Gnome currently, thats why I have GDM. hmm, i could always install gdm again if i would go back to gnome. Anyways Lucid A1 is all about breakage anyhow? :P

---


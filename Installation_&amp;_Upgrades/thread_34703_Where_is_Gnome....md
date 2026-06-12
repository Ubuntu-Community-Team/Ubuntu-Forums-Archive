---
title: "Where is Gnome..."
date: 2005-05-16
forum: Installation &amp; Upgrades
---

### Post by Aiown on 2005-05-16
Hi,

I installed Ubuntu on my Dell Dimension 8400 machine. Everything went fine, except when I login I only see an empty bar on the top and one on the bottom with a single icon that supposedly hides the open windows to make the desktop visible.

I cannot do anything there, not even click or right-click, and the only way to get out is with CTRL-ALT-DELETE.

The same thing happened when I installed Kubuntu and installed Gnome over it. None of theGnome applications worked, and logging into Gnome only produced the two empty bars.

What is going on?

---

### Post by Ali_Baba on 2005-05-16
Not sure.You should check all gnome packages from Synaptic packet manager. Maybe theres missing something. Could be.

---

### Post by lao_V on 2005-05-16
or try re-installing ubuntu-desktop

---

### Post by Aiown on 2005-05-17
[QUOTE=lao_V]or try re-installing ubuntu-desktop[/QUOTE]

Can you tell me how on earth I can do it? I install Ubuntu, and the only desktop that should work, Gnome, is dead. I cannot edit the config files, cannot run apt, nothing. The only thing that is functional is the login screen.

---

### Post by lao_V on 2005-05-18
[QUOTE=Aiown]Can you tell me how on earth I can do it? I install Ubuntu, and the only desktop that should work, Gnome, is dead. I cannot edit the config files, cannot run apt, nothing. The only thing that is functional is the login screen.[/QUOTE]

Once you login, are you able to run 'sudo apt-get install ubuntu-desktop'?

---

### Post by SNo0py on 2005-05-18
Press Strg.+Alt.+1, log in and then run the commands to update your system...

---

### Post by ssam on 2005-05-18
when you get to the login screen do Crtl+Alt+F1. then login on the command line. from here you should be able to do 
sudo apt-get install ubuntu-desktop

---

### Post by BAshworth on 2005-05-18
At the login screen, check to see if Gnome is an available choice under sessions.  If it is, make sure that is the session that is being selected.

---


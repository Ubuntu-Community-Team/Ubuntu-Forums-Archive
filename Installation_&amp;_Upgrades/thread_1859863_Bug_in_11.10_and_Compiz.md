---
title: "Bug in 11.10 and Compiz"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by irv on 2011-10-14
I've install 11.10 now 5 times on a fresh hard drive with a clean install. As soon as I open the CompizConfig Settings Manager to make any changes, like the size of the icons in the Dash, the Settings Manager crashes. From this point on, the only way I can get back to a working desktop is to come in under recovery mode. As soon as I restart the system and try to start normal I do not have the dash or a good panel. And I have no idea how to fix this except re-installing everything again. 

I have a Dell Inspiron 1521 and was able to run 11.04 on down with no problems like this.

Can 11.10 run under Metafile by removing Compiz and installing it?

---

### Post by irv on 2011-10-14
Seeing I am having so many problems with Ubuntu 11.10, I am going to give kubuntu another try. It has been a few years since I tried it. I am downloading it as I write this. I will come back and let all know how it went.

---

### Post by irv on 2011-10-14
> **irv said:**
> Seeing I am having so many problems with Ubuntu 11.10, I am going to give kubuntu another try. It has been a few years since I tried it. I am downloading it as I write this. I will come back and let all know how it went.

Well, I got it downloaded and installed and loving it. It has really improved since I last tried it.
After I tried Ubuntu when 11.04 came out, I didn't like Unity. And with 11.10 keeping to Unity I think I am going to stay with Kubuntu. For the past year I have been using lubuntu with xfce and switching to gnome 3.

Well time should tell if I will stick with kde, but so far it will do. I am not having any problems with it yet.

---

### Post by thatguruguy on 2011-10-14
If you do try again, and compiz breaks on you, do the following:

If you can get back to your login, choose "Unity2d".

Open CompizConfig Settings Manager, and check the "Ubuntu Unity" plugin.  It seems that it will become unchecked if compiz crashes.  Check the box to activate it.  It will ask you to resolve some conflicts; choose to enable whatever the Unity plugin needs.

Restart the computer, and this time choose  "Unity" from the login.  The problem should be fixed.

---

### Post by irv on 2011-10-14
> **thatguruguy said:**
> If you do try again, and compiz breaks on you, do the following:

If you can get back to your login, choose "Unity2d".

Open CompizConfig Settings Manager, and check the "Ubuntu Unity" plugin.  It seems that it will become unchecked if compiz crashes.  Check the box to activate it.  It will ask you to resolve some conflicts; choose to enable whatever the Unity plugin needs.

Restart the computer, and this time choose  "Unity" from the login.  The problem should be fixed.

Thanks for the fix, I file this because I plan on loading it on another hard drive down the road. When I went to login I looked for away to load Unity2d but didn't  see it as an option on the login screen.

---

### Post by Quackers on 2011-10-14
Try gnome-shell instead :-)

---

### Post by punkybouy on 2011-10-17
Next to your login field on the login page is a "gear' or some icon.  Click it and the 2D option should be available.

---

### Post by irv on 2011-10-17
> **punkybouy said:**
> Next to your login field on the login page is a "gear' or some icon.  Click it and the 2D option should be available.

Thanks I have been thinking about installing it again. I have a 500 gig HD in my laptop and am running Win7, Kubuntu With KDE, and will load Ubuntu and run a triple boot.

or maybe I would be better off loading the Unity desktop from the Muon Package manager so I could switch between desktops from the login screen?

---

### Post by irv on 2011-10-17
OK I installed Unity desktop from the Muon Package manager so I could switch between desktops from the login screen? I am under Unity and I still can't make the Icons smaller from Compiz Manager. 

[ATTACH]204665[/ATTACH]

---

### Post by atentik on 2011-10-17
Having this problem also

---

### Post by irv on 2011-10-18
> **atentik said:**
> Having this problem also

I believe this is a bug. In fact I can't change anything from Compiz. The only thing I can think is wrong is the connection between Unity and Compiz manager is broken. They are not talking to one another.

I am back on KDE until this gets fixed. Maybe I might move on and try 12.04.

---

### Post by samjaynes on 2011-10-18
Same here - Google CCSM and 11.10, a lot of reports on this.  Mostly referring to booting as 2D and re-enabling unity plugin and resolving the conflicts.

Waiting until an official bug is resolved before I try again.

---

### Post by larrypg on 2011-10-18
might not have anything to do with it but...you might want to try a larger icon size - somewhere around 38 to 40

---


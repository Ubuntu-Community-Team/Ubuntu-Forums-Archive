---
title: "Visual express under Ubuntu"
date: 2011-06-08
forum: Installation &amp; Upgrades
---

### Post by Theadamlt on 2011-06-08
Hi all,

In would like to install Visual basic on my Ubuntu machine.
Ive tried using Wine, but i run into this error: "Unable to find volume for file extraction. Please verify that you have proper permissions." Does anyone have a solution? If not, does anyone know an alternative? 

Thank you in advance

Adam

---

### Post by Mr. Shannon on 2011-06-08
What is your reason for installing Visual Basic on your computer?  Are you trying to make programs for windows?

---

### Post by Theadamlt on 2011-06-08
Haha, actually, yes. I don't like to use windows myself, but i make programs for Windows users. A little ironic

---

### Post by Mr. Shannon on 2011-06-08
Look at **Mono**, its in the repositories.  If you do an internet search you can find some stuff about cross compiling as well.  I don't know how good it is but it would not need Wine and that might make things simpler.

---

### Post by Theadamlt on 2011-06-09
Hmm... How do i exactly do this? Cant figure it out. 

Thanks

---

### Post by Mr. Shannon on 2011-06-09
What is it you can't figure out?

---

### Post by Theadamlt on 2011-06-10
Is mono just a program that i have to install from synaptic?

---

### Post by Mr. Shannon on 2011-06-14
The IDE is **monodevelop** and the compiler for Visual Basic seems to be **mono-vbnc** and yes they are in the repositories so you can install them by any of the normal means in Ubuntu (including Synaptic).  If you use the software center there seem to be a lot of add-ons for mono so you may look through there for anything you feel is missing from **monodevelop**.

---

### Post by Theadamlt on 2011-06-16
Cool! I will check it out!

---

### Post by Theadamlt on 2011-06-20
Okay, do you know how to get the tools button so i can add the buttons like in the windows version?

---

### Post by directhex on 2011-06-21
> **Theadamlt said:**
> Okay, do you know how to get the tools button so i can add the buttons like in the windows version?

The GUI designer only works for C# apps. To design a GUI with VB.NET, you'll need to follow another route (e.g. design a GUI with Glade, and use Glade# to display it)

---


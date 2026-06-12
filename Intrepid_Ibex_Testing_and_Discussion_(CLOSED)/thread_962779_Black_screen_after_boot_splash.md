---
title: "Black screen after boot splash"
date: 2008-10-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by go7Ul1ai on 2008-10-29
Hello,

I love intrepid, the only trouble is, I've been having a problem since the Alpha 1 days. I turn on my laptop, when the Ubuntu splash screen has finished doing it's thing, the screen stays black and doesn't load into the gdm. No matter what I do, nothing will get it past that screen. I have to power cycle my laptop and try again, I will have to do this quite a few times and If I'm lucky, it will load the GDM up and I can log in.

Anyone know what's causing this and how I can fix it, I'm sure it's not doing my laptop any good.

Lee Jarratt

x

---

### Post by revoman3 on 2008-10-29
That's a strange, it never happened to me when I tried it, have you tested your laptop with another OS recently?

---

### Post by go7Ul1ai on 2008-10-29
> **revoman3 said:**
> That's a strange, it never happened to me when I tried it, have you tested your laptop with another OS recently?

Yes, I've gone to the lengths of installing Microsoft Windows Vista with Service Pack 1 and after that, installing Ubuntu 8.04.1, then back to Intrepid Ibex Release Candidate (fully upgraded). 
The problem only occurs with Intrepid.

Lee

x

---

### Post by revoman3 on 2008-10-29
That's very odd, did the live cd work?

---

### Post by go7Ul1ai on 2008-10-29
> **revoman3 said:**
> That's very odd, did the live cd work?

Aye, live CD and live USB worked.

Lee

x

---

### Post by revoman3 on 2008-10-29
Yet after you've installed it, it doesn't work. It doesn't make sense, why not post a bug report and see if it is fixed at a later date. I read through some of the bug reports and it seems like a lot of people have trouble with Intrepid on Laptops, I'm not sure why though.

---

### Post by go7Ul1ai on 2008-10-29
> **revoman3 said:**
> Yet after you've installed it, it doesn't work. It doesn't make sense, why not post a bug report and see if it is fixed at a later date. I read through some of the bug reports and it seems like a lot of people have trouble with Intrepid on Laptops, I'm not sure why though.

I might just do that, thanks for your help :)

---

### Post by jerrylamos on 2008-10-29
I've been getting the Intrepid black screen on my IBM Thinkpad since about Aug 13.  See launchpad Bug #259385.  I can get Intrepid going by doing the following:

Boot in rescue mode
select root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume

The developer comments on the Bug say there is a "blacklist" of graphics hardware that compiz will not be activated for.  Looking at the posts in this forum there are a number of different configurations which have symptoms like yours, some of whom have reported results by removing compiz.  It can be installed again from synaptic if you wish.

Jerry

---

### Post by go7Ul1ai on 2008-10-30
Thanks for the reply, turns out it isn't Compiz that is causing it. I've removed compiz using the instructions you provided, it is still happening.

Lee

---

### Post by revoman3 on 2008-10-30
They haven't exactly made Intrepid Laptop friendly have they? Your both using a laptop and you have both had this symptom. I have a PC and Compiz installed, and I don't have any problems at all.

---


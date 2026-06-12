---
title: "Keryx offline installation tool question"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by jopiping on 2010-02-16
generally a newbie asking this question.

We at the office are planning some sort of an ICT Camp for out-of-school youth and adults that would basically teach them how to utilize the computers at their community e-Learning Centers back in their areas by showing them the various projects that they could create using creative software like Avidemux, Kino and the like.

We do need to set-up the workstations with the software mentioned above.  However we are not sure if the venue would have an Internet connection, which would enable us to access the repositories and install the s/w via the Ubuntu Software Center.

One possible solution I thought about is using Keryx.  But I do have some question regarding this solution:
1.  Will the solution work?:)
2.  If it will, we probably won't know the specs of the computers that we will be using until the day of the set-up at the venue.  and we would want that we would have the keryx with the updated repositories ready by then.  If we set-up keryx using a workstation with different specs, would it be ok to use that keryx profile (or whatever it is called) to update the workstation that we would be using?

Hope someone can help me.  If my question is not clear, please do ask me for further clarification.  Thank you very much in advance.

---

### Post by mac9416 on 2010-02-17
Hey, jopiping,

Keryx ships with "default" projects for 9.10, 9.04, and 8.04. For each of those, there are both 32- and 64-bit versions. These default projects are designed to work with  Ubuntu, Kubuntu, and Xubuntu and with both 32- and 64-bit architectures.

So if you load each of the six default projects and download the software you'll need (kino, Avidemux, etc.), you will have all packages necessary to install on any 9.10, 9.04, or 8.04 machines running Ubuntu, Kubuntu, or Xubuntu.

Some machines may not fall into this category, so you may want to bring along Ubuntu 9.10 live CDs for folks to install beside their regular OSs.


I hope that makes some sense. If anything at all needs clarification, please let me know and I'll do what I can to help!

---


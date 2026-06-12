---
title: "HELP! Java+Frostwire"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by CitrusOrange on 2008-05-11
I'm lost without automatix on this new build of Ubuntu. I can't get java installed correctly to run Frostwire.

So far I've tried the add/remove software java options and the manual java.com download and both have not worked.

I need help configuring it. I've looked in the docs and they are for 7.10 so I avoided it in case of any differences.

---

### Post by Pumalite on 2008-05-11
Try:
sudo aptitude install ubuntu-restricted-extras

---

### Post by CitrusOrange on 2008-05-11
> **Pumalite said:**
> Try:
sudo aptitude install ubuntu-restricted-extras

Ok thanks but this hasn't fixed my java and frostwire issue.

---

### Post by iPirates on 2008-05-12
Yeah I've got a similar problem

---

### Post by iPirates on 2008-05-12
Ok, so I fixed my problem.

Apparently I had two versions of Java installed; a second java (JDK) was installed along with the sun version.  So i opened up synaptic and removed the sun-java6-jdk version, and typed this in the terminal:

sudo update-java-alternatives -s java-6-sun

and frostwire now works.

hope this helps

---

### Post by CitrusOrange on 2008-05-12
> **iPirates said:**
> Ok, so I fixed my problem.

Apparently I had two versions of Java installed; a second java (JDK) was installed along with the sun version.  So i opened up synaptic and removed the sun-java6-jdk version, and typed this in the terminal:

sudo update-java-alternatives -s java-6-sun

and frostwire now works.

hope this helps

Didn't work for me, however I used the config command and issued one through five and after I did that, frostwire started launching and works like normal.


sudo update-alternatives --config java

There are 5 alternatives which provide java.

I went and did all 5 of them in a row.

---


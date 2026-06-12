---
title: "Need Help Installing Alien (Help Please)"
date: 2011-09-05
forum: Installation &amp; Upgrades
---

### Post by aaron1o1 on 2011-09-05
Hi let me start of by saying Hello
First Post this is my 2nd time using a ubuntu dist on one of my laptops 
First time didnt turn out so well on my (Dell xps) because I didnt and couldnt find wifi support 

2nd time around ( Alienware M15x) worked great out of the box wifi support and everything

Now I am trying to install Alien so that I can convert rpm files

lockkstarr@ubuntu:~$ sudo apt-get install alien
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package alien

I've looked over several forums and tried different methods and decided to make an account to become a member and learn through you guys and bring this problem to the experts ;) 

Thanks guys any input would be amazing

---

### Post by Mark Phelps on 2011-09-06
Unless you've actually converted these .rpm files before and CONFIRMED that the resulting .deb files work -- you should really not be using alien.  

Convering .rpm files is a real hit-and-miss proposition.  Some files work, many do not.

IT's much better to hunt around for .deb files, or to compile from source.

---

### Post by aaron1o1 on 2011-09-06
So alien won't always be able to convert the rpm files? Wasn't aware of that I appreciate the feedback

I finally got it installed and for future refrence anyone who is having this problem I solved it by 

Going into Synaptic Package Manager - Settings - Repositories and checking the first 3 boxes
Then follow that 

Onto the update tab and I checked all four boxes

Exit the settings and click reload and viola now you're ready to 

sudo apt-get install alien

---

### Post by kr651129 on 2011-09-06
I've never had a problem with rpm to deb via alien.  Though I think this is because I've only ever used alien for library installs and tool-chains other than software.

---

### Post by aaron1o1 on 2011-09-07
I think the only reason I had a problem was because I never had my repositories enables and such /face palm

---

### Post by Mark Phelps on 2011-09-08
I have tried several such conversions -- and in each case, they failed for one reason or another.  Not saying that it won't EVER work, just saying that the result varies enormously by the individual rpm package you're trying to convert.  Alien is not a miracle cure that allows you to use .rpm files instead of .deb files.

---


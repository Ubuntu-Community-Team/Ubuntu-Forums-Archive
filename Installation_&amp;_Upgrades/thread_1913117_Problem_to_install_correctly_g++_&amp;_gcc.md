---
title: "Problem to install correctly g++ &amp; gcc"
date: 2012-01-21
forum: Installation &amp; Upgrades
---

### Post by poolet on 2012-01-21
Ok. There are thousand similar problem is google and I have read a lot of them but they didn't help me so I decided to post another one maybe I am lucky and find the solution!!!  The problem is with gcc++ libraries. I don't know why but it's **** me off.. I have already try everything.. build esential install manualy libraries... etc... I have also check the installation dev(lib) of my laptop since the eclipse working fine on my laptop and in synaptic all the packets that are installed in my laptop are install for my desktop and still the problem isn't fixed.. I can debug c++ and c# project in my laptop but not at desktop.. This is silly!! I don't know what to do.. Note: My laptop and my deskop run with the same distro and same ubuntu version, As I mention before it took me 2 hours to check and confirm that all the packets at my laptop are the same for my deskop. I have also reinstall all the packets to see if there is some luck but nothing..... The compiler isn't let ne to build the project... At the end I have try to run the project manually with terminal but seems that isn't respond... If you know any tips or any thread that explain ecxatly how to install g++ and gcc++ please inform me as soon as possible...

Please if you have any ideas let me know as soon as possible because I really really desperate!!!
Thank you in advance!!
Regards!!!!

---

### Post by dino99 on 2012-01-22
your best friends are logs :)
i suppose you have installed some extra/non genuine source(s), so might be some conflicts, again glance at warnings/errors, its the first step. And dbg & dbgsym can help you more too.
(http.//ddebs.ubuntu.com distro main restricted universe multiverse)

---

### Post by poolet on 2012-01-23
> **dino99 said:**
> your best friends are logs :)
i suppose you have installed some extra/non genuine source(s), so might be some conflicts, again glance at warnings/errors, its the first step. And dbg & dbgsym can help you more too.
(http.//ddebs.ubuntu.com distro main restricted universe multiverse)

hey dino99 thanks for your reply... :D I think you are right....logs are a good company...! :D I will try to un-install all the libraries that I have download and I will install again only the specific that eclipse and QDevelop used... If isn't helps then step by step to to see whats going on.. or a fresh clear installation of ubuntu and thats it... :P 

Thank you in advance!!!

---


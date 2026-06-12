---
title: "Ubuntu 18.04 LTS keeps freezing on me"
date: 2020-09-03
forum: Installation &amp; Upgrades
---

### Post by xigmitang-64 on 2020-09-03
I haven't used Ubuntu on my laptop for awhile.  The version of Ubuntu on that laptop has its origin from Malaysia.   When I opened my Ubuntu runned laptop, i did an upgrade.  
My question is:  is Ubuntu 18.04 LTS and Google Chrome not compatible?  What browser is?
 It seems like since I updated Ubuntu and downloaded Google Chrome, my one laptop keeps freezing every time i try to do anything.  I couldn't move the cursor on my mouse, can't close the windows, basically everything freezes.  I have since uninstalled Google chrome and went back to using my Firefox 80.0.  My system is still freezing.  
2nd question is:  how can I completely uninstall everything I have on my laptop and reinstall Ubuntu? 
3rd question is:  Is Ubuntu 18.04 LTS stable or should I upgrade to Ubuntu 20.04?
4th question:  Help.  Please explain to  me, step by step, how I can do it so my computer functions smoothly?
 
Thanks

---

### Post by yapidumoac on 2020-09-03
[Beginner's Guide: How To Install Ubuntu Linux 18.04 LTS]("https://www.forbes.com/sites/jasonevangelho/2018/08/29/beginners-guide-how-to-install-ubuntu-linux/")

---

### Post by xigmitang-64 on 2020-09-05
Thanks for responding.  I will certainly check it out.

---

### Post by guiverc on 2020-09-05
You've provided no details on your laptop.

If it's x86 or i386 in architecture, you won't be able to move to Ubuntu 20.04 LTS, as it's not supported. 

I'm not really a user of `chrome`, but I've never had issues on the occasions I've used it.

With the issues you're describing, I'd evaluate your hardware. Try booting the system & running it from *live* media (such as Ubuntu install media using "*Try Ubuntu"*) and see if you have the same issues there; if you do it's likely your hardware.

You can run ramtests, check your HDD/ssd health, but some require some hardware skill (ie. look at your motherboard looking for swollen caps, check PSU is providing enough power etc).

Yes Ubuntu 18.04 LTS is stable, as it's been in production systems longer than 20.04, it's actually more stable. It has two software stacks it can use, the GA stack being the oldest is more stable, but you have the option of using HWE (which is default is chosen by ISO used to install your system) which is now running the stack from Ubuntu 20.04 LTS.  

FYI:  I have two IBM laptops that do not like the HWE stack (from Ubuntu 20.04 LTS) when on Ubuntu 18.04 LTS. Both laptops are really old from 2003 and just don't like the 5.4 kernel ([bug has been raised]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1892011")). They are however perfectly stable on the GA stack of Ubuntu 18.04 LTS.  Your laptops hopefully aren't this old though.

---


---
title: "Toshiba laptop vs Ubuntu"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by hawkhock on 2011-02-07
Am former Ubuntu user with a new Toshiba laptop. From research, it appears that Toshiba laptops do not take kindly to Ubuntu dual booting with Windows 7. Most of the issues concern booting, audio, video or wireless. As much as I would like to dual boot I am not savvy enough to deal with all the hardware issues

Would like to install Wubi 10.10 to use for basic daily ops including Open Office, email, web surfing.  Yes, I know this is not optimum but appears to be a logical option.  

As I understand it Wubi 10.10 has NOT had any GRUB updates to date.  IS THIS STILL VALID?

IF YES, will the following steps provide some surety of a clean install on a Toshiba Satellite P500 --

1. Download Wubi and create Live CD or Live USB
2. DO I NEED TO CHANGE BIOS to boot from CD for the install?
3. Install Wubi
4. Reboot -- should have no problem at this stage with dual boot options -- YES or NO?
5. DO NOT allow any automatic updating.
6. Locate Synaptic packages and lock both the GRUB packages per the Wubi Megathread instructions.
7. DO I NEED TO change BIOS back to boot from hard drive?

Thanks in advance to anyone who answers.

G in UT

---

### Post by movieman on 2011-02-07
I have a Qosmio F60 and it basically just works with 10.04 dual-booting with Windows. I'm still not sure whether I'm going to upgrade to 10.10.

---

### Post by hawkhock on 2011-02-07
Don't mean to be dense but are you referring to Wubi or dual boot with Ubuntu 10.04?

---

### Post by itz_nsn on 2011-02-07
I am a Ubuntu beginner and i had very bad experiences with Toshiba for dual-boot ( Toshiba Satellite L305D AMD processor) laptop - major problem i had to face was that my system fan would not run and the temperature would shoot up to 47degrees F and then further and then would exceed the bios temperature and the laptop would shutdown - i dont know how it will fare for you - recently after an update in 10.10 my whole system screwed up and i lost all my data - i am trying to get some help in this forum to recover my data 

If you have enough ram, i would suggest using virtual-box rather than dual booting 

but again there are a lot of ppl successfully running dual-boots with all the precautions - ( in my case i am upset because i did nothing - only an automatic update and my entire system crashed - i did not have any mods or any weird kind of software in ubuntu that might have caused this )

---

### Post by Quackers on 2011-02-07
Toshiba seem to have acpi problems, but they seem to be solvable, in the main.

---

### Post by hawkhock on 2011-02-07
Thanks itz-nsn - I've been reading similar posts re Toshiba laptops which is why I am reluctant to try it. Didn't think about using a virtual box. Will explore that option.  My sig is wrong; I have 8g RAM and 500G hard drive so I should have plenty for virtual box. Thanks for the suggestion.

---

### Post by Old_Grey_Wolf on 2011-02-07
> **hawkhock said:**
> Toshiba Satellite P500

Check out Google for the P500.

This is one of the hits I got:  [http://www.linlap.com/wiki/toshiba+satellite+p500](http://www.linlap.com/wiki/toshiba+satellite+p500)

---

### Post by stchman on 2011-02-07
I have Ubuntu installed on my A205 Satellite laptop and all works perfectly.  I have also installed Ubuntu on an A105 as well with Atheros wireless and ATI graphics.

No problem.

---

### Post by Old_Grey_Wolf on 2011-02-07
A followup to my prevous post.

I have Ubuntu 10.04 LTS running on a Toshiba Mini Notebook. It is a 10.1 inch NB305. Ubuntu works great on it. I checked out the specs for the Notebook before I bought it to determine what network and graphics chips it used. I also did some Googling before I bought it. 

It is the only Toshiba I have. It is the only Netbook/Notebook I have. I mostly use Dell or Lenovo laptops and HP or Lenovo Desktops.

---

### Post by dummy910 on 2011-02-07
I have an **old Toshiba laptop** around the house that I run 10.10 LXDE on. It's almost laughable, but it runs almost perfectly still.:lolflag:  

[http://reviews.cnet.com/laptops/toshiba-satellite-a65-s126/4507-3121_7-30914580.html?tag=specs](http://reviews.cnet.com/laptops/toshiba-satellite-a65-s126/4507-3121_7-30914580.html?tag=specs)

A Toshiba A65-S126 Circa 2004, with 368mb of RAM (4200rpm)60gb hard drive, basically a 2004 economy laptop. Battery long gone, running DC connection and believe it or not, **LXDE Ubuntu runs just fine** on this old beast. Sure it's laggy when it comes to running the horrid flash crap, and it's not capable of gaming, but what old laptop is?

Amazing, but this old robot just keeps marching along it does. I'll run this old dog till she dies, and it will only pull an Ubuntu Sled it will... I wiped windows from it's hard drive many moons ago as **it's Linux or nothing for this old girl**.

---

### Post by hawkhock on 2011-02-07
Thanks for all your help so far. It appears from the [www.linlap.com](www.linlap.com) link that my laptop is compatible with Ubuntu 10.04 except for a headphone sound issue. Am still concerned about partioning issues as Win7 is bit different from my old XP on Dell. Still exploring virtual installation. Will mark this thread as solved for now.
G in UT

---


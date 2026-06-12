---
title: "Noobie at Ubuntu needs help :)"
date: 2007-12-26
forum: Installation &amp; Upgrades
---

### Post by Chimei on 2007-12-26
Hi guys,

As you can see this is my first post! Before migrating to Ubuntu, i thought that openSuSe was the world, until i convinced myself to try Ubuntu, and thus far it has been fantastic! I love everything about it! I do however have 1 problem, which might be trivial to ubuntu experts on this forum. The problem is, Ubuntu loads up 'randomly'. Sometimes it loads into the GUI, sometimes it doesnt. This happens even right after a clean install. I do however get some weird things pop up 'Unable to allocate resources yada yada' *right after* grub, which i think may be related to why it  sometimes doesnt boot. Im probably being abit vague about the problem, but thats the best i can describe it as. Anyway, I am very enthused about being a member of the community! Any replies are much appreciated.

Edit:
I am using Gutsy Gibbon 7.10 :)

Cheers

---

### Post by PmDematagoda on 2007-12-26
Hello and welcome to Ubuntu:).

Could you please elaborate on your problem about the GUI starting up inconsistently on Ubuntu? Also could you post the specifications of your PC?

---

### Post by Chimei on 2007-12-26
Wow, that you for the prompt reply!
When i was using SuSe, normally all the services are activated during the bootup sequence and this can be visible by pressing escape. When i use ubuntu, its just a long black screen during startup, and the only way i can figure out if it hasnt frozen is by looking at my harddrive light on the laptop. My computer randomly does not get to the login screen. Although on a few occasions, it took almost 5 minutes to load up. As for my computer specs, im using a Compaq B1900 laptop. Specifications can be found here: [http://www.cnet.com.au/laptops/laptops/0,239035653,339272817,00.htm](http://www.cnet.com.au/laptops/laptops/0,239035653,339272817,00.htm)

Once again thanks again for the prompt reply

---

### Post by PmDematagoda on 2007-12-26
Did you install the drivers for your ATi card?

---

### Post by Chimei on 2007-12-26
Yup, i intalled the ATI driver under the restricted driver section. Do you think my graphics driver is causing the problem?

---

### Post by Casual Fan on 2007-12-26
I had a somewhat similar problem when I was running Gutsy--it took a long time to boot. You can search and find many threads on this problem on the forum. You can also go to Applications>Add/Remove and install Startup Manager, and click the box to display the splash screen during boot. That gets rid of the black sceen, and for some reason, really speeds up the boot time. With your system, you should be booting up in well under a minute.

Hope that helps...:)

---

### Post by Chimei on 2007-12-26
Thanks for the reply Casual Fan
Ill give it a go and let you know how it goes :)

Cheers

---

### Post by Chimei on 2007-12-28
Thanks everyone for your support

I have managed to solve the problem by disabling quiet mode in the boot section of grub.

^^;

---


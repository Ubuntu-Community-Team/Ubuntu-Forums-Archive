---
title: "Nvidia big problem (sort of newb)"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by Aflack on 2008-11-06
i just went through a whole buncha stuff loggin into ubuntu on amd 64bit quad core... now i installed my graphic drivers for my GeForce 8300 and 9300. rebooted and it brought my to log into my account with black background and white text... cant remember the error. if you really need it i cant try to get it in a minute. any suggestions?

---

### Post by Aflack on 2008-11-07
no one knows?

---

### Post by Tiny Grasshopper on 2008-11-07
I also have a [similar problem]("http://ubuntuforums.org/showthread.php?t=966466")

---

### Post by Aflack on 2008-11-07
anyone lol?

---

### Post by Aflack on 2008-11-07
im the only person having problems with nvidia? on amd 64bit?

---

### Post by Aflack on 2008-11-07
this is a joke right? o.o

---

### Post by Aflack on 2008-11-08
i dont mean to spam but seriously... anyone??

---

### Post by hyperdude111 on 2008-11-08
your x-server is broken (i think)

You need to log into failsafe terminal and type
"sudo auto-remove ubuntu-desktop"
then type
"Sudo apt-get install ubuntu-desktop"

Be warned this can go wrong, it is safer to save your doccuments with a live cd the re-install ubuntu

Good Luck

---

### Post by Aflack on 2008-11-08
i dont have any docs, so ill just try that. this happens every time i try to install drivers though.

---

### Post by Tiny Grasshopper on 2008-11-08
I notice that you and I both have two graphics card presumably with the intention of running sli. The reply in [my bug]("https://bugs.launchpad.net/bugs/295160") suggested trying the install with one graphics card. I'm going to do that later. Perhaps you could try that.

update: I took out one of the graphics cards and it worked on an existing ubuntu install. reinstalling with kubuntu 32-bit to see if that works as well. I figure it will.

---

### Post by Aflack on 2008-11-08
i might. i tried it once but then i accidentally installed the second one but i didnt think much of it. ill try it later. chattin with friends now.

---

### Post by Aflack on 2008-11-08
yeah i tried one graphic card and still got an error and it brings me to login to ubuntu login.

---

### Post by Tiny Grasshopper on 2008-11-09
I should mention that when i took out one of the graphics card, it gave trouble in booting. So I swapped it out with the other one and then it worked.

Also I re-enabled the drivers after switching to just the one card

---

### Post by Aflack on 2008-11-09
i just tried to install one graphic card driver in ubuntu lol i dont have other cards to  switch out and in

---

### Post by Aflack on 2008-11-23
Help is good.

---

### Post by Aflack on 2008-11-23
guys please help i cannot do anything graphic related in ubuntu   no compiz or anything no games nothing, please help me enable my graphic cards

---

### Post by Treelova on 2008-11-24
Hi there,
I've made a post on that specific problem under this thread [http://ubuntuforums.org/showthread.php?t=991131]("http://ubuntuforums.org/showthread.php?t=991131") its to do with the configuration of your xorg.conf file you need to specify where your graphic card is siting. 

Hope this helps:KS

---

### Post by Aflack on 2008-11-24
im confused, how do i edit the file and do i have to reinstall ubuntu or can i just do it from the terminal i get?

---


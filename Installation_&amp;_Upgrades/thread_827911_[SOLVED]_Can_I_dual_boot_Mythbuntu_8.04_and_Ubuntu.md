---
title: "[SOLVED] Can I dual boot Mythbuntu 8.04 and Ubuntu 8.04"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by bmwman on 2008-06-13
Can I dual boot Mythbuntu 8.04 and Ubuntu 8.04? Long story short, I spent days trying to set up MythTV on my Ubuntu machine. Finally I got pissed and wiped the whole OS and installed Mythbuntu. It does come preconfigured so that solved that problem.Mythbuntu is just set as an appliance and can be upgraded to regular workstation which I did. Now my problems is the Mythbuntu doesn't use Gnome (i think it's xfce but not sure)and everything is totally different. I do want to have my regular Ubuntu gnome environment and i'm not sure If I can set up everything manually the it should be in Ubuntu. I was just thinking to install a whole new Ubuntu OS since I have enough space on the HDD.

Any recommendations?

---

### Post by Pumalite on 2008-06-13
Just go aheah and install it in the free space. Let Grub install to MBR. You'll have a new Grub and dual boot.(go 'Manual')

---

### Post by bmwman on 2008-06-13
But is it gonna let me select which one to boot into like windows bootloader does? Normally I can see only the kernel version. I can certainly try it tonight. And I assume that I can use the same SWAP partition and don't need to create a second one, correct?

---

### Post by Pumalite on 2008-06-13
You can ignore /swap. Just pick '/' and /home. (New home for the new OS)

---

### Post by doorman on 2008-06-13
Can't you just install gnome in mythubuntu and then choose it as your default login session? And if mythTV works just in xfce, log out and log in to a xfce session...

---

### Post by milton1 on 2008-06-13
you could also try adding the gnome desktop environment to your existing mythbuntu install
```
sudo apt-get install ubuntu-desktop
```

---

### Post by bmwman on 2008-06-13
Cool, I'll try that later. 
Any way to install Gnome and remove the XFCE in Mythbutnu? 
Ultimatelly I would like to have only one system, but until I figure it out I can use dual boot.

Thanks for the fast response.

---

### Post by bmwman on 2008-06-13
> **doorman said:**
> Can't you just install gnome in mythubuntu and then choose it as your default login session? And if mythTV works just in xfce, log out and log in to a xfce session...

Your response was faster than I'm typing. Ultimately that's what I want. How to install the Gnome tho? I picked option to upgrade from Mythbuntu and it downloaded 470 packages and seems like most of the regular stuff is in there. Maybe even Gnome is installed but how can I select it as default environment and not go to XFCE? And I assume that MythTV stuff  should work fine with Gnome.

---

### Post by milton1 on 2008-06-13
The code in my previous post will install gnome. Once it is done, there should be a menu in the login screen that allows you to pick your session type; you would choose gnome there.

---

### Post by bmwman on 2008-06-13
> **milton1 said:**
> The code in my previous post will install gnome. Once it is done, there should be a menu in the login screen that allows you to pick your session type; you would choose gnome there.

OK, will do that. The current setup is logging automatically tho(which I hate anyway) and I don't have any options to choose. Hope after installing it I can choose.

---

### Post by bmwman on 2008-06-13
> **milton1 said:**
> you could also try adding the gnome desktop environment to your existing mythbuntu install
```
sudo apt-get install ubuntu-desktop
```

 sudo apt-get install ubuntu-desktop
[sudo] password for bmw-man: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I already have it but how do I can remove the xfce and log into gnome? I can't find any settings and I don't have options when I log in since it logs in automatically.

---

### Post by bmwman on 2008-06-13
I figured it out. GREAT :)

Now I have a fully working MythTV and Gnome.

---


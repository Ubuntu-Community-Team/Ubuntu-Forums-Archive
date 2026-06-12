---
title: "I have a question about ubuntu."
date: 2013-03-23
forum: Installation &amp; Upgrades
---

### Post by Estrobeda on 2013-03-23
I like ubuntu's style.
I like that it is easy to make preferences and so but i don't like the installation in ubuntu.

Everything in ubuntu is easy but the installations, many programs do you have to install with the terminal and when i search how to do stuff in the os
many results is to get used to the terminal becouse you will need it so much.

My question is will ubuntu solve installation issues like package not found, and error's when installing? 
I like ubuntu but i can't use ubuntu as much as windows becouse i can't install things that you should be able to even in linux.
An example is wine i have tried to install wine and i actualy succeded once but then windows crached and i had to reformat the computer and 
becouse i had ubuntu running along side windows ubuntu also was removed.
Since then i have tried to install wine but every try i make results in error and it isent the only program with that issue.
Will Ubuntu fix this kind of problems? becouse all about ubuntu is great if you dont count the terminal and installing issues.
Note that i havent used linux before but since i first used ubuntu i liked it alot but it has so many limitations if you arent familliar with the terminal,
will ubuntu be easier to use for people like me?
I hope that ubuntu will be easier becouse i kinda hate windows other than gaming but i have no other choice when i cant install things i need.

If this will be solved is there a date when it will?

---

### Post by oldos2er on 2013-03-23
> **Estrobeda said:**
> My question is will ubuntu solve installation issues like package not found, and error's when installing? 

These problems could be caused by a misconfigured package manager, not using the correct repositories, or something similar. If you can copy and paste the errors here, or post screenshots (whichever is easier for you) I'm sure we could get your problems straightened out.

---

### Post by ibjsb4 on 2013-03-23
Will Your problem be fixed by Ubuntu?  No, not likely, since not everyone is having your problem.

My first question would be; did you update after you installed ubuntu?  Updating is required before you can install programs.

---

### Post by Bashing-om on 2013-03-23
Estrobeda; Hi ! Welcome to the forum/

I will relate my experience for your instruction:
I have installed ubuntu countless times from as far back as version 8.04; On any number of machines for several people. I have never had the problems as you describe.

edit ! Verify system requirements for the chosen distribution !
a) Download the .iso and check the md5sum
b) Burn the .iso image as an "image" to disk at a slow write speed
c) Set in bios the boot priority, boot the disk and verify the disk integrity
d) Be aware of how you want to install ubuntu and choose the proper install selection
e) Follow the install wizard's prompts
DONE, no problems ->
Now. once installed, do all the updates from the standard repositories and avoid any outside sources install of any other packages.
Learn to use ubuntu's package managers to become aware of what packages are available and have a really good reason to deviate from ubuntu's repositories; always try the open source alternatives first.[INDENT=2]
that is the best of my advise for a good experience

[/INDENT]

---

### Post by Estrobeda on 2013-03-23
Ok thanks everyone i think it might be the update problem i will try to reinstall and update and test again if it doesent work i will post the errors.

---

### Post by Bashing-om on 2013-03-23
Estrobeda;

An edit to my prior post; verify the system requirements for  the chosen distribution. Insufficient ram can be a drastic hindrance !
[INDENT=3]
ubuntu, my operating system of choice

[/INDENT]

---

### Post by Estrobeda on 2013-03-30
I solved the problem, i had installed ubuntu with wubi and then uninstalled it but i think that when i tried to reinstall it there was somekind of error becouse when i reformated to computer the installation was correct and now ubuntu works perfectly. I wont uninstall it again.
And i tried to install ubunu to a new partition by burning the installation to cd but when you choose the partition you have to first choose what type like *_[COLOR=#ff0000]nfts[/COLOR]_* etc then the [COLOR=#ff0000]**_direction point_**[/COLOR] or maby it was [COLOR=#ff0000]**_move point_**[/COLOR] wich i had no idea what it was. So i tried the option install alongside windows but in the end the same problem with the *_[COLOR=#ff0000]"pointer"[/COLOR]_* so i used wubi. My question is were to find what choose i should make or what does this pointer and type mean? I want to know that becouse the wubi installation has a size limit max 30gb if im not wrong and i want atleast 65gb.

---

### Post by Thee on 2013-03-30
Try this, it will tell you all the necessary steps to install Ubuntu alongside with Windows:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by oldos2er on 2013-03-30
Thee posted a good link for you to follow up.

Just a couple things; the term you're looking for is *mount point.* The root partition is mounted at "/" for example. Also if you install Ubuntu to its own partition rather than using Wubi, you'll need to choose to format it as ext4 or some other Linux-native file system.

---

### Post by tgalati4 on 2013-03-30
Ubuntu will never get easier to install.  It's easy to drive a car, but have you ever swapped an engine?  Computers come with operating systems installed.  Very few come with Ubuntu already installed.  That may change in the future as linux pushes 3% of the desktop market.

---

### Post by Estrobeda on 2013-03-31
ok thanks again for the replies

---


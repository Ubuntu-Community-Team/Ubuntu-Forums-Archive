---
title: "Dependency is not satisfiable when try to install.deb"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by beatt on 2010-03-06
hi

if i try whatewer .deb file to install on ubuntu 8, or on ubuntu studio 9, i got this message- depedency is not...

example i try puredata to load it on ubuntu 8,  i got the message above...

please to help me
b

---

### Post by MelDJ on 2010-03-06
did you install the correct .deb for your version of ubuntu?

---

### Post by akand074 on 2010-03-06
> **MelDJ said:**
> did you install the correct .deb for your version of ubuntu?

Yeah, make sure its x86 if your using 32bit or x86_64 if your using a 64bit version of Ubuntu, because otherwise I believe ubuntu will automatically install the dependencies for you. If it states what the dependencies are you can go and install them manually through Synaptic or apt-get in the terminal.

---

### Post by beatt on 2010-03-06
where can i check that 32 bit or 64 ?

---

### Post by MelDJ on 2010-03-06
in terminal  type:
uname -a

---

### Post by sisco311 on 2010-03-06
Exactly how did you try to install the package?

Did you use the package manager or did you download the .deb file from somewhere?

puredata is in the universe repositories. Is the repo enabled (System -> Administration -> Software Sources)?

---

### Post by beatt on 2010-03-06
i 686 gnu/linux . what this mean ? this is a 64 bit sys, right?

---

### Post by MelDJ on 2010-03-06
> **beatt said:**
> i 686 gnu/linux . what this mean ? this is a 64 bit sys, right?

its 32 bit

---

### Post by beatt on 2010-03-06
then the 386 .deb not installable to i 686 ?

how can i solve the depedency -problem ?

---

### Post by MelDJ on 2010-03-06
i386 and i686 are 32 bit.
so installing i386 programs in i686 should be okay.
it would be easier if you show us where you got the package

---

### Post by sisco311 on 2010-03-06
So, why don't you want to install it from the repos?

```
sudo software-properties-gtk -e universe
sudo apt-get update
sudo apt-get install puredata
```

---

### Post by beatt on 2010-03-06
i tryed i386 deb in 686 system...i dont know what is the problem. with deb manager is tryed, and with terminal too. i have not yet acess to the wireless, because i dont know to add applications from console...

i have downloaded from another comp the deb files, then i pasted to my ubuntu, and tryed to install like i read how to...

what you recommend?

---

### Post by MelDJ on 2010-03-06
i presume you downloaded it from : [http://puredata.info/downloads](http://puredata.info/downloads) ?

you can try finding the dependencies from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)  

but it will be easier if you configure you wireless and use the way sisco311 showed

---

### Post by akand074 on 2010-03-06
Yes do exactly what sisco311 said, go to your main menu > Accessories > Terminal and then copy paste each line one by one into the terminal and it will be fully installed.

---

### Post by beatt on 2010-03-06
many thanks, i will try.

this mean that always must to select the newest or compatibile versions for the actual ubuntu system, if not ,then be problems with install?

the depedency problems is because the version differences?

i dont know how to set up the wireless( airlive usb)...i try all the variations but it dont go...

ubuntu see the signal and the provider too, but i dont know to connect.

---

### Post by MelDJ on 2010-03-06
the dependency problems happen because the program needs other packages so that it can be run.

make a new thread about you wireless problem here: [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336) and i am sure someone will help you out. 

good luck

---

### Post by beatt on 2010-03-07
Can you recommend some lectures abot this depedency-compatibility, packets, i386-686, etc ?

Because I tryed in 686 the 686deb  packages, and 386 deb packages too, and always got error messages.

Depedency messages , and cant install messages....

I tryed with sudo apt commands too, and I got the same messages....

I want to know how can I isntall packeges, files without internet...Because I download it on Xp, then I paste to ubuntu.

---

### Post by MelDJ on 2010-03-07
> **beatt said:**
> 
I want to know how can I isntall packeges, files without internet...Because I download it on Xp, then I paste to ubuntu.


you might want to see: [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

---


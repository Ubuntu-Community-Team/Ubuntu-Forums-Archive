---
title: "How to install ubuntu without GUI"
date: 2005-02-24
forum: Installation &amp; Upgrades
---

### Post by isaac on 2005-02-24
HI,

  i'm new to ubuntu and i have problem installing ubuntu without a gui. Can i know how to install ubuntu without a gnome/gui? just runing the minimun requirement for linux?

thanks in advance.

---

### Post by bored2k on 2005-02-24
[QUOTE=isaac]HI,

  i'm new to ubuntu and i have problem installing ubuntu without a gui. Can i know how to install ubuntu without a gnome/gui? just runing the minimun requirement for linux?

thanks in advance.[/QUOTE]



ur a n00b and u dont want gui ? c'est bizarre !!!

anyway, boot up ur ubuntu install disk , type expert and press enter, this will give u control on things, allowing u to select minimal install "for servers that need only the minimum"

when u boot, press F1 and then F2, etc, this will tell u in greater detail

---

### Post by poofyhairguy on 2005-02-24
[QUOTE=bored2k]ur a n00b and u dont want gui ? c'est bizarre !!!

anyway, boot up ur ubuntu install disk , type expert and press enter, this will give u control on things, allowing u to select minimal install "for servers that need only the minimum"

when u boot, press F1 and then F2, etc, this will tell u in greater detail[/QUOTE]

or type

linux custom

---

### Post by DJ_Max on 2005-02-24
[QUOTE=bored2k]ur a n00b and u dont want gui ? c'est bizarre !!!
[/QUOTE]
He said he was new to Ubuntu, not new to Linux. [-(

---

### Post by bored2k on 2005-02-24
[QUOTE=DJ_Max]He said he was new to Ubuntu, not new to Linux. [-([/QUOTE] 
lol my bad ... most live discs R using the same boot up menu, so i thought he  noob

g0od point tho  :|  :p

---

### Post by isaac on 2005-02-25
sorry,  i still don't get it I used the live CD to boot and type "expert" it work but i choose all the things I need and the installation went well... but there's still gui after the installtion finish? what happen? what's the problem here?


by the way... the command "linux custom" seems to be not working.

---

### Post by bored2k on 2005-02-25
[QUOTE=isaac]sorry,  i still don't get it I used the live CD to boot and type "expert" it work but i choose all the things I need and the installation went wel[/QUOTE]


u wont get package selection lik u do in mdk or xandros or slackware .... if u select minimal install custom-expert u will probably get no GUI


u can still apt-get remove gnome gdm and edit init script to start in shell

---

### Post by isaac on 2005-02-25
i don't know what happen I have tried to reinstalled again and again and my last method I used is installed  package from the internet... I ended up with w Aptitude menu.. a place for me to choose which package I wanted to installed...

I have choose to remove the gnome entirely from the unbuntu installation.. and i works well.. although my 1st intention was to install the default unbuntu with gui and remove the gnome later.

thanks every one for the help here...

I have another problem now. the command "make-kpkg" cannot be found after i installed the ubuntu without the gui(exclude gnome package entirely) .. 

So do anyone know which package  I need to get, using "apt-get" to install this "make-kpkg" command?

thanks =)

---

### Post by az on 2005-02-25
When installing from the cd, you type "custom" at the prompt and you end up with a base system that takes up about 350 megs of hard drive space.  There is a help screen that describes this.

You are looking to the kernel-package package, for make-kpkg.

You will need build-essential, too, if you do not already have it installed.

---

### Post by isaac on 2005-02-27
thanks ... i get it now =)[http://www.ubuntulinux.org/wiki/KernelBuildpackageDetailedHowto](http://www.ubuntulinux.org/wiki/KernelBuildpackageDetailedHowto)

---


---
title: "PLEASE HELP DESPERATE adobe flash download help!!!"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by wce on 2010-06-30
i do believe i have the ubuntu 8.04, and i have the intel atom processor/dell mini 9. i've been trying at least a yr to download and search how to download flash. recently i saw that when i searched flash in the synaptic package manager flash-nonfree or something like that showed up....then i deleted it completely because i got scared. then i read that we were suppose to select that to download it, but when i researched that in my add/remove application it wasnt there. i don't know what to do?! ive been trying forever. also when i try to go to the adobe flash website idk which to chose. the tar.gz or the version for 8.04 plus, but when i click 8.04 and try to download it, it says wrong architecture i836!! i've tried forever. how can i download it? PLEASE HELP(: sorry if this is confusing. idk how to download anything, i'm a ubuntu n00b.

---

### Post by atomizer on 2010-06-30
You downloaded the 32 bit version while you have a 64 bit ubuntu.

open synaptic package manager (system=>administration=>synaptic package manager) and search for "flash". two of the result should be adobe-flashplugin and flashplugin-nonfree

Install one of them. (checkbox "mark for install" and press the apply button)

---

### Post by howefield on 2010-06-30
You won't get 64 bit flash. It has been "temporarily" dropped due to a security hole and is not supported. 

You'll need to use 32 bit flash with nspluginwrapper.

The above should sort you out, but if you have trouble with buttons after installing 32 bit flash, you might try the following...

Open a terminal and type

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

press enter, and place the following before the last line

```
export GDK_NATIVE_WINDOWS=1
```

---

### Post by wce on 2010-07-08
thanks !

---

### Post by wce on 2010-07-08
thanks i accidently deleted it, and then it came back when i checked today(:

---

### Post by wce on 2010-07-08
wait so i installed the nonfree thing in the package installer, where do i go to next??

---

### Post by howefield on 2010-07-08
> **wce said:**
> where do i go to next??

Probably to youtube to test it :)

---

### Post by wce on 2010-07-08
yeah it still says you need to install missing plugins and it says you need to upgrade adobe flash? but it doesn't make sense because i installed it with the package manager?

---

### Post by howefield on 2010-07-08
Have you closed and restarted the browser since installing flash ?

---

### Post by wce on 2010-07-08
> **howefield said:**
> Have you closed and restarted the browser since installing flash ?

yesss i even restarted the computer

---


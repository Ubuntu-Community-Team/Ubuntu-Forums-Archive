---
title: "Software sources"
date: 2015-09-08
forum: MINT
---

### Post by Edward 000 on 2015-09-08
[COLOR=#000000][INDENT]I couldn't install Ubuntu because of my graphics card all I saw is bunch of dots so I installed Linux mint compatible mode and installed Ubuntu from Linux mint but now I have another problem Software sources option is not opening, I click on Software sources and nothing happens. [/INDENT]


[/COLOR]

---

### Post by deadflowr on 2015-09-08
While I don't quite understand
[COLOR=#000000] > I installed Linux mint compatible mode and installed Ubuntu from Linux mint [/COLOR]

The usual terminal command to open software sources is
```
software-properties-gtk
```

---

### Post by Edward 000 on 2015-09-08
> **deadflowr said:**
> While I don't quite understand
[COLOR=#000000] 

The usual terminal command to open software sources is
```
software-properties-gtk
```

 I am receiving this. I think I removed some important files.

---

### Post by Edward 000 on 2015-09-08
> **deadflowr said:**
> While I don't quite understand
[COLOR=#000000] 

The usual terminal command to open software sources is
```
software-properties-gtk
```

I couldnt Install Ubuntu so I used Linux Mint Cinnamon and today I decided to install Unity

---

### Post by ajgreeny on 2015-09-08
It sounds as if you have installed unity on Mint which may be the reason for this problem; whilst Mint is based on Ubuntu it is not the same OS and there could be packages and system files that are different, or have different paths.  I am not sure about software-sources but Mint certainly has some different applications from those in Ubuntu for installing and updating packages.

---

### Post by Edward 000 on 2015-09-09
I had to fresh install mint and installed unity that's the only way I can use Unity because when I try to install Ubuntu the screen turn into dots and freeze but Linux mint has compatible mode to install it and it works for me this way

---

### Post by coffeecat on 2015-09-09
> **Edward 000 said:**
> I had to fresh install mint and installed unity that's the only way I can use Unity because when I try to install Ubuntu the screen turn into dots and freeze but Linux mint has compatible mode to install it and it works for me this way

Rather than struggling to get Unity installed in Linux Mint, let's see if you can boot up Ubuntu. If you can boot the live session of Mint you should be able to boot Ubuntu live.

Start your live DVD or live USB of Ubuntu - whichever you are using - and as soon as you see the purple screen with the small icons representing a person and a keyboard at the bottom of the screen, tap the space bar. Select your language and you are then confronted with an old-style menu. Press F6 and among the options there should be something like "safe graphics mode". I believe this is the same as Mint's compatibility mode. Boot up with the system in safe graphics mode and see if you can get a usable desktop. If you can, you can then make a decision as to whether you want to reinstall with Ubuntu or struggle on trying to get Unity installed in Mint.

---

### Post by Edward 000 on 2015-09-21
> **coffeecat said:**
> Rather than struggling to get Unity installed in Linux Mint, let's see if you can boot up Ubuntu. If you can boot the live session of Mint you should be able to boot Ubuntu live.

Start your live DVD or live USB of Ubuntu - whichever you are using - and as soon as you see the purple screen with the small icons representing a person and a keyboard at the bottom of the screen, tap the space bar. Select your language and you are then confronted with an old-style menu. Press F6 and among the options there should be something like "safe graphics mode". I believe this is the same as Mint's compatibility mode. Boot up with the system in safe graphics mode and see if you can get a usable desktop. If you can, you can then make a decision as to whether you want to reinstall with Ubuntu or struggle on trying to get Unity installed in Mint.

Thanks very much, I did what you tell me and installation went successfully!! Didn't know Ubuntu had advanced options! Thanks!

---


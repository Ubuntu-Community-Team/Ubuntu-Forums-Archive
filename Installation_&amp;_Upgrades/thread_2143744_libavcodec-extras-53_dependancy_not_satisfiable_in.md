---
title: "libavcodec-extras-53 dependancy not satisfiable installing package"
date: 2013-05-09
forum: Installation &amp; Upgrades
---

### Post by KELLOGGVOIDS on 2013-05-09
Hello (I'm pretty sure i have an attachment.)
If you can see it, its a picture of a package I opened in the software manager, and that message keeps coming up.
I have removed and reinstalled libavcodec-extra-53, libavcodec53, libavutil-extra-51, and libavutil51 and there isn't any
change. I even tried it by themselves, and together installed. (extras and regulars.)
The package is dolphin emulator 3.5. (NOTE:: Do I need to say this for forum rules? I OWN THE GAMES I WILL BE USING ON THIS EMULATOR, THIS IS NOT ILLEGAL.)

---

### Post by KELLOGGVOIDS on 2013-05-09
oh, I think I should mention I also installed the restricted extras after I removed the regulars (you know..not the extras. just libavcodec53, libavutil51)

---

### Post by KELLOGGVOIDS on 2013-05-10
please...anyone. I'm not a pro, so if  I did anything wrong here, with a post, or with the way I'm explaining my problem, or with the way I tried to solve it..If its in the wrong section.sorry.

---

### Post by Bashing-om on 2013-05-10
KELLOGGVOIDS; Hi !

I will start the ball rolling. Let us see what condition the management of the packages are in. Post the output - between code (#) tags - of terminal command:
```
sudo dpkg -C
``` note that is an upper case "c".
See:```
man dpkg
```
>         -C, --audit
              Searches for packages that have been installed only partially on
              your system. dpkg will suggest what to do with them to get  them
              working.[INDENT=3]
just try'n to help

[/INDENT]

---

### Post by KELLOGGVOIDS on 2013-05-10
So, I should post what came out after sudo dpkg -C?
Actually, nothing came.. 

ollie@ollie-System-Product-Name:~$ sudo dpkg -C
[sudo] password for ollie: 
ollie@ollie-System-Product-Name:~$

---

### Post by Bashing-om on 2013-05-11
KELLOGGVOIDS;

The non output from "dpkg -C" means that the package manager is happy. // Installed from another source than the regular repositories such that the package manager is not aware of it. 
dolphin emulator 3.5. : I do not see that package in the ubuntu 12.04 repository. How did you install it and what version/distribution are you running ?[INDENT]
we be look'n

[/INDENT]

---

### Post by KELLOGGVOIDS on 2013-05-11
This is my reinstall of ubuntu... (since my first post).  It worked before this reinstallation. I don't think I did anything differently.

[http://dolphin-emu.org/download/?ref=btn](http://dolphin-emu.org/download/?ref=btn)
ubuntu 12.04 64bit

I got it from here.

---

### Post by KELLOGGVOIDS on 2013-05-11
oops..... I did some googling, and I remembered something.
[http://code.google.com/p/dolphin-emu/wiki/DolphinUbuntuPackages](http://code.google.com/p/dolphin-emu/wiki/DolphinUbuntuPackages)

Problem solved. 

Is my computer compromised in any way for posing my computer name up top from the terminal?
Thanks for your posts. Appreciated.

---

### Post by Bashing-om on 2013-05-11
KELLOGGVOIDS;

Well your first posted link's install would explain why the package manager does not cope with installing/resolving dolphin's dependencies.

The second method is preferable and the package manager will pick it up.... Glad ya got it resolved !

Please mark this thread as "solved"
Interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.

Other matter:
> Is my computer compromised in any way for posing my computer name up top from the terminal?
No reference given to where, what, when or why- but, in general I can not see where divulging the name of a computer could be considered as a compromise in security.[INDENT=2]
Its all a learning experience

[/INDENT]

---


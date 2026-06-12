---
title: "Help with .rpm CAD Installation"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by Dylnuge on 2007-10-11
Hello.

I recently downloaded GraphiteCAD. However, it is rpm only, not even source, so I used alien. I had two problems.

Problem 1: The 3d-Drafting package tries to overide files that it shares with the 2d-Drafting package. I would like to allow this, but the package manager just gives me an error,

Problem 2: When trying to run it, I get this error:
```
dnugent@tzWS001:~$ cd /opt/GraphiteOne/bin
dnugent@tzWS001:/opt/GraphiteOne/bin$ ./graphiteone
'./graphiteone: 19: function: not found
usage : graphiteone [options]
Options:
   --ogl=[yes|no]               Enable/Disable OpenGL display driver (default is no).
   --fsaa-mode=[0..5]           Enable FSAA mode for nVidia graphic cards (experimental!).
   --python=[python executable] The python executable to use (default is python).
   --paths=[path:...]           More entries for PYTHONPATH.
dnugent@tzWS001:/opt/GraphiteOne/bin$ ./graphiteone --ogl=yes
./graphiteone: 19: function: not found
usage : graphiteone [options]
Options:
   --ogl=[yes|no]               Enable/Disable OpenGL display driver (default is no).
   --fsaa-mode=[0..5]           Enable FSAA mode for nVidia graphic cards (experimental!).
   --python=[python executable] The python executable to use (default is python).
   --paths=[path:...]           More entries for PYTHONPATH.
dnugent@tzWS001:/opt/GraphiteOne/bin$ 

```

Not exactly sure what it means by function not found...

Thanks for any help,
Dylan

---

### Post by Dylnuge on 2007-10-12
...Anyone?

---

### Post by blondebeard on 2008-05-06
hello im a fabricator and i dont like going to windoze to draft and im trying to install the same program and and i tried sudo alien -i and to convert and install with apt get and can get to work either yet. have you figured it out yet or do you want to collaborate to get this to work or is their an alternative 3d cad out there for me to use. im willing to help you if you are still interested to get this program working.

---

### Post by cubeist on 2008-05-06
> **blondebeard said:**
> hello im a fabricator and i dont like going to windoze to draft and im trying to install the same program and and i tried sudo alien -i and to convert and install with apt get and can get to work either yet. have you figured it out yet or do you want to collaborate to get this to work or is their an alternative 3d cad out there for me to use. im willing to help you if you are still interested to get this program working.

Here are some alternatives:
[http://ubuntuguide.org/wiki/Alternatives#Computer_Aided_Design](http://ubuntuguide.org/wiki/Alternatives#Computer_Aided_Design)

I would also add Blender to that list. It is not specifically a cad program but there is great flexibility in the program and you may find it works well for your needs.

---

### Post by deepthought on 2008-05-23
Here are some more alternatives
[https://help.ubuntu.com/community/UbuntuScience#head-3cdf7bb4c23423811354a77a7ebeaff72498b692](https://help.ubuntu.com/community/UbuntuScience#head-3cdf7bb4c23423811354a77a7ebeaff72498b692)

---


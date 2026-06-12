---
title: "UT2004 Karmic"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Drezliok on 2009-10-23
I know it's not official yet and this might need to be in a different forum but It's only days away.

I can't get my ut2004. I haven't gotten it to run since 9.04 so I think it's still valid.

[http://forums.epicgames.com/showthread.php?t=477085](http://forums.epicgames.com/showthread.php?t=477085)
The link above is the IDENTICAL error and I did the same thing as suggested.

I made a symbolic link. (which was suggested on the ubuntuforums too) Then I got the same error he got.

```
drezliok@drezliok-desktop:~$ ut2004
./ut2004-bin: /usr/lib/libstdc++.so.5: version `GLIBCPP_3.2' not found (required by ./ut2004-bin)
./ut2004-bin: /usr/lib/libstdc++.so.5: version `CXXABI_1.2' not found (required by ./ut2004-bin)

```

Now I noticed they had a fix but it's for Fedora, I tried installing the file from Ubuntu repos and we don't have that file. Unless it's spelled different.

```
drezliok@drezliok-desktop:~$ sudo apt-get install compat-libstdc++
[sudo] password for drezliok: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compat-libstdc

```


Any Idea as to what I can do. I miss my fav game.
Drezliok

---

### Post by Perfect Storm on 2009-10-23
I have ut2004 DVD working on 9.10 64-bit - check the UGA guide: [http://gwos.org/doku.php/guides:64bit:ut2004](http://gwos.org/doku.php/guides:64bit:ut2004)

libstdc++5 is no longer part of the Ubuntu repository. It's now libstdc++6. In the guide it shows how to install the libstdc++5 for 64-bit, but you could experiment by symblink libstdc++6 with libstdc++5 and see if it works.

---

### Post by Drezliok on 2009-10-23
> **Artificial Intelligence said:**
> I have ut2004 DVD working on 9.10 64-bit - check the UGA guide: [http://gwos.org/doku.php/guides:64bit:ut2004](http://gwos.org/doku.php/guides:64bit:ut2004)

libstdc++5 is no longer part of the Ubuntu repository. It's now libstdc++6. In the guide it shows how to install the libstdc++5 for 64-bit, but you could experiment by symblink libstdc++6 with libstdc++5 and see if it works.

Unfortunately I haven't gotten a 64bit proc yet. Still using the trusty old P4.

I will look into this.

The symbolic link has been made already but for some reason it says it's missing 2 things. GLIBCPP_3.2 and CXXABI_1.2

---

### Post by Perfect Storm on 2009-10-23
Try this:
remove the symblink you made. Download the 9.04 version of libstdc++5 for your 9.10

---

### Post by Drezliok on 2009-10-23
> **Artificial Intelligence said:**
> Try this:
remove the symblink you made. Download the 9.04 version of libstdc++5 for your 9.10

I was think thinking about that myself, but I don't know to to remove a symblink.

It's late here, I will look it when I get a chance tomorrow.

---

### Post by Drezliok on 2009-10-26
OK!!!

Learned how to remove the symbolic link I added. Game tries to start now. But I have a NEW ERROR!!! crud.

```
drezliok@drezliok-desktop:~$ ut2004
open /dev/[sound/]dsp: Device or resource busy
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  130 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x13c
  Serial number of failed request:  167
  Current serial number in output stream:  168

```

I have no clue as to what to do now.

---

### Post by Drezliok on 2009-10-27
Could I get a Mod to Move this back to the Games and Leisure section of the forum after Karmic goes live?

I was getting help there but since the move I haven't had any help. But I am patient.

Thankyou for your time,
Drezliok

---


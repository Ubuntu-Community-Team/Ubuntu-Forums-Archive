---
title: "[SOLVED] songbird"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by want2bdifferent on 2008-07-18
hey i dont know if this is the right section as i am new anyway.

I just downloaded songbird 0.6 of the get songbird site and i do not know how to install it.

I am running Ubuntu 7.04

any help would be appreciated
thanks

---

### Post by Partyboi2 on 2008-07-18
that looks to be a source file, it would probably be easier to look for a deb package and install it that way. Have a look [[COLOR=Blue]here[/COLOR]]("http://www.getdeb.net/search.php?keywords=songbird") for a deb, after downloading all you have to do is double click the deb package to start installing it.

---

### Post by want2bdifferent on 2008-07-18
thankyou heaps, all i want it for is iPod support

---

### Post by meindian523 on 2008-07-18
iPod support is available on Rhythmbox and amarok too.But I'm not too sure if they support the 3rd generation,if that is what you have.

---

### Post by want2bdifferent on 2008-07-18
I have a third generation ipod nano.

but now i have another problem whenever i try to open songbird it just says "starting songbird" down the bottom and then nothing.

---

### Post by meindian523 on 2008-07-18
Please run ```
songbird
``` in terminal and post any error messages here.Did you install using a *.deb?

---

### Post by want2bdifferent on 2008-07-18
I did install using a *.deb

this is the error message i got in terminal
emily@fred:~$ songbird
./songbird: symbol lookup error: /usr/share/Songbird/xulrunner/libxul.so: undefined symbol: g_once_init_enter_impl

thanks again

---

### Post by meindian523 on 2008-07-18
Nopes,I put up my hands here.I can't even get what that message means.

---

### Post by want2bdifferent on 2008-07-18
would it matter what version i am using? cos like i said i am only running 7.04

---

### Post by Partyboi2 on 2008-07-18
looks like there could be a problem with xulrunner built against  a newer glib
[http://bugzilla.songbirdnest.com/show_bug.cgi?id=10295](http://bugzilla.songbirdnest.com/show_bug.cgi?id=10295)
[http://getsatisfaction.com/songbird/topics/undefined_symbol_in_libxul_so](http://getsatisfaction.com/songbird/topics/undefined_symbol_in_libxul_so)

---

### Post by mikewhatever on 2008-07-18
You could try uninstalling the deb file and install the tar.gz package using this guide --> [http://www.howtoforge.com/installing_songbird_on_ubuntu_gutsy_gibbon](http://www.howtoforge.com/installing_songbird_on_ubuntu_gutsy_gibbon)

---

### Post by want2bdifferent on 2008-07-18
oh what i have tried so far is:
-un-installing the deb file and re-installing it
-i have tried the previous' posts suggestion and i still have the same problems

---

### Post by meindian523 on 2008-07-19
It's a known bug,you have to wait till it's resolved or find out what to do from the links partyboi pasted.

---

### Post by mikewhatever on 2008-07-19
> **meindian523 said:**
> It's a known bug,you have to wait till it's resolved or find out what to do from the links partyboi pasted.

It's odd because I don't seem to be affected.

---

### Post by meindian523 on 2008-07-20
It's a problem with the glibc version with which Songbird was compiled,atleast that's what sense I can make of the bug report.
You not having a problem is probably because your glibc is older.

---

### Post by want2bdifferent on 2008-07-23
oh i have upgraded to hardy heron. it is working now

thanks everyone

---


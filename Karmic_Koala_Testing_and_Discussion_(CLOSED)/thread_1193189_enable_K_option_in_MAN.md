---
title: "enable K option in MAN"
date: 2009-06-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by fcvsub on 2009-06-21
hi , iam fedora user , and i decided to give ubuntu a try .

 iam using man a lot , especially  capital K option ,  to search in the whole man pages .   

there is a big difference between small k ( -k ) option and capital K ( -K ) small k only search in the title and in the description , but the capital k in all the text in the whole man pages , this will give you any thing you search for i think K option is very import , so please re-build the package and enable that , 

Example : 

i want to know about /dev/null , 

so i will ask man for it , with this command : 

```
man -K /dev/null 
```and man will search in the whole database ( man pages ) , and give me any page match that pattern and contain /dev/null :) 

the output :

```
$ man -K /dev/null
/usr/share/man/man4/zero.4.gz? [ynq] y
/usr/share/man/man4/null.4.gz? [ynq] y
Man page /usr/share/man/man4/null.4.gz is identical to /usr/share/man/man4/zero.4.gz
/usr/share/man/man1/funzip.1.gz? [ynq] y
/usr/share/man/man1/ssh.1.gz? [ynq] n
/usr/share/man/man1/sh.distrib.1.gz? [ynq] y
/usr/share/man/man1/egrep.1.gz? [ynq] y
/usr/share/man/man1/netscsid.1.gz? [ynq] n
/usr/share/man/man1/rgrep.1.gz? [ynq] y
```i think its  clear  now :) 

and thank you for your interesting and voting   :)

---

### Post by taavikko on 2009-06-21
I use / to search for wanted expression, isn't that sufficient for you?

---

### Post by inportb on 2009-06-21
Now, I've never tried the / search option... nor have I ever searched the manual locally, so I would not know. If I need to find something, I Google for it :)

This -K option sounds useful, but if / works, why not?

---

### Post by SuperSonic4 on 2009-06-21
> **inportb said:**
> Now, I've never tried the / search option... nor have I ever searched the manual locally, so I would not know. If I need to find something, I Google for it :)

This -K option sounds useful, but if / works, why not?

Same here.

If you want -K to work you could try creating an alias in .bashrc 

Something like ```
alias man='man -K'
``` which may or may not work

---

### Post by fcvsub on 2009-06-21
thank u every body , i am re-phrase the post , please read it again

---

### Post by xebian on 2009-06-21
No. Most of the times I use man *command* just to get the full usage that you can't get from --help. 

Or you can get your own special version say get Fedora's man.

---

### Post by taavikko on 2009-06-21
> **fcvsub said:**
> thank u every body , i am re-phrase the post , please read it again

Oh, I misunderstood the original idea. This actually sounds good in my opinion. To be able view meaning/usage of different apps/places/etc...

could you post a sample using
"man -K /dev/null" what the fuzz is about.

---

### Post by fcvsub on 2009-06-22
[taavikko]("http://ubuntuforums.org/member.php?u=286985") : you can build man from source , and try it 

the output :

```
$ man -K /dev/null
/usr/share/man/man4/zero.4.gz? [ynq] y
/usr/share/man/man4/null.4.gz? [ynq] y
Man page /usr/share/man/man4/null.4.gz is identical to /usr/share/man/man4/zero.4.gz
/usr/share/man/man1/funzip.1.gz? [ynq] y
/usr/share/man/man1/ssh.1.gz? [ynq] n
/usr/share/man/man1/sh.distrib.1.gz? [ynq] y
/usr/share/man/man1/egrep.1.gz? [ynq] y
/usr/share/man/man1/netscsid.1.gz? [ynq] n
/usr/share/man/man1/rgrep.1.gz? [ynq] y
```

---

### Post by hugmenot on 2009-06-23
What about apropos?

```
apropos null
```

---

### Post by fcvsub on 2009-06-24
reported :  [https://bugs.launchpad.net/ubuntu/+source/man-db/+bug/390575](https://bugs.launchpad.net/ubuntu/+source/man-db/+bug/390575)

---

### Post by 23meg on 2009-07-14
Colin Watson [has implemented it]("http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/2009/07/14#2009-07-14-man-db-K""). It should arrive with the next upload.

---

### Post by wayne_cat on 2009-07-14
Will the new package be the default system or an option that I can choose (like vi / vim)?

---

### Post by taavikko on 2009-07-14
> **wayne_cat said:**
> Will the new package be the default system or an option that I can choose (like vi / vim)?

If I understood correctly that it's just a feature (option) introduced to an existing package.

---

### Post by garba on 2009-07-14
thanks for the tip, i didn't know of this feature of "man"

---


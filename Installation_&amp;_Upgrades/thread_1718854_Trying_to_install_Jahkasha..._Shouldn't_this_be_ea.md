---
title: "Trying to install Jahkasha... Shouldn't this be easy?!"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by Kangaji on 2011-03-31
Hey folks,

     So I just started using Ubuntu, and now I'm trying to install some video editing software called "Jahkasha". I keep trying and trying, but can't figure out how to open either the tar.gz or .run files. I really like Ubuntu, but if I can't install files I might as well just go back to Windows...

     HELP!!!
     T_T

---

### Post by Enigmapond on 2011-03-31
Is there any special reason why you need this particular editor? There are better ones available right through the repositories PiTiVi, Cinelerra, Auteur and a number of others native to Linux and so much easier to install.

---

### Post by Kangaji on 2011-04-01
> **Enigmapond said:**
> Is there any special reason why you need this particular editor? There are better ones available right through the repositories PiTiVi, Cinelerra, Auteur and a number of others native to Linux and so much easier to install.


Nah, I just really thought it was pretty looking. I was looking into installing Cinelerra as an alternative, but I just can't seem to figure out how to install THAT ONE either.
:P

---

### Post by Enigmapond on 2011-04-01
Very easy..Open the terminal and do:

```
sudo add-apt-repository ppa:cinelerra-ppa/ppa
sudo apt-get update && sudo apt-get install cinelerra
```

But I would also look at PiTiVi which is in the repos.

```
sudo apt-get install pitivi
```

Cheers!

---

### Post by Kangaji on 2011-04-01
> **Enigmapond said:**
> Very easy..Open the terminal and do:

```
sudo add-apt-repository ppa:cinelerra-ppa/ppa
sudo apt-get update && sudo apt-get install cinelerra
```But I would also look at PiTiVi which is in the repos.

```
sudo apt-get install pitivi
```Cheers!


Works perfectly now! Thanks dude!
^.^b

---

### Post by Enigmapond on 2011-04-01
No problem! Good Luck..:) You should mark this thread as "Solved" in the Thread Tools on the upper right, for others' benefit.

Cheers!

---


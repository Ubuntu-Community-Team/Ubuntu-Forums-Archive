---
title: "bash and mkdir last argument mangling?"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by HankB on 2009-10-04
I'm accustomed to using $_ to represent the last argument of the previous command when typing a sequence of commands. Recently I have noticed that the actual last argument to mkdir seems to get replaced by _filedir. I have only noticed that during interactive use. An example is shown below.
```
hbarta@bonsai:~/Music/podcast$ mkdir 2009-10-03
hbarta@bonsai:~/Music/podcast$ mv ../hpodder/*/*mp3 $_
mv: target `_filedir' is not a directory
hbarta@bonsai:~/Music/podcast$ echo ../hpodder/*/*mp3 $_
../hpodder/Amateur_Traveler_Podcast___travel_for_the_love_of_it/202AmateurTraveler.mp3 ../hpodder/NPR__Car_Talk_Podcast/npr_113469541.mp3 ../hpodder/NPR__Wait_Wait..._Don_t_Tell_Me__Podcast/npr_113471353.mp3 ../hpodder/The_Onion_Radio_News/podcast_redirect.mp3 _filedir
hbarta@bonsai:~/Music/podcast$ 
```

Is this a bug in bash or mkdir or am I overlooking something that causes this to be normal behavior? It does not happen all of the time and I am not sure how to reliably duplicate it.

thanks,
hank

---

### Post by slakkie on 2009-10-04
I always use $!, since it works also in zsh and other shells.

```

mkdir /path/to/dir
cd $!

```

--edit--

$! should be !$

---

### Post by HankB on 2009-10-06
> **slakkie said:**
> I always use $!, since it works also in zsh and other shells.

```

mkdir /path/to/dir
cd $!

```

```
hbarta@cypress:~$ mkdir test
hbarta@cypress:~$ cd $!
hbarta@cypress:~$ pwd
/home/hbarta
hbarta@cypress:~$ 
```

:confused:

---

### Post by DaithiF on 2009-10-07
> **HankB said:**
> ```
hbarta@cypress:~$ mkdir test
hbarta@cypress:~$ cd $!
hbarta@cypress:~$ pwd
/home/hbarta
hbarta@cypress:~$ 
```:confused:
if this doesn't work then you're probably not running bash as your shell.
start a new bash shell interactively and try again -- if it works then check your shell setting in /etc/passwd -- it may be set to /bin/sh rather than /bin/bash

---

### Post by slakkie on 2009-10-07
> **HankB said:**
> ```
hbarta@cypress:~$ mkdir test
hbarta@cypress:~$ cd $!
hbarta@cypress:~$ pwd
/home/hbarta
hbarta@cypress:~$ 
```

:confused:

Errrr, !$ sorry

```

mkdir -p /tmp/test
cd !$

```

---

### Post by HankB on 2009-10-07
> **slakkie said:**
> Errrr, !$ sorry

```

mkdir -p /tmp/test
cd !$

```

```
hbarta@cypress:~$ mkdir test
hbarta@cypress:~$ cd !$
cd test
hbarta@cypress:~/test$ 

```

:guitar:

I still wonder if the mangling of the value of $_ is a bug or a feature.

thanks,
hank

---


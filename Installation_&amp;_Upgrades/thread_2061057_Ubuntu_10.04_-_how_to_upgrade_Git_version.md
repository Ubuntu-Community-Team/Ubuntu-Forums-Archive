---
title: "Ubuntu 10.04 - how to upgrade Git version"
date: 2012-09-21
forum: Installation &amp; Upgrades
---

### Post by Lavix on 2012-09-21
How is it possible to upgrade GIT version from 1.7.0.4 to the latest one?

Thanks

---

### Post by josephmills on 2012-09-21
Hope that this helps :) 
[https://launchpad.net/~voronov84/+archive/andreyv/+build/3731617](https://launchpad.net/~voronov84/+archive/andreyv/+build/3731617)

---

### Post by Lavix on 2012-09-21
Sorry for such a stupid question, - but how to install that, what should I donwload, please.

---

### Post by josephmills on 2012-09-21
No questions are stupid,

here is what I think that you have to do, You said that you are on 10.04 so there is a ppa that you can use but it is only up to 1:1.7.10-0 
and not 
1:1.7.12-0

to add this ppa to your system 
```
sudo add-apt-repository ppa:voronov84/andreyv
```
then 
```
sudo apt-get update
```
then if you already have git installed just upgrade it. 
```
sudo apt-get upgrade
```
If it is not installed 
```
sudo apt-get install git
```

that should get you up to 

1:1.7.10-0 



you could always search launchpad for a newer ppa 
example google 
"ubuntu launchpad git 1:1.7.12"

---

### Post by Lavix on 2012-09-21
Wow, super, it worked as you told. Now I have git --version 1.7.10. Thanks a lot):P

---

### Post by josephmills on 2012-09-21
Sweet can you 
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---


---
title: "Move graphic setup from Lubuntu to Mint"
date: 2014-11-01
forum: MINT
---

### Post by birkopf on 2014-11-01
For some reason my second laptop has got a problem with new Lubuntu. Mint is working fine but I really like the way Lubuntu 14.04 looks like. As far as I see there is no theme which I can install in Mint that will give me Lubuntu look. Can I move some folder from Lubuntu to Mint to have the choice of that Lubuntu look ?

---

### Post by ajgreeny on 2014-11-01
You can add the LXDE desktop to Mint surely and then login to an LXDE session.  If you7 then choose the same desktop wallpaper image, etc etc it should look more or less the same.

---

### Post by birkopf on 2014-11-01
Thanks. Mint has got already lxle version. I am wondering more how to recreate exact look of Lubuntu on Mint. There must be a way to copy settings from LLubuntu.

---

### Post by sudodus on 2014-11-01
You can also try [LXLE]("http://lxle.net/") which is different from LXDE.

---

### Post by vasa1 on 2014-11-01
> **birkopf said:**
> Thanks. Mint has got already lxle version. I am wondering more how to recreate exact look of Lubuntu on Mint. There must be a way to copy settings from LLubuntu.
Install lubuntu-desktop on Mint.

---

### Post by howefield on 2014-11-01
Thread moved to the "*MINT*" forum.

---

### Post by birkopf on 2014-11-02
> **vasa1 said:**
> Install lubuntu-desktop on Mint.

How to do that, to have the same look as Lubuntu ?

---

### Post by ajgreeny on 2014-11-02
Because Mint uses the Ubuntu repos, lubuntu-desktop should be available with command ```
sudo apt-get install lubuntu-desktop
```but I am not sure how "safe" it is to install these *ubuntu-desktop packages in Mint; I seem to recall there being some conflicts but I may be remembering wrongly.

See if any error messages appear if you run that command in simulation mode```
sudo apt-get install -s lubuntu-desktop
```

---

### Post by birkopf on 2014-11-03
Thanks for that. I have chosen slightly different route but your advice was great. Basically the goal is accomplished - I have now mint on xfce which is very similar and shares many elements with lxde. I changed the look because those green folders drive me nuts. So far - all works well. I kind of have own Linux now. Certainly from visual perspective

---

### Post by Habitual on 2014-11-04
> **birkopf said:**
> the look because those green folders drive me nuts.That is supposed to be something the user can adjust in LM17.1 due out sometime this month.

---

### Post by birkopf on 2014-11-04
That would be great!
This is pretty much how my set up looks like now on Linux Mint:

[IMG]http://bit.ly/1AcNUbo[/IMG]

---


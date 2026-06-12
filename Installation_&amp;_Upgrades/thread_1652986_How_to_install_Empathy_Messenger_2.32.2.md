---
title: "How to install Empathy Messenger 2.32.2"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by kylewisdom on 2010-12-26
Hello everyone,

I have been using Ubuntu 10.10 for a few weeks now (have been using Ubuntu/Linux on and off for quite a while).

I had to work around some things for a while to get it correctly partitioned with Windows 7 and what not which led to me formatting and reinstalling a few times to get it just right.

Along the way, I was able to upgrade my Empathy messenger from 2.32.1 to 2.32.2. I loved the upgrade as it has the notification icon for me installed which is much nicer than the colored envelope when someone sends me a message.

I have tried to upgrade to it recently and it is not allowing me to do so.

Can anyone help me upgrade back to 2.32.2 from 2.32.1?

Thanks!

---

### Post by karthick87 on 2010-12-26
Welcome to ubuntuforums :)

Type the following in terminal to install latest version of Empathy,
    ```
sudo add-apt-repository ppa:telepathy/ppa
```
```
sudo apt-get update && sudo apt-get upgrade
```  ```
sudo apt-get install empathy
```

---

### Post by kylewisdom on 2010-12-26
> **karthick87 said:**
> Welcome to ubuntuforums :)

Type the following in terminal to install latest version of Empathy,
    ```
sudo add-apt-repository ppa:telepathy/ppa
``````
sudo apt-get update && sudo apt-get upgrade
```  ```
sudo apt-get install empathy
```


I have that in my repositories already and have done all of that, which is why I am so confused. 

I never had a problem with it in prior installations but now it is not working, so just wondering what to do.

---

### Post by karthick87 on 2010-12-26
Try reinstalling the package..

---

### Post by kylewisdom on 2010-12-26
> **karthick87 said:**
> Try reinstalling the package..


Nope, still 2.32.1

---


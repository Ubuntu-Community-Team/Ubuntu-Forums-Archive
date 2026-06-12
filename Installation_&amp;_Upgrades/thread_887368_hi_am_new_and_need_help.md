---
title: "hi am new and need help"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by dariou2 on 2008-08-12
hi am new here and to ubuntu i didnt know if this is the right place to post but i did it anyway 


i have been trying to open the source.list for 3 days now i want to install tor and it says i need to add the source a while back i installed whine and followed the instructions given on this forum i remember there was a code i enter in terminal to open the list i have searched for the thread many times but couldnt find it also i googled it and i only found sources to add 
i really need to open that list to install tor could anyone help plz?

than you,

---

### Post by scriminaci on 2008-08-12
If you want to modify the sources.list file you have to execute in terminal
```
sudo gedit /etc/apt/sources.list
```

then you have to update your repository cache so you have to execute
```
sudo apt-get update
```

ok?

---

### Post by zipperback on 2008-08-12
You can manage your sources list with the following:

System -> Administration -> Software Sources

If it is not one of the official Ubuntu repositories, click on the Third-Party Software tab, and click add, then enter the repository information. Be sure to reload the repository data to enable your system to download all the latest package information.

- zipperback
:popcorn:

---

### Post by dariou2 on 2008-08-12
thanks alot guys 
and one more question so if i want to install tor i have to click on the third party tab? because its not from ubuntu right?

---


---
title: "Various Installation Problems"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by Arador Aristata on 2007-12-21
Firstly, Hello to all.

I am an absolute beginner with Linux and have been struggling a bit with Ubuntu(Gutsy) on my PC. The biggest problem is that I can not get my bluetooth to use my Nokia as a modem. Now I have downloaded Blueman and have been trying to install it.

Problem 1: To install blueman you need to have certain things installed on Ubuntu. I have been able to download all of these (Log into windows, search, download, restart, log into ubuntu, install, see error, restart, log into windows, search forums, restart, rinse, repeat) and install all but one. Pyrex. The error it gives me has to do with my writing permissions in the main folders. Even though I am a member of root and admin, I can not create folders in usr/lib/ and just about any folder apart from my own.

If I run "python setup.py install" after I extracted the tarball it tells me cannot create [pathtofolder]:Permission deneid. I can not log in with root as it tells me the root user can not log in this way. If I try to set the permission manually it tells me I can not change the permissions as I am not the owner of the folders.

Please could someone help me out a bit? Installing files manually is a pain and I want to get my net access working in Ubuntu.

Problem 2: I also tried to manually install XMMS. The error I get pertains to it not being able to find giblib 1.2.2 or newer on my system. From what I was able to see on Synaptics, I have 2.1.1 installed. The error tells me that if I do have it installed I must make sure the full path is giblib_config. Where do I go to edit this and how do I do it exactly?

I am sorry that I do not have the specific messages. Forgot flashdisk at home today.

Thank you in advance.
Regards
Arador

---

### Post by PmDematagoda on 2007-12-21
For problem 1:-

To install Blueman you will have to give it root permissions, so:-

```
python setup.py install
```
should look like this:-

```
**sudo** python setup.py install
```

"sudo" being the part that grants root permissions to the particular command you are trying to execute.

---

### Post by Arador Aristata on 2007-12-21
Ahh. Thank you very much. Like I say, yesterday was the first day I have ever worked with Linux in my life so a lot I still need to learn but loving every moment of it.

---

### Post by Partyboi2 on 2007-12-21
> The error it gives me has to do with my writing permissions in the main folders. Even though I am a member of root and admin, I can not create folders in usr/lib/ and just about any folder apart from my own.Try
```
sudo nautilus
```That will open nautilus as root.
> If I run "python setup.py install" after I extracted the tarball it tells me cannot create [pathtofolder]:Permission deneid. I can not log in with root as it tells me the root user can not log in this way. If I try to set the permission manually it tells me I can not change the permissions as I am not the owner of the folders.What happens if you put sudo infront.

```
sudo python setup.py install
```

---

### Post by Arador Aristata on 2007-12-21
Will put the sudo infront when I get home this afternoon. I've seen it once or twice but didnt realise what it did. Thank you for your help guys. Really appreciate it. And thanks for the tips.

---

### Post by Partyboi2 on 2007-12-21
This link will explain more about sudo
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Welcome to ubuntu!

---

### Post by Arador Aristata on 2007-12-21
Thank you. That explained a lot.

Anyone have an idea about the giblib problem?

---

### Post by Partyboi2 on 2007-12-21
> **Arador Aristata said:**
> Thank you. That explained a lot.

Anyone have an idea about the giblib problem?
Can you post the exact error message for it?

---

### Post by Arador Aristata on 2007-12-21
*** The giblib-config script installed by giblib could not be found
*** If giblib was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GIBLIB_CONFIG environment variable to the
*** full path to giblib-config.
configure: error: Cannot find giblib: Is giblib-config in the path?

---

### Post by Partyboi2 on 2007-12-21
have you got the giblib-dev package installed?

Edit: Isn't Xmms available from add/remove?

---

### Post by Arador Aristata on 2007-12-21
I have giblib installed. Thing is I use my phone to connect with GPRS and I first have to get that figured out before I can do the rest.

---

### Post by Arador Aristata on 2007-12-22
Im still having a hell of a time gtting blueman installed. Is there any other pakage you would suggest I use to get my Nokia's modem set up through bluetooth? Once I have that setup, it should be a lot easier to install pakages.

---


---
title: "Cannot login on Ubuntu One from Software Center"
date: 2016-10-02
forum: Installation &amp; Upgrades
---

### Post by sasuke83 on 2016-10-02
Hi guys,

when I try to install Telegram from the Software Center (Ubuntu 16.04 LTS), it shows me a dialog to login to Ubuntu One with the "Single Sign-On" system. 
I already have an Ubuntu One account, but when I enter my email and password it shows the following error: "Incorrect email or password".
I tried to login via internet, using firefox, and the username and password work correctly. 
So, I changed my password and I tried to login again... but nothing. It not works. It returns always the same error.
(This happens only when I try to login from the software center)

What can be the problem?

Thanks in advance.

---

### Post by ajgreeny on 2016-10-02
You have obviously managed to login to the forum which uses the SSO password, so make sure you are using that password when asked for it in the SC, if that is really what you are being asked for.

As far as I'm aware the SC needs your system username account password, not the SSO one, though I have never used the SC or gnome-software or any of those applications.  For me it is a choice between the command line apt-get, or if I use a GUI, synaptic is my choice, and both of those ask for the username account password to authorise, not the SSO password.

---

### Post by sasuke83 on 2016-10-02
See screenshot of Ubuntu-software window.
[http://imageshack.com/a/img924/2549/7hH36d.png](http://imageshack.com/a/img924/2549/7hH36d.png)

Uhm... it asks me the SSO account info. (Sorry the screenshot is in italian)

---

### Post by ajgreeny on 2016-10-02
So it does!

As I said I do not use Ubuntu-software, as it is now called, so was not aware of this.  However, I note this is a non-libera package which means it is probably not in the normal Ubuntu repos and therefore has other authorisation requirements to synaptic or apt-get.

Is this a paid for package or is it still free of cost?

---

### Post by deadflowr on 2016-10-02
It's a snap package, which is why it asks for UbuntuOne.
Try installing it ala the snap command line:
```
sudo snap install telegram-sergiusens

```

---

### Post by ajgreeny on 2016-10-02
Ah!

I do not know anything about snap packages as I'm still using 14.04 where they are not available.

---

### Post by marcodasilva26 on 2016-10-03
Having the same exact issue can't download from "ubuntu software" because SSO is incorrect?!

---

### Post by sasuke83 on 2016-10-11
> **deadflowr said:**
> It's a snap package, which is why it asks for UbuntuOne.
Try installing it ala the snap command line:
```
sudo snap install telegram-sergiusens

```

Thanks!! From terminal works correctly. But... can be considered a bug?

---

### Post by oldsmobile_mike on 2016-10-11
Same problem here, can't sign into Ubuntu One through the app to download programs, keeps saying "incorrect email or password", even though I've reset it five times.  Looks like a bug!  :(

---

### Post by deadflowr on 2016-10-11
> **sasuke83 said:**
> Thanks!! From terminal works correctly. But... can be considered a bug?

Yep, and here it is:
[https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1616943]("https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1616943")
No need to comment unless you can actually add anything useful, just add yourself as being affected.

---

### Post by mlcasellas on 2016-10-12
Thank you for this solution!!! ;-) I had the same problem today installing krita 3.0.1.1 from the Software Center Xubuntu. Finally I got it from the terminal. And I suscribed to the Bug([https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1616943](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1616943)). Thanks again [COLOR=#000000]ajgreeny!!! :-) [/COLOR]

---

### Post by leorikzz on 2016-10-18
> **deadflowr said:**
> It's a snap package, which is why it asks for UbuntuOne.
Try installing it ala the snap command line:
```
sudo snap install telegram-sergiusens

```

thank you for solution :KS

---

### Post by runlevel0 on 2016-11-26
> **ajgreeny said:**
> You have obviously managed to login to the forum which uses the SSO password, so make sure you are using that password when asked for it in the SC

Well quite obviously yes... but AFAIK neither I nor the OP use his/her email as a password, right? 


I am rather very sure that the SC is _NOT_ asking me for my system password but for my email adress, but of course, I could be wrong though: 
English is not my first language and I may have misinterpreted some nuance in the way the expression "Email address:" is spelled.
;)

---

### Post by deadflowr on 2016-11-26
> **runlevel0 said:**
> Well quite obviously yes... but AFAIK neither I nor the OP use his/her email as a password, right? 


I am rather very sure that the SC is _NOT_ asking me for my system password but for my email adress, but of course, I could be wrong though: 
English is not my first language and I may have misinterpreted some nuance in the way the expression "Email address:" is spelled.
;)

The Ubuntu Software uses  the same account info used to login to this place: the forums. (Ubuntu Single Sign-on; SSO)
Of course nothing should stop someone from deciding to use the same email address as the password......
(except common sense)

Your English is fine, from the little I've read.
(Much better than some, even some for which English is their first language, including me)

---

### Post by gunkan on 2017-01-27
Same problem here, incorrect email or password... :( fresh ubuntu 16-10 install.  Tried to install VLC from Ubuntu Software and error.

---

### Post by howefield on 2017-01-27
> **gunkan said:**
> Same problem here, incorrect email or password... :( fresh ubuntu 16-10 install.  Tried to install VLC from Ubuntu Software and error.

Well, the answer is in the thread so read a little more...

Just in case you are inadvertently trying to install the "snap" package which does indeed need SSO credentials, there is another VLC package available, the traditional deb package which will install just fine from the Software Centre, the snap package will be described in the details section a "daily" so you will know which one is which or just install VLC from the terminal.

```
sudo apt install vlc
```

---

### Post by nwillo on 2017-03-06
I did the following to solve my problem of logging in Ubuntu Software Center:
1. Uninstall the software center
```

sudo apt purge gnome-software

```
2. Then run an update
```

sudo apt update

```
3. Reinstall Software Center
```

sudo apt install software-center

```

This did me the trick. My machine runs Ubuntu 16.10 dual boot along side Windows 10

---

### Post by howefield on 2017-03-06
> **nwillo said:**
> I did the following to solve my problem of logging in Ubuntu Software Center:

Shouldn't have to uninstall anything, applying normal updates should give you the fixes to sort out logging into Ubuntu Software application.

---


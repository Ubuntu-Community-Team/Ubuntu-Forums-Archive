---
title: "Mozilla FireFox And Yahoo!!"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by rutz on 2006-08-27
**hi ppl i m new to linux ....some probs in installing yahoo here is the error i get whem installing**


```
root@ubuntu:/home/rutwik # dpkg -i Desktop/ymessenger_1.0.4_1_i386.deb
(Reading database ... 58028 files and directories currently installed.)
Preparing to replace ymessenger 1.0.4-2 (using .../ymessenger_1.0.4_1_i386.deb) ...
Unpacking replacement ymessenger ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 ymessenger depends on libgtk1.2 (>= 1.2.0); however:
  Package libgtk1.2 is not installed.
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger
root@ubuntu:/home/rutwik #


```


while i wanted to install new firefox 1.5.6

here is the error 

```
root@ubuntu:/home/rutwik # cd /home/rutwik/Desktop/firefox-1.5.0.6
root@ubuntu:/home/rutwik/Desktop/firefox-1.5.0.6 # ./configure
bash: ./configure: No such file or directory
root@ubuntu:/home/rutwik/Desktop/firefox-1.5.0.6 # make
make: *** No targets specified and no makefile found.  Stop.
root@ubuntu:/home/rutwik/Desktop/firefox-1.5.0.6 # sudo checkinstall
sudo: checkinstall: command not found
root@ubuntu:/home/rutwik/Desktop/firefox-1.5.0.6 #

```


plzzz lemme know how to install it and if yahoo nad msn doesnot support ubunto](*,) lemme know any other sw to access ma accouts ...... and the steps of installation ......and also the problem with ma mozilla installation .....

and can i also know few sites where i can download aplication for ubuntu:-\" :-\" 

thanx in advance :D 


regrds,
rUTz!!

---

### Post by meng on 2006-08-27
Yahoo messenger for linux is extremely old (version 1, Windows version is several more) and I would recommend using gaim or some other multi-protocol client instead. Gaim is installed by default.

One wonders why you need Firefox 1.5.0.6, when updated Ubuntu comes with 1.5.0.5. What is missing from x.x.x.5 that is present in x.x.x.6?

---

### Post by gerbman on 2006-08-27
> **rutz said:**
> 
and can i also know few sites where i can download aplication for ubuntuI would recommend sticking to software listed by the package manager (System -> Administration -> Synaptic Package Manager) as much as possible. The problems you're having are caused by the fact that you're trying to install software without using the package manager, which is fine, but is usually more difficult. The Yahoo! and Firefox problems are both caused by missing supporting software - software that will be downloaded and installed automatically by Synaptic. If you need any help with Synaptic, just ask.

---

### Post by rutz on 2006-08-27
plzzzzz gimme help for watever itrequire to install apps in ubuntu........... specially yahoo and msn or optional client form which i can connect ot yahoo or msn .....(plz post the links of tat apps  ) and all ma downloaded apps r o the desktop the do not show up in manager ....................

---

### Post by rutz on 2006-08-27
> **meng said:**
> Yahoo messenger for linux is extremely old (version 1, Windows version is several more) and I would recommend using gaim or some other multi-protocol client instead. Gaim is installed by default.

One wonders why you need Firefox 1.5.0.6, when updated Ubuntu comes with 1.5.0.5. What is missing from x.x.x.5 that is present in x.x.x.6?

wher can i find this gaim ...............

how to install and run


i dunno anything m new as i told u ...............

---

### Post by tht00 on 2006-08-27
> **rutz said:**
> wher can i find this gaim ...............

how to install and run


i dunno anything m new as i told u ...............

It should already be installed.

Application -> Internet -> Gaim

---

### Post by tht00 on 2006-08-27
Also, you should probably read this:
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by rutz on 2006-08-27
> **tht00 said:**
> Also, you should probably read this:
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)


**as u can c i have given u all the errors it get and i have told u i m new to this enviornment ...so i have read all the documentation and then pooste ma errors .......**

---

### Post by gerbman on 2006-08-27
> **rutz said:**
> **as u can c i have given u all the errors it get and i have told u i m new to this enviornment ...so i have read all the documentation and then pooste ma errors .......**We've already pointed out clear solutions to your problems.

1) If you want to connect to Yahoo! and MSN networks, go to "Applications -> Internet -> GAIM Instant Messenger" - that program will handle both networks.

2) If you want to install software, go to "System -> Administration -> Synaptic Package Manager". Once Synaptic is open, you can search for software by clicking the "Search" button, and install software by clicking the box next to items you want to install, clicking "Mark for Installation", and then hitting the "Apply" button.

Software you download from the internet won't show up in Synaptic. I would recommend installing software you find in Synaptic until you're familiar with the environment (specifically the command line found at "Applications -> Accessories -> Terminal").

---


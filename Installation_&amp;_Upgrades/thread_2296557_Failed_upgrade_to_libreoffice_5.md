---
title: "Failed upgrade to libreoffice 5"
date: 2015-09-26
forum: Installation &amp; Upgrades
---

### Post by lesliek2 on 2015-09-26
I've been using libreoffice 4 with ubuntu 12.04 for a long time now.

I use libreoffice a lot, but encounter a very annoying problem when using it (the addition of extra spaces every time I re-open a document that I've earlier worked on), so I decided to try libreoffice 5, hoping that that would make the problem disappear.

However, attempting the upgrade has caused new problems.

I followed the instructions here: [http://www.webupd8.org/2015/08/install-libreoffice-50-in-ubuntu-or.html](http://www.webupd8.org/2015/08/install-libreoffice-50-in-ubuntu-or.html)

However, one package wouldn't install: python-uno.

I therefore decided to follow the instructions given at the above link to revert to libreoffice 4.

Those instructions haven't worked either. The message I got when I tried to revert was:

leslie@ubuntu:~$ sudo apt-get install ppa-purge
[sudo] password for leslie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 python-uno : Depends: libreoffice-core (= 1:4.0.4~rc2-0ubuntu1~precise1) but 1:5.0.2~rc2-0ubuntu1~precise2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
leslie@ubuntu:~$ sudo ppa-purge ppa:libreoffice/libreoffice-5-0
sudo: ppa-purge: command not found
leslie@ubuntu:~$ 

I'm not very technically skilled and just don't know what I should be doing now either to complete the installation of libreoffice 5 (my preferred course) or to revert to libreoffice 4.

I'd be very grateful for guidance.

Leslie

---

### Post by v3.xx on 2015-09-26
Try removing it with dpkg.
```
sudo dpkg -r libreoffice-5-0
```
then clean it up
```
sudo apt-get autoclean
sudo apt-get autoremove
```
also be sure it is not in your sources list
```
software-properties-gtk
```
then
```
sudo apt-get update && sudo apt-get upgrade
```
If you get any errors, please post.

---

### Post by claracc on 2015-09-27
Do you have ppa-purge software package installed?

---

### Post by Bucky Ball on 2015-09-27
The instructions for removing and reverting the changes are on the link you provided. So you're saying you did this?

```
sudo add-apt-repository ppa:libreoffice/libreoffice-5-0
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by lesliek2 on 2015-09-27
Thank you for your reply v3.xx.

As I said in my original post, my preferred option is to complete the installation of libreoffice 5, rather than revert to libreoffice 4, so I'd like to postpone trying what you suggest until I'm sure I can't complete the installation or, at least, use libreoffice 5 without completing it.

The output I posted above suggests that I do "apt-get -f install" to get installed the version of python-uno that libreoffice 5 wants, but I don't know whether that will work or, if it does, whether it will cause problems for other programs I now use that are relying on the version of python-uno I presently have installed. I think now that I should have said in my original post that, as far as I can tell, libreoffice 5 is working on my computer despite my not having installed the version of python-uno that libreoffice 5 wants.

Do I really need this new version of python-uno if libreoffice 5 is working? What does python-uno do?

Thanks again,

Leslie

---

### Post by lesliek2 on 2015-09-27
Thanks for your reply claracc.

As the output I originally posted shows, I tried to install ppa-purge, but that didn't work. My limited understanding of these things suggests to me that apt-get wants to solve the python-uno problem before it will install ppa-purge.

Thanks again,

Leslie

---

### Post by lesliek2 on 2015-09-27
Thanks for your reply Bucky Ball.

Yes, I did run the commands that you quoted. They resulted in my having installed all of the libreoffice 5 packages except the package for the version of python-uno that libreoffice 5 wants. As i mentioned above, libreoffice 5 seems to me to be working even without that package, which led me to ask the questions that I asked in my reply to v3.xx's post.

Thanks again,

Leslie

---

### Post by kurt18947 on 2015-09-28
Step one on every troubleshooting flowchart I'm familiar with has as its first step:

> Is it working? Don't mess (or something;)) with it

The first thing that pops up on a Google search:

[https://pypi.python.org/pypi/unotools](https://pypi.python.org/pypi/unotools)

Another option to install the missing package

[http://askubuntu.com/questions/418225/how-do-i-install-the-python-uno-package](http://askubuntu.com/questions/418225/how-do-i-install-the-python-uno-package)

---

### Post by lesliek2 on 2015-09-28
Thanks for your reply kurt18947.

I've been using the wordprocessing module of libreoffice 5 since my original post without any apparent problems, despite the lack of installation of the latest python-uno, so I think I'll just continue with it, as you suggest.

As I've mentioned before, I have an earlier version of python-uno installed: 1:4.0.4~rc2-0ubuntu1~precise1.

The one that isn't installing is: 1:5.0.2~rc2-0ubuntu1~precise2.

I'm assuming that I could delete the downloaded but uninstalled package in some way, so that it doesn't keep showing up in my update manager window. Maybe I'll try that and see what happens.

Thanks again,

Leslie

---

### Post by kurt18947 on 2015-09-28
You're welcome. I think - I'm no Libreoffice pro - that python can be used as a scripting language, something like VBA in MSOffice. I don't know if python has a role beyond that or not.

---


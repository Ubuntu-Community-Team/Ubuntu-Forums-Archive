---
title: "can't update"
date: 2013-01-25
forum: Installation &amp; Upgrades
---

### Post by tuxpenguin42 on 2013-01-25
I've been having a lot of problems with updates recently, and none of the fixes I've found seem to work. 

I get this:
[IMG]http://i.imgur.com/eEmgCNg.png[/IMG]

Using apt-get upgrade on the command line only installed some of the updates, and none of the other things I've found works. Changing the servers actually makes it worse, as some of the updates disappear. Running apt-get update doesn't show any missing keys.

I'm using Ubuntu 12.04, in case that makes a difference.

Thanks for any help.

---

### Post by slooksterpsv on 2013-01-25
[http://www.webupd8.org/2010/05/automatically-import-all-missing.html](http://www.webupd8.org/2010/05/automatically-import-all-missing.html)

I'd try that as I wonder if it's a GPG key error. This adds a repo and has you install a piece of software that gets the keys from the repos that you need.

---

### Post by tuxpenguin42 on 2013-01-25
> **slooksterpsv said:**
> [http://www.webupd8.org/2010/05/automatically-import-all-missing.html](http://www.webupd8.org/2010/05/automatically-import-all-missing.html)

I'd try that as I wonder if it's a GPG key error. This adds a repo and has you install a piece of software that gets the keys from the repos that you need.

After running that it says there are no missing keys, and I get the same error in the update manager.

---

### Post by arpanaut on 2013-01-25
If you trust the external repositories you have enabled, and you are not getting any errors from apt-get upgrade, just held packages, then you may need to run
```
sudo apt-get dist-upgrade
```
to get any upgrades that are new package versions in the repositories, before you accept the dist-upgrade pay close attention as to what the command says it is going to do. If it is going to remove a whole bunch of things cancel, and post the output from the terminal here.

---

### Post by tuxpenguin42 on 2013-01-25
> **arpanaut said:**
> If you trust the external repositories you have enabled, and you are not getting any errors from apt-get upgrade, just held packages, then you may need to run
```
sudo apt-get dist-upgrade
```to get any upgrades that are new package versions in the repositories, before you accept the dist-upgrade pay close attention as to what the command says it is going to do. If it is going to remove a whole bunch of things cancel, and post the output from the terminal here.

That worked, thanks so much!

---

### Post by arpanaut on 2013-01-25
YAY!

Upgrade manager and Software Center does at times have issues with third party repositories, so if you trust the repositories you have enabled then it is sometimes necessary to go to the terminal to get done what you want done, but as I said, be careful and pay attention to what the command's output is saying it is going to do. The terminal is a powerful tool, but it will do exactly what you tell it too, sometimes with undesired results.  Make sure you know what is going on before you use it.

---


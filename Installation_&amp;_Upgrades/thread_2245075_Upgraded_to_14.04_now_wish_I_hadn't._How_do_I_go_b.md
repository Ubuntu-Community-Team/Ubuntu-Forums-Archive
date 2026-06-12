---
title: "Upgraded to 14.04 now wish I hadn't. How do I go back?"
date: 2014-09-21
forum: Installation &amp; Upgrades
---

### Post by glennbates on 2014-09-21
How do I uninstall the upgrade and get back what I had? I think I upgraded to 14.04 but not sure.

---

### Post by sudodus on 2014-09-21
I'm sorry. There is no return from an upgrade to a newer version (for example 12.04 LTS to 14.04 LTS), except if you backed up your system before starting the upgrade process.

Can you read your important private data (documents, pictures, video clips, mail-box files etc)? Otherwise tell us and you can get help with methods to recover those data.

-o-

Updating and upgrading (accepting security updates and bugfixes etc) is highly recommended and a standard task to be performed more than once every week.

***Upgrading to a new version is a risky task, and should only be performed when there is a good and current backup*** of the system or at the very least of all your important private data.

---

### Post by grahammechanical on 2014-09-21
> [COLOR=#000000]I think I upgraded to 14.04 but not sure.[/COLOR]

doesn't the login screen tell you that you are logging into Ubuntu 14.04? What does About This Computer say?

---

### Post by glennbates on 2014-09-21
> **grahammechanical said:**
> doesn't the login screen tell you that you are logging into Ubuntu 14.04? What does About This Computer say?

If it does, I never see it.

---

### Post by ibjsb4 on 2014-09-21
```
lsb_release -a
```
Will tell you what your running.  If you find yourself on 14.04, like already stated, you can't go back unless you do a reinstall.  But you can install another desktop that may work better for you.
```
sudo apt-get install gnome-session-flashback
```
At the login screen, click on the icon and choose your desktop.

---

### Post by glennbates on 2014-09-25
> **ibjsb4 said:**
> ```
lsb_release -a
```
Will tell you what your running.  If you find yourself on 14.04, like already stated, you can't go back unless you do a reinstall.  But you can install another desktop that may work better for you.
```
sudo apt-get install gnome-session-flashback
```
At the login screen, click on the icon and choose your desktop.

Ubuntu 14.04.1 LTS

How do I install another desktop without deleting any of my installations?

---

### Post by ibjsb4 on 2014-09-25
> How do I install another desktop without deleting any of my installations? 
This will not delete any packages, but if you are referring to Unity packages they will not be usable in a flashback session.

[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)

---


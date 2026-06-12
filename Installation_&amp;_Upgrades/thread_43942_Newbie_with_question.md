---
title: "Newbie with question"
date: 2005-06-23
forum: Installation &amp; Upgrades
---

### Post by the_pc_dude on 2005-06-23
I don't mean to be an pain trying to learn ubuntu. I have  a prob when I installed ubuntu in expert mode some appz that require root pwd don't show up when executed but when I installed ubuntu default mode everything runs well. why does it do this?

---

### Post by mulino on 2005-06-24
Hi,

you can set the root's password using

-> sudo passwd root

To get a root shell use

-> sudo -s

You have to enter YOUR password when using sudo. There is one system administrator which can use sudo to become root. :-)

check the following out:
[http://ubuntuforums.org/showthread.php?t=42662&highlight=sudo+passwd+root](http://ubuntuforums.org/showthread.php?t=42662&highlight=sudo+passwd+root)

There are a lot threads about your topic. Just search the forum.. :-)

/mulino

---

### Post by the_pc_dude on 2005-06-24
no, when  I execute an app that requires an root pwd I type the root pwd in it will not do anything,give an warning,the window  bar for the app will be in the task bar   and ubuntu will search for  1-2 mins and the bar will disappear nothing no warning nothing. Sorry was clear on what I was saying. P.S This is only when I install in Expert Mode. Oh by the way Help! Please

---

### Post by mulino on 2005-06-24
.. does

$ sudo <root_app_name>

not work? You should be prompted a window asking for YOUR password, since you have to ue sudo.

/mulino

---

### Post by the_pc_dude on 2005-06-24
Hi, I tried what said in your other post it's not working I'm having sudo problems it says that I'm not in the sudoers file and also unable to pick up public/pickup directory

---


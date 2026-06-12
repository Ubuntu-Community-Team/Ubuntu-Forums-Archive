---
title: "couple of questions on a new install"
date: 2009-08-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kelean on 2009-08-02
I just installed 9.10 karmic Alpha3.  Most everything is running very well.  I was able to to get my winXP to show up in the grub2 at startup.  

How do I change the default timer from 10 seconds to something more?  I have not been able to find any thing.

When I start up and get to the desktop I am presented with a bow asking for my password.  It assumes I want to mount my win partition.  I do not, how do I turn this off?

What happened to the shut dowm button?  All I have is logout.

Thanks Kelean.

---

### Post by wayne_cat on 2009-08-02
> **kelean said:**
> I just installed 9.10 karmic Alpha3.  Most everything is running very well.  I was able to to get my winXP to show up in the grub2 at startup.  

How do I change the default timer from 10 seconds to something more?  I have not been able to find any thing.

When I start up and get to the desktop I am presented with a bow asking for my password.  It assumes I want to mount my win partition.  I do not, how do I turn this off?

What happened to the shut dowm button?  All I have is logout.

Thanks Kelean.

the "mount problem" ..

[https://bugs.edge.launchpad.net/ubuntu/+source/policykit-1-gnome/+bug/395122](https://bugs.edge.launchpad.net/ubuntu/+source/policykit-1-gnome/+bug/395122)

the grub2 configuration ...

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by Yofel on 2009-08-02
You can change the default timer for grub2 by modifying GRUB_TIMEOUT in /etc/default/grub.

The automount of your partition is known as bug [396448]("https://bugs.launchpad.net/bugs/396448")

I don't know what happend to your shutdown button though, I still have mine. You could use 'sudo halt' in a terminal as a workaround until somebody else knows more.

---

### Post by kelean on 2009-08-02
Thank you everyone for the information.  Default timeout reset.  Thanks for the link to the grub2 wiki page.  I had looked at that but did not read down far enough.  I read the bug reports,  I found my shut down button.  I forgot to look under System.  I was use to having the shut down button on the User Switch Applet.

Thanks again for the help and info.  Kelean.

---

### Post by wayne_cat on 2009-08-02
> **kelean said:**
> Thank you everyone for the information.  Default timeout reset.  Thanks for the link to the grub2 wiki page.  I had looked at that but did not read down far enough.  I read the bug reports,  I found my shut down button.  I forgot to look under System.  I was use to having the shut down button on the User Switch Applet.

Thanks again for the help and info.  Kelean.

one thing that the most people forget at the moment. You have to run the command
"update-grub" after editing /etc/default/grub to install the new grub configration

---

### Post by kelean on 2009-08-02
I did but I went back and read more on the wiki and figured it out.

---

### Post by ranch hand on 2009-08-02
> **kelean said:**
> Thank you everyone for the information.  Default timeout reset.  Thanks for the link to the grub2 wiki page.  I had looked at that but did not read down far enough.  I read the bug reports,  I found my shut down button.  I forgot to look under System.  I was use to having the shut down button on the User Switch Applet.

Thanks again for the help and info.  Kelean.
You can right click on your panel and "add" "shut down".  I put it near the user applet.

i assume this will be fixed, we are in the time when things should start to come together.

---


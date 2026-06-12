---
title: "Reinstalling doesn't fix problems - why?"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by tjk on 2007-05-02
I had a lot of problems that I wanted to correct, so I decided that reinstalling K/X/ubuntu would correct the situation.  However nothing changed.

I have a separate partition for my home directory and this data was preserved when I reinstalled.  As a result I believe that all my problems are stored somehow in the home directory, but I have no idea where or what I should do to correct the problem.

Here are some of my problems:
 - in Xubuntu, after I login I just get the wallpaper and a cursor nothing else...
 - in Gnome, I cannot change the themes, and if I do the system crashes until it is reset to the default human theme
- in Kubuntu, (my default session) my biggest concern (among many) is that I cannot use any of the various sync packages for my palm pilot

Any ideas on what I need to delete / correct in my home directory to fix these problems?

---

### Post by Rospo Zoppo on 2007-05-02
It's just an idea, but what about trying a fresh installation with a new home and seeing if the problems persist? If you fix this way, you know for sure where is the problem.. Sorry my terrible english.. :)

---

### Post by tjk on 2007-05-02
> **Rospo Zoppo said:**
> It's just an idea, but what about trying a fresh installation with a new home and seeing if the problems persist? If you fix this way, you know for sure where is the problem.. Sorry my terrible english.. :)

I'm somewhat hesitant to do this since it already takes me days to reinstall all the packages that I use, and it would be a lot more of a hassle if I lost all my settings and preferences that are contained in the home directory.  And in addition I would have to go through and determine what is critical data that I need to preserve and what isn't.

However, I will do this test as a last resort.

---

### Post by ajgreeny on 2007-05-02
What about adding a new user, even if only temporary, to check if it is something in your current home partition.  If the problems still persist at least you now know where the culprit is.  Al you now need to do is find it in detail.

---

### Post by dannyboy79 on 2007-05-02
these are not unsolvable problems. the xubuntu problem has to do with letting Xfce-desktop control your dekstop and then your icons will show up.

the gnome themes i'd have to investigate but  it shounds like you have a corrupt theme stored somewhere it is suppose to retrieve the themes from

and kubuntu not syncing with palm pilot, I have used used gpilot and it did work with  my Treo 600. but I hear Kpilot is just as good.

here's a good guide:

[http://www.faqs.org/docs/Linux-HOWTO/PalmOS-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/PalmOS-HOWTO.html)

---

### Post by tjk on 2007-05-02
> **ajgreeny said:**
> What about adding a new user, even if only temporary, to check if it is something in your current home partition.  If the problems still persist at least you now know where the culprit is.  Al you now need to do is find it in detail.

I hadn´t thought of this option.  I set up a new user and everything is working (except my palm syncro).  I even have sound/video !!!!!!  :)  :)  :)   

 I just really hate the idea of reconfiguring all my settings... uggg!!  :(   If anyone can suggest a way to import preferences to a new user that would be great...

---

### Post by tjk on 2007-05-02
> **dannyboy79 said:**
> 
and kubuntu not syncing with palm pilot, I have used used gpilot and it did work with  my Treo 600. but I hear Kpilot is just as good.

here's a good guide:
    [http://www.faqs.org/docs/Linux-HOWTO/PalmOS-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/PalmOS-HOWTO.html)

Thanks for the guide, I will check it out.  

As per my previous message: all my other major problems were solved by creating a new user (except I don´t like the idea of reconfiguring all my preferences)

---

### Post by dannyboy79 on 2007-05-03
> **tjk said:**
> Thanks for the guide, I will check it out.  

As per my previous message: all my other major problems were solved by creating a new user (except I don´t like the idea of reconfiguring all my preferences)


you could always copy folders from your old users home dir to the new users 1 at a time and hten restart the machine. if something stops working (sound or whatever) than you know that that was the offending folder/program and then simply undo that copying of the folder. then restart and the problem should disappear, then move onto the next folder until you've transferred over most of the folders and files that don't cause problems. Then which ever folder's caused errors, you'll only need to reconfigure those settings which caused the failures. The hidden folders most always have the name of the program so you'll kno what program's you'll need to reconfigure. good luck

---

### Post by ajgreeny on 2007-05-03
Don't forget that by default the new user will not have admin group permissions unless you add them for that user.  By default only the first user can have sudo rights, all others have to be given them by the first user who can sudo.

---

### Post by dannyboy79 on 2007-05-03
you can find out by typing imn 

groups

when you're logged in as your new user and if admin isn't there, than you would add it with 

sudo usermod -G admin username . 

That's all there is to it. However, if the user is already a member of other groups, you'll want to add the -a option, like so: 

sudo usermod -a -G admin username .

---


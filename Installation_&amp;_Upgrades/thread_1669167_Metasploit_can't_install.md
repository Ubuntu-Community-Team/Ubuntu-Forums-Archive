---
title: "Metasploit can't install"
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by Kondry on 2011-01-17
Hello everyone, I am having some problems installing Metasploit, I followed many tutorials, I have all the stuff needed to install it, but when I come to install it, it asks me for a port for my DataBase.. but when I try and db_connect with postgres, it says that the command is not found.

So I try using an open port anyways, IE port 80, and a few other ones that I have open that are not in use [82 , 6669 , etc]

But everytime I just get this message
[IMG]http://i.min.us/iemvwm.png[/IMG]

As you can tell from this post, I'm not great with Linux, so I did try one other thing, probably very stupid, but whatever, I tried running VNC on ports to see if it could sub for a DB, obviously not lol.

Can anyone please help me install this? I really need it to test out the penetration levels of my website.

---

### Post by dino99 on 2011-01-17
[http://www.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu](http://www.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu)

maybe you can try w3af from synaptic

---

### Post by Kondry on 2011-01-17
> **dino99 said:**
> [http://www.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu](http://www.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu)

maybe you can try w3af from synaptic
Thats the guide I have been following.

---

### Post by reqqq on 2011-03-27
_you have to follow & try things _as i did lots of times & worked the way i want 
the last time i installed it as i remember i started from [http://ubuntuforums.org/archive/index.php/t-1000698.html ]("http://ubuntuforums.org/archive/index.php/t-1000698.html")

i did not installed ruby from the instructions above but from [http://www.youtube.com/watch?v=NmWYZVUln4E](http://www.youtube.com/watch?v=NmWYZVUln4E)

then follow the steps from [http://www.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu](http://www.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu)
dont forget to install subversion 

then while installin the dependencies verify from the generic linux installation way that all were build as they have to do etc that ruby can load rubygems 

& then install framework as the above link says 
check if you can load console as instructions say 

then finally install postgress 

there are more ways maybe easier but i dont know if you can make it work 
for my personal network works fine

hope helped a little bit

---

### Post by reqqq on 2011-03-27
> **Kondry said:**
> Hello everyone, I am having some problems installing Metasploit, I followed many tutorials, I have all the stuff needed to install it, but when I come to install it, it asks me for a port for my DataBase.. but when I try and db_connect with postgres, it says that the command is not found.

So I try using an open port anyways, IE port 80, and a few other ones that I have open that are not in use [82 , 6669 , etc]

But everytime I just get this message
[IMG]http://i.min.us/iemvwm.png[/IMG]

As you can tell from this post, I'm not great with Linux, so I did try one other thing, probably very stupid, but whatever, I tried running VNC on ports to see if it could sub for a DB, obviously not lol.

Can anyone please help me install this? I really need it to test out the penetration levels of my website.

that error just says to install postgress first as i remember trying this way installing framework & then install framework with binary installer

ps why u need metasploit for your website you can try w3af as dino99 says !!!!

---

### Post by abdellatef1 on 2011-03-27
my friend is very aesy
me is great this tutorial 
install metasploit on ubuntu 
very easy 
[http://www.aljyyosh.com/vb/showthread.php?t=24744&page=1]("http://www.aljyyosh.com/vb/showthread.php?t=24744&page=1")

good luck 
allah akbar

---


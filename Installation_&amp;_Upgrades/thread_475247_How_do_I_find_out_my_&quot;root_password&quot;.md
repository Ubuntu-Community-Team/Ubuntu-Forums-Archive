---
title: "How do I find out my &quot;root password&quot;?"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by Chappy7777 on 2007-06-15
I am trying to install Limewire using Gdeb, and the package installer is asking me for my root password. (I am using 6.06LTS) When I 1st installed the OS, it never asked for a root password. I was under the impression that root and admin password were the same. Obviously not, as my Admin PW works fine when asked for it (Login, Synaptic, etc), but I don't have a root password. Is there a way for a NooB to create one at this point (2 mos or so after installing 6.06)?  

I don't understand why 6.06 never asked for a separate password for a root account. For one thing I never created a root account. I did not know it was needed. Some poor explaining by the author of the book that helped me get this going. He writes "If you have experience with other Linux distroes, you may be surprised to learn that the root account is disabled by default in Ubuntu. There is therefore no installation step for inputting a root password."

He does go on to say that "you can set up a root password later at any time after the system is installed, so if having a root account is important to you, don't worry."

So I may have messed up, but I had some help. How do I get a root password so I can open Limewire (or maybe Frostwire)? 

Do I need a root account for other stuff? Likely, I assume the root account allows one to get deeper into the OS and hence it's being off by default. That seems like a MS kinda move to me.

Anyhow, please help amd explain in as simple terms as is humanly possible. Pretend I am your great grandmother w/memory problems. :)

---

### Post by Chappy7777 on 2007-06-15
I just opened System/Administration/Users and Groups. I saw, when I clicked on "show all groups", that Root popped up in the left hand column. I am thinking if I highlighted it and clicked add, I might end up where I need to be to add a Root Group, which would need a password. 

Can it be that simple? I am not about to try messing around with something I know nothing about. If I had just installed and setup this OS, I wouldn't care, but I have spent too much time getting it together to want to toast it now.

---

### Post by davefields on 2007-06-15
Ubuntu does not have a root password by default.
 Open up a terminal (accessories - terminal)  and then enter

sudo passwd root

then enter your new root password.

You will then have root access.

Hope this helps..............

---

### Post by Bachstelze on 2007-06-15
You do not have a root password and, despite what other might tell you, do not need one.

---

### Post by Chappy7777 on 2007-06-15
> **davefields said:**
> Ubuntu does not have a root password by default.
 Open up a terminal (accessories - terminal)  and then enter

sudo passwd root

then enter your new root password.

You will then have root access.

Hope this helps..............
=============================================
Dave, I tried what you suggested. I got as far as seeing PASSWORD: blinking cursor after typing what you said. But when I tried to type a password in to the right of PASSWORD, nothing happened except "sorry, try again".

Should I wait for the bold cursor to stop blinking? What can I be doing wrong? What you showed me is eimple enough. But it didn't work. I am using 6.06LTS if that matters, which I doubt.

I know I don't need the root password to run this OS, but I do if I want to get Limewire or Frostwire working. And I do,

Thnx, more ideas?

---

### Post by davefields on 2007-06-15
When a program asks for a password and you just hit "enter", the program will close without any mention of a reason. If you are God,Jesus ,Mohammed, or Jack Daniels, it may work for you.
 If not, I would suggest creating your own root password using the steps mentioned above.

---

### Post by smartboyathome on 2007-06-16
> **Chappy7777 said:**
> =============================================
Dave, I tried what you suggested. I got as far as seeing PASSWORD: blinking cursor after typing what you said. But when I tried to type a password in to the right of PASSWORD, nothing happened except "sorry, try again".

Should I wait for the bold cursor to stop blinking? What can I be doing wrong? What you showed me is eimple enough. But it didn't work. I am using 6.06LTS if that matters, which I doubt.

I know I don't need the root password to run this OS, but I do if I want to get Limewire or Frostwire working. And I do,

Thnx, more ideas?


Whenever you type sudo, there is a password field that comes up and it asks you for your DEFAULT password. So that "password" field you tried to type your new password into is actually for your user password. Just run the command again, except using your user password for the first password, and THEN setting the root password.

---

### Post by davefields on 2007-06-16
Sorry for replying so soon...

Does this not work for you.....


sudo passwd root

enter new password

enter new password again

new password created

then in a terminal type su -

enter root password
and you will have root access providing you are working in that terminal.



(please disregard my last post if it offends you...)

---

### Post by smartboyathome on 2007-06-16
You must have typed sudo before. Sudo only brings up the new password IF you have used sudo during the same terminal session. This is why I like su - better ;)

---

### Post by Chappy7777 on 2007-06-16
Dave, I was not offended. I have been married 3 times, so I no longer offend easily. :)

When I first read your response I didn't understand it, and wondered why you sounded so mad. Then I read it again and realized what you were saying. So, no hard feelings.

I am a little confused here. It sorta sounds like I am getting 2 different answers. Yours and Sitathomes. 

I am going to go with typing what I did, but when asked for password put in my admin password, then expect to see another "enter new password" (or something close) pop up and fill it in. 

If that doesn't work I'll try the su- method. One or the other should work.

of course, if I do get a root password, I will still need to figure out how to get Limewire or Frostwire open and working. I have both downloaded. After reading a few posts in here, it kind of scares me. Well, 1 step at a time.

---

### Post by bapoumba on 2007-06-16
Please read: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo").
There are actually very little cases where you need to enable the root account, please use sudo/gksudo (CLI/GUI) instead.

---

### Post by Bachstelze on 2007-06-16
> **bapoumba said:**
> There are actually very little cases where you need to enable the root account, please use sudo/gksudo (CLI/GUI) instead.

And if you spot one, you should report it as a major bug, since Ubuntu's policy is to never use a root password.

---


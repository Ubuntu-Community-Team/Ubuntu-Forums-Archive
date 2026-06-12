---
title: "kde programs like amarok and k3b in ubuntu 6.10"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by wxnker on 2007-01-21
I'm a pretty new ubuntu user, but I like it a lot so I'm not that interested in installing the kubuntu-desktop to run a couple of kde programs like amarok and k3b. To be honest I tried installing kubuntu-desktop but I got an kstartupconfig error and could not solve it. :-\" 

So I tried installing **k3b** and **amarok** in ubuntu 6.10 but they do not work.

_**K3B:**_
I used the following install method.
[COLOR="Red"]sudo aptitude update
sudo aptitude install k3b[/COLOR]

k3b does not start at all. No error message - Nothing happens.
What could be wrong? Do I need to install some kde package in ubuntu to make kde programs run?

_**AMAROK:**_
I installed amarok with the synaptic package manager.

When trying to run amarok I get error messages:

(a) There was an error setting up inter-process communications for KDE. The message returned by the system was:

Could not read network connection list
/home/ppp/.DCOPserver_PPP-desktop__0

Please check that the "dcopserver" program is running!

(b)Malformed URL
file:///

After this the wizard starts up and when I'm done I get error (a) again and another error:

amarok could not find any sound-engine plugins. amarok is now updating the KDE configuration ... etc.

It suggests that amarok is installed under the wrong prefix.

I.m lost and I have searched the forum for a solution to my problems. I'm a newbie though and I do not have any experience with KDE.

I've read in these forums that kde programs like k3b should work in gnome/ubuntu 6.10 but they do not in my system. What is wrong? What do I need to setup to make KDE programs work in gnome? 

Be gentle and help this newbie (in learning mode) :biggrin: 

wxnker

---

### Post by wxnker on 2007-01-21
This solved the problem:

$ sudo chown -R myusername:myusername /home/myusername/.*

I finally found a solution in this forum. I don't have any clue what this fix is about though, but it works. :biggrin: 

I solved the k3b issue by installing "GRAVEMAN" and it's the best burner-solution for gnome I've seen yet. So for now I do not need K3B. 

wxnker

---

### Post by JamieC on 2007-01-21
It gives you ownership permissions on your home directory. Thanks for posting the solution for others. I'm glad you've got it working.

---

### Post by wxnker on 2007-01-21
Oh I see. Thanks for the info.

BTW how do I mark this thread as resolved? I've seen post with a [resolved] mark at the end. Is this done by changing the headline? Should I do this?

I feel kinda goofy for asking, but I cannot see this option anywhere. Well perhaps I just am... :lolflag:

---

### Post by Bheegerji on 2007-12-15
> $ sudo chown -R myusername:myusername /home/myusername/.*

It didn't solve my problem with Amarok. Instead, it created a new one.
I have two user accounts in my Ubuntu. After executing that command I'm not able to access my secondary account. How do I reverse the command?

---


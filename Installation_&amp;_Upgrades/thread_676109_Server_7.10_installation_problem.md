---
title: "Server 7.10 installation problem"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by ulfja on 2008-01-23
Hi

I am totaly new to this and i have tried to install server 7.10 severel times.
after removing cd when i am told to and restart the computer am i have to log on in a text based enviroment. After the log on i get this line up on the screen,  ulf@ulfja:~$

What am i supposed to write to get the program started?

Ulf :-)

---

### Post by mikewhatever on 2008-01-23
> **ulfja said:**
> Hi

I am totaly new to this and i have tried to install server 7.10 severel times.
after removing cd when i am told to and restart the computer am i have to log on in a text based enviroment. After the log on i get this line up on the screen,  ulf@ulfja:~$

What am i supposed to write to get the program started?

Ulf :-)

The last line is a command prompt. You can type commands you need, not quite sure what you want to start though. Here is some info on setting up Ubuntu server:
[http://www.google.co.il/search?q=ubuntu+perfect+server&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.il/search?q=ubuntu+perfect+server&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=server&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=server&titlesearch=Titles)

If you want a GUI, look here [https://help.ubuntu.com/community/ServerGUI?highlight=%28server%29](https://help.ubuntu.com/community/ServerGUI?highlight=%28server%29)

---

### Post by tehet on 2008-01-23
Apparently it installed ok. Now what do you want to do with the server? You might want to install and configure some of the following:
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[https://help.ubuntu.com/community/ProFTPD?action=show&redirect=ProFTP](https://help.ubuntu.com/community/ProFTPD?action=show&redirect=ProFTP)
[https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide)

---

### Post by ulfja on 2008-01-23
Hi,

Thanks for your answers. I thought that when the installation comes to the point where I am prompted to remove the cd I was done and then able to start the server program. Like in an O/S. I was hoping to do so and then continue to connect my hard drives and Internet connection as well as my two laptops to it.

But, it seems like I have missed a few things here. Is there a lot left to do before I am done?

Regards,
 Ulf

---

### Post by ulfja on 2008-01-23
How can i find and see what i want to install. I have only the server computer here now and i cant figure out how to install anything after i have enabled the root acount. 

[http://www.howtoforge.com/perfect_server_ubuntu7.10_p3](http://www.howtoforge.com/perfect_server_ubuntu7.10_p3)

This is the user manual i am following

Ulf

---

### Post by Lostincyberspace on 2008-01-23
I think Yoiu might want to install regular ubuntu not the server. REgular ubuntu has a Graphic User Interface. Ther is no specific server program, because a server is computer that gives out information to other computers. THere are also programs that run on servers like Apache for webpages, MYSQL for databeses, I hope we are getting you pointed in the right direction.

---

### Post by ulfja on 2008-01-23
I really think i have been totally lost, what i need it to is this.

I want to hava a "server" option so i can connect all the laptops in the house to the same network. 

I want the server to have the internet connection

I want to connect both mac and Windows.

I want several different usb hard drives to be connected to the server for backup and for storing music and movies.

Is this something that is possible with one or more Linux solutions?

Regards Ulf :-)

---

### Post by Lostincyberspace on 2008-01-23
Possible yes very possible I have done it my self before, easy quick no way on earth or in heaven. I took me over a month to get it set up right since it requires setting up virtualmachines and you need a bunch off networkcards if you are going to use it as a router. you could set up a firewall box It would be a lot easier and could most of the differnt things you need

---

### Post by ulfja on 2008-01-23
Tusen takk for your answer :-)

Mow it is time to find out about this "firewall box. Complicated solutions are not fun, it takes to much time.

Thamks again, Ulf

---

### Post by Lostincyberspace on 2008-01-23
for fire wall you could use monowall or smoothwall smooth wall I think has a better gui both you acces through a web interface after some minor command line things so it shouldn't be to hard and there is pretty good documentation on the main sites.

---

### Post by ulfja on 2008-01-23
I will try to download Smoothwall and install it on my machine. Maybe it is exactly what i need :-)

Ulf

---


---
title: "Questions about installing Ubuntu on a server"
date: 2012-08-23
forum: Installation &amp; Upgrades
---

### Post by Jasongtelford on 2012-08-23
Hi there

I seen on the Ubuntu website that there is a server edition. This is good because I wan to install Ubuntu on a server:  specifically this server, "Dell 2950 Twin Quad Core 2.66Ghz 16GB RAM SATA/SAS RAID PowerEdge Server VMware". 

However I have three questions that I could not find the answers to. 

-----

1:  can I install Ubuntu on to my server, create user accounts and then have my client machines connect to the server so the users can login without needing Ubuntu installed on each individual machine. 

This is basically what the idea of a server is, but all the stuff ive read talks about web servers, which isn't what I want. 

2:  will I be able to install Ubuntu onto the server listed above.  The lists of servers I saw did not include mine.  

3:  can I allow my users to access their desktops via the Internet (like a virtual enviroment). 

I did this at university with UNIX. Basically, I went to the university website, logged into my student area and then clicked on the link. A login box asked me to login to UNIX and then it loaded a virtual desktop in full screen mode.  I then had access to all the program's and files and I was able to interact with the enviroment as though it was a traditional desktop (just accessed via. Web-browser using a java applet). 

Can I do this with ubuntu so my users can login to their user accounts from any machine by using a java enabled browser, such as google chrome or Mozilla Firefox? 

----

I think that's it for now, ii hope someone can assist me and thank so much.

---

### Post by mastablasta on 2012-08-24
you should put this into server section of forums.
 
otherwise, yes i believe you can do that. i read about it somehwere (though i am not sure where and i amnot sure if it was Ubuntu's parent Debian or Ubuntu itself.

---

### Post by Jasongtelford on 2012-08-24
> **mastablasta said:**
> you should put this into server section of forums.
 
otherwise, yes i believe you can do that. i read about it somehwere (though i am not sure where and i amnot sure if it was Ubuntu's parent Debian or Ubuntu itself.

Hi , 

Thanks ... I will repost it into the server forum. Thanks also for your response.

---

### Post by darkod on 2012-08-24
I wouldn't say that the idea of a server exactly. The idea of a server is to provide services, like web server, database, file server, etc.

You say without having ubuntu on each machine. What exactly do you mean? Any machine needs to have an OS to actually be able to work. If you question is whether that OS needs to be ubuntu, no, it doesn't. But an OS will need to exist.

What the users will or will not be able to do depends on what will you configure on the server. I have not done anything similar to what you need, so I don't know much to help, but I am sure someone else will.

As for installing the server version on the specified model, usually it covers a great number of servers. Even if your server is not specifically mentioned, 99% it would install OK. For example, I have installed server 10.04 LTS on DELL PowerEdge 850 without any issues. (I used 10.04 because 12.04 was not released yet).

---


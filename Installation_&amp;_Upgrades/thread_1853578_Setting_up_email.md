---
title: "Setting up email"
date: 2011-10-02
forum: Installation &amp; Upgrades
---

### Post by computerfox on 2011-10-02
Hello everyone,

I have one last step to learn how to host multiple domains-email.  I can already host and maintain files for multiple domains, but I'm having tons of trouble setting up the emails, maybe I just don't completely understand it.

My set up-I have Dovecot for incoming, which is set up at the moment to accept imap.  I would like to make sure I set this up correctly

For smtp, I'm trying to use postfix, but I can't get it to send out email.

I set up an MX with my dns, so I'm certain there's something wrong with my configuration.  Again, I've never set up a mail server and would like help.  Any suggestions would be appreciated.  Thank you.

---

### Post by computerfox on 2011-10-02
anyone?

---

### Post by computerfox on 2011-10-02
some more information of my system to help give me a straight answer-i have ubuntu 6 and i administer my system mostly via webmin.  also, it's a ppc. any ideas?

---

### Post by hansdown on 2011-10-02
Hi computerfox.

Are you running 6.06?

You may have better luck, with a newer version.

10.04 is rock solid, and it has support until 2013.

---

### Post by computerfox on 2011-10-02
Correct.  And agreed.  I actually do have a copy of 11, but my server is an old G3 PowerMac PPC, so I can not install 11 on that.  So far whatever I researched, it tells me I need some packages, primarily SASL, which I think I managed to install.  I'm actually trying to configure it right now, but I just want to make sure I follow the correct steps to setting my mail up on 6.  I had somewhat of a success with 10 in the past, but right now I'm stuck with 6.  Any ideas?

---

### Post by hansdown on 2011-10-02
Sorry, I should have asked, if you are using the server edition.

This is the 11.04 server download.

Choose the 64bit download.

[http://www.ubuntugeek.com/step-by-step-ubuntu-11-04-natty-lamp-server-setup.html](http://www.ubuntugeek.com/step-by-step-ubuntu-11-04-natty-lamp-server-setup.html)

---

### Post by computerfox on 2011-10-02
:shock: Can you reread my post please....  #-o

---

### Post by hansdown on 2011-10-02
```
, but I just want to make sure I follow the correct steps to setting my mail up on 6.
```

[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

Please be advised, that 6.06 server, reached end of life in june, 2011.

This means; no more updates.

---

### Post by computerfox on 2011-10-03
okay, so i upgraded a new computer to ubuntu 11 and now all of my domains are messed up.

they all point to the same virtual host.

list of virtual hosts:

default
default
foxwebhosting.dyndns.org
foxwebhosting2.dyndns.org
dox2dox.com
computerfoxdesign.net

they all point to computerfoxdesign.net

i have the config files separately in sites-available and sites-enabled.  

i remember having this issue a while back, but completely forgot how i fixed it.  any ideas?

---

### Post by computerfox on 2011-10-03
nevermind.  got it by doing this: [http://ubuntuforums.org/showthread.php?t=1057960](http://ubuntuforums.org/showthread.php?t=1057960)

---

### Post by Bucky Ball on 2011-10-03
Long-term support releases recommended for servers. ;)

---

### Post by computerfox on 2011-10-03
agreed!

okay, so now i have everything back up (stupid problem), now i need to start working on the reason i chose to go through this pain-mail.  i'm trying to setup mail for multiple domains (obviously) and in the picture is what i have so far.  please explain how i can go about fixing this.  if i can learn how to do this, i think for the most part i learned the basics of servers and would enable me to continue learning about networks.

i've tried sending a message to myself, but i believe it failed, even though it isn't listed in the queue for mail.

any ideas or suggestions?

---

### Post by computerfox on 2011-10-04
Some more information on my setup- I have my dns setup with zonomi. Would I also have to create a zone and add the mx record or is that step already done if I have an mx with zonomi?

---


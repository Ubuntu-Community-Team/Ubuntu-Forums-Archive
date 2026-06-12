---
title: "How to access https apt repository with basic authentication?"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by mountainshows on 2008-05-22
I have created an apt repository for a custom application, which works fine without configuring authentication on the http server.

I would like to set up the server to use basic authentication, but I do not know how to configure apt-get so that it will provide a username and password when querying that one server.

Which config file (apt-file.conf?, apt.conf.d/*) should be modified, and how do you specify the login parameters for the https server? 

This is for both hardy and gutsy releases.

thanks!

Ryan

---

### Post by jillmashley on 2008-07-30
I too am wondering if there is a way to implement client authentication with apt against a specific repository I have created. 
Did you happen to figure out how to do this?

Any help is appreciated!

---

### Post by jillmashley on 2008-08-19
The way I wound up implementing client authentication was to set up an ssh connection to the server, rather than using https. Within ssh I implemented protocol 2, HostBasedAuthentication. I turned *off* password authentication and used PubKeyAuthentication only in my sshd_config on the server. This had the desired effect for me of providing a way to not only authenticate the server, but the clients as well. Don't know if it will be useful to you. 
Thanks!

---


---
title: "i cant install framework-3.1"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by markomk on 2008-10-17
hey i just install ubuntu and i need help to install framework.i never work with linux before :S but i liked now :) so when i try to start framework this show me:

 --->ruby msfconsole

./lib/rex/socket/ssl_tcp_server.rb:4:in `require': no such file to load -- openssl (LoadError)
	from ./lib/rex/socket/ssl_tcp_server.rb:4
	from ./lib/rex/socket/comm/local.rb:5:in `require'
	from ./lib/rex/socket/comm/local.rb:5
	from ./lib/rex/socket.rb:22:in `require'
	from ./lib/rex/socket.rb:22
	from ./lib/rex.rb:71:in `require'
	from ./lib/rex.rb:71
	from msfconsole:10:in `require'
	from msfconsole:10

any solution? :)
tnx

---

### Post by Partyboi2 on 2008-10-17
Have you got the libopenssl-ruby package installed?
You can install it with
```
sudo apt-get install libopenssl-ruby 
```

---

### Post by markomk on 2008-10-19
> **Partyboi2 said:**
> Have you got the libopenssl-ruby package installed?
You can install it with
```
sudo apt-get install libopenssl-ruby 
```

Well i installed libopenssl-ruby and its ok now :) tnx friend\\:D/

---


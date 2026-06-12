---
title: "Stuck on an upgrade error"
date: 2006-12-31
forum: Installation &amp; Upgrades
---

### Post by slugkilla on 2006-12-31
I was upgrading from Dapper to Edgy and recived many errors and it crashed. I typed in gksu "update-manager -c" again and it gave me the message

 "Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

So I issued this comand only to get another error 

"dpkg: error processing spring-basedata (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 spring-basedata
E: Sub-process /usr/bin/dpkg returned an error code (1)"

Well this is not looking good! I'm not sure if i need this spring thing. How do i fix all of this??
Thanks

---

### Post by slugkilla on 2006-12-31
Spring is some game that I don't want at all. I can't remove it before it tells me to "sudo apt-get install -f" but that woun't work because of spring. I'm only halfway done with the upgrade and I really need a stable system. Any advise would be great. thanks

---

### Post by riven0 on 2006-12-31
> **slugkilla said:**
> Spring is some game that I don't want at all. I can't remove it before it tells me to "sudo apt-get install -f" but that woun't work because of spring. I'm only halfway done with the upgrade and I really need a stable system. Any advise would be great. thanks

Usually with dependency problems, if nothing else works I do it the hard way:

> sudo updatedb

> locate *whatever_offending_program*

Then I manually delete all the entries with **sudo rm -r /path/offending_program** and that always works.

But, before you try something like that, have you done?:
> 
sudo apt-get -f remove

---

### Post by slugkilla on 2006-12-31
Well it's not complaining about spring after i did that! Thanks a lot. After it finishes fixing everything I'll see if the upgrade works. Thanks again.

Edit: Thanks again, everything is great. Tons of programs that i didn't use are now gone from my comp. Strange but I can put the ones I like back.

---


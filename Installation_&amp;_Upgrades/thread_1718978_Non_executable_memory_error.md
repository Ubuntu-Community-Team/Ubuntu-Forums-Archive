---
title: "Non executable memory error"
date: 2011-04-01
forum: Installation &amp; Upgrades
---

### Post by Manic_Aardvark on 2011-04-01
[FONT=Arial][SIZE=2]Hi forum, I'm new to Ubuntu so be gentle, I have decided to load the OS on a old HP Compaq DX2000 MT to see if its for me before putting it on my main machine.

I loaded Ubuntu version 10.10 last night everything was fine except I could not get my wireless adapter to work, I decided to connect via ethernet to get the latest updates and drivers.

After the updates and restart I now get the non executable memory error. when I enter [/SIZE][/FONT]
/usr/bin/check-bios-nx --verbose

[FONT=Arial][SIZE=2] I am told I have NX capabilities and should go to the bios and enable it. There is nothing in
the bios to enable as far as I can see. So I enter the command 

 [/SIZE][/FONT]sudo rm /etc/update-motd.d/20-cpu-checker[FONT=Arial][SIZE=2] 

I get a return stating command not found, what am I doing wrong ?

:confused:
 

[/SIZE][/FONT] [SIZE=3]
[/SIZE]

---

### Post by Manic_Aardvark on 2011-04-01
Here's a thought in the copied command : sudo rm /etc/update-motd.d/20-cpu-checker
should the forward slashes be back slashes ?

:(
[FONT=Arial][SIZE=2] [/SIZE][/FONT]

---

### Post by mörgæs on 2011-04-01
No, you are writing it correctly. Backslashes are only used in an inferior operative system.

Have you tried running a full memory test on the machine?

---

### Post by Manic_Aardvark on 2011-04-01
Thanks for the reply, at lunch time I will try the command again and if I have no luck I will use the memory test option and post the results.

Thanks for those handy PDF links on your post.

I have been using [http://books.google.com/books?id=kHLlJzI6L20C&printsec=frontcover#v=onepage&q&f=true](http://books.google.com/books?id=kHLlJzI6L20C&printsec=frontcover#v=onepage&q&f=true)

The more information the better.

:D

---


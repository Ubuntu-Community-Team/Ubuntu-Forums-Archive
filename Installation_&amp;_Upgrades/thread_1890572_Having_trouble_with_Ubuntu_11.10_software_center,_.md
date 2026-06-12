---
title: "Having trouble with Ubuntu 11.10 software center, please help?"
date: 2011-12-03
forum: Installation &amp; Upgrades
---

### Post by lonekingc4 on 2011-12-03
Hi from Bangladesh. This is my first post here.

 I recently installed Ubuntu 11.10 and it is so cool. But I am having  some trouble with the software center. Every time I select a software  from there and click "use this source", it starts installing but after a  few seconds, it stops and tells me to check my internet connection. My  connection is fine, there is no problem with that. I can't even listen  to music or play videos, it always asks me for some plugin update or  some sort. Then it searches for that and tells me for a package update. I  accept that but after a few seconds, same old story, "check your  internet connection" :(

I did "ping www.google.com" for about a minute and it said "1% packet  loss".

Ok, I know my connection is not as fast as in developed  countries, but it is one of the best in my country. Moreover, I am  also using Zorin OS, which is modified Ubuntu I think, and there is no  problem with the Software Center there. It works fine. So I am pretty  sure that my internet connection is not responsible for this problem.

How can I fix that? Cheers.

---

### Post by oldtimer7777 on 2011-12-03
I'm not entirely sure what it could be without further details..

What I would do if I didn't know what the problem was, is make sure I have everything I need installed and upgraded on my system first.

Here is a good checklist to double check that you have everything you need installed and running on there:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

It helps to have a guide to get everything just right when you are first starting out with Ubuntu, and hopefully that will guide you in the right direction to figure this out.

> **lonekingc4 said:**
> Hi from Bangladesh. This is my first post here.

 I recently installed Ubuntu 11.10 and it is so cool. But I am having  some trouble with the software center. Every time I select a software  from there and click "use this source", it starts installing but after a  few seconds, it stops and tells me to check my internet connection. My  connection is fine, there is no problem with that. I can't even listen  to music or play videos, it always asks me for some plugin update or  some sort. Then it searches for that and tells me for a package update. I  accept that but after a few seconds, same old story, "check your  internet connection" :(

I did "ping www.google.com" for about a minute and it said "1% packet  loss".

Ok, I know my connection is not as fast as in developed  countries, but it is one of the best in my country. Moreover, I am  also using Zorin OS, which is modified Ubuntu I think, and there is no  problem with the Software Center there. It works fine. So I am pretty  sure that my internet connection is not responsible for this problem.

How can I fix that? Cheers.

---

### Post by cuberts on 2011-12-03
> **lonekingc4 said:**
> Hi from Bangladesh. This is my first post here.

 I recently installed Ubuntu 11.10 and it is so cool. But I am having  some trouble with the software center. Every time I select a software  from there and click "use this source", it starts installing but after a  few seconds, it stops and tells me to check my internet connection. My  connection is fine, there is no problem with that. I can't even listen  to music or play videos, it always asks me for some plugin update or  some sort. Then it searches for that and tells me for a package update. I  accept that but after a few seconds, same old story, "check your  internet connection" :(

I did "ping www.google.com" for about a minute and it said "1% packet  loss".

Ok, I know my connection is not as fast as in developed  countries, but it is one of the best in my country. Moreover, I am  also using Zorin OS, which is modified Ubuntu I think, and there is no  problem with the Software Center there. It works fine. So I am pretty  sure that my internet connection is not responsible for this problem.

How can I fix that? Cheers.

Try installing the software through the terminal. Go to Applications > Accesories > Terminal
Then type 
```
sudo apt-get install [software here] 
```
If it successfully gets installed, then it is obviously an issue with the Ubuntu Software center itself, meaning there must have been some error during the installation...
However if it still fails to be installed then we can only assume that it's your connection, like the Software Center says.

---

### Post by lonekingc4 on 2011-12-04
> **cuberts said:**
> Try installing the software through the terminal. Go to Applications > Accesories > Terminal
Then type 
```
sudo apt-get install [software here] 
```
If it successfully gets installed, then it is obviously an issue with the Ubuntu Software center itself, meaning there must have been some error during the installation...
However if it still fails to be installed then we can only assume that it's your connection, like the Software Center says.
Nope. It doesn't work either. It says

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'synaptic' has no installation candidate"


It happens when I tried with other softwares as well. I tried "sudo apt-get update" also but still it says some error and failure messages about some packages.

I am not sure what the problem is with my connection. I am using a 1 mbps connection fine and smoothly, browsing the net, playing online chess etc. Software center is the only place I am having this message that something is wrong with my connection. Again, the software center in Zorin OS does not cause this problem.

---

### Post by lonekingc4 on 2011-12-04
> **oldtimer7777 said:**
> I'm not entirely sure what it could be without further details..

What I would do if I didn't know what the problem was, is make sure I have everything I need installed and upgraded on my system first.

Here is a good checklist to double check that you have everything you need installed and running on there:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

It helps to have a guide to get everything just right when you are first starting out with Ubuntu, and hopefully that will guide you in the right direction to figure this out.
The site you suggested has many "sudo apt-get" commands. But "sudo apt-get" commands are not working here. If you need more details, please ask, I will provide them as much as I can. Cheers.

---

### Post by lonekingc4 on 2011-12-04
Ok, kinda' solved it. It was obviously a problem with the 11.10 version. I just installed 11.04 version and everything works fine now. I guess it's a bug of 11.10. Anyways, thanks for your answers :D Cheers.

---


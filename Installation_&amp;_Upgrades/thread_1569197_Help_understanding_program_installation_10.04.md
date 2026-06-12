---
title: "Help understanding program installation 10.04"
date: 2010-09-06
forum: Installation &amp; Upgrades
---

### Post by ubu newb on 2010-09-06
[FONT=Arial][SIZE=2][COLOR=Navy]I am trying to install a program[/COLOR][/SIZE][/FONT][COLOR=Navy] on to Ubuntu 10.04.  Its called Gempak 5.11 and it is a weather software.  Not sure if it works but I'd like to try it out.  Problem I am having is understanding the editing and verifying settings.

Within my home directory I have created another directory called gempak.

rick@rick-U:~/gempak$ and unpacked with 
[/COLOR][B][COLOR=Navy]
[/COLOR][/B]

[COLOR=Navy]I unpacked the tar.gz into the above using:[/COLOR][COLOR=Navy][FONT=Arial][SIZE=2]gunzip -c gempak_upc5.11.4.tar.gz |tar -xvf-[/SIZE][/FONT]  and now I am stuck at what to do next.  The file I downloaded is the source code distribution.  

Here are the instructions: [http://tinyurl.com/2epn3sf](http://tinyurl.com/2epn3sf)

Can someone point me in the right direction?

Thanks


[/COLOR]

---

### Post by sikander3786 on 2010-09-06
Extract the package and it should have a "Read Me" or "Install" file with instructions.

Further more this thread might help.

[http://ubuntuforums.org/showthread.php?t=246092](http://ubuntuforums.org/showthread.php?t=246092)

And at last, I will recommend that you install all the software from the repositories. There are many weather applets available for Ubuntu in the repositories. Consider them.

Right Click on a panel, select "Add to panel" and type "Weather" in the dialogue box. That is what I use.

---

### Post by androiddev on 2010-09-06
From your position in the instructions, you need to configure as needed and run make. That's what I gather from reading the remaining instructions.

---

### Post by ubu newb on 2010-09-06
> 
And at last, I will recommend that you install all the software from the repositories. There are many weather applets available for Ubuntu in the repositories. Consider them.


Completely different program than what is available from the repositories.  

 > From your position in the instructions, you need to configure as needed  and run make. That's what I gather from reading the remaining  instructions. 	

That I understand.  It's the how I don't understand.  I am not sure what they want me to do editing those files.

---


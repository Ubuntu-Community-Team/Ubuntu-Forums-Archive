---
title: "Real Player"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by mimart7 on 2006-11-05
Hi All:

     I am having a problem installing Real Player 10.  I have tried going to the Real Player web site downloading .bin file to my desktop. I have tried using sudo apt-get, but I am not sure of the command line to install the app.  I am running the the 64 version of Edgy.  Any help would be most appreciated.

](*,) 
Mike

---

### Post by ingo on 2006-11-06
a *.bin file is an executable file. however, because of security issues, you have to allow it to become executable first:

sudo chmod -x /path_to_your_bin_file

note that there is a space between sudo and chmod, chmod and -x, -x and path

once done, enter the following

sudo ./path_to_your_bin_file

or 

sudo sh /path_to_your_bin_file

---

### Post by abhisheknegi on 2006-11-21
but where to install real player , i  installed it in my home directory but it cudnt work frm there..suggest further settings for proper installation

---

### Post by ingo on 2006-11-21
what is the exact path you installed it to?

and while you're at it, pls give the output of ls -l of that directory

a little more info than "it couldn't work from there" would also be beneficial. why not? what error messages if any? pls be as detailed as poss. we can only help if we know what is going on!

---


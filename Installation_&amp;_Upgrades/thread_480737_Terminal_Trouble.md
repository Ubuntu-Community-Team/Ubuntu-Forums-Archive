---
title: "Terminal Trouble"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by lukeisthecoolest on 2007-06-21
i am having trouble downloading wine using the terminal. Whenever i try to download it i get an error message saying:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
luke@luke-laptop:~$ sudo apt-get install wine
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
luke@luke-laptop:~$

---

### Post by NeoLithium on 2007-06-21
It's easy to fix :)  Just open up a terminal window and type in:
```
sudo dpkg --configure -a
```

Let it do it's thing and you'll be back up again :)

---

### Post by Majorix on 2007-06-21
Why do you want to download using the terminal after all? Firefox doesn't work?

---

### Post by NeoLithium on 2007-06-21
> **Majorix said:**
> Why do you want to download using the terminal after all? Firefox doesn't work?

I'm assuming that the Original Poster was using apt-get to install wine from the repositories.

---

### Post by Majorix on 2007-06-21
Oh sorry I must have missed that part in his post.

---

### Post by lukeisthecoolest on 2007-06-21
that worked but now i get this error:
Fetched 126kB in 1s (95.8kB/s)
Reading package lists... Done
luke@luke-laptop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-bin: Depends: sun-java6-jre (= 6-00-2ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
luke@luke-laptop:~$

---

### Post by lukeisthecoolest on 2007-06-21
**BUMP**
i need help

---

### Post by Persianelfster on 2007-06-21
did you run the sudo apt-get -f install ?

---

### Post by lukeisthecoolest on 2007-06-21
now what do i press?

[IMG]http://i185.photobucket.com/albums/x87/lukeisthecoolest/Screenshot-lukeluke-laptop.png[/IMG]

---

### Post by Persianelfster on 2007-06-21
enter and arrow keys to get around

---

### Post by lukeisthecoolest on 2007-06-21
i am stuck here:
4-1 [10.2MB]
Fetched 10.2MB in 18s (560kB/s)                                                
Selecting previously deselected package wine.
(Reading database ... 112659 files and directories currently installed.)
Unpacking wine (from .../wine_0.9.39~winehq0~ubuntu~7.04-1_i386.deb) ...
Setting up wine (0.9.39~winehq0~ubuntu~7.04-1) ...

luke@luke-laptop:~$

---

### Post by Persianelfster on 2007-06-21
its installed now... see no error message and you ended with a luke@laptop:~$ meaning the command is finished. congrats now try do you have an exe file?

---

### Post by lukeisthecoolest on 2007-06-21
i don't know how to find it?

sry for the newbishness

---

### Post by Persianelfster on 2007-06-21
find wine or the exe file?

---

### Post by lukeisthecoolest on 2007-06-21
i looked in add/remove programs and found this:

[IMG]http://i185.photobucket.com/albums/x87/lukeisthecoolest/Screenshot-Add-RemoveApplications.png[/IMG]

but i don't see it in my applicastions bar!?!?!?

---

### Post by Persianelfster on 2007-06-22
its installed, you see you just don't run wine by it self, you run it when you have an exe file and you select open with and type in wine.  and it will make the application think its windows, you try to install something it will give it a C file name and everything, and then stuff will start appearing in your applications menu under Wine programs or something named similar. But don't worry its installed you just private message me or post a new thread if you have problems running it on a exe file.  With the newbieish its fine, you have to start somewhere.  And you aren't being stupid, you are just trying to get some help, and many people here will try and help you ill be on for a while, but i think thats all for this?

---

### Post by lukeisthecoolest on 2007-06-22
is there a way i could +rep you? i feel that you deserve something

---

### Post by Persianelfster on 2007-06-22
nah don't worry about it, just trying to help people on the forum, thats the point right? :-)

---

### Post by lukeisthecoolest on 2007-06-22
well thanx and if ur ever in NJ and you need a custom comp. I'm your guy

---


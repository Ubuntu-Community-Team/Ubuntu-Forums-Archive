---
title: "Problem with the login after installation!"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by Kaladze on 2012-04-28
Hello forum, 

So, I've upgraded from 11.10 to 12.04 and now I have problems with the login (with the graphic interface). 
What I have done? : I've enter the password and hit enter, afterwards it stay like that (logging in). I can move my cursor or change things in the upper menu, even I can restart. 
Another strange thing is when I'm in this state (logging in...) if I hit left or right arrow the password field just resets, but after this I cannot type anything in the password field.
Other thing, with the combination Ctrl+Alt+F1... I can login. 
In 11.10 all were fine, but I have found something that if it is the same user as in 11.10 will not work to login. I've created a new user and delete the old one, eventhough i've lost all my settings.
Bottom of line, can anyone please help me with some adivices ?

PS: My graphic card is an Ati Radeon and my Processor is from Intel (64bit).

---

### Post by josephmills on 2012-04-28
> **Kaladze said:**
> Hello forum, 

So, I've upgraded from 11.10 to 12.04 and now I have problems with the login (with the graphic interface). 
What I have done? : I've enter the password and hit enter, afterwards it stay like that (logging in). I can move my cursor or change things in the upper menu, even I can restart. 
Another strange thing is when I'm in this state (logging in...) if I hit left or right arrow the password field just resets, but after this I cannot type anything in the password field.
Other thing, with the combination Ctrl+Alt+F1... I can login. 
In 11.10 all were fine, but I have found something that if it is the same user as in 11.10 will not work to login. I've created a new user and delete the old one, eventhough i've lost all my settings.
Bottom of line, can anyone please help me with some adivices ?

PS: My graphic card is an Ati Radeon and my Processor is from Intel (64bit).

Hello there lets see if we can fix this up :) 

We are going to have to work from tty1 or in other words press ctrl+alt+f1 and sign in. 

Now you have to install a program so that we can get information from you. 

```
sudo apt-get --yes install pastebinit
```

after installed lets get some info (I also had this happen to me when testing alpha 12.04 from dec--> feb) 

```
touch ~/.logaroo && dpkg-query -l | grep -e linux-image -e lightdm -e unity > ~/.logaroo && apt-cache policy dump lightdm >>~/.logaroo && lspci -nn |grep VGA >> ~/.logaroo && lsmod >>~/.logaroo && cat ~/.logaroo | pastebinit  && rm ~/.logaroo 
```


then let us see the link

---

### Post by Kaladze on 2012-04-29
[http://paste.ubuntu.com/954598/](http://paste.ubuntu.com/954598/) and thank you very much for the quick answer :D

---

### Post by anejo on 2012-04-29
Bump!

---

### Post by The Bright Side on 2012-04-29
Hey guys,

I have the same problem and did some more research. Didn't find a solution, but I collected all my findings in this thread:
[http://ubuntuforums.org/showthread.php?p=11887414#post11887414](http://ubuntuforums.org/showthread.php?p=11887414#post11887414)

Let's move there and try to work on a fix together.

---

### Post by Kaladze on 2012-04-29
as is said here:
[http://ubuntuforums.org/showthread.php?t=1967945&page=2](http://ubuntuforums.org/showthread.php?t=1967945&page=2)
installing gdm helped me to login from the GUI interface. 
Thanks a lot guys!

---

### Post by sdiotmvug on 2012-04-29
Jalan Menuju Kebenaran dimulai di sini : [http://a.roadtrue.comAnda](http://a.roadtrue.comAnda) dapat mempublikasikan link Anda di halaman "situs Anda".

---


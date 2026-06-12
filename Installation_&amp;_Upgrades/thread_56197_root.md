---
title: "root"
date: 2005-08-11
forum: Installation &amp; Upgrades
---

### Post by speedemonV12 on 2005-08-11
Hey im having problems...the ubuntu system is the best i have ever seen, and i love it.....but when i install,,, i do not get an option to type in a root password

so i have no root,...anyone can help me with this....how do i find out the root password....there is one but i dont know what it is... LIKE IT SAYS TYPE root password in order to do thiss....but i dont know it...it didnt give me the option so i cant install anything like deb packages....please help

thanks

---

### Post by Beej on 2005-08-11
Your root password is the same as your user password (or it is for me) When I use sudo in terminal, or I'm using synaptic, I just use the same password I log in with. 

Hope this helps.

---

### Post by speedemonV12 on 2005-08-11
YA  that works for like bringing up system controsl...but when i am in regular terminal and i type su it doesnt work
and i cant run deb package kuz my pass is wrong for some reason
 anyone else??


thanks

---

### Post by invalid on 2005-08-11
The equivalent to 'su' in ubuntu is 'sudo -s' - this will bring you to a root terminal.

Cheers,
Cb

---

### Post by DancingSun on 2005-08-11
You should try "sudo" in front of the command you want to execute.  After you press enter, you will be prompt for a password.  Enter your user password.  This works for me.

---

### Post by speedemonV12 on 2005-08-11
okay but i downloaded a limewire deb package...and when double clicked it to run it ...it asked for root password, and it did not work...kept sayin invalid password....and is there also no way that you can log in as root?


or is there some other way that i am supposed to install deb packages...for that matter how to i install packages?lool lololol :)  :)  :)  :)  :)  \\:D/  \\:D/  \\:D/

---

### Post by invalid on 2005-08-11
Open a terminal and type:

sudo dpkg -i packagename.deb

It will ask you for a password ( the same that you use which works other places)

Cheers
Cb

---

### Post by speedemonV12 on 2005-08-11
okay and what is    -i   what does that mean?

---

### Post by invalid on 2005-08-11
-i means to install

---

### Post by speedemonV12 on 2005-08-11
ahhh i c...thanks i will try it...and c 

thanks
speedy


by the way...ubuntu if for sure the best distro ever...much better support...thanks to you guys here in the forum...way to go ubuntu!!!!

---


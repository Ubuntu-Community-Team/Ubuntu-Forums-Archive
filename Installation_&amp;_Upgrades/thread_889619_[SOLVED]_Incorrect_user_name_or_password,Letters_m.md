---
title: "[SOLVED] Incorrect user name or password,Letters must be typed in correct case."
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by rokytnji on 2008-08-14
I have just installed Xubuntu using Wubi on another laptop. I've done this before with no problems. Now on this install When I give my user name and password I get the incorrect user name or password banner. I have tried different combinations in case I miss stroked a key or had caps locked without knowing but I am still not able to log in. Is there a way to fix this?

---

### Post by rokytnji on 2008-08-14
Okay I rebooted into recovery mode and enabled root shell prompt and as a test typed sudo ifconfig and got a readout without being asked sudo's password?

My line starts as: root@administrator- laptop:~#

---

### Post by rokytnji on 2008-08-14
I am not sure how this happened but now I am able to log in. On a hunch I typed in "administrator" and then my usual password and it logged me in. Now I just need to change the user name while I am in the GUI of Xubuntu.

---

### Post by meindian523 on 2008-08-14
Recovery mode by default gives root acess to the machine,that's how you were not asked the sudo password and your line was > root@administrator- laptop:~#

---

### Post by rokytnji on 2008-08-14
I have been googling to try to find a way to change my user name from administrator to what I usually use. any link or knowledge you could provide is very much appreciated.

---

### Post by meindian523 on 2008-08-14
I believe if you just open another session(Ctrl+Alt+F2 for text,Ctrl+Alt+F7 for GUI) and enter your usual username and password,it should log you in.If not,please post any errors.

---

### Post by rokytnji on 2008-08-14
By opening another session do you mean I should reboot and try to log in with my regular user name and password or just open Desk 2 and try what you suggested.

---

### Post by meindian523 on 2008-08-14
Just open Desk 2.

---

### Post by rokytnji on 2008-08-14
I used the text mode and my error just states : Login incorrect.

---

### Post by rokytnji on 2008-08-14
When I used administrator as the user name then it would log me in.

At the end I have 

administrator@administrator-laptop:~$

---

### Post by meindian523 on 2008-08-14
You can't change usernames,though you can change passwords.Try rebooting and entering your usual username and password.

---

### Post by hyper_ch on 2008-08-14
ok, as in the root shell run
```

cat /etc/passwd | grep 1000

```
The first user created on ubuntu starts with UID 1000 --> hence we filter for that.

Now you have the username name for that user. You can now also change his password:

```

passwd USER

```
where USER is the real username.


Now try again to login as usual.

---

### Post by hyper_ch on 2008-08-14
> **meindian523 said:**
> You can't change usernames,though you can change passwords.Try rebooting and entering your usual username and password.

And of course you can change usernames (but probably not recommended) by editing the passwd file.

---

### Post by meindian523 on 2008-08-14
I didn't know that.The only way I thought to change a username was to create a new user and migrate the /home/<old_username> to /home/<new_username>.

---

### Post by rokytnji on 2008-08-14
Well guys I entered cat /etc/passwd | grep 1000 

Then i entered passwd USER using my usual user name and  I got

passwd: unknown user (my name)

---

### Post by hyper_ch on 2008-08-14
You can create aliases and you can also change the username... but root is hardcoded for a few things so it's not adviced to change it. You can also appoint multiple users the same home directory....

Have a look at /etc/passwd

---

### Post by hyper_ch on 2008-08-14
> **rokytnji said:**
> Well guys I entered cat /etc/passwd | grep 1000
What did that return and what exactly did you enter for the passwd command?

---

### Post by rokytnji on 2008-08-14
The line below reads

administrator:x:1000:1000:administrator User...:/home/administrator:bin/bash
administrator@administrator-laptop~$ passwd  (my name)
passwd: unknown user (my name)
administrator@administrator-laptop:~$

I am having to type these out by hand as I am on the desktop posting this. Sorry for the delay.

---

### Post by hyper_ch on 2008-08-14
> **rokytnji said:**
> The line below reads

administrator:x:1000:1000:administrator User...:/home/administrator:bin/bash
administrator@administrator-laptop~$ passwd  (my name)
passwd: unknown user (my name)
administrator@administrator-laptop:~$

I am having to type these out by hand as I am on the desktop posting this. Sorry for the delay.

so you entered

```

passwd administrator

```
?

---

### Post by rokytnji on 2008-08-14
No. User name is "administrator"

Password is my name. 

I am trying to change my user name from administrator.  It 
logs me in when I use "administrator" as the user name. As long as I do that I am ok. It has taken me awhile to figure that out that somehow when I downloaded Xubuntu through Wubi that my user name wasn't entered and it used administrator as default for the user name.

---

### Post by rokytnji on 2008-08-14
No. User name is "administrator"

Password is my name. 

I am trying to change my user name from administrator.  It 
logs me in when I use "administrator" as the user name. As long as I do that I am ok. It has taken me awhile to figure that out that somehow when I downloaded Xubuntu through Wubi that my user name wasn't entered and it used administrator as default for the user name.

---

### Post by hyper_ch on 2008-08-14
actually, I have no clue what you're talking about. What do you use, what works, what does not... I am totally lost.

---

### Post by meindian523 on 2008-08-14
hyper_ch:
i]OP uses Xubuntu in WUBI.
ii]He forgot to put the username while installing,so apparently Xubuntu took the default as administrator(which I've no idea about,whether that indeed IS the default behavior)
iii]Now he wants to change the username from administrator to something else.
iv]His password is his name.<alarm bells for security nightmare>

---

### Post by hyper_ch on 2008-08-14
the username he chose during install is "administrator" as shown by the cat&grep commands.

---

### Post by rokytnji on 2008-08-14
My name is very unusual like my avatar name and is not widely known. It is not my actual name.

---

### Post by meindian523 on 2008-08-14
> **hyper_ch said:**
> the username he chose during install is "administrator" as shown by the cat&grep commands.
Probably,but the issue at hand is to change it to something else.I heard you mention the /etc/passwd file?

---

### Post by hyper_ch on 2008-08-14
yes I did... well the TO doesn't express clearly what he wants...

I know for sure now the username he setup during install is "administrator". Besides that the TO will have to say what he wants.

---

### Post by rokytnji on 2008-08-14
Change user  login name< from administrator to something else.

---

### Post by hyper_ch on 2008-08-14
alter it in the /etc/passwd file

---

### Post by rokytnji on 2008-08-14
Thank you both for all the help.

---


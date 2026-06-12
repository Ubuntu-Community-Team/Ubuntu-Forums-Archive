---
title: "I messed up... please help"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by Chondro_Biak on 2007-09-25
So I thought I would take a short cut and change my user profile to root in the users options... So I changed my directory from home/username to /root and changed my permissions from username to root... If you go into your user profiles you should be able to see what I mean if I said that wrong... Well that obviously didn't work so I logged out and was going to try login in as root and found out I can't log in at root except from the terminal... So I tried to log back in and it would not let me because of the settings I changed... I can get to the terminal, but I have no clue how to change these settings from the terminal... Any chance you have a few minutes to give me a play by play?? It all has to do with my profile... I can see the settings from the terminal, but don't know how to change them...

thanks


*EDIT*

sudo usermod -d /home/username username    Worked!!!

---

### Post by pay on 2007-09-25
Try ```
sudo chown 644 /home/<you>
sudo chmod <you>:<you> /home/<you>
```

---

### Post by Chondro_Biak on 2007-09-25
It did not work... told me to try help for both...

---

### Post by Wim Sturkenboom on 2007-09-25
@pay

Are you sure ? I did chown 644 about 20 years ago on some files and I could not touch them anymore. The sysadmin send me a nice banner stating 'idiot' after he fixed the issue :)

---

### Post by Wim Sturkenboom on 2007-09-25
> **Chondro_Biak said:**
> It did not work... told me to try help for both...chmod should be chown and chown should be chmod.

---

### Post by pay on 2007-09-25
> **Wim Sturkenboom said:**
> chmod should be chown and chown should be chmod.Yeah, it's 2 in the morning, what can you expect:)

---

### Post by nvteighen on 2007-09-25
I understand what you did. You didn't change permissions of your home folder, but which folder you assign as home.

I think I have the solution. I suppose you're in recovery mode logged in as root, so no sudo would be needed.

1. Type:
```

usermod -d /home/[username] [username]

```
2. Reboot using
```

reboot

```

That should work. If it doesn't, you can do the same but manually, this way (things between brackets are "variables"):

1. ```

nano /etc/passwd

```
2. You'll see lots of lines that look this way:
```

[username]:x:[UID]:[GID]:[Your name],,,:[HOME FOLDER PATH]:[TERMINAL PATH]

```
3. Locate carefully the line that starts with your username. (Very carefully!)
4. Change the home folder path to what it should be.
5. Save using Ctrl+o
6. Reboot with "reboot".

This information is based on man pages and some filesystem deep diving... hope it works, but it really should.

---

### Post by Chondro_Biak on 2007-09-25
nvteighen

I can get to the normal Ubuntu log in screen just fine, but it will not let me log in... 

I can get to the terminal one of 2 ways... I can enter the failsafe terminal mode by changing the session, or I can press crtl, alt F1 and to a login terminal... 

Do you still suggest I try your method or does that change things???

thanks

---

### Post by nvteighen on 2007-09-25
No, actually I think you may have problems using those ways because you'll still be logged as yourself and usermod does not allow to change anything to a logged user.

Please, reboot your computer and when GRUB appears (or press ESC immediately after BIOS to make GRUB menu appear) and select Recovery Mode. That will lead you into a command line session like Ctrl+Alt+F1, but logged in as root.

Edit: (Forgot to answer the most important). There shouldn't be any problem...  The only thing is that maybe it's safer to use the second and manual method, because if anything goes wrong you will be able to restore the file  to its previous state.

---

### Post by Chondro_Biak on 2007-09-25
OK... I will get that a shot in a sec... 

But before I do............ Is there a way to backdoor Ubuntu??? IF I can get in I know exactly what to change...

---

### Post by nvteighen on 2007-09-25
You mean to "attack" your PC from another? Well, I don't know how to do that... (and also think that all operating systems are meant to not allow such things!)

---


---
title: "E: dpkg was interrupted,"
date: 2019-05-15
forum: Installation &amp; Upgrades
---

### Post by oneleded on 2019-05-15
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```
 After Installing Lubuntu - Guide (Things to do & Apps to Install)  <---this is where i made my mistake, i forgot to look at the date. the thread was posted 'nov., 13. 2011...  now, apt-get, and package manager, are in conflict.
the 1st 2 lines, both start with ' E: ' , i have tried to run them, with 'run'. it just aint working out. i am running this exactly as stated, with all the marks, as quote marks, hyphens, an such.
i think i need different instruction. online, when i try to get help, everyone uses different punctuation, to mark the command you need, there should be a better way. maybe in between arrows. -->  command  <--  ....
any way, i'm stuck for the moment.. help

---

### Post by QIII on 2019-05-15
Or between code tags?  Would that be clear enough?

What do you mean by running it with 'run'?  Why would you do that?

---

### Post by Bashing-om on 2019-05-15
oneleded; Hey hey ...

and if you follow the package manager's suggestion:
```

sudo dpkg --configure -a

```
what results ?

[INDENT][INDENT]when all else fails, follow the instructions :)
[/INDENT][/INDENT]

---

### Post by oneleded on 2019-05-15
dpkg --configure -a ;  _cache->open ; failed, please report ;  if you can read this i got 3 commands. is this what you mean.

---

### Post by QIII on 2019-05-15
It would be helpful if you would enclose the results of your command in code tags.

Where do you see three commands?

You have been instructed to try only one command:

```
dpkg --configure -a
```

You will need to prepend that with sudo.

---

### Post by oneleded on 2019-05-15
> **Bashing-om said:**
> oneleded; Hey hey ...

and if you follow the package manager's suggestion:
```

sudo dpkg --configure -a

```
what results ?

[INDENT][INDENT]when all else fails, follow the instructions :)
[/INDENT][/INDENT]

i will try that again. this time it works. i did do a reset since the last time. now for the 2nd command line.

---

### Post by Bashing-om on 2019-05-15
oneleded; Sorry -

not formatted in the context of the command and the return - it is gibberish to me.
For example, on my clean system:
```

sysop@x1804mini:~$ sudo dpkg --configure -a
[sudo] password for sysop: 
<where your output would go here>
sysop@x1804mini:~$ 

```

[INDENT][INDENT]helps when I can see what I am looking at
[/INDENT][/INDENT]

---

### Post by QIII on 2019-05-15
What "second command line"?

---

### Post by oneleded on 2019-05-15
> **QIII said:**
> It would be helpful if you would enclose the results of your command in code tags.

Where do you see three commands?

You have been instructed to try only one command:

```
dpkg --configure -a
```

You will need to prepend that with sudo.
at the time when it fist happened, when i ran the command with sudo,  _cache->open() failed, please report. .. the terminal was giving me a,  (  , error...  that mark should not be there

---

### Post by oneleded on 2019-05-15
for me the second command line would be;   _cache->open() failed, please report.

---

### Post by oneleded on 2019-05-15
> **Bashing-om said:**
> oneleded; Sorry -

not formatted in the context of the command and the return - it is gibberish to me.
For example, on my clean system:
```

sysop@x1804mini:~$ sudo dpkg --configure -a
[sudo] password for sysop: 
<where your output would go here>
sysop@x1804mini:~$ 

```

[INDENT][INDENT]helps when I can see what I am looking at
[/INDENT][/INDENT]

sudo dpkg --configure -a  ;   this time, it worked, it didnt work before. 
this is the second command line i think.  _cache->open() failed, please report.
i thought it might be two lines, because the terminal didnt accept the, ( , quote mark.

---

### Post by Bashing-om on 2019-05-15
oneleded; HoKay :)

Look, think and see that
> 
E: _cache->open() failed, please report.

is the system telling you ERROR (E) - Houston, we have a problem.
--------------

Now we need to know if there is still a problem. For us to know if there is a situation please show us - Between those code tags - the outputs of terminal commands:
```

sudo apt update
sudo apt upgrade
sudo apt -f install
sudo dpkg -C

```

[INDENT]here we see what condition the condition is in[/INDENT]

---

### Post by oneleded on 2019-05-15
sorry for my confusing words; this was the 1st command; sudo dpkg --configure -a .. it worked this time;. i think the other might be two commands. i have to re-edit this in a second or two;;

---

### Post by oneleded on 2019-05-15
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring ttf-mscorefonts-installer &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; TrueType core fonts for the Web EULA                                        
 &#9474;                                                                             
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                           
 &#9474;                                                                             
 &#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement         
 &#9474; ("EULA") is a legal agreement between you (either an individual or a        
 &#9474; single entity) and Microsoft Corporation for the Microsoft software         
 &#9474; accompanying this EULA, which includes computer software and may include    
 &#9474; associated media, printed materials, and "on-line" or electronic            
 &#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your        
 &#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be      
 &#9474; bound by the terms of this EULA. If you do not agree to the terms of        
 &#9474; this EULA, you may not use the SOFTWARE PRODUCT.                            
 &#9474;                                                                             
 &#9474;                                  <Ok>                                       
 &#9474;                                                                           &#9474; 
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
             this is where i get stuck; i was on, sudo apt upgrade. i cant give an answer here, in the terminal. the terminal freeze's, when this shows up, i cant go anywhere, within it.
i can close the terminal, and start over. let me try this again, i can give you the output of sudo apt install. just not sudo apt update

---

### Post by Bashing-om on 2019-05-15
oneleded; 

Here you have to accept the (E)end (U)sers (L)icense (A)grrement - EULA.
to do that:
use the space bar to page down, Tab to highlight "Ok", then Enter to accept.

[INDENT][INDENT]not to intuitive at all !
[/INDENT][/INDENT]

---

### Post by oneleded on 2019-05-16
i've had 4 strokes 2 major, intuition is relative. not that that matter's.. i just havent been here before. dont want to seem like a jerk. i appreciate your help, an then some. i hope you'll keep helping me.
here i go again; i sound awful, dont i, sorry for that. i tried the space tab, nothing, then tried the arrow-down tab, it worked. i got hte tab to work, and run the other 2 commands.sudo apt -f install
sudo dpkg -C.. no problems. should i have another problem with this, i will let ya know. for now, i marking it as solved. its one of the quicker problems i got solved with help. i did say thank's didnt i.
i did read what you said vvvv, behind me. it will be marked solved, till it aint.

on the side; my family, dont know what i am saying, since i was little, still dont. my best friend, didnt understand me, for near 15 yrs. been friends for < 35 years. my syntax, dialect, is different. dont know why, just is.
again, much thank's.
that oneleded, what a whine, would ya like some cheese with that wine

---

### Post by Bashing-om on 2019-05-16
oneleded; He he ---

Help is what we do :)

If the issue is now under control ->
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT]and we do something different next time
[/INDENT]

---


---
title: "boot password lost"
date: 2015-05-25
forum: Installation &amp; Upgrades
---

### Post by salwa_mell on 2015-05-25
I lost my user password; the password is needed to upgrade the authentication fails i followed the steps to change the password but when I choose the boot in the grub menu he says enter the password for maintenance or press control D 
and I can't write any thing else please help me I am a complete begginer

---

### Post by Bashing-om on 2015-05-25
salwa_mell; Hi ! Welcome to the forum.

What release and desktop are you using ? As I am unfamiliar with :
> 
says enter the password for maintenance or press control D 

I do not know where that advisory comes from.

In changing the password; did you do something like this tutorial ?
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

requires additional info to enable mind-reading.
[INDENT][INDENT]just the facts, ma'am [/INDENT][/INDENT]

---

### Post by Elfy on 2015-05-25
do you get warning as described in the question here? 

[http://askubuntu.com/questions/19692/system-displays-file-system-maintenance-error-press-ctrld-while-booting](http://askubuntu.com/questions/19692/system-displays-file-system-maintenance-error-press-ctrld-while-booting)

---

### Post by salwa_mell on 2015-05-25
thanks for replying the problem  comes after this step[IMG]http://www.psychocats.net/ubuntu/images/resetpassword01.jpg[/IMG] I am using Ubuntu 14.04 32bits[IMG]http://www.psychocats.net/ubuntu/images/resetpassword01.jpg[/IMG]

---

### Post by Elfy on 2015-05-25
and what happens if you Ctrl+D ?

---

### Post by salwa_mell on 2015-05-25
nothing just goes back to the grub menu

---

### Post by salwa_mell on 2015-05-25
nothing just goes back to the grub menu

---

### Post by Bashing-om on 2015-05-26
salwa_mell; Well ...

That is not good:
> 
nothing just goes back to the grub menu


Let's do this in an attempt to isolate the fault. Can you boot to terminal ?
at the grub menu with a normal kernel selected press the 'e' key for edit mode -> boot parameters screen;
Arrow down to the line starting with 'linux' and arrow across to "quiet splash", replace these terms with the term "text" - without the quotes;
key combo ctl+x to continue the boot process to TTY1.
Login here with username and password ( there is no response to the screen when password is entered, enter your password blindly and hit the enter key).

If You can get to the TTY1 we look at access authorizations, or perhaps graphics driver.
Else we look at it as a booting issue.

[INDENT][INDENT]fault isolation
[INDENT][INDENT][INDENT]to retoration
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---


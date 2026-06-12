---
title: "Cannot Log In"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by merlinus on 2012-05-05
I just installed 12.04. and the login screen will not accept my password.  I know it is correct because I can use it to unlock the Users dialog box, and I am not getting "incorrect password" when typing it in at the login screen.

It seems to accept the password, because the screen goes black for a moment, but then the login screen reappears.

I can login as Guest, but then cannot use sudo to, for example, rm ~/.Xauthority

I did not have this problem on any of my other three computers with the new install.

---

### Post by sangi on 2012-05-17
I installed 12.04 on my Toshiba laptop 3 days ago and I was using it without any problems so far. Since today morning, I am unable to login. When I enter my password, it says incorrect. I am 100% sure that the password is correct. However, I am able to login to the Guest account.

I have tried resetting the password through *passwd username* from root shell. It says password has been successfully reset but when I try logging in again, it says password incorrect. I can't do *sudo rm .Xauthority  *when I am logged in as a Guest. I am unable to log in to my account.

Please help.

---

### Post by BlackfootDave on 2012-05-17
> **sangi said:**
> I installed 12.04 on my Toshiba laptop 3 days ago and I was using it without any problems so far. Since today morning, I am unable to login. When I enter my password, it says incorrect. I am 100% sure that the password is correct. However, I am able to login to the Guest account.
 
I have tried resetting the password through *passwd username* from root shell. It says password has been successfully reset but when I try logging in again, it says password incorrect. I can't do *sudo rm .Xauthority *when I am logged in as a Guest. I am unable to log in to my account.
 
Please help.
 
I am having a similar problem gaining access to the platform itself. I cannot log in at all. I have installed it with windows and it is asking for a password login. But I didn't set up a password to begin with. Is it the same password that I login on my Windows acct.?
 
Please help.
Thx.

---

### Post by jadtech on 2012-05-17
oh boy maybe I wont reboot  hehe

did you both install the updates yesterday one  being a security update having to do with passwords and the other having to do with unity greeter ..

---

### Post by jadtech on 2012-05-17
temporary solution maybe to create a new user with admin  until it can be sorted out ..

---

### Post by BlackfootDave on 2012-05-17
> **jadtech said:**
> oh boy maybe I wont reboot hehe
 
did you both install the updates yesterday one being a security update having to do with passwords and the other having to do with unity greeter ..
 
I did install yesterday. I ran the platform for the first time and it had the computer name then asked for a password. I assumed it was the same password as for my Win acct. No dice. I looked at the properties as a guest and noticed that there was a login password that was encrypted but there were only five "dots" instead of the normal number for my password. How can I access this information?
 
Thanks for your reply. Are there any other threads that can help me. I'm new to the forums and I'm not used the navigation yet.
 
BlackfootDave

---

### Post by jadtech on 2012-05-17
> **BlackfootDave said:**
> I did install yesterday. I ran the platform for the first time and it had the computer name then asked for a password. I assumed it was the same password as for my Win acct. No dice. I looked at the properties as a guest and noticed that there was a login password that was encrypted but there were only five "dots" instead of the normal number for my password. How can I access this information?
 
Thanks for your reply. Are there any other threads that can help me. I'm new to the forums and I'm not used the navigation yet.
 
BlackfootDave

well  I believe there is some one who may be able to walk you through  going live cd and helping change the password  or since you don't have much  to lose just do the install again this time remember  the password you type this is important you cant do nothing  with Linux without an admin password not even everyday updates or program installs ..

---

### Post by BlackfootDave on 2012-05-17
> **jadtech said:**
> well I believe there is some one who may be able to walk you through going live cd and helping change the password or since you don't have much to lose just do the install again this time remember the password you type this is important you cant do nothing with Linux without an admin password not even everyday updates or program installs ..
 
 
Um. I gues I'm not making myself very clear. I installed the software directly from the sight and I was never asked to enter a password. I'll try and reinstall again though. Thanks.:p

---

### Post by Tass on 2012-05-31
OK - I'm double-posting here, but I think I have the solution:

I've had the same issue as everyone else and I think I've resolved it.  I tried removing the Xauthority file and at the time I thought it had worked, with no success.

Turns out it was because I was using the guest account to try delete the file.  The guest account won't let you run any commands as sudo, but running it without sudo didn't give any indication that it hadn't succeeded.

So - here's what I did:
 - From the login, press Ctrl + Alt + F1
 - As the prompt log in with a user with admin privileges
 - Type sudo rm ~/.Xauthority
 - Reboot! (sudo shutdown -r now)

And that worked for me - hopefully it'll work for you too!

---


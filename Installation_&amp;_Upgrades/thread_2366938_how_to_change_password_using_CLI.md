---
title: "how to change password using CLI"
date: 2017-07-24
forum: Installation &amp; Upgrades
---

### Post by nickTaylor1181 on 2017-07-24
Hi All


New laptop with latest version of Ubuntu Studio.


I need to change the password - and I need to use passwd to do it, because the GUI won't let me use the password I want to use.

This works fine.... until I reboot... and then it goes into an "enter password" loop... when I enter the password, the screen goes blank for a bit, then it asks for my password again.


So I Ctrl-Alt F3... change the password back to the old password... then I can log in again... but then I'm back with the old password.


I suspect this has something to do with keyrings, but I can't see any way of accessing keyrings.


So... if someone could advise how to change a password using the CLI so that I can actually log in with it, I would be eternally grateful.


Any help most appreciated.





Nick

---

### Post by westie457 on 2017-07-24
Hi this old tutorial may be of some help. 

[https://www.psychocats.net/ubuntu/resetpassword](https://www.psychocats.net/ubuntu/resetpassword)

---

### Post by nickTaylor1181 on 2017-07-28
Hiya - thanks for getting back to me.

That old tutorial doesn't work - it just says 

[I]Authentication token manipulation error
password unchanged

[/I]I'm not sure if it would anyway - it this keyring thing (I think) - using a CLI changes the password but not the keyring, so the two get out of sync.

---

### Post by westie457 on 2017-07-28
Not sure if this is the fix you are looking for. 

[https://ubuntuforums.org/showthread.php?t=2286953](https://ubuntuforums.org/showthread.php?t=2286953)   post #5 has the instructions.

Unfortunately my knowledge of the Cli and commands is not good enough to make proper suggestions plus I do not want to ruin your system with incorrect commands.

---

### Post by nickTaylor1181 on 2017-07-28
Hiya

This isn't anything to do with chrome. This is to do with the basic linux user password itself - the one that is used about 20 times a day - I really really don't want it to be fiddely and complicated.

I can't change it using the GUI because someone has added a new "feature" which stops me using the password that I want to use... I can change it using a CLI, but for some reason, it is stored in two places now, so when I come to log in, I just go into a permanent loop where it doesn't say "wrong password", it just re-displays the login box over and over again.

So to get into the system, I have to drop back to a CLI, change the password to what it was before... then I can log in. But then I'm back where I started, with a fiddely complicated password that other people know.

---

### Post by nickTaylor1181 on 2017-07-28
If I use the GUI it says "Password too simple" - if I try the same password again, the GUI hangs.

I cannot believe how difficult this is - it's taken days just to try to change a password.

---

### Post by nickTaylor1181 on 2017-07-28
I've tried installing seahorse... tried every as many permutations and combinations of keyring unlockings and password changes as I can think of.

I've tried going to ./.local/share/keyrings and deleting the contents.

Then when I reboot - same result : it loops forever at the login screen and I can't get back in until I drop back to a CLI and change my password back to the old one.


Does anyone know where this "old password" is being stored?

---

### Post by nickTaylor1181 on 2017-07-28
Okay - figured out how to override the whole password complexity situation:


1. Open common-password config file

   sudo nano /etc/pam.d/common-password



2. Comment/add below:

     #password   [success=1 default=ignore]      pam_unix.so obscure sha512
     password    [success=1 default=ignore]      pam_unix.so minlen=1 sha512


From:

[http://www.icc-computer.com/HowTo/Server/Server%20-%20Linux/How%20to%20disable%20password%20complexity%20check%20on%20Ubuntu%20server%2014.10.txt](http://www.icc-computer.com/HowTo/Server/Server%20-%20Linux/How%20to%20disable%20password%20complexity%20check%20on%20Ubuntu%20server%2014.10.txt)

---


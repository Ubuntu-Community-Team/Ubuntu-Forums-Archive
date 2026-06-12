---
title: "Just installed --- but can't logon as System Administrator"
date: 2006-02-21
forum: Installation &amp; Upgrades
---

### Post by grubuntu on 2006-02-21
Hello

I'm brand new to ubuntu.  I installed on a clean HDD with an ubuntu cd, the Hoary Hedgehog release.  

During installation my cable modem connection couldn't be detected.  In order to address that (now that the os is up and running) I'm being prompted for the appropriate password.

Per the strong advice given during setup, I created a user account other than System Administrator.  I assumed that such a thing would mean IN ADDITION TO, that is, that I'd have two accounts.  Regardless, I gave them both the same password.  Now whenever I'm prompted for a password appropriate to administrative priveleges, I get nothing.  Either that or I get a message denying access, something about a 'child'.

It looks like it's imperative I resolve this in order to gain internet access and in order to be able to install hardware-specific drivers.  I'd sure appreciate some coaching.

Should I just reinstall the os ...this time doing something different?

---

### Post by aysiu on 2006-02-21
There is no root or administrator account.
There's a *sudo* account where you can temporarily gain root privileges with your user password:

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)
[http://www.psychocats.net/linux/permissions.php](http://www.psychocats.net/linux/permissions.php)

---

### Post by grubuntu on 2006-02-21
Thanks Aysiu, but...

Yeah, none of this is working.  I don't have Terminal listed under Applications -> Accessories.  I can right-click the Desktop and open it from there though.

I've tried both *sudo* commands and *gksudo* commands in keeping with the literature on the subject.  (Thanks for the links).  However, each time I use them I receive either an error message or a prompt for a password.  The password fails every time.

I so looked forward to having a Linux machine.  Don't at all mind having to use a command line.  But geez, trouble right off the bat??

If I'm to go with the odds here, what I'm experiencing "straight out of the box" can't be much less than common enough.

Maybe someone who's experienced the same thing will be so kind as to walk me through how they resolved it, direct me to prior threads and such.

I am in the right place for help aren't I?

---

### Post by aysiu on 2006-02-21
[QUOTE=grubuntu]
If I'm to go with the odds here, what I'm experiencing "straight out of the box" can't be much less than common enough.[/quote] Not from what I've seen. This is weird. I don't see this happen that often, and definitely not on a clean install.

> 
I am in the right place for help aren't I? Yes!

---

### Post by andyjoe1 on 2006-02-21
go to your terminal type in sudo passwd then hit enter type in password when ask  then it should ask you to retype it but when you are typing it in you wont see anything typing

---

### Post by grubuntu on 2006-02-21
Thanks again.

Aysiu ...Oh no , not to argue, just to inform.  I'm sure you know your stuff.  I had Windows ME on this HDD before I formatted it to free it up for Ubuntu.  Scandisk reported that all sectors were good.  So I assumed Ubuntu would take without a hitch.  The problem --- probably --- is my having used the same password for both accounts.  Just guessing.

AndyJoe1 ...yeah, same kind of error message.  Says I'm not on the sudoer list.  I'll wait a while, you know, to see if someone offers up a remedy.  If not, I'll go ahead and reinstall.  Question though (so I don't create more problems), is there going to be a way for me to format my HDD from inside Ubuntu beforehand?

All to learn from, eh?

---

### Post by grubuntu on 2006-02-22
I was hoping to return with a positive report, but ...

I reinstalled Hoary Hedgehog. (This time I configured the network manually --- probably shouldn't have left it with the name Ubuntu though).

Anyway, because of the trouble I had on the **first** install, this time I decided not to create a second user account.  After all, the instructions say this can be done later.

Problem is, now I can't logon **at all**.  I tried the username *root*, but got a message saying "the system administrator cannot log on from here".

Will someone tell me what username I need to use, that is, to go with the password I assigned to root during setup?

Please?

---

### Post by grubuntu on 2006-02-23
More specifically, when I try to login as *root* I get the message "The system administrator is not allowed to login from this screen."

What this message does indicate however is that the program recognizes my password. If I type in a wrong password (or no password) or try to login under any other name I get the message "Incorrect username or password."

However ...

Since my last post was viewed by twenty plus members and yet without any suggestions, appearance has it I'm in the wrong place for help along these *particular *lines, that is, something this out of the ordinary.

Can someone direct me to perhaps a thread where matters of this sort are dealt with?

...lest grubuntu --> flubuntu --> scrubuntu

---

### Post by jal on 2006-02-25
I'm new to ubuntu too, grubuntu. Please treat my comments below as encouragement only, I must defer to the experts.

UNIX has a different paradigm for access than Windows; instead of logging in as an administrator account doing stuff and logging out, normally you log onto a box as yourself, and then 'change' to another account which has been set up specificly for the job at hand.

I would suggest (see disclaimer above, there are probably better ways) that you do yet another install, but this time _do_ set up a user account and password. (I'm sure that assigning duplicate passwords for accounts does no harm, after all, think what would happen if someone else accidently chose your password).

You should be able to log in after the install using that user account and password. Then try andyjoe1's experiment with sudo. He changed your password, I'll do something less drastic.

(On my system, KMenu is the bottom left icon) Select 
Kmenu -> System -> Konsol to get up a "command window" and
at the prompt (my prompt shown below will differ from yours) enter the command "cat /etc/sudoers".

john@acknak:~$ cat /etc/sudoers

I expect that will fail. Then try out sudo:

john@acknak:~$ sudo cat /etc/sudoers

sudo may ask for a password - enter the password for the account you intially logged in as. Do _not_ use a root password (harmless but will fail).

That should show you the contents of the file, but more importantly, if it works, it proves that you are able to execute commands with root priviledges.

If you're really determined to become the root account, you would then do (same password as for the above experiment):
sudo su - root

Enter "exit" to return to the original account:
root@acknak:~ # exit

---

### Post by grubuntu on 2006-02-25
Jal ...thanks for your suggestions.

I was just stopping in to give a progress report and was, admittedly, surprised to find a response after so long.

I did do another reinstall. This time I chose the linux-image-386 as kernel instead of linux-386.  This made for a successful installation of the linux base system. It had failed the other times.

At this point everything looks good.  I did set up that user account. When prompted for a password, that one's doing the trick so far.

Problem is, ubuntu still can't recognise my cable modem connection even though I've plugged in all the right numbers.  I'll chip away at that and then look for an appropriate thread if it stumps me.

Thanks again, Jal, for the time you took to help me out.  Made my day.

---


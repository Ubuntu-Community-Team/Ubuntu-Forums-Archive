---
title: "dpkg was interrupted, you must manually run 'dpkg"
date: 2017-03-19
forum: MINT
---

### Post by jenelle on 2017-03-19
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


i go to install upgrades that have shown up and the above message has shown it's self , i am not sure i will be able to fix and might have to wait till brother comes and visits but i will see if i can try , 
i did try to look for where i can report this problem like it tells me too but i can not find that either . 

so no0t sure how to fix it and hope i can thanks otherwise updates wont happen till brother visits

think system is MINT 17 think thats right

---

### Post by deadflowr on 2017-03-19
Moved to* Mint sub-forum*

I believe mint needs a special package to install prior to running the updates.
mintupdate I think it's called.

But that's as far as I know anything mint and updating.
And it's probably all wrong

---

### Post by lisati on 2017-03-19
Don't panic! Before you worry too much about reporting, could you please open a terminal and run **dpkg --configure -a**, and report back the result.

That's about all I know to suggest for that particular error message. Not having used MINT, I'll defer to the wisdom of others about other packages that might be needed.

---

### Post by jenelle on 2017-03-19
> **lisati said:**
> Don't panic! Before you worry too much about reporting, could you please open a terminal and run **dpkg --configure -a**, and report back the result.

That's about all I know to suggest for that particular error message. Not having used MINT, I'll defer to the wisdom of others about other packages that might be needed.

dpkg: error: requested operation requires superuser privilege


is what it says i am an admin to be able to update as i have to put in password etc so is there another level ?
which is probably my brother if there is

> **deadflowr said:**
> Moved to* Mint sub-forum*

I believe mint needs a special package to install prior to running the updates.
mintupdate I think it's called.

But that's as far as I know anything mint and updating.
And it's probably all wrong

thanks  :-)

---

### Post by #&amp;thj^% on 2017-03-19
> **jenelle said:**
> dpkg: error: requested operation requires superuser privilege
is what it says i am an admin to be able to update as i have to put in password etc so is there another level ?
which is probably my brother if there is
It is possible he changed the permissions for your Account...but to see if you have Adminisative rights you could check with:

The simpliest way to discover who has Admin (sudo) rights, is with **"-l & -U" options** together, just type users it will list e.g.: me then:
Example:
```
$ sudo -l -U me
[sudo] password for me: 
User me may run the following commands on me-pc:
    (ALL) ALL

```

If the user does not have Admin (sudo) access, it will print that a user is not allowed to run sudo on localhost:

  ```
 sudo -l -U me
   User me is not allowed to run sudo on localhost.
```
Hope that was useful.
Regards

---

### Post by jenelle on 2017-03-21
> **1fallen said:**
> It is possible he changed the permissions for your Account...but to see if you have Adminisative rights you could check with:

The simpliest way to discover who has Admin (sudo) rights, is with **"-l & -U" options** together, just type users it will list e.g.: me then:
Example:
```
$ sudo -l -U me
[sudo] password for me: 
User me may run the following commands on me-pc:
    (ALL) ALL

```

If the user does not have Admin (sudo) access, it will print that a user is not allowed to run sudo on localhost:

  ```
 sudo -l -U me
   User me is not allowed to run sudo on localhost.
```
Hope that was useful.
Regards
jenelle@JEM-Desktop ~ $ sudo - l - U jenelle
[sudo] password for jenelle: 
hSorry, try again.
[sudo] password for jenelle: 
Sorry, try again.
[sudo] password for jenelle: 



what is meant to be sudo password?? it wont take password i use to get into my page ??

---

### Post by lisati on 2017-03-21
The password won't show when you type it, this is a normal security precaution.

---

### Post by jenelle on 2017-03-21
is it what i sign into my page as we have one for me one for dad and one for brother

---

### Post by lisati on 2017-03-21
It's the password for the Ubuntu user you're signed in as.

---

### Post by #&amp;thj^% on 2017-03-21
> **jenelle said:**
> is it what i sign into my page as we have one for me one for dad and one for brother
It is the same password you used to login to your session with:
To see if you are allowed to make changes to the system or have sudo privileges use this:
```
id me
```
Paste back what is returned so we can see it here.
> **lisati said:**
> It's the password for the Ubuntu user you're signed in as.

+1:D

---

### Post by jenelle on 2017-03-22
> **1fallen said:**
> It is the same password you used to login to your session with:
To see if you are allowed to make changes to the system or have sudo privileges use this:
```
id me
```
Paste back what is returned so we can see it here.


+1:D

id jenelle
uid=1001(jenelle) gid=1001(jenelle) groups=1001(jenelle),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),27(sudo),29(audio),30(dip),44(video),46(plugdev),109(netdev),113(lpadmin),120(scanner),130(sambashare)



when i tried my password it didnt work ???

> jenelle@JEM-Desktop ~ $ sudo -l -U jenelle
Matching Defaults entries for jenelle on JEM-Desktop:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User jenelle may run the following commands on JEM-Desktop:
    (ALL : ALL) ALL
    (root) NOPASSWD: /usr/lib/linuxmint/mintUpdate/checkAPT.py
jenelle@JEM-Desktop ~ $ [sudo] password for me: ########
[sudo]: command not found
jenelle@JEM-Desktop ~ $ User me may run the following commands on me-pc:
User: command not found
jenelle@JEM-Desktop ~ $     (ALL) ALL



i re tried other one i pasted here so i could put in password etc before putting in to terminal not sure if this is different again or helpful but no harm in trying it again different to what i did last night

---

### Post by #&amp;thj^% on 2017-03-22
> **jenelle said:**
> id jenelle
uid=1001(jenelle) gid=1001(jenelle) groups=1001(jenelle),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),27(sudo),29(audio),30(dip),44(video),46(plugdev),109(netdev),113(lpadmin),120(scanner),
130(sambashare)

when i tried my password it didnt work ???
This group with the =1001 has Admin Rights, so now you should be good to go.

> **jenelle said:**
> jenelle@JEM-Desktop ~ $ [sudo] password for me: hawksheroes
If this is your password I would change this quickly...not good to show here, for some eye's.:(
But you should now be able to run what was suggested by the package manager:
```
**sudo** **dpkg --configure -a**
```
The password you now know.
If there is more errors shown in the terminal, Paste them back here so we can see them.

---

### Post by jenelle on 2017-03-22
> **1fallen said:**
> This group with the =1001 has Admin Rights, so now you should be good to go.


If this is your password I would change this quickly...not good to show here, for some eye's.:(
But you should now be able to run what was suggested by the package manager:
```
**sudo** **dpkg --configure -a**
```
The password you now know.
If there is more errors shown in the terminal, Paste them back here so we can see them.

when i did bottom bit this comes up

>  sudo dpkg --configure -a
[sudo] password for jenelle: 
Setting up libnm-util2:amd64 (1.2.6-0ubuntu0.16.04.1) ...
Setting up gir1.2-gtk-3.0:amd64 (3.18.9-1ubuntu3.2) ...
Setting up libnm-glib4:amd64 (1.2.6-0ubuntu0.16.04.1) ...
Setting up desktop-file-utils (0.22-1ubuntu5.1) ...

Configuration file '/etc/gnome/defaults.list'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** defaults.list (Y/I/N/O/D/Z) [default=N] 

so next step to that is just want to make sure i press right option which my guess is I would that be right ??

i am only guessing at which to do , sorry very green when doing this stuff usually rely on brother but one day i may not be able to do that thanks for all that are trying to help me too

---

### Post by #&amp;thj^% on 2017-03-23
Sorry we seem to be on different time zones...But just accept the changes, by pressing "Y" and enter. (Don't worry on being Green...we all were at one time):smile:
Good News though, things look like so far, that it should go relatively smooth for you now.:)
If not post back any errors from the Terminal you see...and we will try and solve them.

---

### Post by jenelle on 2017-03-23
> **1fallen said:**
> Sorry we seem to be on different time zones...But just accept the changes, by pressing "Y" and enter. (Don't worry on being Green...we all were at one time):smile:
Good News though, things look like so far, that it should go relatively smooth for you now.:)
If not post back any errors from the Terminal you see...and we will try and solve them.

```
defaults.list (Y/I/N/O/D/Z) [default=N] ? y
Installing new version of config file /etc/gnome/defaults.list ...
Setting up libnm0:amd64 (1.2.6-0ubuntu0.16.04.1) ...
Setting up libnm-gtk-common (1.2.6-0ubuntu0.16.04.2) ...
Setting up network-manager (1.2.6-0ubuntu0.16.04.1) ...
Setting up libgtk-3-bin (3.18.9-1ubuntu3.2) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Setting up libnma-common (1.2.6-0ubuntu0.16.04.2) ...
Setting up libnma0:amd64 (1.2.6-0ubuntu0.16.04.2) ...
Setting up gir1.2-networkmanager-1.0:amd64 (1.2.6-0ubuntu0.16.04.1) ...
Setting up libnm-gtk0:amd64 (1.2.6-0ubuntu0.16.04.2) ...
Setting up network-manager-gnome (1.2.6-0ubuntu0.16.04.2) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
jenelle@JEM-Desktop ~ $ 
```

thats what come up so hope that means i did rith thanks will see if they will install now

seems to be doing the trick so far

wahooo it worked thank you :-)

thank you for all your help :-)

and i did change my password like you told me to due to me posting it here :-)

---

### Post by #&amp;thj^% on 2017-03-24
> **jenelle said:**
> and i did change my password like you told me to due to me posting it here :-)

Your Welcome...Glad things are well. :smile:
Now if I may make one more suggestion, to keep things clean on your system.
```
sudo apt-get autoremove --purge
```
This cleans old kernels up and some left behind config files.   This will help prevent future problems.
Kind Regards
Props to lisati..;)

---

### Post by jenelle on 2017-03-26
> **1fallen said:**
> Your Welcome...Glad things are well. :smile:
Now if I may make one more suggestion, to keep things clean on your system.
```
sudo apt-get autoremove --purge
```
This cleans old kernels up and some left behind config files.   This will help prevent future problems.
Kind Regards
Props to lisati..;)

cool thanks

---


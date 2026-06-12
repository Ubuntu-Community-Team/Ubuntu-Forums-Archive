---
title: "Existing password not working after 11.10 update"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by dm13178 on 2011-10-13
First I gotta say that I switched from windows to ubuntu 7 months ago, and I'm happier for it.
 
However, after upgrading to 11.10 (64-bit version) My password doesn't work. 
 
I had originally set up the machine to login automatically and still does so. I just can't make any system changes.
 
How can I change the password w/o having to export all my data to cloud/external drives and redo the system?
 
Thanks.

---

### Post by OsakaWilson on 2011-10-14
I have the same problem (also 64 bit). However I didn't have an automatic login, so I am stuck at the login screen.I did notice that although it returns me to the login screen as if it doesn't recognize my password, it does not say "Invalid Password" like it does if I put in an invalid password. 

I'm curious whether it is the same with yours.

---

### Post by uk144 on 2011-10-14
I have the same problem . I use my old password but does not log me in. However I do Nootka get a password errer message thatni do if I use a random password. Can anyone help here?

Thanks

---

### Post by grim2 on 2011-10-14
I also have this problem.  I'm also running 64 bit.  Now, I have two user accounts on my machine.  The admin account doesn't work, the user account does.  I'm not sure this is relevant but, in the admin account, I had reverted to the Gnome desktop and upgraded from there.  The other account was left alone, presumably in Unity, because it was never used.

I'd like to get this fixed.  Thanks in advance.

---

### Post by matt_symes on 2011-10-14
Hi

Try to boot in to the recovery console (root account) and change your password from there.

Type this to delete your existing password.

```

passwd -d <your_user_name>
```

Then type this to add a new password.

```
passwd <your_user_name>
```

Hopefully that will fix it for you.

Kind regards

---

### Post by viky.nandha on 2011-10-14
Hi,

I also experience the same issue. But, the problem doesn't seem to be with password, because I can login from tty1 (Ctrl + Alt + F1).

My works are stalled because of this. Expecting a fix urgently.

---

### Post by matt_symes on 2011-10-14
Hi

> **viky.nandha said:**
> Hi,

I also experience the same issue. But, the problem doesn't seem to be with password, because I can login from tty1 (Ctrl + Alt + F1).

My works are stalled because of this. Expecting a fix urgently.

Interesting. Can everybody else log into a console ?

Kind regards

---

### Post by uk144 on 2011-10-14
I have the same problem. 

When i tried to delete my passowrd in root I got the message... 'cannot lock /etc/shadow; try again later' and so was unable to change my password. Any suggestions why this is the case?

---

### Post by matt_symes on 2011-10-14
Hi
> 
When i tried to delete my passowrd in root I got the message... 'cannot  lock /etc/shadow; try again later' and so was unable to change my  password. Any suggestions why this is the case?Boot back into root console and look for these files.

```
/etc/group.lock
/etc/passwd.lock
/etc/shadow.lock
```If you find them delete them. You can then try to change your password again. 

As others can log into a tty i am not sure if this will fix it though.

Kind regards

---

### Post by savvar on 2011-10-14
> **matt_symes said:**
> Hi



Interesting. Can everybody else log into a console ?

Kind regards


same issue. can also log in console

---

### Post by matt_symes on 2011-10-14
Hi

> same issue. can also log in console

It sound like a lightdm or pam issue maybe. Have you tried reconfiguring lightdm from the console ?

Kind regards

---

### Post by uk144 on 2011-10-14
Can you give any guidance about what and how to config? Thx

---

### Post by matt_symes on 2011-10-14
Hi

From the console, try this.

```
sudo service stop lightdm
```

```
sudo dpkg-reconfigure -phigh lightdm
```

```
sudo service start lightdm
```

Also, what's the output of

```
ls /etc/pam.d/
```

Kind regards

---

### Post by uk144 on 2011-10-14
Sudo service stop lightdm met with the response 'unrecognised service'

---

### Post by vak on 2011-10-14
*After* upgrade?? My screen got locked *during* upgrade! The pass isn't accepted for some reason. 

Text console e.g. via Alt-CTRL-F1 let's me logging OK. I don't even know if upgrade has finished or no.

---

### Post by matt_symes on 2011-10-14
Hi

I am updating my Natty to Oneric now. I will have a play and I will post back later.

Kind regards

---

### Post by uk144 on 2011-10-14
> **vak said:**
> *After* upgrade?? My screen got locked *during* upgrade! The pass isn't accepted for some reason. 

Text console e.g. via Alt-CTRL-F1 let's me logging OK. I don't even know if upgrade has finished or no.
I have the same behaviour - It lets me log in using Text console  via Alt-CTRL-F1, but not from gui interface. weird!

---

### Post by vak on 2011-10-14
> **uk144 said:**
> I have the same behaviour - It lets me log in using Text console  via Alt-CTRL-F1, but not from gui interface. weird!
my 
```
sudo dpkg-reconfigure lightdm
```
gives me
```
...: lightdm is broken or not fully installed.
```

---

### Post by 23dornot23d on 2011-10-14
Check out some of  the links in the upgrade problems below .... to do with Login
there may be a fix in one of the links already  ......


Failure Graphics - Lightdm
[http://ubuntuforums.org/showthread.php?t=1859133](http://ubuntuforums.org/showthread.php?t=1859133)
       Login Problem
[http://ubuntuforums.org/showthread.php?t=1859288](http://ubuntuforums.org/showthread.php?t=1859288)
[http://ubuntuforums.org/showthread.php?t=1859349](http://ubuntuforums.org/showthread.php?t=1859349)
[http://ubuntuforums.org/showthread.php?t=1859233](http://ubuntuforums.org/showthread.php?t=1859233) >>> [COLOR=Red]**SOLVED**[/COLOR][COLOR=Green]
[[COLOR=Black]http://ubuntuforums.org/showthread.php?t=1859373[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1859373")[/COLOR]

---

### Post by vak on 2011-10-14
> **23dornot23d said:**
> Check out some of  the links in the upgrade problems below .... to do with Login
there may be a fix in one of the links already  ......

Since I didn't find my case there I've created it:
[http://ubuntuforums.org/showthread.php?p=11341137](http://ubuntuforums.org/showthread.php?p=11341137)

Feel free to ad it to your list.

P.S. ever worst Ubuntu upgrade that happened to me. [COLOR="DarkOrchid"]**Catastrophic Ocelot**.[/COLOR]

---

### Post by 23dornot23d on 2011-10-14
This one is yours - I usually pick them up on the first page ..... the link is slightly different
but yours is on the list .......

[COLOR=Red]**[http://ubuntuforums.org/showthread.php?t=1859373](http://ubuntuforums.org/showthread.php?t=1859373)**[/COLOR]
and this one
[http://ubuntuforums.org/showthread.php?t=1859741](http://ubuntuforums.org/showthread.php?t=1859741)

I will try to keep up with the ones coming in ...... and I have tried highlighting the
problem in the sections that I think the devs can work on ........

---

### Post by vak on 2011-10-14
> **23dornot23d said:**
> This one is yours - I usually pick them up on the first page ..... the link is slightly different
but yours is on the list .......

[COLOR=Red]**[http://ubuntuforums.org/showthread.php?t=1859373](http://ubuntuforums.org/showthread.php?t=1859373)**[/COLOR]

I will try to keep up with the ones coming in ...... and I have tried highlighting the
problem in the sections that I think the devs can work on ........
In the link above stated *after* upgrade. In my case it is *during*. No reboot even yet happened. Plus, dpg-reconfigure lightdm says "lightdm is broken or not fully installed"

---

### Post by uk144 on 2011-10-14
> **23dornot23d said:**
> Check out some of  the links in the upgrade problems below .... to do with Login
there may be a fix in one of the links already  ......


Failure Graphics - Lightdm
[http://ubuntuforums.org/showthread.php?t=1859133](http://ubuntuforums.org/showthread.php?t=1859133)
       Login Problem
[http://ubuntuforums.org/showthread.php?t=1859288](http://ubuntuforums.org/showthread.php?t=1859288)
[http://ubuntuforums.org/showthread.php?t=1859349](http://ubuntuforums.org/showthread.php?t=1859349)
[http://ubuntuforums.org/showthread.php?t=1859233](http://ubuntuforums.org/showthread.php?t=1859233) >>> [COLOR=Red]**SOLVED**[/COLOR][COLOR=Green]
[[COLOR=Black]http://ubuntuforums.org/showthread.php?t=1859373[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1859373")[/COLOR]
This one worked for me 

[http://ubuntuforums.org/showthread.php?t=1859233](http://ubuntuforums.org/showthread.php?t=1859233) >>> SOLVED

rm .Xauthoity


Thank you

---

### Post by 23dornot23d on 2011-10-14
I am just trying to keep a list of problems to do with upgrades ...... 

will add to it stating yours is during install though .....

---

### Post by dm13178 on 2011-10-14
> **OsakaWilson said:**
> I have the same problem (also 64 bit). However I didn't have an automatic login, so I am stuck at the login screen.I did notice that although it returns me to the login screen as if it doesn't recognize my password, it does not say "Invalid Password" like it does if I put in an invalid password. 

I'm curious whether it is the same with yours.

In my case, I get the invalid password error message, but I am happy to know it's not just me who has had problems with the new distro.

I'm also glad that the community is so willing to help with all issues.

---

### Post by viky.nandha on 2011-10-14
[http://ubuntuforums.org/showpost.php?p=11341151&postcount=7](http://ubuntuforums.org/showpost.php?p=11341151&postcount=7)

This worked; am back home :)

---

### Post by hannes88 on 2011-10-14
I had the same problem but I discovered that when I made the update, the keyboard on the login-screen was changed to English (instead of Swedish which I normally use). Maybe you're having the same problem?

---

### Post by matt_symes on 2011-10-14
Hi

> **vak said:**
> In the link above stated *after* upgrade. In my case it is *during*. No reboot even yet happened. Plus, dpg-reconfigure lightdm says "lightdm is broken or not fully installed"

Have you tried reinstalling lightdm ?

Kind regards

---

### Post by dm13178 on 2011-10-15
After trying many suggestions in this thread, I ended up backing up every thing and doing a fresh installation.  This fixed the issue.  

One little weird thing, the system seemed to hang right and the last part of the installation, during the process kill.  Waited for several minutes for a message or automatic restart which never came.  

Hit the enter key and system restarted.  I haven't had any issues since then.

---

### Post by arno48 on 2011-10-16
> **dm13178 said:**
> 
 
I had originally set up the machine to login automatically and still does so.
 

I am not able to set up the machine to login automatically and it goes on asking for password every time I boot my Natty  11.04.
As none else uses my computer I would prefer to access directly, without any typing password. 

Could you please tell me how to get an automatic login?
Thanks

---

### Post by Tigerkermit on 2011-10-17
I can log in with my account but I lost root privilegs !!
If I try to log in as root or run sudo, my root passwd is not longer accepted.

So I lost ability to change anything !! :twisted:

Has anyone an idea ?
Is there any standard root passwd ?

I fear when I run the update from 11.04, I got the message
Removing group "admin" (98)

I guess there is any issue with the new acoount policies ?

---

### Post by SynDaily on 2011-10-18
> **matt_symes said:**
> Hi



Interesting. Can everybody else log into a console ?

Kind regards

Yes.

Can login on a tty. Used:
# sudo passwd root

to get a GUI login as root. I can login via my girl friends account also but she's not in the su group. 

Other background that maybe of use:

In the last upgrade I didn't like the Fisher Price interface so I disabled the unity plugin from the compiz manager. In this upgrade I choose gdm when upgrading.

HTH to debugger this problem.

Cheers

Si

---

### Post by SynDaily on 2011-10-18
> **Tigerkermit said:**
> I can log in with my account but I lost root privilegs !!
If I try to log in as root or run sudo, my root passwd is not longer accepted.

So I lost ability to change anything !! :twisted:

Has anyone an idea ?
Is there any standard root passwd ?

I fear when I run the update from 11.04, I got the message
Removing group "admin" (98)

I guess there is any issue with the new acoount policies ?

There used to be an old unix trick for restarting in single user mode and changing root passwd. That sound be enough information for you to get googling with.

HTH

---

### Post by hwaly12 on 2011-11-08
maybe temporary treating. 

termial mode.

passwd

(prenset pw)  ****** 
(new pw) ******
(confirm pw) ******


It's not answer completly.

I want to recover your computer system.

---

### Post by mdzeko on 2012-05-08
sorry.. noob posting

---

### Post by mdzeko on 2012-05-08
same problem.. GUI log in doesn't work, but sudo -i -u works when i root.
I have updated from 11.10 to 12.04 LTS. Also cannot change password with passwd from root..

---

### Post by mdzeko on 2012-05-08
> **mdzeko said:**
> same problem.. GUI log in doesn't work, but sudo -i -u works when i root.
I have updated from 11.10 to 12.04 LTS. Also cannot change password with passwd from root..
Ok, i was able to change the password but nothing changed (in the GUI mode still cannot log in). i couldn't change the password cause the recovery was in read only mode, but i run the failsafe graphics mode and that changed it to read/write. Turned out to be unhelpfull, but i realised that it might be something about a package called fglrx? anyone?

---


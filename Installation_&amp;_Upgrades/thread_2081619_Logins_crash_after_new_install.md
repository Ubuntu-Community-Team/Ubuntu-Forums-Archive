---
title: "Logins crash after new install"
date: 2012-11-07
forum: Installation &amp; Upgrades
---

### Post by spectre2028 on 2012-11-07
In trying out different distros, I've been using the same /home partition to keep my login the same. Was on Mint for a while. Just tried Fuduntu and not caring for it, I installed Xubuntu 12.04.

Problem is that when I go to login with my same old user name, it appears to accept my credentials and initiate the login.  But then it appears to crash and I'm returned back to the login window.

I used the guest account to login and add a new user, under which I can login okay. So I suspect the problem is that the old user has some kind of invalid parameter in an initialization file that Xubuntu doesn't like.  Problem is, I don't know where to begin looking:

1. Is there a log file of some sort that would detail the reason for a failed login?

2. Any ideas what init file to look at for the invalid parameter that Xubuntu is having a problem with?

I suppose if worst comes to worst, I can just copy all my files over to the new user and stick with that. But if for no other reason than the learning experience, I'd like to solve the problem with the original user account.

---

### Post by Toz on 2012-11-07
> **spectre2028 said:**
> 1. Is there a log file of some sort that would detail the reason for a failed login?
Have a look at **~/.xsession-errors** and **/var/log/lightdm/lightdm.log**

> 2. Any ideas what init file to look at for the invalid parameter that Xubuntu is having a problem with?
Have a look at the ownership of certain files in your home directory - specifically **~/.Xauthority** and **~/.ICEauthority**. Incorrect ownership of these files has been known to cause issues like this.

---

### Post by spectre2028 on 2012-11-07
Bingo! .xsession-errors was an unholy MESS, with about four screens of errors, so I was about to give up on trying to salvage that user.

Then I decided as a last-ditch effort to use sudo to change the permissions of those two specific directories to the user name in question. Then, what the heck, I thought maybe I should do the same with the entire user name's directory & files (not a bad idea, I hope!).

After changing ownership of the directory & files, I logged out and logged right in using the credentials previously problematic.  Problem solved!  Thank you.

---


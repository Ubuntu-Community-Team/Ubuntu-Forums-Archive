---
title: "No root password in Ubuntu install"
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by sqlpython on 2007-08-28
I have installed many LINUXes but not Kubuntu. I am accustomed to being queried for a root password for the root user during the install..this did not happen and I was asked to make One user.
 I opened Settings > Users after install and tried to apply a password to root but it does not seem to work..when I su in a terminal..Yet I can open the Root Shell without a password..
 Can someone point me to a wiki or guide to explain this root user difference with Kubuntu..
I would like a login for the root user and a password for root that works.. Thanks much.

 Otherwise all works well on my Inspiron 1501 Installs..7.04 is Great.

---

### Post by deanjm1963 on 2007-08-28
with ubuntu/kubuntu you use the command " sudo " instead of " su "

you can create a root password by typing in a terminal

sudo passwd root
(enter your user/login password) hit enter

it will then ask you for a password

after that you can then use " su "

all administrative tasks, e.g. adding/removing software you still need to use your own password.. not the administrator password

to log into KDE as root user you need to edit the " kdmrc " file which is located in /etc/kde3/kdm folder

search for "root" and find " allow root login " - change false to true

you need to save this file and reboot for it to take effect.

---

### Post by bapoumba on 2007-08-28
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")
Here is a little reading on the subject ;)

And welcome aboard!

---

### Post by vikramsharma on 2007-08-28
You change the root password directly by going to "Users and Groups" System_>Administration_>Users and Groups.  Once you are there, you would be asked for your user password.  Select "root" and click on "Properties".  In the section "Account" third sub-category is "Password" you can choose any password that you want for root and write it there.  It's much easier to do, sorry I could not explain it in a better way.

---

### Post by sqlpython on 2007-08-28
Thanks everyone..
I had used vikramsharma suggestion before I came back to the thread.
Unfortunately, no success.. I opened Users and Clicked on administrator then root and entered the password..as this is a new install I am  keeping all passwords simple until I am finished with setup so all is REAL Easy to remember.

 Now I reboot and anything that needs an su or sudo does not work..i.e Adept Manager or Root Shell..nor can I su or sudo anywhere in any shell..get in a shell
> :~$ sudo passwd root
sudo: must be setuid root
l:~$ su
Password:
su: Authentication failure
Sorry.
:~$su

 If I try to open a Root Shell or Package Manager..((anything that needs sudo authentication...I Notification Error pops up with
> 
>> Error- KDE su <<
X  Su returned with an error

>>>> OK <<<<<<<

 So basically somehow root access is gone and user access is good..
 Any Ideas?
Has anyone ever seen an error like the above...seems to me that even if the Root Password were successfully changed, KDE should pop up a Password Box/Field but that does not happen..

---

### Post by dilipkk on 2007-08-28
hi...

i am also having same problem.. i changed /usr/bin permissions using:
sudo chmod -R  /usr/bin

from then i am getting this problem..

any suggestions ?

thanx in advance ....

---

### Post by merlinus on 2007-08-28
Maybe something here will help:

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

-merlin

---

### Post by dilipkk on 2007-08-29
it worked.... 

thanx for your suggestion ..i got again sudo back...i was trying to get help from so many days...today...got it....again thanx....

---

### Post by vikramsharma on 2007-08-29
> **sqlpython said:**
> Thanks everyone..
I had used vikramsharma suggestion before I came back to the thread.
Unfortunately, no success.. I opened Users and Clicked on administrator then root and entered the password..as this is a new install I am  keeping all passwords simple until I am finished with setup so all is REAL Easy to remember.

 Now I reboot and anything that needs an su or sudo does not work..i.e Adept Manager or Root Shell..nor can I su or sudo anywhere in any shell..get in a shell


 If I try to open a Root Shell or Package Manager..((anything that needs sudo authentication...I Notification Error pops up with


 So basically somehow root access is gone and user access is good..
 Any Ideas?
Has anyone ever seen an error like the above...seems to me that even if the Root Password were successfully changed, KDE should pop up a Password Box/Field but that does not happen..

I just changed my root password using the method I described, not a problem.  I am attaching a screenshot of the window.

---


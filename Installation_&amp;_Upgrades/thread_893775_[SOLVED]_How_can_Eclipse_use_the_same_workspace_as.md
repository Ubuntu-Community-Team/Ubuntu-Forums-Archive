---
title: "[SOLVED] How can Eclipse use the same workspace as Apache webroot ?"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by pe7er on 2008-08-18
I've just managed to manually install Eclipse 3.3 on Ubuntu 8.04 (for AMD 64) (topic: [http://ubuntuforums.org/showthread.php?t=892976](http://ubuntuforums.org/showthread.php?t=892976) ).

I also installed Apache / PHP / MySQL.
Apache uses **/var/www** as webroot.

At the start of Eclipse 3.3 I have to select a workspace.
If I choose **/var/www** as workspace, then Eclipse will display the error message:
> Workspace Unavailable
Workspace in use or cannot be created, choose a different one.

Does anyone know why this error occurs?
Is it because Apache already uses **/var/www** as webroot?

Or is it because Eclipse 3.3 is run from my user account (without sudo) 
and the permissions on /var/www are 755 (40755) and the group/owner is root/root.

How can I solve it?

---

### Post by pe7er on 2008-08-22
If I run Eclipse from command line with root rights:
```
cd /usr/local/opt/eclipse
sudo ./eclipse
```then I am able use /var/www as workspace.

However, this way the PHP plugin that I installed is not visible when run from root account. 
That's because I installed the PHP plugin when I ran Eclipse from my own account.

Therefore I suppose that the problem is caused by ownership of /var/www
I tried to change the ownership with 
```
sudo chown my_user_account:my_user_account /var/www 
```
I can see that my_user_account is the owner + group on /var/www
but starting Eclipse from within my_user_account results again in the error:
> Workspace Unavailable
Workspace in use or cannot be created, choose a different one.

I would like to be able to run Eclipse from my user account,
and use /var/www as workspace because that way I can see my website + php files in action while developing in Eclipse.

Does anyone have an idea how to solve this issue?

---

### Post by pe7er on 2008-08-22
I seemed to have solved it....
There was a hidden directory in **/var/www/.metadata**

First I tried to delete /var/www/.metadata/.lock and then start Eclipse,
but got the same error.

I changed the ownership + group to my_user_account with
```
sudo chown my_user_account:my_user_account /var/www
```
and then** I deleted the whole /var/www/.metadata** with ([COLOR="Red"]**be careful with the following command!**[/COLOR])
```
sudo rm -r /var/www/.metadata
```

After I restarted Eclipse, and selected the /var/www as workspace,
Eclipse recreated the /var/www/.metadata directory with my_user_account as user/group, 
so the error was resolved!

Note: instead of deleting the /var/www/.metadata directory, 
you might also try to change the ownership (with CHOWN -R) that directory to your user account...

---

### Post by black scorpio on 2009-11-04
Got have the same problem also a while ago i just only run the command on terminal

> sudo chown user_name:user_name /var /www

and it work smoothly....


thank you mate...

---

### Post by pradnya on 2010-12-08
sudo chown -R user_name:user_name /var /www

ya this solved the problem,Thanks.

---


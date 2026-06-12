---
title: "limit firefox"
date: 2015-04-19
forum: MINT
---

### Post by flex567 on 2015-04-19
I have 3 user accounts on my comp: seba,guest and prog 

I would like to give access to firefox to just seba and guest. How can I do that ? 

I have linux mint 17.1

---

### Post by flaymond on 2015-04-21
Well, you can chown the application.

A couple links that might be solution and reference in your case -

[http://askubuntu.com/questions/215139/how-can-i-change-user-permission-settings-for-an-application](http://askubuntu.com/questions/215139/how-can-i-change-user-permission-settings-for-an-application)
[http://manpages.ubuntu.com/manpages/saucy/man1/chown.1.html](http://manpages.ubuntu.com/manpages/saucy/man1/chown.1.html)

---

### Post by matt_symes on 2015-04-21
Hi

You can use an access controls list (ACL) to do this.

You would disallow the user prog from running firefox. Here's an example.

I am user matthew and i have another user john on this laptop. I disallow john from running the shell script test.sh by using setfacl and stopping his privileges.

```
matthew-laptop:/home/matthew:1 % cat ./test.sh 
#!/bin/bash

echo "hello";
matthew-laptop:/home/matthew:1 % whoami
matthew
matthew-laptop:/home/matthew:1 % sudo -u john ./test.sh
hello
matthew-laptop:/home/matthew:1 % sudo setfacl -m u:john:--- ./test.sh
matthew-laptop:/home/matthew:1 % sudo -u john ./test.sh              
sudo: unable to execute ./test.sh: Permission denied
matthew-laptop:/home/matthew:1 % ./test.sh                           
hello
matthew-laptop:/home/matthew:1 % sudo setfacl -m u:john:rwx ./test.sh
matthew-laptop:/home/matthew:1 % sudo -u john ./test.sh              
hello
matthew-laptop:/home/matthew:1 %

```

This is blacklisting as opposed to whitelisting but in your case it makes little difference.

A point to note is that /usr/bin/firefox is a symbolic link to a shell script.

```
matthew-laptop:/home/matthew:1 % file $(which firefox)
/usr/bin/firefox: symbolic link to `../lib/firefox/firefox.sh' 
matthew-laptop:/home/matthew:1 %
``` 

This shell script calls, after some work, ```
/usr/lib/firefox/firefox
``` on a default install of Ubuntu.

That should point you in the right direction.

Kind regards

---


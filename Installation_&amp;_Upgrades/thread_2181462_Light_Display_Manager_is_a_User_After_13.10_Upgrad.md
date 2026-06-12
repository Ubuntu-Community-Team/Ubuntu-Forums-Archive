---
title: "Light Display Manager is a User After 13.10 Upgrade"
date: 2013-10-18
forum: Installation &amp; Upgrades
---

### Post by gerowen on 2013-10-18
Just upgraded to 13.10 and noticed something strange. I now have a user on the login screen labeled "Light Display Manager". It's not the end of the world, I can still log in and do what I need to do, but just thought it was a bit strange. I've googled around a little but nothing was really helpful that I found, and a search here didn't turn anything up so I figured I'd toss it out there.

---

### Post by Toz on 2013-10-18
What version did you upgrade from?

Have a look at the "minimum-uid" value in /etc/lightdm/users.conf file. It should be set to 500 so that it doesn't display any of the system users with uids less than 500 (user uids can be viewed via "cat /etc/passwd").

---

### Post by gerowen on 2013-10-18
I upgraded from 13.04.  My minimum-uid variable is already set to 500.  Here are the contents of my users.conf file.  I wonder if just adding the lightdm user to the hidden-users line would work.

```

#
# User accounts configuration
#
# NOTE: If you have AccountsService installed on your system, then LightDM will
# use this instead and these settings will be ignored
#
# minimum-uid = Minimum UID required to be shown in greeter
# hidden-users = Users that are not shown to the user
# hidden-shells = Shells that indicate a user cannot login
#
[UserAccounts]
minimum-uid=500
hidden-users=nobody nobody4 noaccess
hidden-shells=/bin/false /usr/sbin/nologin

```

---

### Post by Toz on 2013-10-18
> **gerowen said:**
> I upgraded from 13.04.  My minimum-uid variable is already set to 500.  Here are the contents of my users.conf file.  I wonder if just adding the lightdm user to the hidden-users line would work.

You could try, but you shouldn't have to. Does your /etc/lightdm/lightdm.conf file have anything in it that would be forcing the lightdm user to show up? Are there any other system users (with uids less than 500) showing up?

---

### Post by gerowen on 2013-10-18
> **Toz said:**
> You could try, but you shouldn't have to. Does your /etc/lightdm/lightdm.conf file have anything in it that would be forcing the lightdm user to show up? Are there any other system users (with uids less than 500) showing up?

Here's my lightdm.conf contents:
```

marcus@adams-desktop:~$ cat /etc/lightdm/lightdm.conf
[SeatDefaults]
user-session=ubuntu
greeter-session=unity-greeter

```

No other system users are showing up on the login screen, only the "Light Display Manager" one.

---

### Post by Toz on 2013-10-18
What is the lightdm user uid?
```
cat /etc/passwd | grep lightdm
```

Try adding lightdm to the hidden-users field in /etc/lightdm/users.conf file to see if it works. You'll need to restart lightdm for it to take effect.

---

### Post by gerowen on 2013-10-18
> **Toz said:**
> What is the lightdm user uid?
```
cat /etc/passwd | grep lightdm
```

Try adding lightdm to the hidden-users field in /etc/lightdm/users.conf file to see if it works. You'll need to restart lightdm for it to take effect.

```

lightdm:x:110:116:Light Display Manager:/var/lib/lightdm:/bin/false

```

---

### Post by Toz on 2013-10-18
Did adding "lightdm" to the hidden-users field work?

---

### Post by Jan D on 2013-10-18
There is a bug opened in launchpad (please mark it as "affects you"): [https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1235785](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1235785)

---

### Post by Toz on 2013-10-18
> **Jan D said:**
> There is a bug opened in launchpad (please mark it as "affects you"): [https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1235785](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1235785)

Interesting. I have a number of Xubuntu 13.10 installs and it I don't see this behaviour. I wonder if its somehow related to unity-greeter? (Xubuntu uses gtk-greeter).

---

### Post by ttd1232004 on 2013-10-18
> **gerowen said:**
> Just upgraded to 13.10 and noticed something strange. I now have a user on the login screen labeled "Light Display Manager". It's not the end of the world, I can still log in and do what I need to do, but just thought it was a bit strange. I've googled around a little but nothing was really helpful that I found, and a search here didn't turn anything up so I figured I'd toss it out there.

I have got it the same problem asyou, however, I couldn't log in with my user password.
Is there some thing wrong here!????/

---

### Post by gerowen on 2013-10-18
> **Toz said:**
> Did adding "lightdm" to the hidden-users field work?

Yep.  Adding it to the hidden-users line caused it not to be displayed on the login screen.  Thanks for the help and for following up, :-)

---

### Post by liquidcross on 2013-10-18
I had it appear briefly on my users list, but then after a reboot, it was gone. Weird.

---

### Post by PJs Ronin on 2013-10-18
> **liquidcross said:**
> I had it appear briefly on my users list, but then after a reboot, it was gone. Weird.
Same here.   First boot of the day and  lightdm appears on the logon screen... [S]doesn't appear with subsequent boots[/S].

Edit:   And as these things go, Light Display Manager is now appearing for me at every boot.

---

### Post by johannesg-s on 2013-10-22
I am experiencing the same issue. Both after I upgraded from 13.04 and also with a clean install of 13.10 (although I do have my /home mapped to a seperate partition that I didn't format during the installation)

---

### Post by liquidcross on 2013-11-19
Still having the same problem here, too. And I can no longer edit lightdm conf to hide the list of users at login.

---


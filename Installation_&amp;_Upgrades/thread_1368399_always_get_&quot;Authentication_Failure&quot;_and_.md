---
title: "always get &quot;Authentication Failure&quot; and sudo password fails"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by mr72 on 2009-12-30
Installed 9.10 (from the same DVD) on two different systems here, same issue.

I created a user, say it's "foo", on the initial install. When I set it to log in automatically it works fine but "sudo <cmd>" prompts for the password and it always fails after "[sudo] password for foo:" as if I am typing in the wrong password (I am not).

If I try and log out and log back in, it won't do the graphical login, says "Authentication Failure".

I have reinstalled about half a dozen times across two different systems, figuring I must have really typoed the password when installing and therefore I must be typing in a wrong password. But after doing this over, and over, and over, it seems clear that I am not actually typing in the wrong password. It's just broken.

Same thing for the GUI synaptic update manager (tells me there are updates available, I try and update, it asks for the password, then tells me "Authentication Failure"). 

Incidentally, if I do "passwd" and change it from the shell, if I type the [correct] password, then try and change it to the current password, it says "Password Unchanged". So clearly somewhere something knows the right password. 

This is a huge PITA since you can't do a freakin' thing on Ubuntu without sudo working.

So what am I doing wrong, or what can I do differently to make this work?

---

### Post by taurus on 2009-12-30
Do you belong to group adm?  You need to belong to group adm to use sudo.

```
id
```

---

### Post by mr72 on 2009-12-30
yep! it's the one and only user account, and it belongs to the group "adm".

"...groups=4(adm)..."

---

### Post by sisco311 on 2009-12-30
Actually you have to belong to the admin group.

Can you use policykit to authenticate yourself as an admin?
If so, what's in the sudoers file?

```
pkexec cat /etc/sudoers
```

---

### Post by mr72 on 2009-12-30
When I do that, I get "Authentication is needed to run '/bin/cat' as the super user" and "Authentication Failure".

also a part of the "admin" group:

"...115(admin)..."

---

### Post by sisco311 on 2009-12-30
Is your user in the admin group?

Did you check the data integrity of the DVD?
[uhelp]community/HowToMD5SUM[/uhelp]

What keyboard layout are you using? Did you change it after installation?

Can you use the su command to authenticate yourself?
```
su username
```

---

### Post by mr72 on 2009-12-30
> **sisco311 said:**
> Is your user in the admin group?

Did you check the data integrity of the DVD?
[uhelp]community/HowToMD5SUM[/uhelp]

What keyboard layout are you using? Did you change it after installation?

Can you use the su command to authenticate yourself?
```
su username
```

No, that says:

* No device configured for user "username".
Password: <type correect password>
su: Authentication Failure

I didn't do a md5sum on the DVD image.
I am about to dl a new 9.10 CD and install it again.
KB layout is USA, buy default. I didn't change it.

this is turning out to be a royal pain.

---

### Post by ChronoSphere on 2010-05-03
I have this exact same problem with all versions of 9.04 and above. The cd's md5 is correct. It works on all pcs in my house except for one. Any solution?

---

### Post by JohnVLang on 2010-05-21
No cure sorry to say, but same issue... upgraded from 8.04 to 10.04 via Update Manager -> Upgrade... after restart couldn't log in... tried re-installing from Live CD, same result "authentication failure" over and over... There has to be a fix out there somewhere... I'm trying to do all this via long distance support to my mother (who, bless her, at nearly 80 is not a command line kinda' gal)... help!?!

J

---

### Post by ChronoSphere on 2010-05-27
The last version that works on my PC is 8.10. All versions from 9.04 and up have this problem. What has changed in the way of authentication between these releases? There has to be a way to get this obscure problem resolved.

---

### Post by Don544 on 2010-10-18
I notice that no one says this is solved and as I have the same problem I wonder if anyone has solved it?
Thank You:
Don
 any attempt results in same as this
don@don-desktop:~$ su don
Password: 
su: Authentication failure
don@don-desktop:~$

---

### Post by JohnVLang on 2010-10-18
Hi Don544,

Still sorry to say - no solution from me... i ended up going back to 9.10 and have not been game enough to try the upgrade again... This was actually for my 80 year old mother in England (i'm in Australia) and i was updating her remotely... try talking your 80 year old mother through command line stuff in Terminal!!! I think i'll just build her a new laptop and send it over...

Cheers, John

---

### Post by TunaCanTommy on 2010-10-18
Have you tried changing your password ? ?

> sudo passwd

---

### Post by TunaCanTommy on 2010-10-18
You can also try setting a new password:


Edit:  [http://psychocats.net/ubuntu/resetpassword]("http://psychocats.net/ubuntu/resetpassword")

---

### Post by rysliv on 2011-01-20
I looked over the command 
```
man sudo_root
```

Use  the command
```
sudo passwd root
[sudo] password for tester: --Your passwd--
Enter new UNIX password: --New passwd--
Retype new UNIX password: --Retype--
passwd: password updated successfully

TYPE SU again

su
Password:
root@testmachine:/home/tester# 
```

Works.

If not, Then make sure your account type is not CUSTOM.
I don't know anything else that could cause it but this seems to resolve the issue from existing.

---


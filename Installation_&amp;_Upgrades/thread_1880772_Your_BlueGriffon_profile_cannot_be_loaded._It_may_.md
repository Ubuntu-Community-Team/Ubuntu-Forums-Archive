---
title: "Your BlueGriffon profile cannot be loaded. It may be missing or inaccessible"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by Peter2009 on 2011-11-14
Hi!

I have installed BlueGriffon 

and I get this message if I try to double click it!

> Your BlueGriffon profile cannot be loaded. It may be missing or inaccessible

If I run on the terminal

```
sudo /home/.BlueGriffon/bluegriffon 
```

It start al right! I did installed on home directory because I did try on a system folder and it was giving me permission problem.

anyone got a idea what is going on?

I did try:

chmod 666 .BlueGriffon ( and some variation) and went manually at the folder too! 

thanks for helping!

---

### Post by Peter2009 on 2011-11-21
> **Peter2009 said:**
> Hi!

I have installed BlueGriffon 

and I get this message if I try to double click it!



If I run on the terminal

```
sudo /home/.BlueGriffon/bluegriffon 
```

It start al right! I did installed on home directory because I did try on a system folder and it was giving me permission problem.

anyone got a idea what is going on?

I did try:

chmod 666 .BlueGriffon ( and some variation) and went manually at the folder too! 

thanks for helping!


I have uninstall this version! and install the 1.3

buy running the installer

```
sudo chmod +x BlueGriffon-1.3-Linux-x86-Install
./BlueGriffon-1.3-Linux-x86-Install

```

I installed under Home

then I changed the the permission by

```
sudo chmod -R 777 .BlueGriffon

```

then I changed the owner and the group (root was for both of them)

```
 sudo chown -Rv username:group .BlueGriffon

```

And I still not being able to open it from the desktop linker

The only way is typing this on the terminal

```
sudo /home/ccc/.BlueGriffon/bluegriffon 
```

What is going on? Thanks for helping

---

### Post by Peter2009 on 2011-11-21
> **Peter2009 said:**
> Hi!

I have installed BlueGriffon 

and I get this message if I try to double click it!



If I run on the terminal

```
sudo /home/.BlueGriffon/bluegriffon 
```

It start al right! I did installed on home directory because I did try on a system folder and it was giving me permission problem.

anyone got a idea what is going on?

I did try:

chmod 666 .BlueGriffon ( and some variation) and went manually at the folder too! 

thanks for helping!

I can see my post in another forum in [here]("http://www.computersupportforums.com/showthread.php?tid=24562") and [here]("http://friendfeed.com/internationale/720f9d5c/ubuntu-your-bluegriffon-profile-cannot-be")
Really weird

---

### Post by Peter2009 on 2011-11-21
> **Peter2009 said:**
> I have uninstall this version! and install the 1.3

buy running the installer

```
sudo chmod +x BlueGriffon-1.3-Linux-x86-Install
./BlueGriffon-1.3-Linux-x86-Install

```

I installed under Home

then I changed the the permission by

```
sudo chmod -R 777 .BlueGriffon

```

then I changed the owner and the group (root was for both of them)

```
 sudo chown -Rv username:group .BlueGriffon

```

And I still not being able to open it from the desktop linker

The only way is typing this on the terminal

```
sudo /home/ccc/.BlueGriffon/bluegriffon 
```

What is going on? Thanks for helping


Did something different here:

I unistall (again)

now installed without using sudo before running the installed file.

The file now got the username and group right, BUT its not opening.

getting the following error:

```
Your BlueGriffon profile cannot be loaded. It may be missing or inaccessible
```

---

### Post by davdo2004 on 2011-11-21
You don't say which version of Ubuntu you are running but you might want to look at .....
[http://www.webupd8.org/2011/01/bluegriffon-new-wysiwyg-editor-which.html](http://www.webupd8.org/2011/01/bluegriffon-new-wysiwyg-editor-which.html)

---

### Post by Peter2009 on 2011-11-21
> **davdo2004 said:**
> You don't say which version of Ubuntu you are running but you might want to look at .....
[http://www.webupd8.org/2011/01/bluegriffon-new-wysiwyg-editor-which.html](http://www.webupd8.org/2011/01/bluegriffon-new-wysiwyg-editor-which.html)

To be honest I didnt want to do this again but anyhow I did it one more time.

and not this does not work!! (it save you to go to the terminal and change the install file to be able to be executable with the chmod -x) .(Note not to davdo2004:  If you joining here looked a my previous post in this threat if you are not following me)

I summary I already have tried this in a different way!!! Thanks for the input

---

### Post by Peter2009 on 2011-12-01
> **Peter2009 said:**
> To be honest I didnt want to do this again but anyhow I did it one more time.

and not this does not work!! (it save you to go to the terminal and change the install file to be able to be executable with the chmod -x) .(Note not to davdo2004:  If you joining here looked a my previous post in this threat if you are not following me)

I summary I already have tried this in a different way!!! Thanks for the input

Come on guy I will like to sort this issue!! :-(

---

### Post by jagrock on 2012-09-02
This issue is present also in ubuntu 12.04. If you installed BlueGriffon and get this message the solution is to change the owner of the profile BlueGriffon directory.

In your home directory make ls -la, it will display the next directory:

```
drwx------  3 root   root       4096 sep  1 18:39 .disruptive innovations sarl

```
Change the owner of ".disruptive innovations sarl" by executing:

```
user@machine:~$ sudo chown -R user.user .disruptive\ innovations\ sarl/

Where user is your username.
```

Regards.

---


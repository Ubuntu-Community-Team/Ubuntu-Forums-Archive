---
title: "Problems after update"
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by rkay on 2010-04-05
Hi, i'm new on this forum, and my english isn't that good :)

i have installed ubuntu 9.10 on my hp nx6325 notebook, and everything was working just fine, then it updated and problem started coming up. 
First the computer wouldn't reboot after the update, blank screen, then i manually reboted and now some programs don't work (ubuntu software center, update maneger, avant window navigator)

i assume the update did some damage, so how can i repair this, is there a recovery tool or something.

hope i didn't open the same topic again, sorry if i did.

so please help with thi

Klemen...

---

### Post by drs305 on 2010-04-05
Hi kray, welcome to the Ubuntu forums.

Sorry you are having problems with the update. 

Do you know what you updated? If you updated the kernel, you can try using the previous one by selecting it in the Grub menu on startup. The previous kernel would normally be the third entry. Look for an entry with a lower number (-19 rather than -20, for example) and not an entry listed as "recovery mode".  See if the problem still exists.

Sometimes you can tell what is wrong by opening the application in a terminal window. There may be error messages generated when starting an application in this manner that will help us determine the problem.

To open a terminal, use the Applications, Accessories, Terminal menu. Next open one of the packages that is creating the problem. We will use Update-Manager. Type the following in the terminal. Once you press ENTER, it will ask for your password. You won't see it as you type - that is normal. Just type it in and press ENTER.

At that point, either the application will open or an error message will be generated in the terminal window. If you get an error message, please tell us what it is.

To start Update Manager:
```
gksudo update-manager
```

To try to update your system via terminal, and possibly download fixes for previous problems, you may also try:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by rkay on 2010-04-05
when i updated it downloaded 274 updates, so i don't really know what it downloaded.

I've tried the previous kernel as you said, but the problems are the same.

running the update maneger in terminal window doesn't do anything, the cursor starts working but the terminal show nothing


klemen@ubuntu:~$ gksudo update-maneger
klemen@ubuntu:~$ 


i've already tried the upgrade and update in terminal, they perform normaly, but the problems stay the same.

thank for your help :)

---

### Post by rkay on 2010-04-05
oh and it didn't ask me for my password like you said, it opened a seperate grey window and asked me for my password. when i tried again it didn't ask me at all.

---

### Post by drs305 on 2010-04-05
> **rkay said:**
> 
klemen@ubuntu:~$ gksudo update-maneger
klemen@ubuntu:~$
thank for your help :)

Just make sure you typed it correctly: 
```
gksudo update-*man**a**ger*
```

It's normally best to cut/paste terminal commands just to prevent typos. One of the nice features is you can highlight text with your mouse, move to where you want to paste it, and click the middle mouse button to paste it.

---

### Post by rkay on 2010-04-05
hehe, how dumb do i feel right now :)

okay here it is:


klemen@ubuntu:~$ gksudo update-manager
Traceback (most recent call last):  File "/usr/bin/update-manager", line 26, in <module>
    import pygtk
ImportError: No module named pygtk
klemen@ubuntu:~$ 


how do i make the code window in threads?

---

### Post by drs305 on 2010-04-05
A few things.

The reason you weren't asked for the password the second time you ran the command is because there is a timeout built in. If you enter the same command requiring root access you will not be asked again for the specified timeout period. The default is 15 minutes I believe, and can be changed by the user by editing the sudoers file (search the forums for examples).

To use "code" tags, you click the **#** symbol in the post's menu. This will insert [noparse]```

```[/noparse] tags. Paste or type between the two.

As for your problem, a search turned up several posts regarding pygtk. You might be able to solve the problem by reinstalling the following:
```
sudo apt-get install --reinstall python-gobject 
```

---

### Post by rkay on 2010-04-05
it worked, thanks a lot, you are a genius :D

all the programs that didn't work now work just fine.

Thanks :D

---

### Post by drs305 on 2010-04-05
> **rkay said:**
> it worked, thanks a lot

:-)

Glad you restored Ubuntu to good working order.

If you wouldn't mind, please mark this thread "Solved". Doing so helps others who are looking for posts with known solutions, and allows the 'helpers' to concentrate on posts that still need attention.

To mark a post 'Solved', click on the "Thread Tools" link at the top right of the first post and select "Mark this thread as solved". You can also mark the post "Unsolved" from the same link if it turns out that more assistance is needed.

---


---
title: "Can't login as administrator in ubuntu 11.10"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by Ditirambe on 2011-10-14
Hello,

I have just upgraded from Ubuntu 11.04 to Ubuntu 11.10 and when trying to log in with my old user account (administrator) it brings me back to the log in screen. I don't get any type of error it's just does as if it's loading the desktop and then goes back to log in screen.

I'm currently logged in as a guest but I have restrictions and I can't modify too much.

Anyone could help me please?

Thanks

---

### Post by collisionystm on 2011-10-14
hit CTRL + ALT + F1

see if you can login there

You can hit CTRL + ALT + F7 to go back to normal screen

---

### Post by rob1s on 2011-10-14
Same problem to me.

Yes I can login when in non-graphical mode (CTRL + ALT + F1), but I can't login normally. It's extremely annoying. Please help.

Thanks in advance!

Robert

---

### Post by mohansathish on 2011-10-14
I hope #7 in [http://ubuntuforums.org/showthread.php?t=1859233](http://ubuntuforums.org/showthread.php?t=1859233) will help your issue.

Kindly mark the thread as closed if you got the solution




-----
Please mark the thread as solved once you have got the solution
Click me: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by pankajso on 2011-10-15
I had the same issue.
Logging in a text console (Alt+Ctrl+F1 at the login screen) and issuing:
sudo rm ~/.Xauthority
solved the issue.
I hope it helps.

---

### Post by kchida on 2011-10-15
Solved x 2!!!

I had the same problems, but nothing I found online worked.  I narrowed it down to a buggy .profile bash script in the home directory. I can reproduce the problem reliably. In my case, it was some bash code for Python pip code completion.  More info in the link.  

[http://askubuntu.com/questions/66482/cant-login-after-installing-11-10/66704#66704]("http://askubuntu.com/questions/66482/cant-login-after-installing-11-10/66704#66704")

---

### Post by gknauth on 2011-10-16
[FONT="Lucida Console"]pankajso[/FONT]'s solution of:  [FONT="Lucida Console"]sudo rm ~/.Xauthority[/FONT]
worked for me.  I logged in remotely and issued that from the command line.

---

### Post by pylon42 on 2011-11-03
Same problem and the posted solution worked for me - thanks!

---

### Post by ifoolb on 2012-06-28
> **pankajso said:**
> I had the same issue.
Logging in a text console (Alt+Ctrl+F1 at the login screen) and issuing:
sudo rm ~/.Xauthority
solved the issue.
I hope it helps.
This also works for me.But I don't know why .Xauthority affects login,anyway I checked it and found it was an empty document.

---

### Post by yeuser on 2012-09-29
Hi,
I had the same problem, but none of above worked for me!
In fact it was just a permission issue, both /tmp and /home could not be accessed by users except root and guest.
It was only a **chmod 777** for me.
Hope this info helps others too.

---


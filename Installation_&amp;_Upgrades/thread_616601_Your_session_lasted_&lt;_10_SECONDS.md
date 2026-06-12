---
title: "Your session lasted &lt; 10 SECONDS"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by goslings on 2007-11-18
I've almost installed Ubuntu .....
But I've just come back to the machine and tried to run from dual boot
and I have the following 
Your session lasted only 10 seconds  .... I've tried going in under the failsafe modes, there is enough disk space I made / swap and a /home all with the suggested settings ....
What is the matter . .... 
be gentile on replies I'll need a step by step (if there is a workaround)

thanks

---

### Post by goslings on 2007-11-18
GRrrr
quick search revealed some solutions, but none seem to work 
So frustrating Ubuntu is soooo close, but  ....
Anyone any idea ??
regards

---

### Post by goslings on 2007-11-19
will have to wait to next weekend now ....
But if anyone has any ideas I would appreciate it.
Tried a raft of stuff last night.
Finally reinstalled ubunto into the predefined areas and redefined the imported users again 
BUT Still no joy

---

### Post by veloce on 2007-11-19
> **goslings said:**
> will have to wait to next weekend now ....
But if anyone has any ideas I would appreciate it.
Tried a raft of stuff last night.
Finally reinstalled ubunto into the predefined areas and redefined the imported users again 
BUT Still no joy

Imported users?

Try checking the ownership and permissions of each users' home directory.

---

### Post by goslings on 2007-11-19
Sorry poor explanation.
the install highlights the users under winxp and allows you set up accounts for them ... 
think I tried this lost of chmods, think they are all as they should be .
thanks

---

### Post by goslings on 2007-11-22
"bump" - As I can only try at weekends.
cant believe nobody has actually experienced this?
regards

---

### Post by veloce on 2007-11-22
So your home directories have these permissions?

drwxr-xr-x 66 username    username  2488 2007-11-23 08:19 username

---

### Post by goslings on 2007-11-23
> **veloce said:**
> So your home directories have these permissions?
drwxr-xr-x 66 username    username  2488 2007-11-23 08:19 username

Yes
chmod 775 on each of the home directories for each user migrated from winxp
Cannot login to any, either by F10 1/2 or via either failsafe 
can *only*  login  via  Ctrl ALt F1
absolute frustration:( , almost at the point of going back to windows 
regards

---

### Post by goslings on 2007-11-24
sadly for me this ubuntu "out of the box" eperiience is beginnng to be a failure
can get into U7.10 
the shear quantity of messages that dropes in here means the likely hood of a response (for me) is unlikely
I've use UNIX for over 20years on mainly SGI 
IRIX was never this querky to set up

drwxr-xr-x or chmod 775 on the home directories 
removed .ICEauthority 
just a real pain 
tried a reinstall
No joy  

Is there a standard reponse (from Ubuntu) that overcomes this major issue for me 
thanks

---

### Post by veloce on 2007-11-24
drwxr-xr-x is 755 not 775

---

### Post by goslings on 2007-11-24
sorry it was a typo meant 755

---

### Post by goslings on 2007-11-24
but makes me think did I do the same typo on the pc 
.... i'll check 
cheers

---

### Post by goslings on 2007-11-24
no i did do 755
still in the dark 
please someone any ideas 
thanks

---

### Post by xeth_delta on 2007-11-24
Do you have enough space on the disk where your system is installed?

```
df -h
```

What are the permissions and who is the owner of your **/tmp**, **/var/tmp** and **/var** directories? They should be owned by root and the permissions **drwxrwxrwt** for **/tmp** and **/var/tmp** and **drwxr-xr-x** for **/var**.

Xeth

---

### Post by goslings on 2007-11-24
> **xeth_delta said:**
> Do you have enough space on the disk where your system is installed?

? They should be owned by root and the permissions **drwxrwxrwt** for **/tmp** and **/var/tmp**and **drwxr-xr-x** for **/var**.
Xeth

Filesystem, size, avail, use, mounted
/dev/sda7 11G, 2.1G, 21%, /
/dev/sda6, 2.5G, 2.4G, 100%, /home 

but I read somewhere that the home directory  needs only to be 2.5Gb
- ah but I have imported all the three users on the winxp system .. so maybe this needed more than the suggested 
It asked for administration account, which I assume is the root account but I cannot modify the permissions of /tmp logging - whats the root passwd - its is not root 
thanks for the clarity

---

### Post by xeth_delta on 2007-11-24
>  Filesystem, size, avail, use, mounted
/dev/sda7 11G, 2.1G, 21%, /
/dev/sda6, 2.5G, 2.4G, 100%, /home 

That might be the problem. I would really recommend a much bigger home directory, if possible, not just 2.5 GB. After all, that's where you will store your personal files.

> It asked for administration account, which I assume is the root account but I cannot modify the permissions of /tmp logging - whats the root passwd - its is not root

You can check the permissions of a file or directory with:
```
ls -al file_or_dir_name
```

If the permissions of a system directory are correct, please do not change them. Putting wrong permissions on **/tmp** could bring many problems.

To execute, a command as root in ubuntu you use **sudo** and your regular password. For instance:
```
sudo apt-get install foo_bar
```

But be careful when you use **sudo**

[EDIT] You should use **sudo** followed by the command you want to run as root, not just **sudo**

---

### Post by goslings on 2007-11-24
thanks
I can boot off the live CD to run Gparted and resize the /home
Do I need to reinstall inorder to  get all imported files off 3 winxpp users ?
I expect the answer to this is yes, as it still says 10 sec time out with 25Gb
In which case the install should have bombed out with not enough space in the 1st place ???

---

### Post by ryanVickers on 2007-11-24
I think I had a similar problem - it also said something about some kind of "authority files"?.... I ended up re-installing :(

---

### Post by xeth_delta on 2007-11-24
> **goslings said:**
> thanks
I can boot off the live CD to run Gparted and resize the /home
Do I need to reinstall inorder to  get all imported files off 3 winxpp users ?
I expect the answer to this is yes, as it still says 10 sec time out with 25Gb
In which case the install should have bombed out with not enough space in the 1st place ???

First of all, make a backup of those important files you have in /home.

I am sorry, what do you mean by imported ccount files? Did you copy them yourself or did the installation do that for you? I did not know the installation cd could import users from Windows.

Did you perhaps mean 2.5 GB instead of 25 GB? Did you resize the partition already?

In principle, you can create user accounts at any time once you installed the system, then copy the files you need from the windows partition on their directories. I am not sure I understand your question.

What do you meanin the last question?

Xeth

---

### Post by theredspecial on 2007-11-24
I had the same error (although I was running Xubuntu for some time already)
Does this post help: [http://ubuntuforums.org/showthread.php?t=621473?](http://ubuntuforums.org/showthread.php?t=621473?)

---

### Post by goslings on 2007-11-25
[QUOTE=xeth_delta;3830631]
To execute, a command as root in ubuntu you use **sudo** and your regular password. For instance:
```
sudo apt-get install foo_bar
```
QUOTE]

sudo just reports 
sudo: must be setuid root ?
looks like tmp is not set correctly

---

### Post by ryanVickers on 2007-11-25
well, you don't just type sudo, it would be sudo and then the command you want to run as root, so if you wanted to run gesit as root, it would be sudo gedit instead of su root and then gedit :p

---

### Post by goslings on 2007-11-26
Thanks for everyones help - only have weekend to play with this as work away

Ran out of patience with trying to mess about with permissions.
Resized /home to take migration of users stuff and reinstalled 
All worked fine. 
udated software, even told me I had 3rd part drivers for wireless bcm43xx
(PC linux fel over at this point)

Now I can enjoy a really good cup of Ubuntu, but expect I'll be back

thanks again.
Ian

---


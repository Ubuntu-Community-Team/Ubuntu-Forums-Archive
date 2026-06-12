---
title: "Login user changed can't open terminal or changed back to the old"
date: 2023-08-28
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2023-08-28
I have run a code with a user A that has changed my login user 
I can see that in Settings/User name A
how can I changed back to the old user ?
It is ubuntu 23.04 not kunbuntu 

Cheers

---

### Post by MAFoElffen on 2023-08-28
What do you mean the user "changed"?

Names? Groups? What and how fif this happen (if you had to guess)?

Trying to understand what has happened so thar it might be corrected...

---

### Post by hoboy on 2023-08-28
lets said that my user was Test after running the code I can't open any terminal that mean I can't use any terminal  when I open ubuntu settings the users I see Test.
I have opened pycharm/terminal I see test@test:~/
but my settings users/name is AA I have not changed to that.
My only option to access terminal is using Pycharm ide.
it was working fine before I run the code

---

### Post by yancek on 2023-08-28
You indicate you ran some code and have had the problem since then.  What code exactly did you run?  Pycharm has its own terminal emulator.  Can you close it and open another terminal?  If you are using the pycharm terminal I don't think you can switch users.  The page below is the pycharm site, did you read through the instructions there?

[https://www.jetbrains.com/help/pycharm/settings-tools-terminal.html#application-settings](https://www.jetbrains.com/help/pycharm/settings-tools-terminal.html#application-settings)

---

### Post by hoboy on 2023-08-28
the problem is that I can't launch any terminal.
when I try to launch the Terminal that is part of ubuntu then terminal windows open, but get the following error message in the terminal.
The child process exited normaly with status 1
Terminal opened windows has relaunch.

---

### Post by ajgreeny on 2023-08-28
Try using Ctrl+Alt+ F1 to get to a tty command line and login there with username and password.
From there you can run the same commands that you normally run in a GUI  terminal.

Assuming you used a normal terminal to run that original troublesome command and not a pycharm terminal, you should find the command by using command ***history***.

---

### Post by MAFoElffen on 2023-08-28
+1 with ajgreeny, except I would use a combination of hot-keys trying <Cntrl><Alt><F2> through <Cntrl><Alt><F6>...

Reason why? vtty1 is usually reserved for the boot messaging service, so most of the time, on Desktop Edition, it still has those messages displayed there. vtty7 is usually reserved for the Graphical Desktop... except for a point of time, sometime back a time ago, when it was left unbound and just started in the next available unused vtty, which was vtty2... That has since changed back with Ubuntu, but still happens with other Distro's.

Because of those, I usually tell people to try <Cntrl><Alt><F4>... which vtty4 is usually always open.

---

### Post by hoboy on 2023-08-29
When I use Ctrl+Alt+F1 I get the desktop with a user I do not have the password.
when I change to the old user I can login ... how can I set the old user that the when the computer start it use the old user to login.

Cheers

---

### Post by yancek on 2023-08-29
If you have more than one user, you should see both user options in the GUI login.  Do you have autologin enabled for the wrong user?  You can change that by first opening a terminal and doing:  su olduser (switch user and replace olduser with the actual user name).  Once that is done, follow the instructions at the link below.

[https://help.ubuntu.com/stable/ubuntu-help/user-autologin.html.en](https://help.ubuntu.com/stable/ubuntu-help/user-autologin.html.en)

It would help greatly if you could post the command(s) you ran to make this change originally that created the problem.

---

### Post by hoboy on 2023-08-29
the tricky part is that the user name that is show in desktop during starting do not exist 
when I run getent passwd
I get test@test:~/
but in the desktop gui there is a user name called tester the desktop always start with this user name but I can't find it in the users defined in ubuntu users, and no password much it.
when I manually change the user to test and password I login ... but no application works, like ubuntu Terminal application when I click on it to launch I get this error "This account is currently not available"
Ctrl + Alt + T  doesn't work it a window is opened then close very quickly, like a blink.
lslogins -u
 UID USER PROC PWD-LOCK PWD-DENY LAST-LOGIN GECOS
   0 root  202                              root
1000 test   131                        11:04 User for WildFly
it shouldn't be this 
1000 test   131                        11:04 User for WildFly
it should be 
1000 test   131                        11:04 User for test
I am also  getting this error
sudo lslogins test.
Failed login terminal:              tty3    


Cheers

---

### Post by hoboy on 2023-08-29
Some body help

---

### Post by MAFoElffen on 2023-08-29
I cannot and will not help you. Sorry.

I deal with solutions based on gathered facts and history. I will not play a guessing game on that.

If you cannot post the command you used and what it changed what from ---> to what it is now, and cannot post what the problem is now... Then I will not guess on how to help you. That just does not make sense to me.

I don't know if you tried to modify the name of the original user, or ???? See? If you provided no specifics, then there is nothing to discuss or answer. It may make sense to you, but seems to not make sense to us.

---

### Post by ajgreeny on 2023-08-29
Guessing what you did and where we are now will not help you solve this!

I will continue for a while to try and as a start please show the output of terminal command ```
ls /home
``` which will list all the users that have been set up on the computer.
Does that list contain the user that you tell us does not exist?

PS:
Any commands used in the past will also show in a simple text file in your home named ***.bash_history***.
To  see it and be able to open it to search for the problem command you may need to use Ctrl+H after you've opened the file manager in order to show hidden files and folders (those with names starting with a period (.)

---

### Post by MAFoElffen on 2023-08-29
+1

I am just guessing from the 100's of commands that someone might use, that if you used chmod to rename a user, what happens is that it changes the user_name... This cannot be done unless you login as root or are at a the elevated status of an admin user, without the user being change logged in. Why, because that command cannot change the name of a user that has any active process running.

What will happen when you do that, is to change the user_name is /etc/passwd & /etc/shadow, with the original UUID & GUID, associated home folder and passwd is still the old ones. But it renames the old user_name to a newer user_name.
```

sudo usermod -l <new-login-name> <old-login-name>
sudo groupmod -n <new-loginname> <old-login-name>
sudo usermod -u <UID> <login-name>
sudo mkdir /home/<New-login-name>
sudo usermod -d /home/<new-login-name> -m <old-login-name>

```
...With what ajgreeny was asking, if the User's $HOME does not match the results from /home/<login-name>

OR... None of that might not be related at all. We just do not know.

---

### Post by hoboy on 2023-08-30
Please don't give up on me.
I can open any terminal at all so I can't even run any terminal command
but I only open Pycharm IDE and use the terminal of that 
test@test:~$ ls /home
linuxbrew  test
I have not run any command to change to use in terminal 
I have run an ansible script that has changed the user I can't see how 
cheer

---

### Post by SeijiSensei on 2023-08-30
Show us the ansible script in [noparse]```

```[/noparse] tags.

---

### Post by MAFoElffen on 2023-08-31
We have asked you what happens if you toggled the hot-keys <Cntrl><Alt><F4>, to get to console VTTY4 to log in and have access to the command line prompt. I didn't see any answers to that.

Another way would be to either start in mode INIT3 or to use the rescue menu to drop down to root prompt.

From either of those 3 methods, you could create a new user, that is a member of the sudo group, to see if that user has a problem or not.

---

### Post by hoboy on 2023-09-01
The issue is solved  but can't find the display saying resolved.
I have actually ask chatgpt that suggested some commands that has solved the problem.

---

### Post by ajgreeny on 2023-09-01
Please mark as **SOLVED** from the **Thread Tools** menu at the top right of every page.

And please don't leave us wondering; what were the answers you received from ChatGPT?

---

### Post by hoboy on 2023-09-01
> **ajgreeny said:**
> Please mark as **SOLVED** from the **Thread Tools** menu at the top right of every page.

And please don't leave us wondering; what were the answers you received from ChatGPT?

Well chatgpt suggested the following  commands that has solved the issue
sudo usermod -s /bin/bash -d /home/test test
sudo passwd test
id -u test
sudo usermod -u 1001 test
sudo find / -user old_uid -exec chown -h new_uid {} +

---

### Post by MAFoElffen on 2023-09-02
LOL, just like was posted already... LOL.

---


---
title: "password not accepted after  installation of Ubuntu 5.04"
date: 2005-03-13
forum: Installation &amp; Upgrades
---

### Post by Victor Warner on 2005-03-13
When accessing various tools/utilities etc which ask for the root password I either get an error message or nothing happens. As examples:

1. SystemAdministration/Shared Folders: error message: "Failed to run shares-admin as user root: Child terminated with 1 status"

2. On icon stating that there are a number of updates available: "Failed to run /usr/bin/update-manager as user root: Child terminated with 1 status"

3. Applications/System Tools/Root Terminal. Asked for password and get the following message: "Failed to run /usr/bin/x-terminal-emulator as user root: Child terminated with 1 status"

Any help to solve this problem would be greatly appreciated.

Victor Warner

---

### Post by alastair on 2005-03-13
Make sure it is nothing silly e.g. capslock on etc. and you use the right password.

[http://www.ubuntulinux.org/support/documentation/faq/root](http://www.ubuntulinux.org/support/documentation/faq/root)

This is YOUR username's password. By default, "root" is disabled.

---

### Post by Victor Warner on 2005-03-13
Alastair,

Thank you for your reply. 

I am sure that I am typing in the right password. I tired the suggestions in the link, but get this message: "victor is not in the sudoers file.  This incident will be reported."

Also how do I check (or reset) the root password?

Any further help would be greatly appreciated.

Victor Warner

---

### Post by tjfitz on 2005-03-14
Victor, I am getting the exact same problem as you. I discovered it by trying to start synaptic. The first time I tried starting synaptic, nothing happened at all. When I tried again, I got the password request box and the same error, "Child terminated with 1 status." I got this error when entering my own password, the root password, and some random characters that aren't a password at all. I was able to log in as root and run synaptic, so obviously the problem isn't with synaptic.

---

### Post by manuska on 2005-04-11
This happened to me too after I messed with some files in /usr. I got it fixed by setting SUID-bit for /usr/bin/sudo.

---

### Post by ryu kun on 2005-04-30
This is my first day on Linux, and experienced the same problem.

After trying, trying and researching, here is how I solved this:

------

1. applications -> system tools -> terminal
2. su (type this and press enter)
3. (enter root password) 
(after correct passwort "yourusername@..." should be "root@...")
4. visudo (type this and press enter)

5. below these lines:

# User privilege specification
root    ALL=(ALL) ALL

add this line:

yourusername ALL = ALL

6. save changes, close the terminal.

------

Now you should be able to run anything in System -> Administrator menu without any trouble.

 :!:  I am not sure that granting your user account the authority to run any command on any host is secure. When I changed the line which we added like: "yourusername ALL = PASSWD: ALL" it should ask your userpassword according to the manual, but this change did not have any effect here, it still dont ask any password when running administration commands.

You may find info about sudoers (list of which users may execute what) here: [http://www.courtesan.com/sudo/man/sudoers.html](http://www.courtesan.com/sudo/man/sudoers.html)

---

### Post by leezer3 on 2005-05-01
I think that the trouble with this, is that it will make your PC much more vunerable, as you're going to be doing everything in super-user mode. Try 
sudo passwd 
& then enter a new password, & maybe that'll help. I also somewhere, (not sure where, have a look in the Wiki) enabled the root account, which solved most of my root probs.

-Leezer-

---

### Post by ryu kun on 2005-05-01
"sudo passwd & then enter a new password method" doesnt work. Still asking a password and giving "child terminated" error whatever you type as password.

Editing the sudoers file as I described above solved the problem but I have doubts about security. 

Any comment about the effect of this on security would be greatly appreciated.

---

### Post by nortoncillo on 2005-05-03
in a console edit   /etc/sudoers

sudoers is a list of users with the permision to use the sudo command, that means, SUper user DO or ejecute that command... 
so you'll need to acces to the sudoers with write permisions...
and add the names of users that will have the permision to use the sudo command..

i do not recomend to add all the users...  just add a few, the experienced ones

---


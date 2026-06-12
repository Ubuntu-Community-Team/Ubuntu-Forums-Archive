---
title: "terminal"
date: 2020-01-06
forum: Installation &amp; Upgrades
---

### Post by angel mike on 2020-01-06
On my new Dell XPS 13 7390 with Ubuntu 18.04 preloaded - I miss-typed the computer name (hostname) as 'michaelb' instead of 'michael'.

I have managed to change the hostname using ```
 **sudo nano /etc/hostname 
``` and ```
 **[B]sudo nano /etc/hosts
```

but in the terminal I now get ```
 michaelb@michael:~$ 
```
[/B]

---

### Post by Holger_Gehrke on 2020-01-06
The default prompt in Ubuntu is '\u@\h:\w\$' which translates to username@hostname:workingDirectory. The 'michaelb' you get as part of the prompt is the user name, the 'michael' is the host name and '~' is shell short hand for your home directory.

Holger

---

### Post by angel mike on 2020-01-07
Thanks for that info Holger - how do I go about amending the terminal prompt?

---

### Post by Holger_Gehrke on 2020-01-07
The various prompts the shell will give you are stored in the variables PS0 to PS4. The primary command prompt is in PS1. By changing the value of that variable you can change the prompt for the current shell. By putting your prompt definition in one of the scripts that run during the start of the shell (~/.profile or ~/.bashrc for setting for a specific user, /etc/profile or /etc/bash.bashrc for changes for all users) you can make your redefinition permanent.There are many special sequences of characters that will be replaced with various informations if they are part of the prompt definition. Those are listed in the manual page for the shell ('man bash') in the section 'PROMPTING'.
Example:
```

PS1='\s-\v\$'

```
would set the prompt to give the name of the shell and it's version followed by a '$' if you're a normal user or a '#' if you're root. If you do a web search for 'bash prompt' you'll find some interesting example of what can be done.

Holger

---

### Post by P-I H on 2020-01-07
I changed this on computer and followed this instruction
You need to edit the computer name in two files:
/etc/hostname 
and
/etc/hosts
These will both need administrative access, so run
sudo nano /path/to/file
Replace any instances of the existing computer name with your new one. When complete run sudo service hostname restart or restart your computer and the name will have been changed.
New name:

---

### Post by Impavidus on 2020-01-07
If you just change your prompt, your old username will still pop up all the time. To actually change the username, have a look here (it's a bit old, but I expect it still works): [https://askubuntu.com/questions/34074/how-do-i-change-my-username](https://askubuntu.com/questions/34074/how-do-i-change-my-username)
Top answer seems best (as usual, but not always). Instead of ctrl+alt+F1 and ctrl+alt+F7, you may need other F keys. There have been some changes recently. Just try. But read the comments and other answers too, as they point out some potential problems.

---

### Post by TheFu on 2020-01-07
> **angel mike said:**
>  
but in the terminal I now get ```
 michaelb@michael:~$ 
```
[/B]

There are good reasons to leave this prompt as is.  That exact prompt can be copy/pasted into rsync or scp to move files between different systems.  It is extremely convenient.

```
rsync -avz michaelb@michael:~/  /tmp/
```
will copy everything in the hostname michael HOME directory for michaelb into a director under /tmp/ on the local machine.  This assumes you have 2 Unix systems and are NOT on the "michael" machine.  Very handy.  It is also useful for use inside most Linux file managers to connect to remove files on other systems using sftp://

There is almost always a good reason for defaults.

Now, about this username michaelb - seems long to me.  I'd make that 'mb' to avoid typing so much.  I prefer short usernames.

---

### Post by angel mike on 2020-01-08
Thanks all for those responses - yes the main problem is changing the Username - not quite that straight forward but did get some guidance from the askubuntu website - I think the easiest way is going to reload the OS with 18.04 install USB. Any thanks once again. I'll mark is solved though.

---

### Post by TheFu on 2020-01-08
> **angel mike said:**
> Thanks all for those responses - yes the main problem is changing the Username - not quite that straight forward but did get some guidance from the askubuntu website - I think the easiest way is going to reload the OS with 18.04 install USB. Any thanks once again. I'll mark is solved though.

Changing a username is trivial, but not if you aren't comfortable editing 4 text files in /etc/ in a consistent way.
The files are passwd, shadow, group, and gshadow.  Also probably want to move the HOME directory to match the newer name, but that isn't strictly mandatory.  Not having the username and HOME directory location match the normal setup can cause human confusion later, but the system really doesn't care.  Same for the mail spool, if you have setup an MTA on the machine.

Changing the matching groupname is completely optional too. But again, it will be different from the typical setup and can cause human confusion later. The system doesn't care.

Find any reference to the username you want to change and change it in all 4 files.  If you can do it (save them) within a second of each other, you can do it on a live system. If you cannot, then boot from a flash drive, use the "try ubuntu" option, mount the partition where /etc/ is located and modify those files.

*This is one of those things that is harder to explain in text than to just do.*
I would open 4 terminals, inside each terminal, I'd use **sudoedit** to edit each file, but not save them until I'm ready to do it all at once. Then I'd save by closing the editor the gshadow, group, shadow, and passwd files as quickly as possible. Definitely in less than 1 second. The problem is that if the sudoedit command checks the current state and it is inconsistent between those files, writing the files could fail.  If that happens, use the **Try Ubuntu** method. No harm done, really.

Just be certain you have a flash drive already setup that boots and has "try ubuntu" option.  I use an Ubuntu-Mate flash drive for this when needed.  It is loaded and marked for that purpose.  There are lots of reasons to have a flash drive setup in that way to handle any other issues that might happen. Both HW failures and my dumb mistakes can be fixed.

Someone could make a **sed** script to do this pretty easily, provided the old username doesn't look like the new username too much.  There might be a way using usermod or is that moduser to accomplish the same thing. I'd have to check the manpages.  Check out the -l option for usermod.

Worst case, this is 3 minutes of time for me.  That's much quicker than doing a fresh install and restoring backup data.  Don't get me wrong, I can do that in 30-45 minutes to have a system with my data, settings, programs all back, but 3 minutes is much better than 45m, right?

---

### Post by angel mike on 2020-01-10
Thanks TheFu for all that - for me a bit too complex so I'll reinstall the OS

---


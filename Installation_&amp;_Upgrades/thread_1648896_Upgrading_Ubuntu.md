---
title: "Upgrading Ubuntu"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by RumboPumbo on 2010-12-19
Hi, i am needing some help in upgrading my ubuntu version,
at the moment i am running Ubuntu 9.04, i am wanting to get to version 10.10, i was going to do the upgrade using the upgrade manager but when i go onto the upgrade management it comes up with the following error message:

[IMG]http://i289.photobucket.com/albums/ll205/SwanseaCity_GP/upgrademanager-1.gif[/IMG]
Is there a way to get rid of this message from coming up so then i can upgrade to 9.10 and then to 10.04 and then finally to 10.10?
[IMG]http://ubuntuforums.org/%3Ca%20href=%22http://s289.photobucket.com/albums/ll205/SwanseaCity_GP/?action=view&amp;current=upgrademanager-1.gif%22%20target=%22_blank%22%3E%3Cimg%20src=%22http://i289.photobucket.com/albums/ll205/SwanseaCity_GP/upgrademanager-1.gif%22%20border=%220%22%20alt=%22Photobucket%22%3E%3C/a%3E[/IMG]

---

### Post by chaanakya_chiraag on 2010-12-19
Can you go to the terminal (Applications->Accessories->Terminal) and type in this command:
```
sudo apt-get update
```When it asks for the password, enter YOUR LOGIN password.  ATTENTION: the password WILL NOT show up as you are typing.
Then try this command:
```
sudo apt-get dist-upgrade
```and see what happens.  If you get any errors with either of the above commands, post your error messages here and we'll try to debug.

---

### Post by RumboPumbo on 2010-12-19
Ok, i did that and the error that came up was:

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by chaanakya_chiraag on 2010-12-19
Try the following:
```
sudo cp -r /var/lib/apt/lists ~/apt/lists
sudo rm -rf /var/lib/apt/lists
sudo apt-get update
```
This will first back up the directory you are about to purge in case something goes wrong.  Then, it will proceed to delete the files it just backed up.  Finally, it will run the update command to refresh the package lists.

---

### Post by RumboPumbo on 2010-12-20
i did that first line of 
```
sudo cp -r /var/lib/apt/lists ~/apt/lists
```but got the result of:
```

Report bugs to <bug-coreutils@gnu.org>.
sudo cp -r /var/lib/apt/lists ~/apt/lists
cp: cannot create directory `/home/lloyd/apt/lists': No such file or directory

```

---

### Post by RumboPumbo on 2010-12-20
...

---

### Post by chaanakya_chiraag on 2010-12-20
Sorry...run this first and then run the previous commands:
```
mkdir ~/apt
```

---

### Post by RumboPumbo on 2010-12-20
ok, i did that code and it came up with the following:
```
E: Could not open lock file /var/lib/apt/lists/lock - open (2 No such file or directory)
E: Unable to lock the list directory

```I went onto the update manager, this time the message didn't appear so I clicked to upgrade Ubuntu, it came up with the release notes, i clicked on upgrade at the bottom but nothing happened.

Thanks so far for the help.

---

### Post by chaanakya_chiraag on 2010-12-20
So can you try this code:
```
sudo touch /var/lib/apt/lists/lock
```
then try the ```
sudo apt-get update
``` command again.

---

### Post by RumboPumbo on 2010-12-20
nope, isnt working, it says: 
```
touch: cannot touch `/var/lib/apt/lists/lock': No such file or directory

```

---

### Post by chaanakya_chiraag on 2010-12-20
hmm...I'm guessing that second command removed the lists directory.  Try this command before the touch command:
```
sudo mkdir /var/lib/apt/lists
```

EDIT: Actually, maybe that command is all that is needed...try the ```
sudo apt-get update
``` command after the one above.  If it doesn't work, try the touch command and then try the update command.

---


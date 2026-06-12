---
title: "Innotek Virtualbox"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by Malice007 on 2007-10-24
I installed VirtualBox and every time I want to load a OS I must go to terminal and type:
sudo chmod 666 /dev/vboxdrv

Or VirtualBox will not run the other OS. 

My question is how can I make it so I do not have to type this every time I want to use this program?

---

### Post by wesley_of_course on 2007-10-24
Afternoon ,  I  believe you need to add yourself to vboxusers group . 
 System , Administration , Users and Groups . User settings , Manage Groups , 
 scroll down and click on vboxusers , click on properties and then put a check mark next to your user name.  Might need to log out and login to take effect , don't remember !

                 Virtual Box is Great !, try a distro or Windows without installing !

             Have Fun . Cheers

---

### Post by Malice007 on 2007-10-24
Hello,

Thanks for your help, but I do not see 

System , Administration , Users and Groups . User settings , Manage Groups ,
scroll down and click on vboxusers , click on properties and then put a check mark next to your user name. Might need to log out and login to take effect , don't remember !



I looked all over the place and I cant even find the System when I open up this program.

---

### Post by craftbrewer on 2007-10-24
He's referring to your Ubuntu System menu.

Alternatively you can edit the /etc/group file manually.

```
# sudo gedit /etc/group
```

Search for the vboxusers group, probably near or at the end of the file and add your login id:
```

vboxusers:x:1002:yourLoginID
```

1002 is my groupid for vboxusers, your groupid may differ.  Relogin and you should be good to go.  The VirtualBox web site also has a tutorial with specific examples for Ubuntu.

---

### Post by BoardDWorld on 2007-10-24
Here's the real easy way:

```
sudo gpasswd -a YOURUSERNAME vboxusers
```

---

### Post by wesley_of_course on 2007-10-24
> **BoardDWorld said:**
> Here's the real easy way:

```
sudo gpasswd -a YOURUSERNAME vboxusers
```

 Thanks and that is a whole lot quicker for many things .

 CLI to the rescue  .

---


---
title: "cd commande not possible as su"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by jaaf64 on 2010-08-29
After installing 10.4 I want to check that some file is present under a su directory but the cd command doesn't work after "sudo".

The problem is the same for both 32 bits and 64 bits versions.

Need help.

---

### Post by mörgæs on 2010-08-29
Please post the exact commands and the output from the system.

---

### Post by jaaf64 on 2010-08-29
Here what I get

> jaaf@jaaf-desktop:~$ sudo cd /usr
[sudo] password for jaaf: 
sudo: cd: command not found
jaaf@jaaf-desktop:~$ 

---

### Post by mörgæs on 2010-08-29
But is ```
cd /usr
``` not enough?

---

### Post by jaaf64 on 2010-08-29
In such a case yes.
I just wanted to demonstrate that the cd command was not found.
In reallity I wanted to access a directory I have no permission for.

sudo cd /var/lib/nxserver/home to check for the presence of a file


> jaaf@jaaf-desktop:~$ cd /var/lib/nxserver/home
bash: cd: /var/lib/nxserver/home: Permission non accordée 
jaaf@jaaf-desktop:~$ 


> jaaf@jaaf-desktop:~$ sudo cd /var/lib/nxserver/home
[sudo] password for jaaf: 
sudo: cd: command not found
jaaf@jaaf-desktop:~$

---

### Post by jaaf64 on 2010-08-29
In fact I came to this because

>  [COLOR="Blue"]From [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

Now, we need to transfer the key to the client machine so that it can be imported in the FreeNX client application. First copy the key to your home directory on the server machine:

sudo cp /var/lib/nxserver/home/custom_keys/client.id_dsa.key[/COLOR] ~/


> jaaf@jaaf-desktop:~$ sudo cp /var/lib/nxserver/home/custom_keys/client.id_dsa.key ~/
cp: impossible d'évaluer «/var/lib/nxserver/home/custom_keys/client.id_dsa.key»: Aucun fichier ou dossier de ce type
jaaf@jaaf-desktop:~$ 


translation


> jaaf@jaaf-desktop:~$ sudo cp /var/lib/nxserver/home/custom_keys/client.id_dsa.key ~/
cp: impossible to evaluate «/var/lib/nxserver/home/custom_keys/client.id_dsa.key»: No file or folder of this type
jaaf@jaaf-desktop:~$



and what to think about this?

> [COLOR="Blue"]jaaf@jaaf-desktop:~$ which cp
/bin/cp
jaaf@jaaf-desktop:~$ which cd
jaaf@jaaf-desktop:~$ cd Documents
jaaf@jaaf-desktop:~/Documents$ 
jaaf@jaaf-desktop:~/Documents$ cd ..
jaaf@jaaf-desktop:~$ sudo cd Documents
sudo: cd: command not found
jaaf@jaaf-desktop:~$[/COLOR]

---

### Post by jocko on 2010-08-29
That's because "cd" is not a program, it is a command that is built-in to the shell (so there is no executable file named "cd" anywhere). And by some reason you can't use sudo to run a built-in command... That's just the way it is.
The only way for you to cd as superuser is to switch to a root shell first:
```
sudo -i
cd /whatever/wherever/
```And don't forget to exit the root shell when you are done with what you're doing:
```
exit
```

But your main problem is that you are trying to copy a file that does not exist (/var/lib/nxserver/home/custom_keys/client.id_dsa.key)...

---

### Post by jaaf64 on 2010-08-29
Thank you very much. 
I feel better now as I discover something I ignored (I means build-in commands and sudo -i).

You are right as for the rest.

---


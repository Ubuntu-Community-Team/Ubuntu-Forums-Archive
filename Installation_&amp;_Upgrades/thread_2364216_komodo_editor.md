---
title: "komodo editor"
date: 2017-06-20
forum: Installation &amp; Upgrades
---

### Post by paul2495 on 2017-06-20
is it possible to download and install this on ubuntu 17/04

---

### Post by howefield on 2017-06-20
Sure, download the tar.gz file from the Kimodo website and extract to the folder of your choosing.

Then using the terminal navigate to the folder where you extracted the package to and run..

```
sudo sh install.sh
```

Eg,
```
cd ~/Downloads/Komodo-Edit-10.2.2-17703-linux-x86_64/
```
```
sudo sh install.sh 
[sudo] password for hugh: 
Enter directory in which to install Komodo. Leave blank and
press 'Enter' to use the default [~/Komodo-Edit-10].
Install directory: 


==============================================================================
Komodo Edit 10 has been successfully installed to:
    /home/hugh/Komodo-Edit-10
    
You might want to add 'komodo' to your PATH by adding the 
install dir to you PATH. Bash users can add the following
to their ~/.bashrc file:

    export PATH="/home/hugh/Komodo-Edit-10/bin:$PATH"

Or you could create a symbolic link to 'komodo', e.g.:

    ln -s "/home/hugh/Komodo-Edit-10/bin/komodo" /usr/local/bin/komodo

Documentation is available in Komodo or on the web here:
    http://docs.activestate.com/komodo

Please send us any feedback you have through one of the
channels below:
    komodo-feedback@activestate.com
    irc://irc.mozilla.org/komodo
    https://github.com/Komodo/KomodoEdit/issues

Thank you for using Komodo.
==============================================================================
```

---

### Post by paul2495 on 2017-06-20
so i have downloaded it and extracted it to a folder on my desktop called komodo the i have follwed your instructions and i have got this 


paul@paul-110-530na:~$ sudo sh install.sh
[sudo] password for paul: 
sh: 0: Can't open install.sh
paul@paul-110-530na:~$ cd ~/komodo/Komodo-Edit-10.2.2-17703-linux-x86_64/
bash: cd: /home/paul/komodo/Komodo-Edit-10.2.2-17703-linux-x86_64/: No such file or directory
paul@paul-110-530na:~$

any thoughts

---

### Post by deadflowr on 2017-06-20
Is it on the Desktop?
(Like literally)

---

### Post by paul2495 on 2017-06-20
yes i created a folder and named it komodo and then extracted the contents of the download to that folder

---

### Post by deadflowr on 2017-06-20
If it's actually on the desktop then run
```
cd ~/Desktop/whatever/the/rest/is
```

---

### Post by paul2495 on 2017-06-20
i give up with it

---

### Post by howefield on 2017-06-20
> **paul2495 said:**
> i give up with it

If you are struggling with the location path, try opening the Files Manager and navigate to the Komodo folder where the install.sh file resides.

Then press the Ctrl + L keys to give you the location, copy and paste it back here... eg for me that would b

```
/home/hugh/Downloads/Komodo-Edit-10.2.2-17703-linux-x86_64
```


[ATTACH=CONFIG]275712[/ATTACH]

---


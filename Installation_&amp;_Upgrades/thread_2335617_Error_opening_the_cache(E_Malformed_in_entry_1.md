---
title: "Error opening the cache(E: Malformed in entry 1"
date: 2016-08-30
forum: Installation &amp; Upgrades
---

### Post by dreaddisk on 2016-08-30
well, I got this tiny red dot in my screen after installed google chrom (wifi run shut off so I couldn't finish the installation). that tells me this

> An error occured, please run Package
Manager from the right-click menu or apt-
get in a terminal to see what is wrong.
The error message was: 'Error: Opening
the cache (E:Malformed entry 1 in list file/
etc/apt/sources.list.d/google-chrome.list
(component),E:The list of sources could
not be read.)'. This usually means that your
installed packages have unmet dependencies.

I tried:
first I updated the packages with the command line. did not work.9error persisted)
second, changed the sources.list but it did not worked
third I tried to uninstall chrome, but it said that I can't because chrome was not in my files.

I cant even do thing in my package manager because of this error.

---

### Post by steeldriver on 2016-08-30
Please provide the output of commands

```

cat -n /etc/apt/sources.list.d/google-chrome.list

cat /etc/lsb-release

```

---

### Post by dreaddisk on 2016-08-30
> **steeldriver said:**
> Please provide the output of commands

```

cat -n /etc/apt/sources.list.d/google-chrome.list

cat /etc/lsb-release

```
sorry, then what? It didn't do anything, I;m afraid.

---

### Post by oldos2er on 2016-08-30
Copy and paste each of those commands in a terminal, one at a time, and copy and paste all their output here into a post.

---

### Post by dreaddisk on 2016-08-30
here goes:

> ```
cat -n /etc/apt/sources.list.d/google-chrome.list
     1    deb [arch=amd64] http://d1.google.com/linux/chrome/deb/stable m

$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS"
```

---

### Post by Bashing-om on 2016-08-30
dreaddisk; Good deal .

Progress made.

That line should end in the term main .
```

deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

```

Fire up your favorite text editor

[INDENT][INDENT]make it so
[/INDENT][/INDENT]

---

### Post by dreaddisk on 2016-08-30
> **Bashing-om said:**
> dreaddisk; Good deal .

Progress made.

That line should end in the term main .
```

deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

```

Fire up your favorite text editor
[INDENT][INDENT]make it so
[/INDENT]
[/INDENT]


thank you for the morale boost. But... could you tell me step by step what should I do now?

---

### Post by Bashing-om on 2016-08-30
dreaddisk; sure !

Make a backup of the file prior to editing .. SOP ..Murphy's law always is in effect . Power failures can and do happen.
```

sudo cp /etc/apt/sources.list.d/google-chrome.list /etc/apt/sources.list.d/google-chrome.list-30Aug2016

```
Let's assume that your favorite text editor is gedit:
```

sudo -H gedit /etc/apt/sources.list.d/google-chrome.list

```
which will open the target file for editing with the elevated privilege to edit a system file.
gedit is a wysiwyg editor ; just place the cursor at the 'm' and add ain .
save the file from the gedit tool bar. Close the editor.
Now run: terminal commands
```

sudo apt update
sudo apt upgrade

```


[INDENT][INDENT]all good now 
[/INDENT][/INDENT]

---

### Post by dreaddisk on 2016-08-30
> **Bashing-om said:**
> dreaddisk; sure !

Make a backup of the file prior to editing .. SOP ..Murphy's law always is in effect . Power failures can and do happen.
```

sudo cp /etc/apt/sources.list.d/google-chrome.list /etc/apt/sources.list.d/google-chrome.list-30Aug2016

```
Let's assume that your favorite text editor is gedit:
```

sudo -H gedit /etc/apt/sources.list.d/google-chrome.list

```
which will open the target file for editing with the elevated privilege to edit a system file.
gedit is a wysiwyg editor ; just place the cursor at the 'm' and add ain .
save the file from the gedit tool bar. Close the editor.
Now run: terminal commands
```

sudo apt update
sudo apt upgrade

```[INDENT][INDENT]all good now 
[/INDENT]
[/INDENT]


I did what you told me and I put the two codes in the gedit text editor. (and I type two "##" in the beginning of each line) I typed the las commands, everything was heading to the right direction, until, suddenly, the last output of the upgrade shows me this ```
N: Ignoring file 'google-chrome.list-30Aug2016' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
 
```

EDIT:  after posted this comment I realize that the red point ceased to exist. Meaning change it to [SOLVED]

---

### Post by Bashing-om on 2016-08-30
dreaddisk; Huh ?

> 
 (and I type two "##" in the beginning of each line) 


Show us what you now have . Paste back the output of :
```

tail -v -n +1 /etc/apt/sources.list.d/*

```

once all is good .. and we know it is good, we can then dispense with that backup file google-chrome.list-30Aug2016 .

[INDENT][INDENT]there is that path that seems right
[INDENT][INDENT][INDENT]but
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---


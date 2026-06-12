---
title: "GPG Error + The following signatures were invalid problem"
date: 2013-06-27
forum: Installation &amp; Upgrades
---

### Post by njsantana on 2013-06-27
While performing an update on my repository via "apt-get update" I received the error message 
```
The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```
I checked and found a post from 2005 on Ubuntu Forums [which you can find here]("http://ubuntuforums.org/showthread.php?t=75813") where the user "heyanowut" provided his found fix.  For one of the steps in his fix he suggested creating a new /var/lib/apt/lists folder with a sub-folder "partial".  The steps he laid out that were most relevant to my issue were:

[LIST]
[*]Rename the old lists folder to something like "lists_bu"
[*]Create a new lists folder with the same name hs the original i.e. "lists" and make sure you have a sub-directory called "partial"
[*]run the clean command
[*]run your update command
[/LIST]
(First step needs to be performed while in directory /var/lib/apt , as shown of course):
```
:/var/lib/apt$ sudo mv lists lists_bu
:/var/lib/apt$ sudo mkdir -p lists/partial
:/var/lib/apt$ sudo apt-get clean all
:/var/lib/apt$ sudo apt-get update
```

Once that is finished and I had no further error messages, I was able to run upgrade tasks as needed.

---


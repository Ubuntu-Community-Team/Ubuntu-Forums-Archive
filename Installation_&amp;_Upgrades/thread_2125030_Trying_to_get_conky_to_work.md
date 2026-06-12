---
title: "Trying to get conky to work"
date: 2013-03-12
forum: Installation &amp; Upgrades
---

### Post by sarar on 2013-03-12
I installed conky, following the instructions from this link: [http://geekyschmidt.com/2009/03/29/conky-setup](http://geekyschmidt.com/2009/03/29/conky-setup)
When i try to run the scripts or conky it doesn't work. Any suggestions? I'm a linux beginner and don't have a lot experience with any of these kinds of things.

---

### Post by Old_Grey_Wolf on 2013-03-12
The Ubuntu Wiki for Conky may be of help to you.

[https://help.ubuntu.com/community/SettingUpConky](https://help.ubuntu.com/community/SettingUpConky)

---

### Post by stinkeye on 2013-03-12
I don't know where your having problems but I couldn't even extract the downloads properly for a start.
He has left the period(.) out before **tar.gz** in the file names of each download.
eg
**conky_scriptstar.gz** should be
**conky_scripts.tar.gz**

Rename each download accordingly and then right click on each and choose extract here.
You then need to press ctrl+h to show hidden files to reveal the extracted **.conkyrc** file.
You should see as in attachment.

Now try again following his directions for placement of the extracted files.
Place the **contents** of the folders not the actual folders themselves into the directories named.

The .conkyrc file is just placed in your home folder.
This is the config conky looks for and loads when you run conky.
If conky can't find ~/.conkyrc it will load the default config which looks like second attachment.

---

### Post by sarar on 2013-03-12
The problem seems to be LXDE. I've heard that other people have had trouble getting conky to work with LXDE and the pcman file manager. I can't get any conkyrc file to work for me. I keep getting this error message:
[1] 2161sarabuck@sarabuck-Gateway-M460:~$ WARNING: gnome-keyring:: couldn't connect to: /run/user/sarabuck/keyring-QQROmP/pkcs11: No such file or directory
Conky: invalid configuration file '/home/sarabuck/.conkyrc'


Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
	This program is calling the Imlib call:


	imlib_context_free();


	With the parameter:


	context


	being NULL. Please fix your program.

---

### Post by stinkeye on 2013-03-12
Have you placed .conkyrc in your home folder.

If so it should open in gedit with...
```
gedit ~/.conkyrc
```

Can also test using the default config with...
```
conky -c /etc/conky/conky.conf
```

This is also an old config and I don't think the weather part works anymore.

I suggest you go here.
[**_[COLOR="#B22222"]Post your .conkyrc files w/ screenshots[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865&page=2168&p=12554035#post12554035")

Plenty of screenshots and configs to look at and people willing to help set up.

---

### Post by sarar on 2013-03-12
It opens with the default config, I just can't get it to work with any other config file. Apparently the problem is PCManagerFM, I'm just not quite sure how to fix it.

---

### Post by stinkeye on 2013-03-12
In the terminal run ...
```
ls -a | grep ".conkyrc"
```

eg should show similar.
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] ls -a | grep ".conkyrc"
**.conkyrc**
```

You can also specify the config to use with the **-c** option.
ie
```
conky -c ~/.conkyrc
```

[COLOR="#FF0000"][SIZE=3]_Edit_[/SIZE][/COLOR]

The conky takes a while to show because this line in the conkyrc either needs to be commented out (place a # at the start of the line)
or changed to show your gmail username and password.
The gmail_parser.py script may be the cause of the gnome keyring error.
```
${color F8DF58}${font FreeSans:size=12}@${font}${execpi 300 python ~/.bin/gmail_parser.py [COLOR="#FF0000"]username[/COLOR] [COLOR="#0000FF"]password[/COLOR] 3}
```
The conkyrc still shows the authors [COLOR="#FF0000"]username[/COLOR] and [COLOR="#0000FF"]password[/COLOR] which he hopefully has changed.

---

### Post by sarar on 2013-03-13
Same error message when I try that. It seems to be looking for Gnome Keyring, which I don't have because I don't use Gnome.

---

### Post by sarar on 2013-03-13
Nevermind, problem solved. I just had my files set up wrong, apparently... Excuse me while I bang my head against the wall.

---

### Post by stinkeye on 2013-03-13
> **sarar said:**
> Nevermind, problem solved. I just had my files set up wrong, apparently... Excuse me while I bang my head against the wall.
I'll join in.
](*,)

---


---
title: "update manager reports a bug. how to fix?"
date: 2014-11-28
forum: Installation &amp; Upgrades
---

### Post by vikka2 on 2014-11-28
Hi, 

I am new to Ubuntu and on 12.04. I was trying to get gtalk on my system but then abandoned the idea. Nevertheless, because I tried, my Update Manager is unable to scan for updates and leaves this message - 

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'http://dl.google.com/linux/talkplugin/deb/' is not known on line 4 in source list /etc/apt/sources.list.d/google-talkplugin.list'

I appreciate tips on how to get rid of this bug. Hope this is the right forum!

---

### Post by mörgæs on 2014-11-28
Thanks for considering to make Buntu better by reporting bugs. However, 12.04 is old and no development is taking place here.
If you have the energy then testing 15.04 and reporting bugs will be appreciated.

---

### Post by ian-weisser on 2014-11-28
The error message may indicate a malformed line, which can be very easy to fix...and perhaps not a bug.

Please open a terminal and try the following command. Copy-and-paste the *complete* output here.
```
less /etc/apt/sources.list.d/google-talkplugin.list
```

---

### Post by Bucky Ball on 2014-11-28
Welcome. Software Updater>Settings>Other Software>disable the repository that update is complaining about. Look for anything that contains 'google-talkplugin.list'.

As you are new to Linux, I would avoiding testing development versions (like 15.04) until you are more familiar. 12.04 LTS is supported until 2017, 14.04 LTS until 2019.

---

### Post by vikka2 on 2014-11-29
Dear All, 

Many thanks for your quick responses. However, as it  turns out, my Ubuntu Software Centre crashes before it opens and thus I can't follow Buggy Bug's advice. I click on  Ubuntu S-w Ctr, then the icon jiggles a bit but  it doesn't open. I realise that it is most prob not a bug. I had fed a command (garnered from google searches for linux google talk) into a terminal before this started. The commans was this (copied from some website) - 
sudo sh -c 'echo "deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main" >> /etc/apt/sources.list.d/google-talkplugin.list'

Pls advice on the way fwd. thanks again, dodo

---

### Post by plucky on 2014-11-29
> **vikka2 said:**
> Dear All, 

Many thanks for your quick responses. However, as it  turns out, my Ubuntu Software Centre crashes before it opens and thus I can't follow Buggy Bug's advice. I click on  Ubuntu S-w Ctr, then the icon jiggles a bit but  it doesn't open. I realise that it is most prob not a bug. I had fed a command (garnered from google searches for linux google talk) into a terminal before this started. The commans was this (copied from some website) - 
sudo sh -c 'echo "deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main" >> /etc/apt/sources.list.d/google-talkplugin.list'

Pls advice on the way fwd. thanks again, dodo

Post output from a terminal for ```
cat /etc/apt/sources.list.d/google-talkplugin.list
```

You can edit the .list file using ```
sudo nano /etc/apt/sources.list.d/google-talkplugin.list
``` and put a # in front of the line ```
deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main
``` will disable that repository.

Good Luck

---

### Post by ian-weisser on 2014-11-29
> **vikka2 said:**
> sudo sh -c 'echo "deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main" >> /etc/apt/sources.list.d/google-talkplugin.list'

Disabling the broken repository listing is a solution, but a temporary solution.

According to the error message you received, you made a typo in the command.
Open the file at /etc/apt/sources.list.d/google-talkplugin.list in any text editor, and fix the typo.
You are correct - it's not a bug. 

Personally, I recommend the 'nano' text editor, which you can open from the terminal.
Since that file is owned by root, you must use 'sudo'. 
Do NOT use a word processor - it will break the file by inserting extra characters.
Example to open the file so you can fix it: ```
sudo nano /etc/apt/sources.list.d/google-talkplugin.list
```

---


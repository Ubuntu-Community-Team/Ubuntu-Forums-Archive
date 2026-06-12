---
title: "Chrubuntu Acer c7 Chromebook harddrive range"
date: 2013-08-20
forum: Installation &amp; Upgrades
---

### Post by kyle8 on 2013-08-20
Posted this in the absolute beginner thread but i'm thinking maybe it's more an installation question. I don't know how to move it. Sorry for the double thread. 

Hi! My son (10) got an acer c7 chromebook last christmas and after  growing bored with it and wanting to play minecraft on his own computer  instead of mine we decided to install ChrUbuntu. 

We followed the instructions here: [http://chromeos-cr48.blogspot.com/2013/05/chrubuntu-one-script-to-rule-them-all_31.html](http://chromeos-cr48.blogspot.com/2013/05/chrubuntu-one-script-to-rule-them-all_31.html)
everything worked fine and he was happy with it for a few weeks. 

He took the chromebook to his moms and when he came back he was upset  because he had restarted his chromebook, didn't wait, and then answered  the questions to set the chromebook up like it was new. 

We needed to install again. I had read some on Crouton and decided to  try that this time. I did not like it. We restored the chromebook to its  original state via USB and decided to go back to installing from
[http://chromeos-cr48.blogspot.com/2013/05/chrubuntu-one-script-to-rule-them-all_31.html](http://chromeos-cr48.blogspot.com/2013/05/chrubuntu-one-script-to-rule-them-all_31.html) and I would better educate him on what to do when he turns the chromebook on.

This time when we follow the instructions I get the following message:

after typing in: [FONT=Arial]**curl -L -O [http://goo.gl/s9ryd;](http://goo.gl/s9ryd;) sudo bash s9ryd **i get the following:

Enter the size in gigabytes you want to reserve for Ubuntu: Acceptable range is 5 to -4 but -5 is the recommended maximum: _

The first time i went through this it gave me the option of 5 to 250 (or something like that I don't remember exactly)

[/FONT][IMG]https://www.dropbox.com/sc/del53ljlzgwlmst/0wX5cK4XO5[/IMG][http://www.dropbox.com/sc/del53ljlzgwlmst/0wX5cK4XO5](http://www.dropbox.com/sc/del53ljlzgwlmst/0wX5cK4XO5)

I want to be able to get back to allocating 100gb or whatever i want in  this step. Any thoughts or help would be greatly appreciated!
Thank you![FONT=Arial]
[/FONT]

---

### Post by b23prodtm on 2013-08-20
Hi, I'm having the same issue on my Acer's .

I had faced a Chrome OS issue, which led me to recover the chromebook system again (root password issue). Chrubuntu was already installed, but came lost after the recovery process finished.
Now I 'm unable to run the chrubuntu script goo.gl/s9ryd as well, some GPT data must have changed in the recovery process..
> 
[COLOR=#000000][FONT=Arial]Enter the size in gigabytes you want to reserve for Ubuntu: Acceptable range is 5 to -4 but -5 is the recommended maximum: _[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]The first time i went through this it gave me the option of 5 to 250 (or something like that I don't remember exactly)[/FONT][/COLOR]
[B]Neither value work there, an error occurs in the script if you press enter without anything else (mk2efs fails and the chromebook freezes.
[/B]
At this time, I can run Crouton, in a chroot. But the chroot does not allow running desktop applications like browsers and has some limitations : the home disk is unwriteable, UbuntuONe is not functional...
:confused:

---

### Post by b23prodtm on 2013-08-20
I tried [SIZE=3][FONT=courier new]sudo bash s9ryd repart '' /dev/sda[/FONT][/SIZE] because it seems the drive was not correctly detected. But the dev/sda7 could not be read while IN USE...

---

### Post by domain-logic on 2013-08-22
> **kyle8 said:**
> 
after typing in: [FONT=Arial]**curl -L -O [http://goo.gl/s9ryd;](http://goo.gl/s9ryd;) sudo bash s9ryd **i get the following:

Enter the size in gigabytes you want to reserve for Ubuntu: Acceptable range is 5 to -4 but -5 is the recommended maximum: _

The first time i went through this it gave me the option of 5 to 250 (or something like that I don't remember exactly)
[/FONT][FONT=Arial]
[/FONT]

Hi everyone.  I have the actual fix for this.
I came across this conversation in a Google search for the answer.  I ended up not finding the answer online, but decided to look into the problem myself. (since I just got this Chromebook Acer C7 this week and anxious to put an alternative OS to play with).

The problem is that the updated utility does not properly detect and partition the harddrive.  ("well, duh" you might be thinking).
And I thought about downloading the script and rewriting it (which I still might do).
But just wait a second...what is wrong with the old script?  Absolutely nothing.
So without wasting time, I used the OLD script to partition (tnyga)..and then when it reboots to ACTUALLY DO THE INSTALL, you use the updated s9ryd.

To be clear: type
[FONT=Arial][B]curl -L -O [http://goo.gl/tnyga;]("http://goo.gl/s9ryd;") sudo bash tnyga
[/B]and select 200 to be the number for GB for the partition.  It works!!

The machine will automatically reboot (and go through diagnostics since you reconfigured it).  It will take 5 minutes or so to completely load.
Then proceed with the rest of procedure (enable wireless, drop to F2 console, then type: [/FONT][FONT=Arial]**curl -L -O [http://goo.gl/s9ryd;](http://goo.gl/s9ryd;) sudo bash s9ryd **)
It will see that the drive is partitioned and it will continue the install.

I just did this on my C7. It worked beautifully (I opted for the xbuntu-desktop lts...so my command was [/FONT][FONT=Arial][B]curl -L -O [http://goo.gl/s9ryd;](http://goo.gl/s9ryd;) sudo bash s9ryd xbuntu-desktop lts  )
Good Luck![/B][/FONT]
[FONT=Arial]

[/FONT]

---

### Post by kyle8 on 2013-08-26
This worked beautifully for me. Thank you!

---

### Post by phyre2 on 2013-10-26
> **domain-logic said:**
> 
To be clear: type
[FONT=Arial][B]curl -L -O [http://goo.gl/tnyga;]("http://goo.gl/s9ryd;") sudo bash tnyga
[/B][/FONT]

This worked excellently for my Samsung Chromebook 550; neither of the s9yrd or 9sgchs scripts would work. Thank you for posting this.

Edit: with the caveat that while the script ran, it's not completing properly- it gets to a point where it reboots the Chromebook (it never prompts me for settings choices), and then when it reboots it won't accept CTRL+L to switch to the Linux install. Something is awry... more investigation required.

---


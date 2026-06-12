---
title: "Installing Firefox 3.6"
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by GSam on 2010-03-16
I have Firefox 3.6 (the downloaded version from Mozilla) in my Home folder and can open it, but Firefox 3.0 remains the browser of choice (on the panel bar) by my computer. I'd like to be able to install 3.6 and do away with 3.0 and another version that doesn't have a version number (both in the ETC folder). I just can't figure how to do that. I'm running Ubuntu 8.10 and have been told that the "official Ubuntu" 3.6 version of FF won't be available until sometime in May. I've tried going through Applications and tried to cut and paste it into the ETC folder. Neither of which worked. Do I have to delete the older versions first? In Windows it would be a simple process, so I don't understand why I can't just install it. Anybody have any suggestions????

3/16/10
In attempting to use Kalasoka's fix I found that my Terminal will not accept my password.
I haven't used the Terminal for a while and was shocked that my password for sudo wouldn't work.
Figured that one out-about the password. Had to go back to the book to remember.
Now I don't think the syntax for creating a new symlink is correct. Help!

---

### Post by wojox on 2010-03-16
Okay, you don't want to run Firefox out of your /home/user directory. Anything you download like that should be set up in /opt.

To install from the ppa run this:

```
sudo bash -c "echo 'deb http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu intrepid main' >> /etc/apt/sources.list"
```

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CE49EC21
```

```
sudo apt-get update && sudo apt-get install firefox-3.6
```

```
sudo apt-get upgrade && sudo apt-get dist-upgrade
```

---

### Post by kalasoka on 2010-03-16
When you run Firefox, it invokes /usr/bin/firefox, which actually is a symlink to firefox-3.0

To use Firefox 3.6 from your downloaded folder, follow these steps:

1. Remove the old symlink
[INDENT]sudo rm /usr/bin/firefox
[/INDENT]2. Create a new symlink pointing to the latest version
[INDENT]sudo ln -s /path/to/firefox-3.6/firefox /usr/bin/firefox
[/INDENT]Now you should be able to use the latest version. Verify this by running
[INDENT]firefox --version
[/INDENT]from the terminal

---

### Post by GSam on 2010-03-16
To KALASOKA:

I think there is something missing in your syntax for creating a new symlink. I have moved Firefox-3.6 to my public folder and tried changing the like to:

sudo ln -s /home/joseph/public/firefox-3.6/firefox/user/bin/firefox

This could be totally wrong, but it was the best I could figure out. sudo still didn't like it. Any more ideas???

---

### Post by wojox on 2010-03-16
You're using 8.10 right?

---

### Post by GSam on 2010-03-16
TO WOJOX:

Yes.....Intrepid Ibex

---

### Post by wojox on 2010-03-16
It's not safe to run web browsers out of your user directory. I would delete it and follow my link above. :D

---

### Post by GSam on 2010-03-16
TO WOJOX:

Well, it seems to have worked, except that instead of having the familiar Firefox icon on the top panel, there is a black box. Is there some way I can change it back to the Firefox icon????
By the way, Thank you! I just cut and pasted your instructions and the machine did the rest. Quite simple (at least for a klutz like myself)
Now if I can change the icon I'll be a happy camper!

---

### Post by GSam on 2010-03-16
TO WOJOX:
Got it! That was also really simple....
Thank You again. I truly appreciate your help.
Joe Green

---

### Post by amnite on 2010-03-17
To Wojox:
I did like you told the one kid to do to install FF 3.6, i input all the commands and wound up with neither the new FF or my old one(No such file or directory). Luckily i had the uncompressed archive, i unsuccessfully tried to install earlier, located in my trash and was able to run it from my desktop to write you this message. Sooo ummm.... any help or ideas on how to get it to work again? Thx

---

### Post by wojox on 2010-03-18
> **amnite said:**
> To Wojox:
I did like you told the one kid to do to install FF 3.6, i input all the commands and wound up with neither the new FF or my old one(No such file or directory). Luckily i had the uncompressed archive, i unsuccessfully tried to install earlier, located in my trash and was able to run it from my desktop to write you this message. Sooo ummm.... any help or ideas on how to get it to work again? Thx

Are you using 9.10? Those instructions only work for 9.10 and 10.04. Let me know and i'll help you for a different version.

---


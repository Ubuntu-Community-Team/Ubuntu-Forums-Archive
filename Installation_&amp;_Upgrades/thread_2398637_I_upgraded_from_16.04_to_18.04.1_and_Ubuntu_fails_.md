---
title: "I upgraded from 16.04 to 18.04.1 and Ubuntu fails to recognize my password"
date: 2018-08-15
forum: Installation &amp; Upgrades
---

### Post by deniseh on 2018-08-15
Hello all,

First of all, I might be new to this forum, but not to Ubuntu. 
Previously, I was a member of the Dutch language forum, but that is offline for the moment. 
Yesterday, I upgraded from Xenial Xerus to Bionic Beaver.
The upgrade went smoothly and when I restarted the pc, I was glad to see a login screen with my name on it! 
However, Ubuntu failed to recognize my password.
I checked, I triple checked and tried again. Ubuntu 18.04.1 still didn't recognize my password. (Yes, the very same password that I used to login here!)
I went to YouTube to find any solutions there, but those weren't very helpful.
Then it hit me: my keyboard is an AZERTY, since I live in Belgium, Europe. 
When I tried to type in my password, using the keys as one would using a QWERTY keyboard, I did get access to the shiny new Bionic Beaver!
Hurray! That was my reaction last night.
I took the tour of the OS and was pretty pleased that I was able to locate all of my programs and files. And I made sure that the keyboard settings were set to AZERTY!
So, I shut down the pc and went to sleep pretty pleased.
But, this morning, I wasn't able to login again.
Yes, I do know my password.
Yes, I did try the AZERTY to QWERTY trick again. 
Yes, I found another trick that says that you should type any lower case key and then hit the backspace and try again, and I still can't login!

Please, pretty please, can somebody help me?

Kind regards,

deniseh

Meanwhile, I was able to get past the login screen by starting up the pc again and using the QWERTY trick
However, after logging in, I notice that my keyboard settings in Ubunty 18.04.1 still show AZERTY. (That's the way I adjusted my settings yesterday)

---

### Post by Impavidus on 2018-08-15
So you set your user keyboard setting to AZERTY, but the system-wide setting is still QWERTY. These settings are not necessarily the same, as multiple users of the same computer may prefer slightly different layouts to make it easier to type accents that only some users need. To change the system-wide keyboard setting, you can try```
sudo dpkg-reconfigure keyboard-configuration
```Use the arrow keys and enter to navigate through the menus.

---

### Post by deniseh on 2018-08-15
Thank you for your answer. It makes a lot of sense and explains why I have this weird problem.
I will try out this solution and will tell you whether it worked or not.

---

### Post by deniseh on 2018-08-17
Thank you very much!
The code did the trick and using the arrows I was able to navigate through the menu and able to select my country and type of keyboard! :D

---


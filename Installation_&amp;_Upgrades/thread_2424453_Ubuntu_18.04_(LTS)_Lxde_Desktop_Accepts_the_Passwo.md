---
title: "Ubuntu 18.04 (LTS) Lxde Desktop Accepts the Password but Does Not Open"
date: 2019-08-08
forum: Installation &amp; Upgrades
---

### Post by warpalawas on 2019-08-08
Hello,
2016 LTS I have updated Ubuntu and installed the 2018.04 LTS on it. I installed Lxde (Lubuntu) as desktop. At the opening, I always press a key to open the warning that even though I was using the computer to enter.
When I couldn't open a rar file today, when I searched how to open a rar file in Ubuntu, I had a code like this and I loaded it and opened my rar file.
```
sudo apt-get install unrar
```
When I try to turn my computer off and after a while, the group passes the screen and when the password screen comes up, I write the password on the screen, I press enter, the screen goes back to the password screen. I've tried many times, always coming to the same place. I have entered the wrong password a few times, again the same screen comes.
The computer doesn't start.

---

### Post by warpalawas on 2019-08-08
When I thought to the terminal screen with ctrl + alt + F1, I tried a few commands given above. When I enter my password and enter it, it first writes something like this.

Ubuntu 18.04.2 LTS panda-Lenovo-3000-N500 tty1
panda-Lenovo-3000-N500 login: _

After a while, the top post goes to itself

Login incorrect
panda-Lenovo-3000-N500 login: _

It is coming.

---

### Post by cruzer001 on 2019-08-08
login is your user name, not your password.
Once your logged in try the command **startx**

---

### Post by warpalawas on 2019-08-08
@cruzer001,
thanks for your answer but it isn't work, it is said "wrong password"

by the way i am searching
When I thought to the terminal screen with ctrl + alt + F1, I tried a few commands given above. When I enter my password and enter it, it first writes something like this.

Ubuntu 18.04.2 LTS panda-Lenovo-3000-N500 tty1
panda-Lenovo-3000-N500 login: _

After a while, the top post goes to itself

Login incorrect
panda-Lenovo-3000-N500 login: _
It is coming.

---

### Post by warpalawas on 2019-08-08
somewhere it is said that
you can use after the ctrl+alt+f1 to login the terminal, you can use that code
```
[COLOR=#333333][FONT=&amp]sudo rm -f .Xauthority[/FONT][/COLOR]
```
i cant copy for that reason i dont know there is a gap between words.
i worte that sudo _rm_-f_.Xauthority
i use _ symbol as a gap. is it true? by the way it isnt work also this code
[IMG]http://i64.tinypic.com/207rwyf.jpg[/IMG]

[COLOR=#000000]When I thought to the terminal screen with ctrl + alt + F1, I tried a few commands given above. When I enter my password and enter it, it first writes something like this.[/COLOR]

[COLOR=#000000]Ubuntu 18.04.2 LTS panda-Lenovo-3000-N500 tty1[/COLOR]
[COLOR=#000000]panda-Lenovo-3000-N500 login: _[/COLOR]

[COLOR=#000000]After a while, the top post goes to itself[/COLOR]

[COLOR=#000000]Login incorrect[/COLOR]
[COLOR=#000000]panda-Lenovo-3000-N500 login: _[/COLOR]

---

### Post by warpalawas on 2019-08-08
[IMG][IMG]http://i63.tinypic.com/2rma1ro.jpg[/IMG][/IMG]

---

### Post by guiverc on 2019-08-08
At the *login*: prompt you should be entering your username instead you typed a command, but the password you provided was your password (but you tried to login to an invalid user account).  The *Login incorrect* response is correct, as you didn't enter use the correct (or your) username

fyi: the reason the error message isn't more clear is for security reasons - to provide fewer clues for hackers, so they don't know if the tried to login with a valid username or not.

---

### Post by warpalawas on 2019-08-09
Hello guiverc,

you mean after the ctrl+alt+f1 to go to terminal, than  writing username then to write password.
after terminal i wrote username and then write the pass word and its screenshot below. i think i entered the comand line. What will i do next?
[IMG][IMG]http://i67.tinypic.com/2s922ps.jpg[/IMG][/IMG]

[FONT=arial]What will I do next?

i wrote
[/FONT]```
[COLOR=#333333][FONT=&amp]sudo apt-get update[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]sudo apt-get upgrade[/FONT][/COLOR]
```[FONT=arial]
and than i tried to acces to  ubunut, it was failed again.[/FONT]

---

### Post by warpalawas on 2019-08-09
[IMG][IMG]http://i67.tinypic.com/v32lhs.jpg[/IMG][/IMG][FONT=arial]I think my problem is that my disk space is full, can it be?When you enter the terminal with ctrl + alt + f1,after entering username + passwordI can write code.to thererespectively

[/FONT]```
[COLOR=#333333][FONT=&amp]sudo apt-get update
[/FONT][/COLOR][COLOR=#333333][FONT=&amp]sudo apt-get upgrade
[/FONT][/COLOR][COLOR=#333333][FONT=&amp]sudo update-grub
[/FONT][/COLOR][COLOR=#333333][FONT=&amp]sudo dpkg-reconfigure -a
[/FONT][/COLOR][COLOR=#333333][FONT=&amp]sudo apt-get install ubuntu-desktop
[/FONT][/COLOR][COLOR=#333333][FONT=&amp]sudo apt-get install ubuntu-desktop
[/FONT][/COLOR][COLOR=#333333][FONT=&amp]sudo apt-get install --reinstall ubuntu-session
[/FONT][/COLOR][COLOR=#333333][FONT=&amp]sudo apt-get install --reinstall ubuntu-desktop[/FONT][/COLOR]
```
then I couldn't get it on the lines ... when I saw it didn't open in my experiments. Error writing to output file - there was no free space on the device (ip no)

[B]might the problem be due to any space in the disk? if it is, how i do free space at this point
in the bottom line it is writen [COLOR=#0000ff]E: /var/cache/apt/archives/ there is no enough space[/COLOR]"

Please forgive me by  my bad English![/B]

---

### Post by guiverc on 2019-08-09
If your disk space is full, don't try and `sudo apt-get install` anything else as it just makes the problem (of lack of disk space) harder to resolve.

The system has commands that can help, eg. `sudo apt-get autoclean` and `sudo apt autoremove` however they need space to run so if you ignored the space problem, you need to fix it before these can be run and help you.

I wonder how much space you allocated to your file-system?  The recommended is 25gb [for Ubuntu] which is fine for most users, however as I like adding software (esp. a second like you have done) I tend to allocate more than the minimum 25gb.  Yes many users get along fine with less (but when you release-upgrade (ie. move from 16.04 LTS to 18.04 LTS) you tend to run into space problems. 

My recommendation is to firstly see how much space you have (you can paste it here, to look at my own system I used `df -hl |grep sda`  (disk free, human format & local drives only then only display "sda" drives as i know that'll show my hdd, it may work for you, or you may need to use only `df -hl` (without the grep portion).

If you get error messages (eg. before you typed in `sudo apt-get install --reinstall ubuntu-session` you had an error message that told you the next `apt-get install` would fail until you'd run the recommended fix.  I suggest you read the messages before moving to the next command, if there are warning or error messages you don't understand, places like this forum are where you can get help, or given english is a second language for you, you could also try irc ([https://wiki.ubuntu.com/IRC/ChannelList](https://wiki.ubuntu.com/IRC/ChannelList)) where you may find a channel in your language/country.

source: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)  for 25gb minimum disk 
(*there are some tiny sizes at the bottom for Lubuntu and Xubuntu, I'll endeavour to make them more realistic in the coming days*)

---

### Post by cruzer001 on 2019-08-09
> Once your logged in try the command **startx**
If nothing happens press: Ctrl+Alt+F7

[s]What does that last line say in that picture? It starts with  E /var/cache/...[/s]
I seen your edit, nevermind

And please do as guiverc suggest.  Does us no good to suggest if there's not any follow thru.  Code **df -h**

---


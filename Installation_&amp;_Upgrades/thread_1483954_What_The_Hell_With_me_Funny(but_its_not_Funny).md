---
title: "What The Hell With me? Funny(but its not Funny)"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by adeee on 2010-05-15
GUys 20 days before i install the ubuntu and still i dont know how i install software.?????????
i asked this question in many time in the forum (How i install any software in linux? how i acces root?) but every one tell me the command sudu su and gksu.. 
no one tell me how it works?

for example i raise question i want to install Lampp on linux.

then a moderator ans me. "If you do want to use Linux/Apache/Mysql/Php, I would suggest you install the LAMP stack, by going to System->Administration-> Synaptic Package Manager->Edit->Mark Packages by task, and select what you need to install.
"
i install APACHE FROM THERE.

But unfortunately  it install automatic. 

i need proper guidance.

sometimes i think why window is eassy and linux is dificult.?
and know i find answer is that the proper guidence is not available..

people suggest me to use ebooks.?

i download these books. ubuntu pocket guide-v1-1, Beginning Ubuntu Linux - From Novice To Professional 2006, Ubuntu Unleashed, Ubuntu Linux Bible 2007

these books are informative. but the terms that included in books are difficult.

so thats the reason i cant learn from ebooks.


i cant see the any window ebook for window learning...

now am using wine software for running some .exe formate.


plz guys tell me how i install software? how i acces root?
how commands are worked..
 
dont suggest me any ebook.

i can read any related topic that have easy and understandable wordings .
but not any ebook.

thanks
adeee

---

### Post by blchinezu on 2010-05-15
Linux is not that difficult with ubuntu, and believe me... there is plenty of guidance.. If you have ubuntu just go to the Ubuntu Software Center and choose the desired app (search it or go by categories), click install and that's about it... It's not that hard.. Usualy you don't have to insert any input. It's very easy.

edit:
as for sudo and su those are terminal commands:
- those are runned from a terminal (Menu > Accesories > Terminal) or script which is not much of an interest as a beginner
if you want to... let's say create a folder named TEST in /etc/ but you don't have permission (which most definitely is true with most of the distributions)
you won't be able to just right click and click create folder from the file browser or create it from terminal with the command: mkdir /etc/TEST because you don't have the permissions
so you'll have to either launch the file browser with root privileges from a terminal: "sudo nautilus" and then you'll be able to do it with right click and create folder (but only from the newly opened window) or run from the terminal the same command for creating the folder (mkdir /etc/TEST) but with sudo at the begining: sudo mkdir /etc/TEST
you will be prompted for your password and it will be done

that's the most simple way i could present sudo

**sudo** executes comands as root (from a terminal or script)
**su** will actually log you (in a terminal or script also) as root
**gksudo** is sudo but with graphical prompt for password, so when it asks for a password a window will pop up with a password field

i hope you'll understand something from this.. i used my own simple words no hard thing..

---

### Post by lisati on 2010-05-15
If you want to learn about sudo, read this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

As for your other questions, people have tried to help you in your other thread.

---

### Post by sarang on 2010-05-15
Take it easy. 
Synaptic downloaded .deb files an installed them for you. These are a lot like windows installer files, in the sense that only minimal work is needed to install software in them. They contain pre-compiled software. When you are not so lucky, you will need to compile from source and install, which can range from being about just as easy to being a gruesome nightmare.

While I understand your excitement, people like me make an effort to use .deb files as much as possible, particularly when the source code is available and can be reviewed when necessary. If the source code is not available, I generally do not trust the compiled binaries easily. 

If you are looking for useful things to look into, I suggest you familiarise yourself with the dpkg and apt programs and with bash shell programming and also other programming languages if you desire.

---

### Post by adeee on 2010-05-15
> **blchinezu said:**
> 
edit:
as for sudo and su those are terminal commands:
- those are runned from a terminal (Menu > Accesories > Terminal) or script which is not much of an interest as a beginner
if you want to... let's say create a folder named TEST in /etc/ but you don't have permission (which most definitely is true with most of the distributions)
you won't be able to just right click and click create folder from the file browser or create it from terminal with the command: mkdir /etc/TEST because you don't have the permissions
so you'll have to either launch the file browser with root privileges from a terminal: "sudo nautilus" and then you'll be able to do it with right click and create folder (but only from the newly opened window) or run from the terminal the same command for creating the folder (mkdir /etc/TEST) but with sudo at the begining: sudo mkdir /etc/TEST
you will be prompted for your password and it will be done




ok thank you i will do. it works,..
so brother an error occured see.
i make the Test folder.. now what the delet command. dir command for folders in home what is rename command? :P

and sudo nautilus error is this..

[IMG]http://img63.imageshack.us/img63/7641/37273631.png[/IMG]

---

### Post by adeee on 2010-05-15
> **sarang said:**
> Take it easy. 
Synaptic downloaded .deb files an installed them for you. These are a lot like windows installer files, in the sense that only minimal work is needed to install software in them. They contain pre-compiled software. When you are not so lucky, you will need to compile from source and install, which can range from being about just as easy to being a gruesome nightmare.. 

many software that i install in this format and i think the software that available on ubunto software center are in this format..
and my question is i see many reviews that .deb files are not good for instalation. manually instalation is best.



> **sarang said:**
> 
If you are looking for useful things to look into, I suggest you familiarise yourself with the dpkg and apt programs and with bash shell programming and also other programming languages if you desire.


What dpkg apt Bash Shell?

---

### Post by blchinezu on 2010-05-15
i'm afraid you won't learn too much about linux if you don't use google a little bit.. before asking someone about something try to find out yourself something about the subject

---


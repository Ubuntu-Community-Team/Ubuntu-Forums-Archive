---
title: "I cannot update  or get any repositories"
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by qwondre on 2010-03-15
I get this when I do  gksu gedit /etc/apt/sources.list

E: Malformed line 61 in source list /etc/apt/sources.list (absolute dist)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


When I do sudo apt-get update, I get this:E: Malformed line 61 in source list /etc/apt/sources.list (absolute dist)

I do not have a line 61. I tried various suggestions  in the forums and commented out lines in the past.

I would like to know what my options are?

---

### Post by CompyTheInsane on 2010-03-15
Can you post what you have in /etc/apt/sources.list?

---

### Post by leorolla on 2010-03-15
```
cat  /etc/apt/sources.list
```

---

### Post by qwondre on 2010-03-17
Yeah, Hi and thanks.
This is what I get:

qwondre@qwondre-netbook ~ $ cat  /etc/apt/sources.list
deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) helena main upstream import
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) karmic partner
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free

---

### Post by leorolla on 2010-03-17
```
cp  /etc/apt/sources.list ~    # backup
sudo rm  /etc/apt/sources.list
sudo gedit  /etc/apt/sources.list

```
Paste the 6 lines you just posted.
Save.
Exit.

Hope it works.

PS: use the "code" tags when copy-pasting terminal output.

---

### Post by qwondre on 2010-03-23
Hi, I just back into town and I did as you suggested and got this:

qwondre@qwondre-netbook:~$ cp  /etc/apt/sources.list ~    # backup
cp: cannot stat `/etc/apt/sources.list': No such file or directory
qwondre@qwondre-netbook:~$ sudo rm  /etc/apt/sources.list
rm: cannot remove `/etc/apt/sources.list': No such file or directory
qwondre@qwondre-netbook:~$ sudo gedit  /etc/apt/sources.list

I got that when I did:

cp  /etc/apt/sources.list ~    # backup
sudo rm  /etc/apt/sources.list
sudo gedit  /etc/apt/sources.list

I also do not understand when you say:

"PS: use the "code" tags when copy-pasting terminal output"


thanks

PS I copied the 6 lines to the terminal but couldnt find a way to "save" it. It didnt look like it worked

---

### Post by leorolla on 2010-03-24
Code means you select things you paste from terminal and click on the "#" on the formatting tools above the text you are editing.

Otherwise write [ CODE ] before and [ /CODE ] after (without the blank spaces).

So, please run
```
ls -l /etc/apt

```

Above I used CODE, otherwise it reads:
ls -l /etc/apt

After you typed "sudo gedit ..." it should open the text editor, and you should place the lines there.

---

### Post by qwondre on 2010-03-25
> **leorolla said:**
> Code means you select things you paste from terminal and click on the "#" on the formatting tools above the text you are editing.

Otherwise write [ CODE ] before and [ /CODE ] after (without the blank spaces).

So, please run
```
ls -l /etc/apt

```

Above I used CODE, otherwise it reads:
ls -l /etc/apt

After you typed "sudo gedit ..." it should open the text editor, and you should place the lines there.

ok, I copied ls -l /etc/apt into terminal and got this:

total 44
drwxr-xr-x 2 root root  4096 2009-12-24 02:03 apt.conf.d
-rw------- 1 root root     0 2009-04-20 09:00 secring.gpg
-rw-r--r-- 1 root root  3460 2010-03-06 11:15 sources.list~
drwxr-xr-x 2 root root  4096 2009-12-29 02:41 sources.list.d
-rw-r--r-- 1 root root  3417 2010-03-15 01:48 sources.list.save
-rw------- 1 root root  1200 2009-05-15 10:43 trustdb.gpg
-rw-r--r-- 1 root root 10724 2009-05-15 10:43 trusted.gpg
-rw-r--r-- 1 root root 10724 2009-05-15 10:43 trusted.gpg~

thanks

---

### Post by leorolla on 2010-03-25
Good!

Next time you place [ CODE ] before and [ /CODE ] after (or click on the "#" above) and it will read like this:

```
total 44
drwxr-xr-x 2 root root  4096 2009-12-24 02:03 apt.conf.d
-rw------- 1 root root     0 2009-04-20 09:00 secring.gpg
-rw-r--r-- 1 root root  3460 2010-03-06 11:15 sources.list~
drwxr-xr-x 2 root root  4096 2009-12-29 02:41 sources.list.d
-rw-r--r-- 1 root root  3417 2010-03-15 01:48 sources.list.save
-rw------- 1 root root  1200 2009-05-15 10:43 trustdb.gpg
-rw-r--r-- 1 root root 10724 2009-05-15 10:43 trusted.gpg
-rw-r--r-- 1 root root 10724 2009-05-15 10:43 trusted.gpg~

```

Please run
```
cat /etc/apt/sources.list~

```
and show us the result (with 'code'!).

---

### Post by qwondre on 2010-03-28
I just do not know what you mean, I do not know the language that you are speaking, sorry.
This is what I have.

qwondre@qwondre-laptop:~$ ls -l /etc/apt
total 40
drwxr-xr-x 2 root root 4096 2009-12-26 15:53 apt.conf.d
drwxr-xr-x 2 root root 4096 2009-10-15 14:24 preferences.d
-rw------- 1 root root    0 2009-10-28 15:56 secring.gpg
-rw-r--r-- 1 root root 3144 2010-03-02 12:14 sources.list
drwxr-xr-x 2 root root 4096 2010-03-02 12:14 sources.list.d
-rw-r--r-- 1 root root 3144 2010-03-02 12:14 sources.list.save
-rw------- 1 root root 1200 2009-10-28 15:56 trustdb.gpg
-rw-r--r-- 1 root root 7073 2010-02-21 01:00 trusted.gpg
-rw-r--r-- 1 root root 6713 2009-10-28 15:56 trusted.gpg~
qwondre@qwondre-laptop:~$ #
qwondre@qwondre-laptop:~$ cat /etc/apt/sources.list~
cat: /etc/apt/sources.list~: No such file or directory
qwondre@qwondre-laptop:~$

---

### Post by leorolla on 2010-03-28
1. CODE

You are posting text here. You are writing your post right now.

Above the box where you type the text, you have formatting options: bold, italic, underline, center, etc etc etc etc etc etc...
(If you don't see that, click on the "go advanced" button.)
One of the formatting buttons you see looks like the # symbol, it is one of the last ones.
Select the part of the text that you want to format like ```
this
``` anc click on the # button. The part of the text that you want to look like that is the text you copy and paste from the terminal.

Now it will be much better for us to read your teminal output.

2. Your files.

Something misterious is happening to your files.

Notice that in the begining you had a file called sources.list in /etc/apt/

Then in another post there was no such file.

Now the file is back there.

Do you use this computer with another Operating System? It might be a virus...
Does anyone else use the computer?
Did you do anything unusual, like opening some doors for external access, do you use it as a server etc?

Hard to guess what is going on.

You can try runnning

```
cat /etc/apt/sources.list
cp  /etc/apt/sources.list ~/sources.list.backup.2      # backup
sudo rm  /etc/apt/sources.list
sudo gedit  /etc/apt/sources.list

```

It will produce some output in the terminal. Please copy and paste it in this topic.

It will also open a windows with the text editor gedit. Inside the editor, paste the following lines: 
```
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) karmic partner
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free     

```Save. Exit.

Now run
```
sudo aptitude update

```Copy and paste the result in this topic.

---

### Post by qwondre on 2010-03-29
> **qwondre said:**
> I just do not know what you mean, I do not know the language that you are speaking, sorry.
This is what I have.

qwondre@qwondre-laptop:~$ ls -l /etc/apt
total 40
drwxr-xr-x 2 root root 4096 2009-12-26 15:53 apt.conf.d
drwxr-xr-x 2 root root 4096 2009-10-15 14:24 preferences.d
-rw------- 1 root root    0 2009-10-28 15:56 secring.gpg
-rw-r--r-- 1 root root 3144 2010-03-02 12:14 sources.list
drwxr-xr-x 2 root root 4096 2010-03-02 12:14 sources.list.d
-rw-r--r-- 1 root root 3144 2010-03-02 12:14 sources.list.save
-rw------- 1 root root 1200 2009-10-28 15:56 trustdb.gpg
-rw-r--r-- 1 root root 7073 2010-02-21 01:00 trusted.gpg
-rw-r--r-- 1 root root 6713 2009-10-28 15:56 trusted.gpg~
qwondre@qwondre-laptop:~$ #
qwondre@qwondre-laptop:~$ cat /etc/apt/sources.list~
cat: /etc/apt/sources.list~: No such file or directory
qwondre@qwondre-laptop:~$

"qwondre@qwondre-laptop:~$ #" is there up above because I guessed that the implied meaning was that when you said:

"Next time you place [ CODE ] before and [ /CODE ] after (or click on the "#" above) and it will read like this:"

I have absolutely no clue in what you are trying to tell me what to do.

---

### Post by leorolla on 2010-03-29
Can you see any formatting difference between these?

total 44
drwxr-xr-x 2 root root  4096 2009-12-24 02:03 apt.conf.d
-rw------- 1 root root     0 2009-04-20 09:00 secring.gpg
-rw-r--r-- 1 root root  3460 2010-03-06 11:15 sources.list~
drwxr-xr-x 2 root root  4096 2009-12-29 02:41 sources.list.d
-rw-r--r-- 1 root root  3417 2010-03-15 01:48 sources.list.save
-rw------- 1 root root  1200 2009-05-15 10:43 trustdb.gpg
-rw-r--r-- 1 root root 10724 2009-05-15 10:43 trusted.gpg
-rw-r--r-- 1 root root 10724 2009-05-15 10:43 trusted.gpg~

```
total 44
drwxr-xr-x 2 root root  4096 2009-12-24 02:03 apt.conf.d
-rw------- 1 root root     0 2009-04-20 09:00 secring.gpg
-rw-r--r-- 1 root root  3460 2010-03-06 11:15 sources.list~
drwxr-xr-x 2 root root  4096 2009-12-29 02:41 sources.list.d
-rw-r--r-- 1 root root  3417 2010-03-15 01:48 sources.list.save
-rw------- 1 root root  1200 2009-05-15 10:43 trustdb.gpg
-rw-r--r-- 1 root root 10724 2009-05-15 10:43 trusted.gpg
-rw-r--r-- 1 root root 10724 2009-05-15 10:43 trusted.gpg~

```

Of course you can.

How did I do that? I formatted the second one to the 'code' format.

Above the box where you type the text, you have formatting options: bold, italic, underline, center, etc etc etc etc etc etc...
One of the formatting buttons you see looks like the # symbol, it is one of the last ones.
Select the part of the text that you want to format like

If you don't see a formatting menu, click on the "go advanced" button.
 
Got it?

Anyway, it's not that important.

You can try running the commands of my previous post, and answering the questions too.

Another question: are you using Linux Mint?

---


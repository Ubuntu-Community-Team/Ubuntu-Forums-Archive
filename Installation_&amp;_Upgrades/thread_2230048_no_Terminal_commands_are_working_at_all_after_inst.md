---
title: "no Terminal commands are working at all after install of Lubuntu 14.04"
date: 2014-06-17
forum: Installation &amp; Upgrades
---

### Post by roler2 on 2014-06-17
I am at a loss. About three weeks ago (I cannot find the original post), I was having difficulty with no Terminal commands working after install of Lubuntu 14.04. All I get are error messages. And it is not random. ALL Terminal commands are reporting errors. I was advised to re-download Lubuntu and make sure the MD5 was correct. I did and it is correct. Then I ran a check for errors on the CD, no errors found.

Then I booted to Try Lubuntu Without Installing. Went to Desktop very fast.

Until I started to input Terminal commands:

sudo: command not found

apt-get: command not found

mkdir: command not found

wget: command not found

sh: command not found

It doesn't matter what you combine these with other commands you will ALWAYS get error messages:

For example trying to install anything:

sudo apt-get install (any Program):

This will yield nothing but error messsages:

"No command sudo found, did you mean:


 Command 'sudo' from package 'sudo-ldap' (universe)
 Command 'sudo' from package 'sudo' (main)"

And so on. . .I didn't write down the other error messages for apt-get. . .the error list sometimes fills up half the Terminal. . .

So I tried the CD on another completely different computer. Once again booted to the Desktop very fast.

Except when I started to input Terminal Commands, same exact error messages. No changes.

I am at a loss. I cannot do anything.

Is the Download itself corrupt even though the MD5 is verified correct? I downloaded directly from the Lubuntu Home Page.

Is there any way to fix this issue?

Any help would be greatly appreciated. Thank you.

---

### Post by squakie on 2014-06-17
Without error messages it is a little hard to know anything about what you are talking about.  Highlight them in the terminal window, then right-click and copy.  Post another reply here, pasting that data between code tags.

---

### Post by roler2 on 2014-06-17
No command 'wget' found, did you mean:
 Command 'wget' from package 'wget' (main)
wget: command not found


No command 'sudo' found, did you mean:
 Command 'sudo' from package 'sudo-ldap' (universe)
 Command 'sudo' from package 'sudo' (main)
sudo: command not found


No command 'mkdir' found, did you mean:
 Command 'mkdir' from package 'coreutils' (main)
mkdir: command not found

---

### Post by deadflowr on 2014-06-17
Odd.
I wonder if your paths are broken(¿) Maybe, or something like that.
Post the output of
```
echo $PATH
```

Edit:
sorry if the paths are broken then that command might not work.(lol)
try the full path
```
/bin/echo $PATH
```

---

### Post by roler2 on 2014-06-17
Forgive me if I did this wrong but this is the Terminal output of those two commands:

$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

$ /bin/echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

---

### Post by kansasnoob on 2014-06-17
Let's start with something simple, please post the full output of:

```
sudo apt-get update
```

---

### Post by roler2 on 2014-06-17
I am once again re-downloading and re-burning to disc. Then I will reinstall instead of utilizing Try Lubuntu Without Installing. It will be alot easier to post commands and error messages while Lubuntu is installed. That way I can work within Lubuntu without having to switch Computers. Please give me until the weekend. Thank you for all your help and patience. I really very much appreciate all the advice and guidance.

---

### Post by roler2 on 2014-06-19
seems to be working better now. . .not as many error messages.  . .however the "lock" screen keeps appearing after the screensaver initializes. . .is there a way to eliminate the lock screen? Is there a configuration file? The "Lock Screen when going for suspend/hibernate" is unchecked in the Power Manager section.

---

### Post by roler2 on 2014-06-20
I have not been able to find the configuration file for the "lock screen". If anyone can assist so I can turn off the Lock Screen and prevent it from appearing after the screensaver initializes I would very much appreciate the assistance. Thank you!

Also, if anyone has commands in MS Word format, you might want to re-type the commands when utilizing AbiWord in Lubuntu. It looks like one of the problems I was having was with AbiWord not being able to transcribe the written command correctly from MS Word format , ultimately creating an error of some form when inputting the command into the Terminal.

I have been able to get Lubuntu 14.04 up and running quite well with very few errors at this point although I still have not finished updating.

Thank you once again for all the assistance.

---

### Post by roler2 on 2014-06-20
I removed light-locker but the lock screen still appears after the screensaver initializes. If there is a fix please advise. Thank you.

Lubuntu is running well right now except for the lock screen. No more errors.

---

### Post by oldos2er on 2014-06-20
> **roler2 said:**
> Also, if anyone has commands in MS Word format, you might want to re-type the commands when utilizing AbiWord in Lubuntu. It looks like one of the problems I was having was with AbiWord not being able to transcribe the written command correctly from MS Word format , ultimately creating an error of some form when inputting the command into the Terminal.


If only you'd given this information in your first post! "Commands in MS Word format" probably have weird formatting characters in them. Best to copy/paste from a plain text editor instead.

---

### Post by roler2 on 2014-06-20
Well. . .I wish I would have known that may be the problem. And yes I will copy and paste from a text editor next time around. Any suggestions on the lock screen issue? That issue was not present in 13.10.

---

### Post by oldos2er on 2014-06-21
Have you checked your Power Manager settings?

Just to clarify regarding "I wish I would have known that may be the problem", most people (well, me) would assume you're simply typing commands into the terminal, or perhaps copy/pasting from the forums or some other Ubuntu web site. Saying "btw, I'm copy/pasting commands from MS Word" would've given us all notice that *that's* the problem we could've helped you with. That's all.  :)

---

### Post by roler2 on 2014-06-22
Yes. . .OK. . .I am a dummy. . .however I incorporated other changes the third time around:

A) I utilized the same CD-ROM to both burn and install (I was utilizing one CD-ROM to Burn and a completely different CD-ROM to install)

b) I re-formatted the Disc before burning and reformatted the Hard Drive using a Windows ME disc prior to install

c) I used InfraRecorder to burn rather than the built-in Windows component

d) I downloaded the .iso using Firefox rather than IE

Also the issue with the weird formatting characters seem to be exclusive with AbiWord. After completely uninstalling AbiWord and installing LibreOffice, I have had no trouble copying commands into the Terminal from the LibreOffice clone of MSWord.

Also I was able to fix the lock screen issue by manually deleting ALL files applicable to Light Locker after uninstall. You apparently have to delete ALL files that remain applicable to Light Locker, even if they don't seem important.

Thank you for all the assistance.

---


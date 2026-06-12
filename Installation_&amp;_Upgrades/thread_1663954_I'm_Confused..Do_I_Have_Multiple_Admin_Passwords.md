---
title: "I'm Confused..Do I Have Multiple Admin Passwords?"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by Alyse on 2011-01-10
I downloaded a driver for my printer today and I opened it in the terminal. Then a window popped up saying "This opporation requires root (administrative) privileges. Please enter the administrative password below:" I typed in the same password that I use when authorizing the installation of programs from the Ubuntu Software Center and I tried it multiple times. Each time, it rejects the password. I even tried downloading something else from the software center, just to make sure the password was correct, but the system had no problem with the password when downloading from the software center. So, is my software center password different from my administrator password?

---

### Post by matt_symes on 2011-01-10
Hi

> So, is my software center password different from my administrator password?

They should be the same. 

What did you type to install the printer driver?

You could post the output of 

```
sudo cat /etc/sudoers
```

Kind regards

---

### Post by Alyse on 2011-01-10
Actually, I did not type anything. I only had it open in the terminal because the instructions instructed me to do so. When I opened it in the terminal, a setup screen popped up to install the printer. Then the window asking me for the admin password popped up. Weirder still, I am sure that I am typing in the same password.

---

### Post by Rubi1200 on 2011-01-10
This could also help us figure this out:
```
cat /etc/passwd
```

---

### Post by Alyse on 2011-01-10
deleting duplicate post

---

### Post by Rubi1200 on 2011-01-10
This could also help us figure this out:
```
cat /etc/passwd
```

---

### Post by Alyse on 2011-01-10
deleting duplicate post

---

### Post by Alyse on 2011-01-10
oops! Each time I posted, the post timed out so I did not realise any of them went through! I am sorry about all those redundant posts.

---

### Post by Alyse on 2011-01-10
> **Rubi1200 said:**
> This could also help us figure this out:
```
cat /etc/passwd
```


....Well, I opened the terminal and pasted cat/etc/passwd and a large amount of text appeared on the terminal screen. ..I am sorry for sounding like an idiot, but, what am I looking for exactly?

---

### Post by ajgreeny on 2011-01-10
> **Alyse said:**
> I downloaded a driver for my printer today and I opened it in the terminal. Then a window popped up saying "This opporation requires root (administrative) privileges. Please enter the administrative password below:" I typed in the same password that I use when authorizing the installation of programs from the Ubuntu Software Center and I tried it multiple times. Each time, it rejects the password. I even tried downloading something else from the software center, just to make sure the password was correct, but the system had no problem with the password when downloading from the software center. So, is my software center password different from my administrator password?
Let's start at the beginning!

What driver, where did you get it, and for what printer?
In what form did the driver download; a .deb file, a tar.gz or some other archive format?
Having opened the terminal what did you actually do with the file(s) you downloaded?

Once we know all that it may be a lot easier to tell you how to proceed.

---

### Post by Alyse on 2011-01-10
lol okay :) & Thank you-- I downloaded it from here: [http://support.lexmark.com/index?page=content&productCode=LEXMARK_INTERACT_S605&actp=RECOMMEND&id=DR16560&segment=DOWNLOAD&userlocale=RU&oslocale=en_US&locale=en](http://support.lexmark.com/index?page=content&productCode=LEXMARK_INTERACT_S605&actp=RECOMMEND&id=DR16560&segment=DOWNLOAD&userlocale=RU&oslocale=en_US&locale=en)

The printer is a lexmark interpret s405

The file I downloaded ended in deb.sh.tar.gz
After downloading it, I put that file in its own folder inside the downloads folder, which I named "lexmark driver." Then, I extracted the contents to that same folder. The extracted file is called lexmark-inkjet-09-driver-1.0-1.i386_ts.deb.sh

---

### Post by sisco311 on 2011-01-10
You have to run the script as root. Open a terminal, type **gksu** then a space. Drag & drop the file in the terminal window and press Enter.

---

### Post by sisco311 on 2011-01-10
D'oh!  

duplicate post

---

### Post by Alyse on 2011-01-10
Okay, I did what you said. After pressing enter, a pop up came and asked for my password. I typed my password and it seemed to be accepted. But then nothing happened. Then I double clicked on the file, told it to run in terminal. As happened previously, the printer setup screen came,  then it asked for my admin password. Then it rejected my password.


I just found this thread regarding a similar problem but with a different lexmark model. I do not understand what was done to fix the problem though. If you have time, would you take a look? [http://ubuntuforums.org/archive/index.php/t-1329495.html](http://ubuntuforums.org/archive/index.php/t-1329495.html)

---

### Post by Alyse on 2011-01-10
Ah, I just found this page: [http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html](http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html)

It says I can set a root password by typing $sudo password root but that same website also says it is not recommended---What do you think? Should I should type it into the terminal?

---

### Post by matt_symes on 2011-01-10
Hi

You could enter a root shell by typing

```
sudo -i
```

and install it that way. Type

```
exit
```

to exit the root shell.

Kind regards

---

### Post by Alyse on 2011-01-10
Oh dear. Uh, Matt? I typed in the sudo passwrd root before reading your message. I created a password that is the same as my admin password and it did actually fix the problem in the sense that the lexmark driver continued installation. ---Please tell me if I need to reverse anything because I have no idea what "root" is.  So the driver seemed to install, but now there is another problem. While setting up the printer, there was a point where it asked me to connect the usb printer cable to the computer, which I did. But nothing happened. 

A setup window told me this:

"You may have a firewall installed. A multicast DNS (mDNS) service firewall exception will be added to allow network printing. If the printer is not detected, please consult your operating system documentation on how to allow mDNS service in your firewall."

---

### Post by Alyse on 2011-01-11
Uh oh...I know a lot of people need help, but does anyone know what I should do from this point?

---

### Post by Imatech64 on 2011-05-15
Hello everyone

Just bought the same printer (Lexmark S405) and had the exact same trouble as Alyse.

The solution I found is :

Open Terminal
Type sudo -i
Then type gksu and drag and drop the extracted file driver and push enter.
The wizard will go one normally.
once the wizard installation is finished go terminal
type exit (to go back to your account)

and close terminal

It worked for me with Ubuntu 10.10.

---


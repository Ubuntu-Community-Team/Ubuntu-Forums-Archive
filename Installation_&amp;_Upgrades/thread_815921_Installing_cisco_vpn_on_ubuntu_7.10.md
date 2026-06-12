---
title: "Installing cisco vpn on ubuntu 7.10"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by shotos on 2008-06-02
Hello, am trying to install cisco vpn on my ubuntu 7.10 server edition. i just downloaded it and tying to unpack it but i keep getting this message
[COLOR="DarkRed"]
kwasi@60-84Kwasi:~$ tar -xvzf vpnclient-linux-4.8.01.0640-k9.tar.gz[/COLOR]

[COLOR="DarkGreen"]tar: vpnclient-linux-4.8.01.0640-k9.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
[/COLOR]
Help will be very much welcomed cuz i need to connect to ma worlplace ntk.

---

### Post by iaculallad on 2008-06-02
Be sure that you are in the same directory of that file you're trying to "untar" before giving the command:

```
tar xzf vpnclient-linux-4.8.01.0640-k9.tar.gz
```

Probably located in your desktop.

```
cd ~/Desktop
tar xzf vpnclient-linux-4.8.01.0640-k9.tar.gz

```

---

### Post by shotos on 2008-06-02
i just did this and here is the result

[COLOR="DarkRed"]kwasi@60-84Kwasi:~/Desktop$ tar xzf vpnclient-linux-4.8.01.0640-k9.tar.gz[/COLOR]

[COLOR="Green"]tar: vpnclient-linux-4.8.01.0640-k9.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
[/COLOR]
the file is located on my desktop......thanks

---

### Post by iaculallad on 2008-06-02
> **shotos said:**
> i just did this and here is the result

[COLOR="DarkRed"]kwasi@60-84Kwasi:~/Desktop$ tar xzf vpnclient-linux-4.8.01.0640-k9.tar.gz[/COLOR]

[COLOR="Green"]tar: vpnclient-linux-4.8.01.0640-k9.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
[/COLOR]
the file is located on my desktop......thanks

:confused: Could you issue the command **ls** on your desktop using your terminal and post it.

---

### Post by shotos on 2008-06-02
unfortunately ubuntu is new to me so i don´t really understand what u mean by issuing the command ls and posting it.

after entering ls:
[COLOR="DarkRed"]kwasi@60-84Kwasi:~/Desktop$ ls[/COLOR]

[COLOR="Sienna"]vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz[/COLOR]

now how do i post it?

---

### Post by iaculallad on 2008-06-02
> **shotos said:**
> unfortunately ubuntu is new to me so i don´t really understand what u mean by issuing the command ls and posting it.

after entering ls:
[COLOR="DarkRed"]kwasi@60-84Kwasi:~/Desktop$ ls[/COLOR]

[COLOR="Sienna"]vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz[/COLOR]

now how do i post it?

From the output of ls, it shows that you're "untarring" a wrong filename.
It should be:

cd ~/Desktop
tar xzf vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz

---

### Post by shotos on 2008-06-02
thanks, it worked

---

### Post by braindrive on 2008-06-24
do you have the vpnclient-linux-4.8.01.0640-k9.tar.gz? Will you be able to share that?

---


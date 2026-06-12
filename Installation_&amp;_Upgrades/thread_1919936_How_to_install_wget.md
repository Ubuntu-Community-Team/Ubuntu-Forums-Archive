---
title: "How to install wget?"
date: 2012-02-03
forum: Installation &amp; Upgrades
---

### Post by ryanzlilboy on 2012-02-03
Hi, all! I'm a noob, and I'm trying to install a download manager software called 'Wget'
Can you please tell me how to install it? I already downloaded the file ([http://ftp.gnu.org/gnu/wget/)]("http://ftp.gnu.org/gnu/wget/"),  wget-1.13.tar.gz
I can't install it... Can you teach me step by step?








sorry for grammatical error or something
[]("http://ftp.gnu.org/gnu/wget/")

---

### Post by MG&amp;TL on 2012-02-03
Wget is already installed on ubuntu by default.

Because it is a *command-line application*, you need to open a terminal to use it:

1. Press Ctrl-Alt-T

2. Type the following:

```
wget http://your-url.com/myfile
```

3. Wget will give you updates regarding your download progress as it goes. When it has finished, it will stop scrolling and return to:

```
user@user-computer:~$
```

You can then open your homefolder, the downloaded file will be there.

For more information on the command-line, the most powerful part of any Linux distribution, see [LinuxCommand.org]("LinuxCommand.org")

---

### Post by ryanzlilboy on 2012-02-03
> **MG&TL said:**
> Wget is already installed on ubuntu by default.

Because it is a *command-line application*, you need to open a terminal to use it:

1. Press Ctrl-Alt-T

2. Type the following:

```
wget http://your-url.com/myfile
```3. Wget will give you updates regarding your download progress as it goes. When it has finished, it will stop scrolling and return to:

```
user@user-computer:~$
```You can then open your homefolder, the downloaded file will be there.

For more information on the command-line, the most powerful part of any Linux distribution, see [LinuxCommand.org]("http://LinuxCommand.org")

I already type "wget http:/your=url.com/myfile" but it keep Retrying. and finally  Giving up.

If Wget was installed on ubuntu by default, how do I use it??? :confused:

---

### Post by MG&amp;TL on 2012-02-03
What are you trying to do?

You were meant to replace "http://your-url.com/myfile" with the URL of what you are trying to download. Copy-paste from a web browser. Some people are so literalist. ;)

You already _are_ using wget, it's just not finding anyting because it can't find the URL you gave it. It is *not* a graphical application, if you want a graphical download manager, there are many available in the software centre.

An example:

```
wget ubuntuforums.org
```

downloads a copy of the ubuntu forums homepage.

---

### Post by ryanzlilboy on 2012-02-03
> **MG&TL said:**
> What are you trying to do?

You were meant to replace "http://your-url.com/myfile" with the URL of what you are trying to download. Copy-paste from a web browser. Some people are so literalist. ;)

You already _are_ using wget, it's just not finding anyting because it can't find the URL you gave it. It is *not* a graphical application, if you want a graphical download manager, there are many available in the software centre.

An example:

```
wget ubuntuforums.org
```downloads a copy of the ubuntu forums homepage.


OMG!!! I'm such a NOOB!!! 
I though Wget is an software just like IDM... Sorry to bother you...

Oh, man, this is so embarassing! <- what a poor noob :P

---

### Post by MG&amp;TL on 2012-02-04
Not a problem, I made a similiar mistake once. :)

Have fun with your *buntu.

---

